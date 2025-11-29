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
  -d "iCx=1868" \
  -d "iCy=1415" \
  -d "Ratio=1" \
  -d "imgWidth=3840" \
  -d "imgHeight=2880" \
  -d "caliRatio=1" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-49.186" \
  -d "P3=98.223" \
  -d "P4=-56.011" \
  -d "P5=751.679" \
  --output MapsXY.zip
```

```bash
curl -X POST "http://140.112.12.82/moilmapgen/process.php" \
  -d "program=0" \
  -d "senWidth=1.55" \
  -d "senHeight=1.55" \
  -d "iCx=1888" \
  -d "iCy=1051" \
  -d "Ratio=1" \
  -d "imgWidth=3840" \
  -d "imgHeight=2160" \
  -d "caliRatio=1" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-45.127" \
  -d "P3=83.504" \
  -d "P4=-39.243" \
  -d "P5=745.135" \
  --output MapsXY.zip
```

```bash
curl -X POST "http://140.112.12.82/moilmapgen/process.php" \
  -d "program=0" \
  -d "senWidth=1.55" \
  -d "senHeight=1.55" \
  -d "iCx=1261" \
  -d "iCy=955" \
  -d "Ratio=1" \
  -d "imgWidth=2592" \
  -d "imgHeight=1944" \
  -d "caliRatio=1" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-31.305" \
  -d "P3=59.67" \
  -d "P4=-30.449" \
  -d "P5=504.702" \
  --output MapsXY.zip
```

```bash
curl -X POST "http://140.112.12.82/moilmapgen/process.php" \
  -d "program=0" \
  -d "senWidth=1.55" \
  -d "senHeight=1.55" \
  -d "iCx=944" \
  -d "iCy=525" \
  -d "Ratio=1" \
  -d "imgWidth=1920" \
  -d "imgHeight=1080" \
  -d "caliRatio=1" \
  -d "P0=0" \
  -d "P1=0" \
  -d "P2=-20.772" \
  -d "P3=35.661" \
  -d "P4=-13.097" \
  -d "P5=370.136" \
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
