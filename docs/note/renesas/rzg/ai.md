# AI

```bash
git clone https://github.com/renesas-rz/meta-renesas-ai.git
```

```bash
# RZ/G2L
TEMPLATECONF=$PWD/meta-renesas/meta-rzg2l/docs/template/conf/ source poky/oe-init-build-env build_rzg2l
# RZ/G2UL
TEMPLATECONF=$PWD/meta-renesas/meta-rzg2l/docs/template/conf/ source poky/oe-init-build-env build_rzg2ul
```

source poky/oe-init-build-env

```bash
# RZ/G2L
source poky/oe-init-build-env build_rzg2l
# RZ/G2UL
source poky/oe-init-build-env build_rzg2ul
```

```bash
# All platforms
bitbake-layers add-layer ../meta-moil
bitbake-layers add-layer ../meta-qt5
bitbake-layers add-layer ../meta-renesas-ai
# For RZ/G2L
bitbake-layers add-layer ../meta-rz-features/meta-rz-graphics
bitbake-layers add-layer ../meta-rz-features/meta-rz-codecs
```

weston image

```bash
# RZ/G2L
MACHINE=smarc-rzg2l bitbake core-image-weston
# RZ/G2UL
MACHINE=smarc-rzg2ul bitbake core-image-weston
```

qt5 image

```bash
# RZ/G2L
MACHINE=smarc-rzg2l bitbake core-image-qt
# RZ/G2UL
MACHINE=smarc-rzg2ul bitbake core-image-qt
```

SDK

```bash
# RZ/G2L
MACHINE=smarc-rzg2l bitbake core-image-qt -c populate_sdk
# RZ/G2UL
MACHINE=smarc-rzg2ul bitbake core-image-qt -c populate_sdk
```

base append

```conf
DL_DIR = "${TOPDIR}/../downloads"
CIP_MODE = "None"
WKS_SUPPORT ?= "1"
IMAGE_ROOTFS_EXTRA_SPACE = "1048576"
```

dev append

```conf
IMAGE_INSTALL_append = " htop "
EXTRA_IMAGE_FEATURES_append = " ssh-server-openssh "
```

moilapp append

```conf
IMAGE_INSTALL_append = " opencv "
PACKAGECONFIG_append_pn-opencv = " gtk opencl python3 "
IMAGE_INSTALL_append = " python3 python3-pygobject "
PACKAGECONFIG:append:pn-gstreamer1.0-plugins-good = " gtk"
```

ai append

```conf
IMAGE_INSTALL_append = " armnn-dev armnn-examples armnn-tensorflow-lite-dev armnn-onnx-dev armnn-onnx-examples tensorflow-lite-python "
IMAGE_INSTALL_append = " tensorflow-lite-staticdev tensorflow-lite-dev tensorflow-lite-benchmark armnn-benchmark "
IMAGE_INSTALL_append = " tensorflow-lite-delegate-benchmark "
IMAGE_INSTALL_append = " onnxruntime "
IMAGE_INSTALL_append = " onnxruntime-benchmark "
IMAGE_INSTALL_append = " tensorflow-lite-staticdev tensorflow-lite-dev tensorflow-lite-python "
IMAGE_INSTALL_append = " tensorflow-lite-benchmark "
IMAGE_INSTALL_append = " ai-tests "
```
