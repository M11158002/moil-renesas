---
sidebar_position: 1
---

# Demo

## Server

```bash
gst-launch-1.0 v4l2src device=/dev/video0 ! "image/jpeg, width=1920, height=1080, framerate=30/1" ! vaapidecodebin ! tee name=t ! queue ! vaapipostproc ! waylandsink fullscreen=true t. ! queue ! vaapipostproc ! videorate ! video/x-raw,framerate=4/1 ! vaapih264enc rate-control=2 ! h264parse ! rtph264pay config-interval=1 ! udpsink host=224.1.1.1 port=5000
```

## Client

```bash
gst-launch-1.0 udpsrc address=224.1.1.1 port=5000 buffer-size=100000000 ! application/x-rtp ! rtph264depay ! h264parse ! omxh264dec ! glupload ! glcolorconvert ! gldownload ! "video/x-raw, format=BGRA" ! queue ! equirectangular ! waylandsink fullscreen=true
```
