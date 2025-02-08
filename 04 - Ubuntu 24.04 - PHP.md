
As of **2024-11-22**.
- Added php8.4, imagick.

## PPA

```
sudo add-apt-repository -y ppa:ondrej/php
sudo apt -y update
sudo apt -y upgrade
```

## Install

### 7.4 - EOL November 28 2022

```
sudo apt -y install \
php7.4 php7.4-bcmath php7.4-cli php7.4-common php7.4-curl php7.4-fpm php7.4-gd \
php7.4-imagick php7.4-intl php7.4-json php7.4-mbstring php7.4-mysql \
php7.4-readline php7.4-xml php7.4-zip
```

### 8.3 - EOL December 31 2027

```
sudo apt -y install \
php8.3 php8.3-bcmath php8.3-cli php8.3-common php8.3-curl php8.3-fpm php8.3-gd \
php8.3-imagick php8.3-intl php8.3-mbstring php8.3-mysql \
php8.3-readline php8.3-xml php8.3-zip
```

### 8.4 - EOL December 31 2028

```
sudo apt -y install \
php8.4 php8.4-bcmath php8.4-cli php8.4-common php8.4-curl php8.4-fpm php8.4-gd \
php8.4-imagick php8.4-intl php8.4-mbstring php8.4-mysql \
php8.4-readline php8.4-xml php8.4-zip
```

## PHP Configuration

### 7.4

```
sudo cp /etc/php/7.4/fpm/php.ini /etc/php/7.4/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/7.4/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/7.4/fpm/php.ini
```

### 8.3

```
sudo cp /etc/php/8.3/fpm/php.ini /etc/php/8.3/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/8.3/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/8.3/fpm/php.ini
```

### 8.4

```
sudo cp /etc/php/8.4/fpm/php.ini /etc/php/8.4/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/8.4/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/8.4/fpm/php.ini
```

## PHP - Composer

```
cat << 'EOF' > /root/install-composer.sh
#!/bin/sh

EXPECTED_CHECKSUM="$(wget -q -O - https://composer.github.io/installer.sig)"
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
ACTUAL_CHECKSUM="$(php -r "echo hash_file('sha384', 'composer-setup.php');")"

if [ "$EXPECTED_CHECKSUM" != "$ACTUAL_CHECKSUM" ]
then
>&2 echo 'ERROR: Invalid installer checksum'
  rm composer-setup.php
  exit 1
fi

php composer-setup.php --install-dir=/usr/local/bin --filename=composer --quiet
RESULT=$?
rm composer-setup.php
exit $RESULT
EOF

chmod 755 /root/install-composer.sh
```

```
/root/install-composer.sh
```

```
rm /root/install-composer.sh
```

## Post-Install

**SET THESE VARIABLES FIRST**

```
# Set this variable
NEWUSER=newusername
PHPVER=version
```

Create a user with the no password to just use ssh keys:

```
adduser --disabled-password $NEWUSER
# Ubuntu 22.04+ homedir must be 755
chmod 755 /home/$NEWUSER
```

Create a copy of the `www.conf` php-fpm pool to create a new pool for the user, but add .disabled extension first to not activate:

```
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

Modify the values to the `$NEWUSER` username:

```
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

Append to the end configurations for logging:

```
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

Remove the extension `.disabled` to activate it and restart phpXX-fpm service.

```
sudo systemctl restart php$PHPVER-fpm
```

Create a new apache2 conf to point to the sock file set in the new php-fpm pool:

```
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf
```

Rename the sock file pointed to in the new apache2 conf file:

```
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf
```

Make sure this new apache2 conf file is referenced in VirtualHosts that need it.
