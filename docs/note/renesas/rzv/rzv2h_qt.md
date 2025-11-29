# RZV2H QT5

If you want to build the qt5 image, you can use the `git clone` or `copy file` method to get the meta-qt5 layer for qt5.

```bash
git clone https://github.com/meta-qt5/meta-qt5.git
cd meta-qt5
git checkout c1b0c9f546289b1592d7a895640de103723a0305
git cherry-pick 77b6060cef9337b184100083746c2e35f531be74
```

If you copy the rz/g meta-qt5 layer to the build directory, you need to apply a patch file to fix the Qt Smart Home URL.

```bash title="dir: ~/work/rzv/yocto"
patch -p1 < 0002-fix_qtsmarthome_url.patch
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
core-image-qt | core-image-qt-rzv2h-evk-ver1.wic.gz <br/> core-image-qt-rzv2h-evk-ver1.wic.bmap

參考 Flash SD Card 步驟，將 image 燒錄到 SD Card。
[Flash SD Card](../general/flash-sdcard.md)
