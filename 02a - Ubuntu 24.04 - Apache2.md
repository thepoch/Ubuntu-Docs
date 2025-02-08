
As of **2024-05-01**.
24.04: Seems to work.
22.04: Works.
20.04: Probably still works.

## PPA

```
sudo add-apt-repository -y ppa:ondrej/apache2
sudo apt -y update
sudo apt -y upgrade
```

## Install

```
sudo apt -y install apache2
```

```
sudo mkdir /var/log/apache2/apache2-domlogs
sudo mkdir /etc/skel/public_html /etc/skel/public_subdomains /etc/skel/logs
```

## Apache2 Configuration

```
cat << 'EOF' > /etc/apache2/conf-available/000homedir.conf
<Directory /home/*/public_*>
  Options All -Indexes
  AllowOverride All
  Require all granted
</Directory>
EOF

cat << 'EOF' > /etc/apache2/conf-available/000security.conf
<DirectoryMatch "/\.git">
  Require all denied
</DirectoryMatch>

<FilesMatch "/\.gitignore">
  Require all denied
</FilesMatch>

<FilesMatch "/*\.log">
  Require all denied
</FilesMatch>
EOF

cat << 'EOF' > /etc/apache2/mods-available/md.conf
<IfModule mod_md.c>
  <Location /md-status>
    SetHandler md-status
    Require local
    #Require ip 192.0.2.0/24
  </Location>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
EOF

sudo cp /etc/apache2/conf-available/security.conf /etc/apache2/conf-available/security-`date +%Y%m%d-%H%M%S`.conf
sudo sed -i 's/^#ServerSignature Off/ServerSignature Off/g' /etc/apache2/conf-available/security.conf
sudo sed -i 's/^ServerSignature On/#ServerSignature On/g' /etc/apache2/conf-available/security.conf
sudo sed -i 's/^ServerTokens OS/ServerTokens Prod/g' /etc/apache2/conf-available/security.conf

sudo a2enconf 000homedir.conf 000security.conf
sudo a2enmod actions headers http2 macro md proxy_fcgi rewrite ssl

sudo cp /etc/apache2/mods-available/ssl.conf /etc/apache2/mods-available/ssl-`date +%Y%m%d-%H%M%S`.conf
sudo sed -i 's/^SSLProtocol all -SSLv3/#SSLProtocol all -SSLv3/g' /etc/apache2/mods-available/ssl.conf
sudo sed -i 's/^SSLCipherSuite HIGH:!aNULL/#SSLCipherSuite HIGH:!aNULL/g' /etc/apache2/mods-available/ssl.conf

cat << 'EOF' >> /etc/apache2/mods-available/ssl.conf

# Jan 2024 - Modern Configuration
SSLProtocol             all -SSLv3 -TLSv1 -TLSv1.1 -TLSv1.2
SSLHonorCipherOrder     off
SSLSessionTickets       off

# Jan 2024 - Intermediate Configuration
#SSLProtocol             all -SSLv3 -TLSv1 -TLSv1.1
#SSLCipherSuite          ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-CHACHA20-POLY1305
#SSLHonorCipherOrder     off
#SSLSessionTickets       off

SSLUseStapling On
SSLStaplingCache "shmcb:logs/ssl_stapling(32768)"

EOF
```

```
sudo systemctl restart apache2
```

## RemoteIP for Cloudflare

```
cat << 'EOF' > /etc/apache2/conf-available/remoteip.conf
RemoteIPHeader CF-Connecting-IP
RemoteIPTrustedProxy 173.245.48.0/20
RemoteIPTrustedProxy 103.21.244.0/22
RemoteIPTrustedProxy 103.22.200.0/22
RemoteIPTrustedProxy 103.31.4.0/22
RemoteIPTrustedProxy 141.101.64.0/18
RemoteIPTrustedProxy 108.162.192.0/18
RemoteIPTrustedProxy 190.93.240.0/20
RemoteIPTrustedProxy 188.114.96.0/20
RemoteIPTrustedProxy 197.234.240.0/22
RemoteIPTrustedProxy 198.41.128.0/17
RemoteIPTrustedProxy 162.158.0.0/15
RemoteIPTrustedProxy 172.64.0.0/13
RemoteIPTrustedProxy 131.0.72.0/22
RemoteIPTrustedProxy 104.16.0.0/13
RemoteIPTrustedProxy 104.24.0.0/14
RemoteIPTrustedProxy 2400:cb00::/32
RemoteIPTrustedProxy 2606:4700::/32
RemoteIPTrustedProxy 2803:f800::/32
RemoteIPTrustedProxy 2405:b500::/32
RemoteIPTrustedProxy 2405:8100::/32
RemoteIPTrustedProxy 2a06:98c0::/29
RemoteIPTrustedProxy 2c0f:f248::/32
EOF

a2enconf remoteip
a2enmod remoteip
```

## Logrotate

```
cat << 'EOF' > /etc/logrotate.d/apache2-domlogs
/var/log/apache2/apache2-domlogs/*.log {
	daily
	missingok
	rotate 14
	compress
	delaycompress
	notifempty
	create 0644 root root
	sharedscripts
}
EOF
```

## Post-Install

Create a user with the no password to just use ssh keys:

```
# Set this variable
NEWUSER=newusername
```

```
adduser --disabled-password $NEWUSER
# Ubuntu 22.04+ homedir must be 755
chmod 755 /home/$NEWUSER
```
