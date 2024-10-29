---
sidebar_position: 1
---

# 3.1 Installation

## Driver Installation

in `Alder Lake-N` architecture the driver is'nt available in the official repository, so you need to install it manually.

[hardware-table](https://dgpu-docs.intel.com/devices/hardware-table.html)

Get device ID

```bash
lspci -nn |grep  -Ei 'VGA|DISPLAY'
```

Example output:

```bash
# Alder Lake-N (N200)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:46d0]
# Tiger Lake (i5-1135G7)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:9A49]
```

| PCI IDs | Name | Architecture | Codename | Kernel | EU number |
|---|---|---|---|---|---|
| 46D0 | Intel® UHD Graphics | Xe | Alder Lake-N | 6.8* | 32 |
| 9A49 | Intel® Iris® Xe Graphics | Xe | Tiger Lake | 5.10 | 80 |

* This driver requires the force-probe kernel parameter.

[Intel® Processor N200](https://www.intel.com/content/www/us/en/products/sku/231804/intel-processor-n200-6m-cache-up-to-3-70-ghz/specifications.html)  
[Intel® Core™ i5-1135G7 Processor](https://www.intel.com/content/www/us/en/products/sku/208658/intel-core-i51135g7-processor-8m-cache-up-to-4-20-ghz/specifications.html)

### Install the Intel Graphics Driver

Install the Intel graphics GPG public key

```bash
wget -qO - https://repositories.intel.com/gpu/intel-graphics.key | sudo gpg --yes --dearmor --output /usr/share/keyrings/intel-graphics.gpg
```

Configure the repositories.intel.com package repository

```bash
echo "deb [arch=amd64,i386 signed-by=/usr/share/keyrings/intel-graphics.gpg] https://repositories.intel.com/gpu/ubuntu jammy client" | sudo tee /etc/apt/sources.list.d/intel-gpu-jammy.list
```

Update the package repository meta-data

```bash
sudo apt update
```

Install packages responsible for computing and media runtimes.

```bash
sudo apt install intel-media-va-driver-non-free libmfx1 libmfxgen1 libvpl2 libegl-mesa0 libegl1-mesa libegl1-mesa-dev libgbm1 libgl1-mesa-dev libgl1-mesa-dri libglapi-mesa libgles2-mesa-dev libglx-mesa0 libigdgmm12 libxatracker2 mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers va-driver-all
```

## Utility Tools Installation

V4L2 Utility Tools Installation

```bash
sudo apt install qv4l2 v4l-utils
```

Hardware Information Tools Installation

```bash
sudo apt install hwinfo vainfo mesa-utils
```

## Development Package Installation

Git Installation

```bash
sudo apt install git git-lfs
```

Build Tools Installation

```bash
sudo apt install make cmake meson ninja-build pkg-config build-essential
```

GStreamer Installation

```bash
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-vaapi gstreamer1.0-libav gstreamer1.0-rtsp libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-good1.0-dev libgstreamer-plugins-bad1.0-dev
```
