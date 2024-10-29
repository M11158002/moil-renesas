---
sidebar_position: 1
---
# 3.2.1 Build

This section will guide you on how to build the MOIL GStreamer Plugin on Ubuntu.

1. Get and Set up the moildev library
2. Clone gst-plugins-bad repository
3. Build MOIL GStreamer Plugin
4. Check MOIL GStreamer Plugin PATH
5. Test MOIL GStreamer Plugin

## 1. Get and Set up the moildev library

```bash
git clone https://github.com/cjchng/mainmoil_6view.git
cd mainmoil_6view
sudo cp lib/libmoildev.a /usr/local/lib/
sudo ldconfig
```

## 2. Clone gst-plugins-bad repository

```bash
git clone https://github.com/M11158002/gst-plugins-bad-dev.git
cd gst-plugins-bad-dev
```

## 3. Build MOIL GStreamer Plugin

```bash
meson setup builddir
meson compile -C builddir
```

## 4. Check MOIL GStreamer Plugin PATH

```bash
export GST_PLUGIN_PATH="$PWD/builddir/gst/geometrictransform/:$GST_PLUGIN_PATH"
gst-inspect-1.0 geometrictransform
gst-inspect-1.0 equirectangular
```

## 5. Test MOIL GStreamer Plugin

go to the test_env directory

```bash
cd test_env
```

Use the video file `endo01.mp4` to test the MOIL GStreamer Plugin.

```bash
gst-launch-1.0 filesrc location=endo01.mp4 ! qtdemux ! h264parse ! queue ! avdec_h264 ! videoconvert!  "video/x-raw, format=BGRA" ! equirectangular ! videoconvert ! autovideosink
```
