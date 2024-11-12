---
sidebar_position: 1
---
# 4.2.1 Build on x86

## Dependencies

To build the GStreamer Instruments, you need to have the following dependencies installed:

[GStreamer](../../moil-gstreamer/build-on-x86.md#311-dependencies)

Vala and GTK3:

```bash
sudo apt install valac libgtk-3-dev
```

## Build

Clone the repository:

```bash
git clone https://github.com/kirushyk/gst-instruments.git
cd gst-instruments
```

Build the project:

```bash
meson setup builddir
meson compile -C builddir
```

## Install

Install the project:

```bash
sudo meson install -C builddir
```
