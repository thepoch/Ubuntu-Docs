
As of **2024-02-01**.
Probably still works on Ubuntu 20.04. Hopefully works on Ubuntu 24.04.

## Install nginx

```
sudo apt update
sudo apt install nginx
```
## nginx Configuration

Edit /etc/nginx/nginx.conf and uncomment "server_tokens off;"
## Template Site Configuration

```
server {
	listen 80;
	listen [::]:80;
	
	server_name $DOMAIN;
	
	root $PATH_TO_SITE;
	index index.html index.htm;
	
	access_log /var/log/nginx/$DOMAIN-access.log;
	error_log /var/log/nginx/$DOMAIN-error.log;
	
	location / {
		try_files $uri $uri/ =404;
		# proxy_pass http://127.0.0.1:8080; # Reverse Proxy
	}
	
	# deny access to .htaccess files.
	location ~ /\.ht {
		deny all;
	}
	
	# deny access to .git files.
	location ~ /\.git {
		deny all;
	}
	
	listen 443 ssl http2;
	listen [::]:443 ssl http2;
	
	#	ssl_certificate /etc/nginx/ssl/$DOMAIN-cert.pem;
	#	ssl_certificate_key /etc/nginx/ssl/$DOMAIN-key.pem;
	
	include /etc/nginx/ssl-options-nginx.conf;
	
	# Force redirect site to https
	#	if ($scheme != "https") {
	#		return 301 https://$host$request_uri;
	#	}
	
	add_header Strict-Transport-Security "max-age=172800;" always;
	add_header Content-Security-Policy "upgrade-insecure-requests;";
}
```
## Other configurations

SSL Configuration:

```
cat << 'EOF' > /etc/nginx/ssl-options-nginx.conf
ssl_session_timeout 1d;
ssl_session_cache shared:MozSSL:10m;  # about 40000 sessions
ssl_session_tickets off;

# Jan 2024 - Modern Configuration
ssl_protocols TLSv1.3;
ssl_prefer_server_ciphers off;

# Jan 2024 - Intermediate Configuration
#ssl_protocols TLSv1.2 TLSv1.3;
#ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-CHACHA20-POLY1305;
#ssl_prefer_server_ciphers off;

# OCSP stapling
ssl_stapling on;
ssl_stapling_verify on;
EOF
```


## TODO

php-fpm doesn't work. Or equivalent of .htaccess in nginx to make Laravel work.
