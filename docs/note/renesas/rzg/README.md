---
sidebar_position: 0
---

# README

Renesas VLP 需要在 Ubuntu 20.04 LTS 系統的環境下建置。  
如果系統不是 Ubuntu 20.04 LTS ，可以使用 Docker Containers ，進行 Renesas VLP 的建置。  
如果使用 vscode 進行開發，可以使用 Dev Containers 自動管理 Docker Containers。  

使用 Docker Containers 建置:
[docker](../general/docker/docker.md)  
使用 VScode Dev Containers 建置:
[vscode](../general/docker/vscode.md)  

## 下載 Renesas VLP Package

Download Link:
[RZ/G Verified Linux Package](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg-linux-platform/rzg-marketplace/verified-linux-package/rzg-verified-linux-package)

Extract RZ/G Verified Linux Package zip file.

```bash title="dir: ~/work/rzg"
unzip RTK0EF0045Z0021AZJ-v3.0.6-update3.zip
```

Extract RZ MPU Graphics Library zip file.

```bash title="dir: ~/work/rzg"
unzip RTK0EF0045Z13001ZJ-v1.2.2_EN.zip
```

Extract RZ MPU Video Codec Library zip file.

```bash title="dir: ~/work/rzg"
unzip RTK0EF0045Z15001ZJ-v1.2.2_EN.zip
```

Make the working directory on your Linux PC.

```bash title="dir: ~/work/rzg"
mkdir yocto
```

Move to the working directory.

```bash title="dir: ~/work/rzg/yocto"
cd yocto
```

Extract RZ/G Verified Linux Package tar.gz file.

```bash title="dir: ~/work/rzg/yocto"
tar zxvf ../RTK0EF0045Z0021AZJ-v3.0.6-update3/rzg_vlp_v3.0.6.tar.gz
```

Extract RZ/G Graphics Package tar.gz file.

```bash title="dir: ~/work/rzg/yocto"
tar zxvf ../RTK0EF0045Z13001ZJ-v1.2.2_EN/meta-rz-features_graphics_v1.2.2.tar.gz
```

Extract RZ/G Codecs Package tar.gz file.

```bash title="dir: ~/work/rzg/yocto"
tar zxvf ../RTK0EF0045Z15001ZJ-v1.2.2_EN/meta-rz-features_codec_v1.2.2.tar.gz
```

Check the working directory to confirm the package contents.

```bash title="dir: ~/work/rzg/yocto"
ls -1
```

If the above command prints followings, the package is extracted correctly.

```bash title="dir: ~/work/rzg/yocto"
extra
meta-gplv2
meta-openembedded
meta-qt5
meta-renesas
meta-rz-features
meta-virtualization
poky
```

Apply a patch file to update vlp to update3.

```bash title="dir: ~/work/rzg/yocto"
patch -p1 < ../RTK0EF0045Z0021AZJ-v3.0.6-update3/vlpg306-to-vlpg306update3.patch
```

Download the patch files.

[Download 0001](../file/0001-gstreamer-moil-plugin.patch)  
[Download 0002](../file/0002-fix_qtsmarthome_url.patch)  

Apply a patch file to add the GStreamer Moil Plugin.

```bash title="dir: ~/work/rzg/yocto"
patch -p1 < 0001-gstreamer-moil-plugin.patch
```

Apply a patch file to fix the Qt Smart Home URL.

```bash title="dir: ~/work/rzg/yocto"
patch -p1 < 0002-fix_qtsmarthome_url.patch
```

Move to the working directory.

```bash title="dir: ~/work/rzg/yocto"
cd meta-renesas
```

Apply a patch file extras.

```bash title="dir: ~/work/rzg/yocto/meta-renesas"
patch -p1 < ../extra/0001-rz-common-recipes-debian-buster-glibc-update-to-v2.2.patch
```

```bash title="dir: ~/work/rzg/yocto/meta-renesas"
patch -p1 < ../extra/0001-rz-common-linux-update-linux-kernel-to-the-latest-re.patch
```

```bash title="dir: ~/work/rzg/yocto/meta-renesas"
patch -p1 < ../extra/0001-rz-common-gst-plugins-bad-Depending-bayer2raw-if-lay.patch
```

Move to the working directory.

```bash title="dir: ~/work/rzg/yocto/meta-renesas"
cd ..
```

Initialize a build using the oe-init-build-env script in Poky and set environment variable TEMPLATECONF to the below path.

```bash title="dir: ~/work/rzg/yocto"
TEMPLATECONF=${PWD}/meta-renesas/meta-rzg2l/docs/template/conf/ source poky/oe-init-build-env build
```

Run the following commands to add necessary layers for AI application to build/conf/bblayers.conf (configration file for layers).

```bash title="dir: ~/work/rzg/yocto/build"
bitbake-layers add-layer ../meta-rz-features/meta-rz-graphics
bitbake-layers add-layer ../meta-rz-features/meta-rz-codecs
```

Run the following command to build the weston image.

```bash title="dir: ~/work/rzg/yocto/build"
MACHINE=smarc-rzg2l bitbake core-image-weston
```

Run the following command to build cross compiler installer.

```bash title="dir: ~/work/rzg/yocto/build"
MACHINE=smarc-rzg2l bitbake core-image-weston -c populate_sdk
```

If you want to build the qt5 image, run the following command to add the meta-qt5 layer for qt5.

```bash title="dir: ~/work/rzg/yocto/build"
bitbake-layers add-layer ../meta-qt5
```

and in local.conf file, add the following line.

```bash title="file: ~/work/rzg/yocto/build/conf/local.conf"
QT_DEMO = "1"
```

Run the following command to build the qt5 image.

```bash title="dir: ~/work/rzg/yocto/build"
MACHINE=smarc-rzg2l bitbake core-image-qt
```

Run the following command to build cross compiler installer.

```bash title="dir: ~/work/rzg/yocto/build"
MACHINE=smarc-rzg2l bitbake core-image-qt -c populate_sdk
```

image file path: ~/work/rzg/yocto/build/tmp/deploy/images/smarc-rzg2l/

image name | file name
--- | ---
core-image-weston | core-image-weston-smarc-rzg2l.wic.gz <br/> core-image-weston-smarc-rzg2l.wic.bmap
core-image-qt | core-image-qt-smarc-rzg2l.wic.gz <br/> core-image-qt-smarc-rzg2l.wic.bmap

Check the sd card device.

```bash
lsblk
```

if the sd card device is /dev/sdb, and sd card is mounted, unmount the sd card.

```bash
sudo umount /dev/sdb1
sudo umount /dev/sdb2
```

Wire the SD card to the host PC.

```bash
sudo bmaptool copy core-image-weston-smarc-rzg2l.wic.gz /dev/sdb
```

如果需要增加 rootfs image 的大小，可以參考以下步驟。

```bash
lsblk
```

```bash
sudo fdisk -l /dev/sdb
```

```bash
sudo growpart /dev/sdb 2
```

```bash
sudo resize2fs /dev/sdb2
```

## Links
