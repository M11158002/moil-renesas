# README

## Install SDK Manager

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/[distro]/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update
sudo apt-get -y install sdkmanager
```

> Replace the highlighted distro with the one that you are using. Supported distros are: ubuntu1804, ubuntu2004, ubuntu2204

## Launch SDK Manager

```bash
sdkmanager
```

* For older SDK versions run: sdkmanager --archived-versions
