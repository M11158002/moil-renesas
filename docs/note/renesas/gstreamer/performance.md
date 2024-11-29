# Performance

1. 測試編解碼器性能
    1. jpeg
    2. h264, h265
2. 測試色彩空間轉換性能
    1. NV12 -> BGRA
    2. I420 -> BGRA
3. 測試 moil remap 性能
    1. bgra
4. 整合測試
    1. jpeg -> I420 -> BGRA -> moil remap -> videosink
    2. h264 -> NV12 -> BGRA -> moil remap -> videosink
    3. h265 -> NV12 -> BGRA -> moil remap -> videosink

## Element

### Video Capture Plugin

v4l2src

### Video Decode Plugin

avdec_h264
avdec_h265
omxh264dec
omxh265dec

### Video Encode Plugin

omxh264enc
omxh265enc

### Video Conversion Plugin

videoconvert
glcolorconvert
vspmfilter (RZ/G2L and RZ/V2H)
vaapipostproc (PC only)

### Video Sink Plugin

waylandsink
glimagesink
vaapisink (PC only)

### Mux/Demux Plugin

mp4mux
qtdemux

### Audio Plugin

alsasink

### Network Protocol Plugin

udpsrc
udpsink

```bash
gst-launch-1.0 videotestsrc ! "video/x-raw, formate=BGRA,width=1920, height=1080" ! fpsdisplaysink text-overlay=false video-sink=fakevideosink -v
```

```bash
gst-launch-1.0 videotestsrc num-buffers=1 ! "video/x-raw, formate=BGRA,width=1920, height=1080" ! filesink location=test.bgra
```

```bash
gst-launch-1.0 videotestsrc num-buffers=1 ! "video/x-raw, formate=NV12,width=1920, height=1080" ! filesink location=test.nv12
```

save to jpeg

```bash
gst-launch-1.0 videotestsrc num-buffers=1 ! "video/x-raw, formate=BGRA,width=1920, height=1080" ! videoconvert ! jpegenc ! filesink location=test.jpg
```

```bash
gst-launch-1.0 filesrc location=test.bgra ! videoparse width=1920 height=1080 formate=BGRA ! imagefreeze ! fpsdisplaysink text-overlay=false video-sink=fakevideosink -v
```
