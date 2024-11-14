---
sidebar_position: 2
---

# Test

```conf
DL_DIR = "${TOPDIR}/../downloads"
SSTATE_DIR = "${TOPDIR}/../sstate-cache"

IMAGE_INSTALL_append = " kernel-module-uvcvideo "
EXTRA_IMAGE_FEATURES_append = " ssh-server-openssh "

IMAGE_INSTALL_append = " curl graphviz "
IMAGE_INSTALL_append = " gst-instruments gst-shark"
PACKAGECONFIG_append_pn-gstreamer1.0 = " tracer-hooks "
```

SSH Server

```bash
EXTRA_IMAGE_FEATURES_append = " ssh-server-openssh "
```

GStreamer Instruments

```bash
IMAGE_INSTALL_append = " gst-instruments "
```

GstShark

```bash
IMAGE_INSTALL_append = " gst-shark "
PACKAGECONFIG_append_pn-gstreamer1.0 = " tracer-hooks "
```
