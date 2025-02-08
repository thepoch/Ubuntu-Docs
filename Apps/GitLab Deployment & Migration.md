# GitLab Deployment & Migration

General steps are:

1. Setup the new server.
2. Install gitlab-ce (Ubuntu): https://about.gitlab.com/install/?version=ce#ubuntu (See below)
3. Create a backup on the current server. (See below)
4. Stop the old server. This avoids it being used.
5. Point domain to new server.
6. From Step 2, run the actual 'apt-get install' command.
7. Restore the backups, configuration, secrets. (See below)

--------------------------------------------------------------------------------
# Install gitlab-ce (Ubuntu)

As of 20211107, the steps below are from https://about.gitlab.com/install/?version=ce#ubuntu .

```
sudo apt-get update
sudo apt-get install -y curl openssh-server ca-certificates tzdata perl
sudo apt-get install -y postfix
curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
```

Best to point the subdomain to the new server then do this:

```
HOSTNAME=hostname
sudo EXTERNAL_URL="https://${HOSTNAME}" apt-get install gitlab-ce
```
--------------------------------------------------------------------------------
# Backup and Restore

1. Create a backup:

```
sudo gitlab-backup create
```

2. Transfer backup (in /var/opt/gitlab/backups/) to new server.
3. Copy /etc/gitlab/gitlab.rb and /etc/gitlab/gitlab-secrets.json to new server.
4. Prepare restoring the backup:

```
sudo mv $TIMESTAMP_$VERSION_gitlab_backup.tar /var/opt/gitlab/backups/
sudo chown git:git /var/opt/gitlab/backups/$TIMESTAMP_$VERSION_gitlab_backup.tar
```

5. Perform the actual restoration:

```
sudo gitlab-ctl stop puma
sudo gitlab-ctl stop sidekiq
sudo gitlab-ctl status

sudo gitlab-backup restore BACKUP=$TIMESTAMP_$VERSION
```

6. Run the last sanity checks:

```
sudo gitlab-ctl reconfigure
sudo gitlab-ctl restart
sudo gitlab-rake gitlab:check SANITIZE=true
sudo gitlab-rake gitlab:doctor:secrets
```

After restoring, probably best to do a reboot of the server.

--------------------------------------------------------------------------------
# Manually renewing Let's Encrypt certificate
```
sudo gitlab-ctl renew-le-certs
```
