# Ubuntu 20.04 - vaultwarden

## Docker

Follow the guide to install docker, docker-compose.
## Create the storage directory

	mkdir /vaultwarden-data/
## Use docker-compose

See here for configuration:

**Reference:** https://github.com/dani-garcia/vaultwarden/wiki/Using-Docker-Compose

I've set up the following custom configurations:

	environment:
	- ADMIN_TOKEN= SECRET...
	- WEBSOCKET_ENABLED=true
	- SIGNUPS_ALLOWED=false
	- SIGNUPS_DOMAINS_WHITELIST=hostname
	- INVITATIONS_ALLOWED=false
	- LOG_FILE=/data/vaultwarden.log
	- LOG_LEVEL=info
	#      - EXTENDED_LOGGING=true
	volumes:
	- /vaultwarden-data:/data
	- /etc/timezone:/etc/timezone:ro
	- /etc/localtime:/etc/localtime:ro

The timezone thing above is required for fail2ban to actually work with the log file.

Then run the following to bring up the things:

	docker-compose up -d

## To remove everything using docker-compose

	docker-compose down

## To enable vaultwarden HTTPS

	The above docker-compose setup enables HTTPS by default via Caddy.

## To update vaultwarden image

	docker pull vaultwarden/server:latest
	
	docker-compose stop
	docker-compose pull
	docker-compose start

## To backup vaultwarden data

Reference: https://github.com/dani-garcia/vaultwarden/wiki/Backing-up-your-vault

	sudo apt -y install sqlite3

Just backup the following:

1. The docker-compose.yml
2. The Caddyfile
3. /vaultwarden-data/ directory, or more properly:

	a. /usr/bin/sqlite3 /vaultwarden-data/db.sqlite3 ".backup '/root/backups/db-$(date '+%Y%m%d-%H%M').sqlite3'"
		- if running in crontab, escape the %. Basically \%.
	b. attachments directory.
	c. config.json file.
	d. rsa_key* files.

## Post Install configuration via /admin

Go to /admin and configure there.

	a. Domain URL : https://HOSTNAME
	b. Per-user attachment storage limit : 102400
	c. Per-organization attachment storage limit : 102400
	d. Trash auto-delete days : 60
	e. Invitation organization name : VaultWardenOrg

Yubikey settings

	Enabled : uncheck

SMTP Email SEttings

	a. Enabled : check
	b. Host : smtp-relay.gmail.com
	c. From Address : noreply@localhost
	d. From Name : VaultWardenOrg

Email 2FA Settings

	a. Enabled : check

## fail2ban

https://github.com/dani-garcia/vaultwarden/wiki/Fail2Ban-Setup

Make sure logging is enabled. This will not work for IPv6 connections.

	sudo apt -y install fail2ban

Create a /etc/fail2ban/filter.d/vaultwarden.local :

	cat << 'EOF' > /etc/fail2ban/filter.d/vaultwarden.local
	[INCLUDES]
	before = common.conf
	
	[Definition]
	failregex = ^.*Username or password is incorrect\. Try again\. IP: <ADDR>\. Username:.*$
	ignoreregex =
	EOF

Create a /etc/fail2ban/jail.d/vaultwarden.local :

	cat << 'EOF' > /etc/fail2ban/jail.d/vaultwarden.local
	[vaultwarden]
	enabled = true
	port = 80,443,8081
	filter = vaultwarden
	#banaction = %(banaction_allports)s
	logpath = /vaultwarden-data/vaultwarden.log
	maxretry = 3
	bantime = 14400
	findtime = 14400
	
	action = iptables-allports[name=vaultwarden, chain=FORWARD]
	EOF

For Admin:

Create a /etc/fail2ban/filter.d/vaultwarden-admin.local :

	cat << 'EOF' > /etc/fail2ban/filter.d/vaultwarden-admin.local
	[INCLUDES]
	before = common.conf
	
	[Definition]
	failregex = ^.*Invalid admin token\. IP: <ADDR>.*$
	ignoreregex =
	EOF

Create a /etc/fail2ban/jail.d/vaultwarden-admin.local :

	cat << 'EOF' > /etc/fail2ban/jail.d/vaultwarden-admin.local
	[vaultwarden-admin]
	enabled = true
	port = 80,443
	filter = vaultwarden-admin
	#banaction = %(banaction_allports)s
	logpath = /vaultwarden-data/vaultwarden.log
	maxretry = 3
	bantime = 14400
	findtime = 14400
	
	action = iptables-allports[name=vaultwarden-admin, chain=FORWARD]
	EOF

    sudo systemctl reload fail2ban

## Email sending

Using Google Workspace for this: https://support.google.com/a/answer/176600?hl=en

GW > Apps > Google Workspace > Gmail > Routing > SMTP relay service
