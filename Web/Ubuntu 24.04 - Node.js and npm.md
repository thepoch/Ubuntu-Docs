
As of **2024-05-01**.
24.04: Seems to work.
22.04: Works.
20.04: Probably still works.

| Version | EOL Date       |
| ------- | -------------- |
| 18      | April 30, 2025 |
| 20      | April 30, 2026 |
| 22      | April 30, 2027 |
# Install

Reference: https://github.com/nodesource/distributions/blob/master/README.md

For whatever the latest LTS version is:

```
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```

For specific versions:

Node.js v20:

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```

Node.js v18:

```
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
```
