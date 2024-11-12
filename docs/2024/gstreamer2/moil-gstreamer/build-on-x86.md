---
sidebar_position: 1
---
# 3.1 Build on x86

## 3.1.1 Dependencies

### Install GStreamer

```bash
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-vaapi gstreamer1.0-libav 
```

### Install GStreamer Development Libraries

```bash
sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-good1.0-dev libgstreamer-plugins-bad1.0-dev
```

## 3.1.2 Build Steps

Clone the moildev library repository

```bash
git clone https://github.com/cjchng/mainmoil_6view.git
cd mainmoil_6view
```

Setup moildev library to `usr/local/lib`

```bash
sudo cp lib/libmoildev.a /usr/local/lib/
sudo ldconfig
```

Clone the gst-plugins-bad repository

```bash
git clone https://github.com/M11158002/gst-plugins-bad-dev.git
cd gst-plugins-bad-dev
```

Setup the build directory

```bash title="meson setup builddir"
The Meson build system
Version: 0.61.2
Source dir: /home/user/work/gst-plugins-bad-dev
Build dir: /home/user/work/gst-plugins-bad-dev/builddir
Build type: native build
Project name: gst-plugins-bad
Project version: 1.19.2
C compiler for the host machine: cc (gcc 11.4.0 "cc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0")
C linker for the host machine: cc ld.bfd 2.38
C++ compiler for the host machine: c++ (gcc 11.4.0 "c++ (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0")
C++ linker for the host machine: c++ ld.bfd 2.38
Host machine cpu family: x86_64
Host machine cpu: x86_64
---
Build targets in project: 220
NOTICE: Future-deprecated features used:
 * 0.56.0: {'Dependency.get_pkgconfig_variable', 'meson.build_root'}

gst-plugins-bad 1.19.2

    Plugins    : accurip, adpcmdec, adpcmenc, aiff, asfmux, audiobuffersplit, audiofxbad, audiomixmatrix,
                 audiolatency, audiovisualizers, autoconvert, bayer, camerabin, codecalpha, coloreffects,
                 debugutilsbad, dvbsubenc, dvbsuboverlay, dvdspu, faceoverlay, festival, fieldanalysis, freeverb,
                 frei0r, gaudieffects, gdp, geometrictransform, id3tag, inter, interlace, ivfparse, ivtc,
                 jp2kdecimator, jpegformat, rfbsrc, midi, mpegpsdemux, mpegpsmux, mpegtsdemux, mpegtsmux, mxf, netsim,
                 rtponvif, pcapparse, pnm, proxy, legacyrawparse, removesilence, rist, rtmp2, rtpmanagerbad, sdpelem,
                 segmentclip, siren, smooth, speed, subenc, switchbin, timecode, transcode, videofiltersbad,
                 videoframe_audiolevel, videoparsersbad, videosignal, vmnc, y4mdec, decklink, dvb, fbdevsink,
                 ipcpipeline, kms, nvcodec, shm, v4l2codecs, closedcaption, dash, dc1394, hls, opencv, openexr, sctp,
                 smoothstreaming, ttmlsubs, waylandsink

  Subprojects
    avtp       : NO Neither a subproject directory nor a avtp.wrap file was found.
    dssim      : NO Neither a subproject directory nor a dssim.wrap file was found.
    libmicrodns: NO Neither a subproject directory nor a libmicrodns.wrap file was found.
    libnice    : NO Neither a subproject directory nor a libnice.wrap file was found.
    libopenjp2 : NO Neither a subproject directory nor a libopenjp2.wrap file was found.
    libsoup    : NO Neither a subproject directory nor a libsoup.wrap file was found.
    openh264   : NO Neither a subproject directory nor a openh264.wrap file was found.
    tinyalsa   : NO Neither a subproject directory nor a tinyalsa.wrap file was found.

Found ninja-1.10.1 at /usr/bin/ninja
```

```bash title="meson compile -C builddir"
ninja: Entering directory `/home/user/gst-plugins-bad-dev/builddir'
--- 
[900/900] Linking target tests/check/elements_dash_mpd
```

## 3.1.3 Check the Plugin

Setup the GStreamer Plugin Path

```bash
export GST_PLUGIN_PATH=$PWD/builddir/gst/geometrictransform/:$GST_PLUGIN_PATH
```

Check the plugin

```bash
gst-inspect-1.0 geometrictransform
gst-inspect-1.0 equirectangular
```

## 3.1.4 Run the Example Pipeline

go to the test_env directory

```bash
cd test_env
```

Use the video file `endo01.mp4` to test the MOIL GStreamer Plugin.

```bash
gst-launch-1.0 filesrc location=endo01.mp4 ! qtdemux ! h264parse ! queue ! avdec_h264 ! videoconvert!  "video/x-raw, format=BGRA" ! equirectangular ! videoconvert ! autovideosink
```
