# RZ V2H

## Yocto Configuration

ssh server

```bash
EXTRA_IMAGE_FEATURES_append = " ssh-server-openssh "
```

usb camera

```bash
IMAGE_INSTALL_append = " kernel-module-uvcvideo "
```

python bind gtk and gstreamer

```conf
IMAGE_INSTALL_append = " python3 python3-pygobject "
PACKAGECONFIG:append:pn-gstreamer1.0-plugins-good = " gtk"
```

python bind dev

```conf
IMAGE_INSTALL_append = " python3-pybind11"
TOOLCHAIN_HOST_TASK:append = " nativesdk-python3-pybind11"
```
