
As of **2024-05-01**.
24.04: Seems to work.
22.04: Works.
20.04: Probably still works.

## Reference

https://github.com/acmesh-official/acme.sh

---
## Install

```
sudo apt -y install socat
```

```
# SET THE EMAIL Variable.
EMAIL=me@localhost
curl https://get.acme.sh | sh -s email=$EMAIL
```

Close the current terminal and reopen it to make the alias take effect.

### Change to Let's Encrypt by default

```
acme.sh --set-default-ca --server letsencrypt
```

---
## Commands
### Issue a certificate

```
ACMEDOMAIN=DOMAINHERE
```

```
acme.sh --issue -d $ACMEDOMAIN -w $WWWPATH
```

```
Example:
acme.sh --issue -d example.com -d www.example.com -w /home/example/public_html
```
### Issue a wildcard certificate using Cloudflare DNS

* While section says "Wildcard Certificate", it also works with normal certificates as a way of verification.
#### In Cloudflare

Get an API Token at https://dash.cloudflare.com/profile/api-tokens

Create a Custom Token with these settings:

| Parameter | Setting |
| ---- | ---- |
| Permissions | Zone - DNS - Edit |
| Zone Resources | Include - Specific Zone - <YOUR_ZONE_NAME> |
| IP Address Filtering | optional |
| TTL | optional |
Then, export the variables:

```
export CF_Token="TOKEN_HERE"           # From the one generated above.
export CF_Account_ID="ACCOUNT_ID_HERE" # Get this from the zone's page.
export CF_Zone_ID="ZONE_ID_HERE"       # Get this from the zone's page.
```

Then:

```
acme.sh --issue --dns dns_cf -d $ACMEDOMAIN -d *.$ACMEDOMAIN
```

---
### Install the certificate

Set this variable so the commands below work easily.

```
ACMEDOMAIN=DOMAINHERE
```
#### Apache

```
mkdir /etc/apache2/ssl/
```

```
acme.sh --install-cert -d $ACMEDOMAIN \
--cert-file      /etc/apache2/ssl/$ACMEDOMAIN-cert.pem \
--key-file       /etc/apache2/ssl/$ACMEDOMAIN-key.pem  \
--fullchain-file /etc/apache2/ssl/$ACMEDOMAIN-fullchain.pem \
--reloadcmd     "sudo systemctl force-reload apache2"
```
#### nginx

```
mkdir /etc/nginx/ssl/
```

```
acme.sh --install-cert -d $ACMEDOMAIN \
--key-file       /etc/nginx/ssl/$ACMEDOMAIN-key.pem  \
--fullchain-file /etc/nginx/ssl/$ACMEDOMAIN-fullchain.pem \
--reloadcmd     "sudo systemctl force-reload nginx"
```

---
#### Point to the certificate files
##### Apache

```
SSLEngine on
SSLCertificateFile "/etc/apache2/ssl/$DOMAIN-fullchain.pem"
SSLCertificateKeyFile "/etc/apache2/ssl/$DOMAIN-key.pem"
```

```
# Force redirect site to https
RewriteEngine on
RewriteCond %{SERVER_NAME} =$DOMAIN [OR]
RewriteCond %{SERVER_NAME} =www.$DOMAIN
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
```
##### nginx

```
ssl_certificate /etc/nginx/ssl/$DOMAIN-fullchain.pem;
ssl_certificate_key /etc/nginx/ssl/$DOMAIN-key.pem;
```

```
# Force redirect site to https
if ($scheme != "https") {
	return 301 https://$host$request_uri;
}
```

---
## Additional

Generate ECC certificates using the parameter:

```
--keylength ec-256
```
## Maintenance

### Manual certificate renewal

```
acme.sh --renew -d $ACMEDOMAIN --force [--ecc]
```
#### Remove certificate and stop renewal

```
acme.sh --remove -d $ACMEDOMAIN [--ecc]
```
### Upgrade acme.sh

To upgrade:

```
acme.sh --upgrade
```

To enable auto-upgrade:

```
acme.sh --upgrade --auto-upgrade
```

To disable auto-upgrade:

```
acme.sh --upgrade --auto-upgrade 0
```
