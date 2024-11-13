---
sidebar_position: 3
---

# WSL Intel Graphics

[Configure WSL 2 for GPU Workflows](https://www.intel.com/content/www/us/en/docs/oneapi/installation-guide-linux/2025-0/configure-wsl-2-for-gpu-workflows.html)

```bash
sudo apt install -y gpg-agent wget
```

```bash
wget -qO - https://repositories.intel.com/graphics/intel-graphics.key |
  sudo gpg --dearmor --output /usr/share/keyrings/intel-graphics.gpg
```

```bash
echo 'deb [arch=amd64,i386 signed-by=/usr/share/keyrings/intel-graphics.gpg] https://repositories.intel.com/graphics/ubuntu jammy arc' | \
  sudo tee  /etc/apt/sources.list.d/intel.gpu.jammy.list
```

TIP: Before pasting the command to your console, run sudo ls and enter your password to prevent the commands from being swallowed by the sudo password prompt.

```bash
sudo apt-get install -y \
  intel-opencl-icd intel-level-zero-gpu level-zero \
  intel-media-va-driver-non-free libmfx1 libmfxgen1 libvpl2 \
  libegl-mesa0 libegl1-mesa libegl1-mesa-dev libgbm1 libgl1-mesa-dev libgl1-mesa-dri \
  libglapi-mesa libgles2-mesa-dev libglx-mesa0 libigdgmm12 libxatracker2 mesa-va-drivers \
  mesa-vdpau-drivers mesa-vulkan-drivers va-driver-all
```

## Verify installation

```bash
sudo apt install mesa-utils
```

```bash
glxinfo -B
```

```bash
sudo apt install clinfo
```

```bash
clinfo
```

```bash
sudo apt install vainfo
```

```bash
export LIBVA_DRIVER_NAME=d3d12
export MESA_D3D12_DEFAULT_ADAPTER_NAME=Intel
export MESA_D3D12_DEFAULT_ADAPTER_NAME=NVIDIA
```

```bash
vainfo --display drm --device /dev/dri/card0
```
