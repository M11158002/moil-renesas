---
sidebar_position: 0
---

# README

Download the RZ/V2H AI SDK Sorce Code zip file.

Extract RZ/V2H AI SDK Sorce Code zip file.

```bash
unzip RTK0EF0180F05000SJ_linux-src.zip
```

Make the working directory on your Linux PC.

```bash
mkdir yocto
```

Move to the working directory.

```bash
cd yocto
```

Extract Yocto recipe package.

```bash
tar zxvf ../rzv2h_ai-sdk_yocto_recipe_v5.00.tar.gz
```

Check the working directory to confirm Yocto recipes content.

```bash
ls -1
```

If the above command prints followings, Yocto recipes are extracted correctly.

```bash
0001-tesseract.patch
0002-sd-image-size-16gb.patch
meta-gplv2
meta-openembedded
meta-renesas
meta-rz-features
meta-virtualization
poky
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
TEMPLATECONF=${PWD}/meta-renesas/meta-rzv2h/docs/template/conf/ source poky/oe-init-build-env
```

Run the following commands to add necessary layers for AI application to build/conf/bblayers.conf (configration file for layers).

```bash
bitbake-layers add-layer ../meta-rz-features/meta-rz-graphics
bitbake-layers add-layer ../meta-rz-features/meta-rz-drpai
bitbake-layers add-layer ../meta-rz-features/meta-rz-opencva
bitbake-layers add-layer ../meta-rz-features/meta-rz-codecs
```

Apply a patch file to add Tesseract Open Source OCR Engine for AI applications.

```bash
patch -p1 < ../0001-tesseract.patch
```

Apply a patch file to change SD card image size.

```bash
patch -p1 < ../0002-sd-image-size-16gb.patch
```

Run the following command to build the weston image.

```bash
MACHINE=rzv2h-evk-ver1 bitbake core-image-weston
```

Run the following command to build cross compiler installer.

```bash
MACHINE=rzv2h-evk-ver1 bitbake core-image-weston -c populate_sdk
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
MACHINE=rzv2h-evk-ver1 bitbake core-image-qt
```

Run the following command to build cross compiler installer.

```bash
MACHINE=rzv2h-evk-ver1 bitbake core-image-qt -c populate_sdk
```

## Links

1. [How to build RZ/V2H AI SDK Source Code](https://renesas-rz.github.io/rzv_ai_sdk/5.00/howto_build_aisdk_v2h.html)
