---
sidebar_position: 1
---

# AI SDK

## Build RZ/V AI Application

```bash
source /opt/poky/3.1.31/environment-setup-aarch64-poky-linux
```

```bash
git clone https://github.com/renesas-rz/rzv_ai_sdk.git
```

```bash
cd rzv_ai_sdk/R01_object_detection/src
```

```bash
mkdir -p build && cd build
```

```bash
cmake -DCMAKE_TOOLCHAIN_FILE=./toolchain/runtime.cmake -DV2H=ON ..
```

```bash
make
```

check the output file `object_detection` in the build folder.

```bash
object_detection
```

## Deploy RZ/V AI Application

```bash
cp /drp-ai_tvm/obj/build_runtime/${PRODUCT}/libtvm_runtime.so .
```

```bash
scp libtvm_runtime.so root@<RZV2H_IP>:/usr/lib64/
```

```bash
cd rzv_ai_sdk/R01_object_detection/exe_v2h/yolov3_onnx
```

```bash
wget https://github.com/renesas-rz/rzv_ai_sdk/releases/download/v5.00/R01_object_detection_deploy_tvm_v2h-v230.so
```

```bash
mv R01_object_detection_deploy_tvm_v2h-v230.so deploy.so
```

```bash
scp -r yolov3_onnx root@<RZV2H_IP>:/home/root/R01_object_detection/
scp object_detection root@<RZV2H_IP>:/home/root/R01_object_detection/
```

```bash
chmod +x object_detection
```

```bash
./object_detection
```
