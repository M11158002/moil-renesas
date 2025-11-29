# Yolo 11 Guide

## Convert Yolo 11 to RZG

yolo11n, yolo11s, yolo11m

640, 416, 320, 256, 192, 160, 128, 96
input shape (1, 3, 640, 640) BCHW and output shape(s) (1, 84, 8400)
input shape (1, 3, 416, 416) BCHW and output shape(s) (1, 84, 3549)
input shape (1, 3, 320, 320) BCHW and output shape(s) (1, 84, 2100)
input shape (1, 3, 256, 256) BCHW and output shape(s) (1, 84, 1344)
input shape (1, 3, 192, 192) BCHW and output shape(s) (1, 84, 756)
input shape (1, 3, 160, 160) BCHW and output shape(s) (1, 84, 525)
input shape (1, 3, 128, 128) BCHW and output shape(s) (1, 84, 336)
input shape (1, 3, 96, 96) BCHW and output shape(s) (1, 84, 189)
YOLO11n summary (fused): 238 layers, 2,616,248 parameters, 0 gradients, 6.5 GFLOPs
YOLO11s summary (fused): 238 layers, 9,443,760 parameters, 0 gradients, 21.5 GFLOPs
YOLO11m summary (fused): 303 layers, 20,091,712 parameters, 0 gradients, 68.0 GFLOPs

Convert to ONNX format

```bash
yolo export model=yolo11n.pt format=onnx imgsz=640
```

Convert to tfilte format

```bash
yolo export model=yolo11n.pt format=tflite imgsz=640
```

## Validate

```bash
yolo val task=detect model=model/640/yolo11n.onnx imgsz=640 data=/ultralytics/ultralytics/cfg/datasets/coco.yaml
```
