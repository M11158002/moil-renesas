---
sidebar_position: 1
---
# 2.1 x86 Platform

## 2.1.1 Hardware Requirements

[Intel® Processor N200](https://www.intel.com/content/www/us/en/products/sku/231804/intel-processor-n200-6m-cache-up-to-3-70-ghz/specifications.html)  
[Intel® Core™ i5-1135G7 Processor](https://www.intel.com/content/www/us/en/products/sku/208658/intel-core-i51135g7-processor-8m-cache-up-to-4-20-ghz/specifications.html)

## 2.1.2 Software Requirements

- Ubuntu 22.04.5 LTS
- Mesa 24.3.0
- OpenGL 4.6
- VA-API 1.22 (libva 2.22.0)
- GStreamer 1.20.3

## 2.1.3 Dependencies Installation

### Intel Graphics Driver

Install the Intel graphics GPG public key

```bash
wget -qO - https://repositories.intel.com/gpu/intel-graphics.key | sudo gpg --yes --dearmor --output /usr/share/keyrings/intel-graphics.gpg
```

Configure the repositories.intel.com package repository

```bash
echo "deb [arch=amd64,i386 signed-by=/usr/share/keyrings/intel-graphics.gpg] https://repositories.intel.com/gpu/ubuntu jammy client" | sudo tee /etc/apt/sources.list.d/intel-gpu-jammy.list
```

Update the package list

```bash
sudo apt update
```

Install packages responsible for computing and media runtimes.

```bash
sudo apt install intel-opencl-icd intel-level-zero-gpu level-zero intel-media-va-driver-non-free libmfx1 libmfxgen1 libvpl2 libegl-mesa0 libegl1-mesa libegl1-mesa-dev libgbm1 libgl1-mesa-dev libgl1-mesa-dri libglapi-mesa libgles2-mesa-dev libglx-mesa0 libigdgmm12 libxatracker2 mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers va-driver-all vainfo hwinfo clinfo mesa-utils
```

### Git & Git LFS

```bash
sudo apt install curl
sudo add-apt-repository ppa:git-core/ppa
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
sudo apt update
sudo apt install git git-lfs
```

### v4l2 tools (Camera)

```bash
sudo apt install qv4l2 v4l-utils
```

## 2.1.4 Environment Setup

If use SSH to connect to the x86 platform, you need to set the DISPLAY environment variable.

```bash
export DISPLAY=:0
# or
export DISPLAY=:1
```

Check the display number by running the following command:

```bash
for n in 0 1 2; do
    export DISPLAY=:$n
    xdpyinfo >/dev/null 2>&1 && echo "Display :$n is available"
done
```

Configure the Git

```bash
git config --global credential.helper cache
git config --global user.name "Your Name"
git config --global user.email "Your Email"
```

## 2.1.5 Check the Hardware Information

```bash title="lspci | grep VGA"
00:02.0 VGA compatible controller: Intel Corporation Device 46d0
```

```bash title="hwinfo --display"
23: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.386]
  Unique ID: _Znp.YSIRXdwBRv1
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Device Name: "Onboard - Video"
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x46d0
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd. [MSI]"
  SubDevice: pci 0xb0a9
  Driver: "i915"
  Driver Modules: "i915"
  Memory Range: 0x6000000000-0x6000ffffff (rw,non-prefetchable)
  Memory Range: 0x4000000000-0x400fffffff (ro,non-prefetchable)
  I/O Ports: 0x5000-0x503f (rw)
  Memory Range: 0x000c0000-0x000dffff (rw,non-prefetchable,disabled)
  IRQ: 151 (1150 events)
  Module Alias: "pci:v00008086d000046D0sv00001462sd0000B0A9bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Driver Info #1:
    Driver Status: xe is active
    Driver Activation Cmd: "modprobe xe"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #23
```

```bash title="glxinfo -B"
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel (0x8086)
    Device: Mesa Intel(R) Graphics (ADL-N) (0x46d0)
    Version: 24.3.0
    Accelerated: yes
    Video memory: 7886MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) Graphics (ADL-N)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 24.3.0-devel (git-9fc8668b66)
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 24.3.0-devel (git-9fc8668b66)
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 24.3.0-devel (git-9fc8668b66)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
```

```bash title="vainfo"
Trying display: wayland
libva info: VA-API version 1.22.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_22
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.22 (libva 2.22.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 24.3.3 ()
vainfo: Supported profile and entrypoints
      VAProfileNone                   : VAEntrypointVideoProc
      VAProfileNone                   : VAEntrypointStats
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Simple            : VAEntrypointEncSlice
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointEncSlice
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointEncSlice
      VAProfileH264Main               : VAEntrypointFEI
      VAProfileH264Main               : VAEntrypointEncSliceLP
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointEncSlice
      VAProfileH264High               : VAEntrypointFEI
      VAProfileH264High               : VAEntrypointEncSliceLP
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline: VAEntrypointFEI
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointEncSlice
      VAProfileHEVCMain               : VAEntrypointFEI
      VAProfileHEVCMain               : VAEntrypointEncSliceLP
      VAProfileHEVCMain10             : VAEntrypointVLD
      VAProfileHEVCMain10             : VAEntrypointEncSlice
      VAProfileHEVCMain10             : VAEntrypointEncSliceLP
      VAProfileVP9Profile0            : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointEncSliceLP
      VAProfileVP9Profile1            : VAEntrypointVLD
      VAProfileVP9Profile1            : VAEntrypointEncSliceLP
      VAProfileVP9Profile2            : VAEntrypointVLD
      VAProfileVP9Profile2            : VAEntrypointEncSliceLP
      VAProfileVP9Profile3            : VAEntrypointVLD
      VAProfileVP9Profile3            : VAEntrypointEncSliceLP
      VAProfileHEVCMain12             : VAEntrypointVLD
      VAProfileHEVCMain12             : VAEntrypointEncSlice
      VAProfileHEVCMain422_10         : VAEntrypointVLD
      VAProfileHEVCMain422_10         : VAEntrypointEncSlice
      VAProfileHEVCMain422_12         : VAEntrypointVLD
      VAProfileHEVCMain422_12         : VAEntrypointEncSlice
      VAProfileHEVCMain444            : VAEntrypointVLD
      VAProfileHEVCMain444            : VAEntrypointEncSliceLP
      VAProfileHEVCMain444_10         : VAEntrypointVLD
      VAProfileHEVCMain444_10         : VAEntrypointEncSliceLP
      VAProfileHEVCMain444_12         : VAEntrypointVLD
      VAProfileHEVCSccMain            : VAEntrypointVLD
      VAProfileHEVCSccMain            : VAEntrypointEncSliceLP
      VAProfileHEVCSccMain10          : VAEntrypointVLD
      VAProfileHEVCSccMain10          : VAEntrypointEncSliceLP
      VAProfileHEVCSccMain444         : VAEntrypointVLD
      VAProfileHEVCSccMain444         : VAEntrypointEncSliceLP
      VAProfileAV1Profile0            : VAEntrypointVLD
      VAProfileHEVCSccMain444_10      : VAEntrypointVLD
      VAProfileHEVCSccMain444_10      : VAEntrypointEncSliceLP
```

## 2.1.6 Check the Software Information

```bash title="lsb_release -a"
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.5 LTS
Release:        22.04
Codename:       jammy
```

```bash title="uname -r"
6.8.0-47-generic
```

```bash title="gst-launch-1.0 --version"
gst-launch-1.0 version 1.20.3
GStreamer 1.20.3
https://launchpad.net/distros/ubuntu/+source/gstreamer1.0
```
