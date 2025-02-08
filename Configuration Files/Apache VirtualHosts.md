
## Non-SSL VirtualHost

```
<VirtualHost *:80>
	ServerName $DOMAIN
#	ServerAlias www.$DOMAIN
	ServerAdmin webmaster@$DOMAIN
	DocumentRoot /home/$USERNAME/public_html
	
	RemoteIPHeader CF-Connecting-IP
	
	ErrorLog ${APACHE_LOG_DIR}/apache2-domlogs/$DOMAIN-error.log
	CustomLog ${APACHE_LOG_DIR}/apache2-domlogs/$DOMAIN-access.log combined
	
	Include conf-available/php$PHPVER-fpm-$USERNAME.conf
</VirtualHost>
```

Variables:
* $DOMAIN - domain name used.
* $USERNAME - username where docroot is stored. Also what php-fpm file is used.
* $PHPVER - php version used.
## SSL VirtualHost

```
<VirtualHost *:80>
	ServerName $DOMAIN
#	ServerAlias www.$DOMAIN
	
	RewriteEngine on
# If there are additional subdomains, add here and end with [OR]
	RewriteCond %{SERVER_NAME} =$DOMAIN
	RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

<VirtualHost *:443>
	ServerName $DOMAIN
#	ServerAlias www.$DOMAIN
	ServerAdmin webmaster@$DOMAIN
	DocumentRoot /home/$USERNAME/public_html
	
	RemoteIPHeader CF-Connecting-IP
	
	ErrorLog ${APACHE_LOG_DIR}/apache2-domlogs/$DOMAIN-ssl-error.log
	CustomLog ${APACHE_LOG_DIR}/apache2-domlogs/$DOMAIN-ssl-access.log combined
	
	SSLEngine on
	Protocols h2 h2c http/1.1
	
	Include conf-available/php$PHPVER-fpm-$USERNAME.conf
	
	SSLCertificateFile "/etc/apache2/ssl/$DOMAIN-fullchain.pem"
	SSLCertificateKeyFile "/etc/apache2/ssl/$DOMAIN-key.pem"
	
	Header set X-Frame-Options "SAMEORIGIN"
	Header set X-Content-Type-Options "nosniff"
	Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"
#	Header set Referrer-Policy "same-origin"
	Header set Referrer-Policy "strict-origin-when-cross-origin"
	
#	Header set Content-Security-Policy "upgrade-insecure-requests"
#	Header set Content-Security-Policy-Report-Only ""
</VirtualHost>
```

Variables:
* $DOMAIN - domain name used.
* $USERNAME - username where docroot is stored. Also what php-fpm file is used.
* $PHPVER - php version used.
