
```
server {
	listen 80;
	listen [::]:80;
	
	# SSL configuration
	
	listen 443 ssl http2;
	listen [::]:443 ssl http2;
	
	ssl_certificate /etc/nginx/ssl/$DOMAIN-cert.pem;
	ssl_certificate_key /etc/nginx/ssl/$DOMAIN-key.pem;
	
	include /etc/nginx/ssl-options-nginx.conf;
	
	root /home/$USERNAME/public_html;
	
	# Add index.php to the list if you are using PHP
	index index.html index.htm index.nginx-debian.html;
	
	server_name $DOMAIN www.$DOMAIN;
	
	location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ =404;
	}
	
	# Force redirect site to https
	if ($scheme != "https") {
		return 301 https://$host$request_uri;
	}
	
	# pass PHP scripts to FastCGI server
	#
	#location ~ \.php$ {
	#	include snippets/fastcgi-php.conf;
	#
	#	# With php-fpm (or other unix sockets):
	#	fastcgi_pass unix:/run/php/php$PHPVER-fpm-$USERNAME.sock;
	#	# With php-cgi (or other tcp sockets):
	#	fastcgi_pass 127.0.0.1:9000;
	#}
	
	# deny access to .htaccess files, if Apache's document root
	# concurs with nginx's one
	#
	#location ~ /\.ht {
	#	deny all;
	#}
}
```
