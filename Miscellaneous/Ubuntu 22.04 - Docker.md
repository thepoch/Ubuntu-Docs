
As of **2024-02-21** untested on Ubuntu 22.04.
Probably still works on Ubuntu 20.04. Hopefully works on Ubuntu 24.04.
## Reference

https://docs.docker.com/engine/install/ubuntu/

## Uninstall any conflicting packages


```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

## Add the Docker repository and install


```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Verify Docker Engine is installed

```
sudo docker run hello-world
```

This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

## Add the user to the docker group

Create the docker group:

```
sudo groupadd docker
```

Add user to the docker group:

```
sudo usermod -aG docker $USER
```

Log out and back in. Verify you can run docker with sudo:

```
docker run hello-world
```

## To automatically start on boot

```
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

## Configure default logging driver

***TODO***

Docker provides [logging drivers](https://docs.docker.com/config/containers/logging/) for collecting and viewing log data from all containers running on a host. The default logging driver, `json-file`, writes log data to JSON-formatted files on the host filesystem. Over time, these log files expand in size, leading to potential exhaustion of disk resources.

To avoid issues with overusing disk for log data, consider one of the following options:

- Configure the `json-file` logging driver to turn on [log rotation](https://docs.docker.com/config/containers/logging/json-file/).
- Use an [alternative logging driver](https://docs.docker.com/config/containers/logging/configure/#configure-the-default-logging-driver) such as the ["local" logging driver](https://docs.docker.com/config/containers/logging/local/) that performs log rotation by default.
- Use a logging driver that sends logs to a remote logging aggregator.
