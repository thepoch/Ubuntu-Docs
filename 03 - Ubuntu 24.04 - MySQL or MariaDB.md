
As of **2024-05-01**.
24.04: Seems to work. MariaDB untested and not updated.
22.04: Works.
20.04: Probably still works.

## MySQL - Use version 8 from Ubuntu repositories
### Install MySQL

```
sudo apt -y update
sudo apt -y install mysql-server mysql-client mysqltuner
```
### Configure MySQL

```
cat << 'EOF' > /etc/mysql/mysql.conf.d/slow_query_log.cnf
[mysqld]
slow_query_log      = 1
slow_query_log_file = /var/log/mysql/mysql-slow.log
EOF

cat << 'EOF' > /etc/mysql/mysql.conf.d/utf8mb4.cnf
[client]
default-character-set = utf8mb4

[mysqld]
character-set-server  = utf8mb4
collation-server      = utf8mb4_general_ci
character_set_server  = utf8mb4
collation_server      = utf8mb4_general_ci
EOF
```
#### Optional

```
cat << 'EOF' > /etc/mysql/mysql.conf.d/disable_unix_socket.cnf
[mysqld]
#unix_socket=OFF
EOF

cat << 'EOF' > /etc/mysql/mysql.conf.d/allowremote.cnf
[mysqld]
#bind-address = 0.0.0.0
EOF
```

---
## MariaDB - 10.11 LTS - EOL February 2028

**NOTE: These repository entries are for jammy (22.04).**
### PPA

```
# MariaDB 10.11 repository list - created 2024-02-01 09:30 UTC
# https://mariadb.org/download/
# deb.mariadb.org is a dynamic mirror if your preferred mirror goes offline. See https://mariadb.org/mirrorbits/ for details.
# deb [signed-by=/etc/apt/keyrings/mariadb-keyring.pgp] https://deb.mariadb.org/10.11/ubuntu jammy main
deb [signed-by=/etc/apt/keyrings/mariadb-keyring.pgp] https://download.nus.edu.sg/mirror/mariadb/repo/10.11/ubuntu jammy main
# deb-src [signed-by=/etc/apt/keyrings/mariadb-keyring.pgp] https://download.nus.edu.sg/mirror/mariadb/repo/10.11/ubuntu jammy main
```
### Install MariaDB

```
sudo apt -y update
sudo apt -y install mariadb-server mariadb-client mysqltuner
```

---
## MariaDB - 10.6 LTS - EOL July 2026
### PPA

```
# MariaDB 10.6 repository list - created 2024-02-01 09:28 UTC
# https://mariadb.org/download/
# deb.mariadb.org is a dynamic mirror if your preferred mirror goes offline. See https://mariadb.org/mirrorbits/ for details.
# deb [signed-by=/etc/apt/keyrings/mariadb-keyring.pgp] https://deb.mariadb.org/10.6/ubuntu jammy main
deb [signed-by=/etc/apt/keyrings/mariadb-keyring.pgp] https://download.nus.edu.sg/mirror/mariadb/repo/10.6/ubuntu jammy main
# deb-src [signed-by=/etc/apt/keyrings/mariadb-keyring.pgp] https://download.nus.edu.sg/mirror/mariadb/repo/10.6/ubuntu jammy main
```
### Install MariaDB

```
sudo apt -y update
sudo apt -y install mariadb-server mariadb-client mysqltuner
```

---
## Configure MariaDB

```
cat << 'EOF' > /etc/mysql/mariadb.conf.d/slow_query_log.cnf
[mysqld]
slow_query_log      = 1
slow_query_log_file = /var/log/mysql/mysql-slow.log
EOF

cat << 'EOF' > /etc/mysql/mariadb.conf.d/utf8mb4.cnf
[client]
default-character-set = utf8mb4

[mysqld]
character-set-server  = utf8mb4
collation-server      = utf8mb4_general_ci
character_set_server  = utf8mb4
collation_server      = utf8mb4_general_ci
EOF
```
### Optional

```
cat << 'EOF' > /etc/mysql/mariadb.conf.d/disable_unix_socket.cnf
[mysqld]
#unix_socket=OFF
EOF

cat << 'EOF' > /etc/mysql/mariadb.conf.d/allowremote.cnf
[mysqld]
#bind-address = 0.0.0.0
EOF
```

---
## Post-Installation

Usual Post-Installation tasks are:

- [ ] Create databases.
- [ ] Create users
- [ ] Grant privileges to the database for the user.
- [ ] Setup database backups.
