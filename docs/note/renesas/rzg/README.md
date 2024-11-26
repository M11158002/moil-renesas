---
sidebar_position: 0
---

# README

Download the RZ/G Verified Linux Package zip file.

Extract RZ/G Verified Linux Package zip file.

```bash
unzip RTK0EF0045Z0021AZJ-v3.0.6-update3.zip
```

```bash
unzip RTK0EF0045Z13001ZJ-v1.2.2_EN.zip
```

```bash
unzip RTK0EF0045Z15001ZJ-v1.2.2_EN.zip
```

Make the working directory on your Linux PC.

```bash
mkdir yocto
```

Move to the working directory.

```bash
cd yocto
```

Extract RZ/G Verified Linux Package tar.gz file.

```bash
tar zxvf ../RTK0EF0045Z0021AZJ-v3.0.6-update3/rzg_vlp_v3.0.6.tar.gz
```

Extract RZ/G Graphics Package tar.gz file.

```bash
tar zxvf ../RTK0EF0045Z13001ZJ-v1.2.2_EN/meta-rz-features_graphics_v1.2.2.tar.gz
```

Extract RZ/G Codecs Package tar.gz file.

```bash
tar zxvf ../RTK0EF0045Z15001ZJ-v1.2.2_EN/meta-rz-features_codec_v1.2.2.tar.gz
```

Check the working directory to confirm the package contents.

```bash
ls -1
```

If the above command prints followings, the package is extracted correctly.

```bash
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

```bash
patch -p1 < ../RTK0EF0045Z0021AZJ-v3.0.6-update3/vlpg306-to-vlpg306update3.patch
```

Move to the working directory.

```bash
cd meta-renesas
```

Apply a patch file extras.

```bash
patch -p1 < ../extra/0001-rz-common-recipes-debian-buster-glibc-update-to-v2.2.patch
patch -p1 < ../extra/0001-rz-common-linux-update-linux-kernel-to-the-latest-re.patch
patch -p1 < ../extra/0001-rz-common-gst-plugins-bad-Depending-bayer2raw-if-lay.patch
```

Move to the working directory.

```bash
cd ..
```

Download the patch files.

[Download 0001](../file/0001-gstreamer-moil-plugin.patch)  
[Download 0002](../file/0002-fix_qtsmarthome_url.patch)  

Apply a patch file.

```bash
patch -p1 < 0001-gstreamer-moil-plugin.patch
patch -p1 < 0002-fix_qtsmarthome_url.patch
```

Initialize a build using the oe-init-build-env script in Poky and set environment variable TEMPLATECONF to the below path.

```bash
TEMPLATECONF=$PWD/meta-renesas/meta-rzg2l/docs/template/conf/ source poky/oe-init-build-env build
```

Run the following commands to add necessary layers for AI application to build/conf/bblayers.conf (configration file for layers).

```bash
bitbake-layers add-layer ../meta-rz-features/meta-rz-graphics
bitbake-layers add-layer ../meta-rz-features/meta-rz-codecs
```

Run the following command to build the weston image.

```bash
MACHINE=smarc-rzg2l bitbake core-image-weston
```

Run the following command to build cross compiler installer.

```bash
MACHINE=smarc-rzg2l bitbake core-image-weston -c populate_sdk
```

If you want to build the qt5 image, run the following command to add the meta-qt5 layer for qt5.

```bash
bitbake-layers add-layer ../meta-qt5
```

and in local.conf file, add the following line.

```bash
QT_DEMO = "1"
```

Run the following command to build the qt5 image.

```bash
MACHINE=smarc-rzg2l bitbake core-image-qt
```

Run the following command to build cross compiler installer.

```bash
MACHINE=smarc-rzg2l bitbake core-image-qt -c populate_sdk
```

If you want resize sd card partition, run the following command.

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
