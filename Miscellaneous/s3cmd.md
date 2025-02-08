
```
sudo apt install s3cmd
```

```
s3cmd --configure
```

| Option | Setting/Parameter |
| ---- | ---- |
| Access Key: |  |
| Secret Key: |  |
| Default Region: | SG |
| S3 Endpoint: | ap-south-1.linodeobjects.com |
| DNS-style: | %(bucket)s.ap-south-1.linodeobjects.com |
| Encryption password: | YOUR_GPG_KEY |
| Path to GPG program: | /usr/local/bin/gpg |
| Use HTTPS protocol: | Yes |
| HTTP Proxy server name: |  |
| HTTP Proxy server port: | 0 |

## Edit the generated .s3cfg
 
```
nano ~/.s3cfg
```

```
host_base = ap-south-1.linodeobjects.com
host_bucket = %(bucket)s.ap-south-1.linodeobjects.com
website_endpoint = http://%(bucket)s.website-ap-south-1.linodeobjects.com/
```


## To sync/backup

```
/usr/bin/s3cmd sync SOURCE s3://BUCKET/directory/
```

Or put in crontab:

```
# Backup to Linode Object Storage - 20201201
00 05 * * * /usr/bin/s3cmd sync --delete-removed --delete-after /home/mysql-backup/mysql-backup/ s3://BUCKET/SUBDIR_IF_NEEDED/
```
