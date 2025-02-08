
## Install

```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
php wp-cli.phar --info
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```
## Update

```
sudo wp cli update
```
## Basic useful commands

WordPress Core:

```
wp core update
wp core verify-checksums
```

Plugins and Themes:

```
wp plugin list
wp plugin update --all
wp plugin verify-checksums --all
wp theme list
wp theme update --all
```

Users:

```
wp user list
```
