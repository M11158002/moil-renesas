# Temp Note

```bash
tar czf yocto-rzv.tar.gz \
    meta-gplv2 \
    meta-moil \
    meta-openembedded \
    meta-qt5 \
    meta-renesas \
    meta-rz-features \
    meta-virtualization \
    poky
```

```bash
. /home/renesas_dev/2024/buildtool/rzg2l/opt/poky/3.1.31/environment-setup-aarch64-poky-linux
. /home/renesas_dev/2024/buildtool/rzg2ul/opt/poky/3.1.31/environment-setup-aarch64-poky-linux
```

```bash
v4l2-ctl --list-devices
v4l2-ctl -d /dev/video0 --info
v4l2-ctl -d /dev/video0 --list-formats-ext
```

```bash
qmake yourproject.pro
make
```

```bash
mkdir build && cd build
cmake ..
make
```

Get remap file

Equirectangular

```bash
curl -X POST "http://140.112.12.82/moilmapgen/process.php" \
  -d "program=0" \
  -d "senWidth=1.55" \
  -d "senHeight=1.55" \
  -d "iCx=342" \
  -d "iCy=290" \
  -d "Ratio=1" \
  -d "imgWidth=640" \
  -d "imgHeight=480" \
  -d "caliRatio=0.354" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-20.772" \
  -d "P3=35.661" \
  -d "P4=-13.097" \
  -d "P5=370.36" \
  --output MapsXY.zip
```

Anypoint

```bash
curl -X POST "http://140.112.12.82/moilmapgen/process.php" \
  -d "program=1" \
  -d "senWidth=1.55" \
  -d "senHeight=1.55" \
  -d "iCx=316" \
  -d "iCy=234" \
  -d "Ratio=1" \
  -d "imgWidth=640" \
  -d "imgHeight=480" \
  -d "caliRatio=0.5" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-19.386" \
  -d "P3=34.964" \
  -d "P4=-15.408" \
  -d "P5=330.853" \
  -d "Mode=1" \
  -d "Alpha=0" \
  -d "Beta=0" \
  -d "Zoom=4" \
  --output MapsXY.zip
```

```bash
curl -X POST "http://140.112.12.82/moilmapgen/process.php" \
  -d "program=1" \
  -d "senWidth=1.55" \
  -d "senHeight=1.55" \
  -d "iCx=632" \
  -d "iCy=467" \
  -d "Ratio=1" \
  -d "imgWidth=1280" \
  -d "imgHeight=960" \
  -d "caliRatio=1" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-19.386" \
  -d "P3=34.964" \
  -d "P4=-15.408" \
  -d "P5=330.853" \
  -d "Mode=1" \
  -d "Alpha=0" \
  -d "Beta=0" \
  -d "Zoom=4" \
  --output MapsXY.zip
```
