# Yolo AI

## uv

[uv](https://github.com/astral-sh/uv)

On macOS and Linux.

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

On Windows.

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

update to the latest version

```bash
uv self update
```

## Ultralytics YOLO

[ultralytics](https://github.com/ultralytics/ultralytics)
[YOLO Face](https://github.com/akanametov/yolo-face)
[ArcFace in Tensorflow Lite.](https://github.com/mobilesec/arcface-tensorflowlite/tree/master)

install the python package

```bash
uv python install 3.12
```

create a virtual environment

```bash
uv venv --python 3.12
```

install the ultralytics package

```bash
uv pip install ultralytics
```

verify the installation

```bash
yolo predict model=yolo11n.pt source='https://ultralytics.com/images/bus.jpg'
```

export the model to tflite

```bash
yolo export model=yolo11n.pt format=tflite
```

scale the model to 320x320

```bash
yolo export model=yolo11n.pt format=tflite imgsz=320
```

try the half model

```bash
yolo export model=yolo11n.pt format=tflite half=True
```
