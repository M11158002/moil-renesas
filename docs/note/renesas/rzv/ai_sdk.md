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
cd ..
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

## Convert ONNX Model to TVM

```python
img = F.resize(img, 732, Image.BILINEAR)
img = F.center_crop(img, 640)
```

```bash
docker pull ultralytics/ultralytics:latest-cpu
docker run -it --rm -v ./data:/workspaces -w /workspaces ultralytics/ultralytics:latest-cpu
```

```bash
yolo export model=yolo11n.pt format=onnx opset=12
```

```bash
# yolov8n.onnx
python3 compile_onnx_model_quant.py ../data/models/yolov8n.onnx -o ../data/output/yolov8n_onnx -t $SDK -d $TRANSLATOR -c $QUANTIZER --images ../data/calibrate_sample -v 100 -s 1,3,640,640 -i images
# yolov8m.onnx
python3 compile_onnx_model_quant.py ../data/models/yolov8m.onnx -o ../data/output/yolov8m_onnx -t $SDK -d $TRANSLATOR -c $QUANTIZER --images ../data/calibrate_sample -v 100 -s 1,3,640,640 -i images


python3 compile_onnx_model_quant.py ../data/models/yolov8n.onnx -o ../data/output/yolov8n_onnx -t $SDK -d $TRANSLATOR -c $QUANTIZER --images $TRANSLATOR/../GettingStarted/tutorials/calibrate_sample/ -v 100 -s 1,3,640,640 -i images


```

```bash
python3 compile_onnx_model_quant.py ../data/models/yolo11n.onnx -o ../data/output2/yolo11n_onnx -t $SDK -d $TRANSLATOR -c $QUANTIZER --images ../data/val2017 -v 100 -s 1,3,640,640 -i images
```

```bash
./random_copy.sh ./val2017 ./calibrate_sample
```
