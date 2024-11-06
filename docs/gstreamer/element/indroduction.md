---
sidebar_position: 1
---

# 1. Indroduction

## File Elements

### [filesrc](https://gstreamer.freedesktop.org/documentation/coreelements/filesrc.html?gi-language=c)

Read data from a file in the local file system.

Basic pipeline

```bash
gst-launch-1.0 filesrc location=video.mp4 ! qtdemux ! h264parse ! avdec_h264 ! videoconvert ! autovideosink
```

VA-API hardware acceleration pipeline

```bash
gst-launch-1.0 filesrc location=video.mp4 ! qtdemux ! h264parse ! vaapih264dec ! vaapipostproc ! autovideosink
```

OpenMAX hardware acceleration pipeline

```bash
gst-launch-1.0 filesrc location=video.mp4 ! qtdemux ! h264parse ! omxh264dec ! videoconvert ! autovideosink
```

### [filesink](https://gstreamer.freedesktop.org/documentation/coreelements/filesink.html?gi-language=c)

Write incoming data to a file in the local file system.

Basic pipeline

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! x264enc ! h264parse ! mp4mux ! filesink location=output.mp4
```

VA-API hardware acceleration pipeline

```bash
gst-launch-1.0 videotestsrc ! vaapipostproc ! vaapih264enc ! h264parse ! mp4mux ! filesink location=output.mp4
```

OpenMAX hardware acceleration pipeline

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! omxh264enc ! h264parse ! mp4mux ! filesink location=output.mp4
```

## Network Elements

### [udpsrc](https://gstreamer.freedesktop.org/documentation/udp/udpsrc.html?gi-language=c)

udpsrc is a network source that reads UDP packets from the network. It can be combined with RTP depayloaders to implement RTP streaming.

Basic pipeline

```bash
gst-launch-1.0 udpsrc port=5000 ! application/x-rtp, payload=96 ! rtph264depay ! h264parse ! avdec_h264 ! videoconvert ! autovideosink
```

change buffer-size

```bash
gst-launch-1.0 udpsrc port=5000 buffer-size=1048576 ! application/x-rtp, payload=96 ! rtph264depay ! h264parse ! avdec_h264 ! videoconvert ! autovideosink
```

VA-API hardware acceleration pipeline

```bash
gst-launch-1.0 udpsrc port=5000 buffer-size=1048576 ! application/x-rtp, payload=96 ! rtph264depay ! h264parse ! vaapih264dec ! vaapipostproc ! autovideosink
```

OpenMAX hardware acceleration pipeline

```bash
gst-launch-1.0 udpsrc port=5000 buffer-size=1048576 ! application/x-rtp, payload=96 ! rtph264depay ! h264parse ! omxh264dec ! videoconvert ! autovideosink
```

Note:

Check system buffer usage

```bash
netstat -s | grep -i buffer
```

change system buffer size

To make temporary changes to the network buffer size:

```bash
sudo sysctl -w net.core.rmem_max=8388608
sudo sysctl -w net.core.wmem_max=8388608
```

To make permanent changes that persist across reboots:

```bash title="/etc/sysctl.conf"
net.core.rmem_max=8388608
net.core.wmem_max=8388608
```

Apply Permanent changes

```bash
sudo sysctl -p
```

### [udpsink](https://gstreamer.freedesktop.org/documentation/udp/udpsink.html?gi-language=c)

udpsink is a network sink that sends UDP packets to the network. It can be combined with RTP payloaders to implement RTP streaming.

Basic pipeline

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! x264enc ! h264parse ! rtph264pay ! udpsink host=<ip address> port=5000
```

VA-API hardware acceleration pipeline

```bash
gst-launch-1.0 videotestsrc ! vaapipostproc ! vaapih264enc ! h264parse ! rtph264pay ! udpsink host=<ip address> port=5000
```

OpenMAX hardware acceleration pipeline

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! omxh264enc ! h264parse ! rtph264pay ! udpsink host=<ip address> port=5000
```

## v4l2 Elements

### [v4l2src](https://gstreamer.freedesktop.org/documentation/video4linux2/v4l2src.html?gi-language=c)

v4l2src can be used to capture video from v4l2 devices, like webcams and tv cards.

Basic pipeline

```bash
gst-launch-1.0 v4l2src /dev/video0 ! videoconvert ! autovideosink
```

## Video Processing Elements

### [videoconvert](https://gstreamer.freedesktop.org/documentation/videoconvertscale/videoconvert.html?gi-language=c)

Convert video frames between a great variety of video formats.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! autovideosink
```

### [videorate](https://gstreamer.freedesktop.org/documentation/videorate/index.html?gi-language=c)

This element takes an incoming stream of timestamped video frames. It will produce a perfect stream that matches the source pad's framerate.

```bash
gst-launch-1.0 videotestsrc ! video/x-raw,framerate=30/1 ! videorate ! video/x-raw,framerate=15/1 ! autovideosink
```

### [videoscale](https://gstreamer.freedesktop.org/documentation/videoconvertscale/videoscale.html?gi-language=c)

This element resizes video frames. By default the element will try to negotiate to the same size on the source and sinkpad so that no scaling is needed. It is therefore safe to insert this element in a pipeline to get more robust behaviour without any cost if no scaling is needed.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! videoscale ! video/x-raw,width=1280,height=720 ! autovideosink
```

### [videocrop](https://gstreamer.freedesktop.org/documentation/videocrop/videocrop.html?gi-language=c)

This element crops video frames, meaning it can remove parts of the picture on the left, right, top or bottom of the picture and output a smaller picture than the input picture, with the unwanted parts at the border removed.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! videocrop top=140 bottom=140 left=160 right=160 ! autovideosink
```

## Test Media Generation Elements

### [videotestsrc](https://gstreamer.freedesktop.org/documentation/videotestsrc/index.html?gi-language=c)

The videotestsrc element is used to produce test video data in a wide variety of formats. The video test data produced can be controlled with the "pattern" property.  
By default the videotestsrc will generate data indefinitely, but if the num-buffers property is non-zero it will instead generate a fixed number of video frames and then send EOS.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! autovideosink
```

### [audiotestsrc](https://gstreamer.freedesktop.org/documentation/audiotestsrc/index.html?gi-language=c)

AudioTestSrc can be used to generate basic audio signals. It support several different waveforms and allows to set the base frequency and volume. Some waveforms might use additional properties.

```bash
gst-launch-1.0 audiotestsrc ! audioconvert ! autoaudiosink
```

## Multithreading Elements

### [queue](https://gstreamer.freedesktop.org/documentation/coreelements/queue.html?gi-language=c)

Data is queued until one of the limits specified by the max-size-buffers, max-size-bytes and/or max-size-time properties has been reached. Any attempt to push more buffers into the queue will block the pushing thread until more space becomes available.

The queue will create a new thread on the source pad to decouple the processing on sink and source pad.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! queue ! autovideosink
```

### [tee](https://gstreamer.freedesktop.org/documentation/coreelements/tee.html?gi-language=c)

Split data to multiple pads. Branching the data flow is useful when e.g. capturing a video where the video is shown on the screen and also encoded and written to a file. Another example is playing music and hooking up a visualisation module.

One needs to use separate queue elements (or a multiqueue) in each branch to provide separate threads for each branch. Otherwise a blocked dataflow in one branch would stall the other branches.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! tee name=t ! queue ! autovideosink t. ! queue ! autovideosink
```

## Capabilities Elements

### [capsfilter](https://gstreamer.freedesktop.org/documentation/coreelements/capsfilter.html?gi-language=c)

The element does not modify data as such, but can enforce limitations on the data format.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! video/x-raw,format=BGRA ! autovideosink
```

## Debugging Elements

### [fakesink](https://gstreamer.freedesktop.org/documentation/coreelements/fakesink.html?gi-language=c)

Dummy sink that swallows everything.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! fakesink
```

### [fakevideosink](https://gstreamer.freedesktop.org/documentation/debugutilsbad/fakevideosink.html?gi-language=c)

This element is the same as fakesink but will pretend to support various allocation meta API like GstVideoMeta in order to prevent memory copies. This is useful for throughput testing and testing zero-copy path while creating a new pipeline.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! fakevideosink
```

### [fpsdisplaysink](https://gstreamer.freedesktop.org/documentation/debugutilsbad/fpsdisplaysink.html?gi-language=c)

Can display the current and average framerate as a testoverlay or on stdout.

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! fpsdisplaysink
```

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! fpsdisplaysink text-overlay=false -v
```

```bash
gst-launch-1.0 videotestsrc ! videoconvert ! fpsdisplaysink text-overlay=false video-sink="waylandsink fullscreen=true" -v
```
