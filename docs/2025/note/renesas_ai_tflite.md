# Renesas AI

## TensorFlow Lite in Renesas embedded

[LiteRT](https://ai.google.dev/edge/litert?hl=zh-tw)  
[Python](https://ai.google.dev/edge/litert/microcontrollers/python?hl=zh-tw)  
[Run an inference using tflite_runtime](https://ai.google.dev/edge/litert/microcontrollers/python?hl=zh-tw#run_an_inference_using_tflite_runtime)  
[TensorFlow Lite Python image classification demo](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite/examples/python/)

V2H needs to create virtual environment and install `tflite-runtime` and `pillow` in the virtual environment.

```bash
python3 -m venv .venv
```

```bash
pip install tflite-runtime pillow
```

Download sample model and image

```bash
# Get photo
curl https://raw.githubusercontent.com/tensorflow/tensorflow/master/tensorflow/lite/examples/label_image/testdata/grace_hopper.bmp > /tmp/grace_hopper.bmp
# Get model
curl https://storage.googleapis.com/download.tensorflow.org/models/mobilenet_v1_2018_02_22/mobilenet_v1_1.0_224.tgz | tar xzv -C /tmp
# Get labels
curl https://storage.googleapis.com/download.tensorflow.org/models/mobilenet_v1_1.0_224_frozen.tgz  | tar xzv -C /tmp  mobilenet_v1_1.0_224/labels.txt
# Move labels
mv /tmp/mobilenet_v1_1.0_224/labels.txt /tmp/
```

edit `label_image.py` to use `tflite_runtime` instead of `tensorflow`:

```python
import tflite_runtime.interpreter as tflite
```

```python
interpreter = tflite.Interpreter(model_path=args.model_file)
```

Run the sample

```bash
python3 label_image.py \
  --model_file /tmp/mobilenet_v1_1.0_224.tflite \
  --label_file /tmp/labels.txt \
  --image /tmp/grace_hopper.bmp
```

You should see results like this:

```bash
0.728693: military uniform
0.116163: Windsor tie
0.035517: bow tie
0.014874: mortarboard
0.011758: bolo tie
```
