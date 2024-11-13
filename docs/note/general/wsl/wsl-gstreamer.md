---
sidebar_position: 5
---

# WSL GStreamer

## Installation

```bash
sudo apt-get install gstreamer1.0-tools gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-libav gstreamer1.0-vaapi
```

```bash
gst-inspect-1.0 | grep vaapi
```

```bash
gst-inspect-1.0 | grep nvcodec
```

```bash
export LIBVA_DRIVER_NAME=d3d12
export MESA_D3D12_DEFAULT_ADAPTER_NAME=INTEL
export MESA_D3D12_DEFAULT_ADAPTER_NAME=NVIDIA
```

```bash
export GST_GL_WINDOW=x11
export GST_GL_WINDOW=wayland
```

```bash
# Intel and NVIDIA VA-API
gst-launch-1.0 -v videotestsrc num-buffers=300 ! video/x-raw,width=1920,height=1080 ! vaapipostproc ! vaapih264enc ! filesink location=~/wsl_test.h264
# NVIDIA NVENC
gst-launch-1.0 -v videotestsrc num-buffers=300 ! video/x-raw,width=1920,height=1080 ! cudaupload ! nvh264enc ! filesink location=~/wsl_test.h264
```

```bash
# Intel and NVIDIA VA-API
gst-launch-1.0 filesrc location=~/wsl_test.h264 ! h264parse ! vaapih264dec ! autovideosink
# NVDIA NVDEC
gst-launch-1.0 filesrc location=~/wsl_test.h264 ! h264parse ! nvh264dec ! autovideosink
```
