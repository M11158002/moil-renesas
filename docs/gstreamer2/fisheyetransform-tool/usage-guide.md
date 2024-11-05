---
sidebar_position: 3
---
# 5.3 Usage Guide

## Create a your camera configuration file

Create a YAML file with the camera configuration. The file should have the following format:

```yaml
camera:
  name: 7730v1
  sensor:
    width: 1.55
    height: 1.55
  icx: 944
  icy: 525
  i_ratio: 1.0
  image:
    width: 1920
    height: 1080
  calibration_ratio: 1.0
  parameters:
    - 0.0
    - 0.0
    - -20.772
    - 35.661
    - -13.097
    - 370.136
```
