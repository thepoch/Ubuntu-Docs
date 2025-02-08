
As of **2024-11-22**.
- Added php8.4, imagick.

## PPA

```
sudo add-apt-repository -y ppa:ondrej/php
sudo apt -y update
sudo apt -y upgrade
```

## Install

```
sudo apt -y install \
php5.6 php5.6-bcmath php5.6-cli php5.6-common php5.6-curl php5.6-fpm php5.6-gd php5.6-imagick php5.6-intl php5.6-json php5.6-mbstring php5.6-mysql php5.6-readline php5.6-xml php5.6-zip
```

```
sudo apt -y install \
php7.0 php7.0-bcmath php7.0-cli php7.0-common php7.0-curl php7.0-fpm php7.0-gd php7.0-imagick php7.0-intl php7.0-json php7.0-mbstring php7.0-mysql php7.0-readline php7.0-xml php7.0-zip \
php7.1 php7.1-bcmath php7.1-cli php7.1-common php7.1-curl php7.1-fpm php7.1-gd php7.1-imagick php7.1-intl php7.1-json php7.1-mbstring php7.1-mysql php7.1-readline php7.1-xml php7.1-zip \
php7.2 php7.2-bcmath php7.2-cli php7.2-common php7.2-curl php7.2-fpm php7.2-gd php7.2-imagick php7.2-intl php7.2-json php7.2-mbstring php7.2-mysql php7.2-readline php7.2-xml php7.2-zip \
php7.3 php7.3-bcmath php7.3-cli php7.3-common php7.3-curl php7.3-fpm php7.3-gd php7.3-imagick php7.3-intl php7.3-json php7.3-mbstring php7.3-mysql php7.3-readline php7.3-xml php7.3-zip \
php7.4 php7.4-bcmath php7.4-cli php7.4-common php7.4-curl php7.4-fpm php7.4-gd php7.4-imagick php7.4-intl php7.4-json php7.4-mbstring php7.4-mysql php7.4-readline php7.4-xml php7.4-zip
```

```
sudo apt -y install \
php8.0 php8.0-bcmath php8.0-cli php8.0-common php8.0-curl php8.0-fpm php8.0-gd php8.0-imagick php8.0-intl php8.0-mbstring php8.0-mysql php8.0-readline php8.0-xml php8.0-zip \
php8.1 php8.1-bcmath php8.1-cli php8.1-common php8.1-curl php8.1-fpm php8.1-gd php8.1-imagick php8.1-intl php8.1-mbstring php8.1-mysql php8.1-readline php8.1-xml php8.1-zip \
php8.2 php8.2-bcmath php8.2-cli php8.2-common php8.2-curl php8.2-fpm php8.2-gd php8.2-imagick php8.2-intl php8.2-mbstring php8.2-mysql php8.2-readline php8.2-xml php8.2-zip \
php8.3 php8.3-bcmath php8.3-cli php8.3-common php8.3-curl php8.3-fpm php8.3-gd php8.3-imagick php8.3-intl php8.3-mbstring php8.3-mysql php8.3-readline php8.3-xml php8.3-zip \
php8.4 php8.4-bcmath php8.4-cli php8.4-common php8.4-curl php8.4-fpm php8.4-gd php8.4-imagick php8.4-intl php8.4-mbstring php8.4-mysql php8.4-readline php8.4-xml php8.4-zip
```

## PHP Configuration

```
sudo cp /etc/php/5.6/fpm/php.ini /etc/php/5.6/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/5.6/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/5.6/fpm/php.ini
```

```
sudo cp /etc/php/7.0/fpm/php.ini /etc/php/7.0/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/7.0/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/7.0/fpm/php.ini

sudo cp /etc/php/7.1/fpm/php.ini /etc/php/7.1/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/7.1/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/7.1/fpm/php.ini

sudo cp /etc/php/7.2/fpm/php.ini /etc/php/7.2/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/7.2/fpm/php.ini

sudo cp /etc/php/7.3/fpm/php.ini /etc/php/7.3/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/7.3/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/7.3/fpm/php.ini

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

```
sudo cp /etc/php/8.0/fpm/php.ini /etc/php/8.0/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/8.0/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/8.0/fpm/php.ini

sudo cp /etc/php/8.1/fpm/php.ini /etc/php/8.1/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/8.1/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/8.1/fpm/php.ini

sudo cp /etc/php/8.2/fpm/php.ini /etc/php/8.2/fpm/php-`date +%Y%m%d-%H%M%S`.ini
sudo sed -i 's/^max_execution_time.*/max_execution_time = 300/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/^max_input_time.*/max_input_time = 600/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/;max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/^max_input_vars.*/max_input_vars = 10000/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/^memory_limit.*/memory_limit = 512M/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/^post_max_size.*/post_max_size = 128M/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/^upload_max_filesize.*/upload_max_filesize = 128M/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/^allow_url_fopen.*/allow_url_fopen = On/g' /etc/php/8.2/fpm/php.ini
sudo sed -i 's/;date.timezone.*/date.timezone = Asia\/Manila/g' /etc/php/8.2/fpm/php.ini

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
```

Create a user with the no password to just use ssh keys:

```
adduser --disabled-password $NEWUSER
# Ubuntu 22.04+ homedir must be 755
chmod 755 /home/$NEWUSER
```

Create a copy of the `www.conf` php-fpm pool to create a new pool for the user, but add .disabled extension first to not activate:

```
PHPVER=5.6
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

```
PHPVER=7.0
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.1
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.2
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.3
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.4
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

```
PHPVER=8.0
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.1
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.2
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.3
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.4
cp /etc/php/$PHPVER/fpm/pool.d/www.conf /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

Modify the values to the `$NEWUSER` username:

```
PHPVER=5.6
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

```
PHPVER=7.0
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.1
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.2
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.3
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.4
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

```
PHPVER=8.0
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.1
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.2
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.3
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.4
sed -i -e "s/; Start a new pool named 'www'./; Start a new pool named '$NEWUSER'./" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/; pool name ('www' here)/; pool name ('$NEWUSER' here)/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/\[www\]/\[$NEWUSER\]/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/^user = www-data/user = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
sed -i -e "s/^group = www-data/group = $NEWUSER/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

sed -i -e "s/listen = \/run\/php\/php$PHPVER-fpm.sock/listen = \/run\/php\/php$PHPVER-fpm-$NEWUSER.sock/" /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

Append to the end configurations for logging:

```
PHPVER=5.6
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

```
PHPVER=7.0
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.1
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.2
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.3
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=7.4
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

```
PHPVER=8.0
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.1
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.2
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.3
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled

PHPVER=8.4
echo "catch_workers_output = yes" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_flag[log_errors] = on" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[error_log] = /home/$NEWUSER/logs/php${PHPVER}_errors.log" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_value[error_reporting] = E_ALL & ~E_NOTICE" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
echo "php_admin_value[disable_functions] = exec,passthru,shell_exec,system" >> /etc/php/$PHPVER/fpm/pool.d/$NEWUSER.conf.disabled
```

Remove the extension `.disabled` to activate it and restart phpXX-fpm service.

```
sudo systemctl restart php5.6-fpm
sudo systemctl restart php7.0-fpm
sudo systemctl restart php7.1-fpm
sudo systemctl restart php7.2-fpm
sudo systemctl restart php7.3-fpm
sudo systemctl restart php7.4-fpm
sudo systemctl restart php8.0-fpm
sudo systemctl restart php8.1-fpm
sudo systemctl restart php8.2-fpm
sudo systemctl restart php8.3-fpm
sudo systemctl restart php8.4-fpm
```

Create a new apache2 conf to point to the sock file set in the new php-fpm pool:

```
PHPVER=5.6
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.0
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.1
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.2
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.3
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.4
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.0
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.1
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.2
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.3
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.4
cp /etc/apache2/conf-available/php$PHPVER-fpm.conf /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf
```

Rename the sock file pointed to in the new apache2 conf file:

```
PHPVER=5.6
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.0
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.1
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.2
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.3
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=7.4
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.0
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.1
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.2
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.3
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf

PHPVER=8.4
sed -i -e "s/fpm\.sock/fpm-$NEWUSER\.sock/" /etc/apache2/conf-available/php$PHPVER-fpm-$NEWUSER.conf
```

Make sure this new apache2 conf file is referenced in VirtualHosts that need it.
