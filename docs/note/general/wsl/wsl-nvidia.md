---
sidebar_position: 4
---

# WSL NVIDIA Graphics

[CUDA on WSL User Guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html)

[CUDA Toolkit 12.6 Update 2 Downloads](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local)

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-6
```

```bash
nvidia-smi
```
