
As of **2024-02-07**.

| Version | EOL Date |
| ---- | ---- |
| 12 | November 14, 2024 |
| 13 | November 13, 2025 |
| 14 | November 12, 2026 |
| 15 | November 11, 2027 |
| 16 | November 9, 2028 |

## Reference

https://www.postgresql.org/download/linux/ubuntu/

## Install

```
sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
```

```
sudo apt-get -y install postgresql
```

### Configure

#### Optional

## Post-Installation

### Database Commands
