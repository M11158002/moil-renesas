---
sidebar_position: 2
---

# Environment

Ubuntu
Docker

## General

change the apt source to the fastest mirror

```bash title="One-Line-Style format >= 22.04"
sudo sed -i 's@//.*archive.ubuntu.com@//mirror.twds.com.tw@g' /etc/apt/sources.list
```

```bash title="DEB822 format <= 24.04"
sudo sed -i 's@//.*archive.ubuntu.com@//mirror.twds.com.tw@g' /etc/apt/sources.list.d/ubuntu.sources
```

```bash "One-Line-Style format change http to https >= 22.04"
sudo sed -i 's/http:/https:/g' /etc/apt/sources.list
```

```bash "DEB822 format change http to https <= 24.04"
sudo sed -i 's/http:/https:/g' /etc/apt/sources.list.d/ubuntu.sources
```

```bash title="update apt source"
sudo apt update
```

## Docker

[Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
[Linux post-installation steps for Docker Engine](https://docs.docker.com/engine/install/linux-postinstall/)

```bash title="Add Docker's official GPG key:"
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

```bash title="Add the repository to Apt sources:"
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
```

```bash title="Install the Docker packages"
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Post-Installation steps for Docker Engine

1. Create the docker group

    ```bash
    sudo groupadd docker
    ```

2. Add your user to the docker group

    ```bash
    sudo usermod -aG docker $USER
    ```

3. Log out and log back in so that your group membership is re-evaluated.

    you can also run the following command to activate the changes to groups:

    ```bash
    newgrp docker
    ```

4. Verify that you can run docker commands without sudo

    ```bash
    docker run hello-world
    ```

## RZ/G2L-EVKIT

## RZ/G2UL-EVKIT

## RZ/V2H-EVK
