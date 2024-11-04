---
sidebar_position: 1
---
# 4.2.1 Build on x86

## Dependencies

To build the GStreamer Shark, you need to have the following dependencies installed

[GStreamer](../../moil-gstreamer/build-on-x86.md#311-dependencies)

Graphviz:

```bash
sudo apt install graphviz libgraphviz-dev
```

## Build

Clone the repository:

```bash
git clone https://github.com/RidgeRun/gst-shark.git
cd gst-shark
```

Build the project:

```bash
meson setup builddir
meson compile -C builddir
```

Test the project:

```bash
meson test -C builddir
```

## Install

Install the project:

```bash
sudo meson install -C builddir
```
