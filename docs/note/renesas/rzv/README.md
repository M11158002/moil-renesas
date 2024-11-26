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

## 下載 RZ/V2H AI Software Development Kit

[RZ/V2H AI Software Development Kit](https://www.renesas.com/en/software-tool/rzv2h-ai-software-development-kit#downloads)

Download the RZ/V2H AI SDK Sorce Code zip file.

Extract RZ/V2H AI SDK Sorce Code zip file.

```bash title="dir: ~/work/rzv"
unzip RTK0EF0180F05000SJ_linux-src.zip
```

Make the working directory on your Linux PC.

```bash title="dir: ~/work/rzv"
mkdir yocto
```

Move to the working directory.

```bash title="dir: ~/work/rzv/yocto"
cd yocto
```

Extract Yocto recipe package.

```bash title="dir: ~/work/rzv/yocto"
tar zxvf ../rzv2h_ai-sdk_yocto_recipe_v5.00.tar.gz
```

Check the working directory to confirm Yocto recipes content.

```bash title="dir: ~/work/rzv/yocto"
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

Apply a patch file to add the GStreamer Moil Plugin.

```bash title="dir: ~/work/rzv/yocto"
patch -p1 < 0001-gstreamer-moil-plugin.patch
```

Apply a patch file to fix the Qt Smart Home URL.

```bash title="dir: ~/work/rzv/yocto"
patch -p1 < 0002-fix_qtsmarthome_url.patch
```

Initialize a build using the oe-init-build-env script in Poky and set environment variable TEMPLATECONF to the below path.

```bash title="dir: ~/work/rzv/yocto"
TEMPLATECONF=${PWD}/meta-renesas/meta-rzv2h/docs/template/conf/ source poky/oe-init-build-env build
```

Run the following commands to add necessary layers for AI application to build/conf/bblayers.conf (configration file for layers).

```bash title="dir: ~/work/rzv/yocto/build"
bitbake-layers add-layer ../meta-rz-features/meta-rz-graphics
bitbake-layers add-layer ../meta-rz-features/meta-rz-drpai
bitbake-layers add-layer ../meta-rz-features/meta-rz-opencva
bitbake-layers add-layer ../meta-rz-features/meta-rz-codecs
```

Apply a patch file to add Tesseract Open Source OCR Engine for AI applications.

```bash title="dir: ~/work/rzv/yocto/build"
patch -p1 < ../0001-tesseract.patch
```

Apply a patch file to change SD card image size.

```bash title="dir: ~/work/rzv/yocto/build"
patch -p1 < ../0002-sd-image-size-16gb.patch
```

Run the following command to build the weston image.

```bash title="dir: ~/work/rzv/yocto/build"
MACHINE=rzv2h-evk-ver1 bitbake core-image-weston
```

Run the following command to build cross compiler installer.

```bash title="dir: ~/work/rzv/yocto/build"
MACHINE=rzv2h-evk-ver1 bitbake core-image-weston -c populate_sdk
```

If you want to build the qt5 image, run the following command to add the meta-qt5 layer for qt5.

```bash title="dir: ~/work/rzv/yocto/build"
bitbake-layers add-layer ../meta-qt5
```

and in local.conf file, add the following line.

```bash title="dir: ~/work/rzv/yocto/build/conf/local.conf"
QT_DEMO = "1"
```

Run the following command to build the qt5 image.

```bash title="dir: ~/work/rzv/yocto/build"
MACHINE=rzv2h-evk-ver1 bitbake core-image-qt
```

Run the following command to build cross compiler installer.

```bash title="dir: ~/work/rzv/yocto/build"
MACHINE=rzv2h-evk-ver1 bitbake core-image-qt -c populate_sdk
```

image file path: ~/work/rzv/yocto/build/tmp/deploy/images/rzv2h-evk-ver1/

image name | file name
--- | ---
core-image-weston | core-image-weston-rzv2h-evk-ver1.wic.gz <br/> core-image-weston-rzv2h-evk-ver1.wic.bmap
core-image-qt | core-image-qt-rzv2h-evk-ver1.wic.gz <br/> core-image-qt-rzv2h-evk-ver1.wic.bmap

參考 Flash SD Card 步驟，將 image 燒錄到 SD Card。
[Flash SD Card](../general/flash-sdcard.md)

## Links

1. [How to build RZ/V2H AI SDK Source Code](https://renesas-rz.github.io/rzv_ai_sdk/5.00/howto_build_aisdk_v2h.html)
