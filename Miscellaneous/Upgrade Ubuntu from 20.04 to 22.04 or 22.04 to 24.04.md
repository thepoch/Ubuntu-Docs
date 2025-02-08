
**2024-03-03** - Tested upgrade from 20.04 to 22.04.
**2024-08-30** - Tested upgrade from 22.04 to 24.04.

Some notes from: https://askubuntu.com/a/1302428
## 20.04 to 22.04, 22.04 to 24.04

Open the failsafe ssh on port 1022:

```
sudo ufw allow 1022/tcp comment 'Open port ssh tcp port 1022 as failsafe option for upgrades'
```

Fully update the current OS (reboot if necessary):

```
sudo apt update
sudo apt -y upgrade
```

```
reboot
```

Do the upgrade (reboot after):

```
RELEASE_UPGRADER_ALLOW_THIRD_PARTY=1 do-release-upgrade
```

```
reboot
```

Make sure everything is fully updated, probably enable or fix 3rd-party repos:

```
sudo apt --fix-broken -y install
sudo apt -y autoremove --purge
sudo apt update
sudo apt -y dist-upgrade
```

Close the failsafe ssh on port 1022:

```
sudo ufw delete allow 1022/tcp
```

Find any stray configuration files or new ones:

```
find /etc/ -iname "*.dpkg-*"
find /etc/ -iname "*.ucf-dist"
find /etc/ -iname "*.distUpgrade" # Mostly in /etc/apt/
```

-----

**Note:**

* Upgrading from 20.04 to 22.04 upgrades to MariaDB 10.6.
* Upgrading from 20.04 to 22.04 upgrades to MariaDB 10.11.

Reinstall PPA, clean up old MariaDB:

```
sudo add-apt-repository -y ppa:ondrej/apache2
sudo add-apt-repository -y ppa:ondrej/php

sudo apt remove --purge mariadb-client-10.5 mariadb-client-10.6 mariadb-server-10.5 mariadb-server-10.6 && sudo apt install --reinstall mariadb-client mariadb-server
```