---
sidebar_position: 3
---
# 5.3 Usage Guide

## Supported map types and parameters

- AnyPointM1
  - alpha_offset
  - beta_offset
  - zoom
- AnyPointM2
  - thetaX_degree
  - thetaY_degree
  - zoom
- PanoramaM_Rt
  - alpha_max
  - ic_alpha_degree
  - ic_beta_degree

## Example

Create a YAML file:

Configure the camera parameters:

```yaml title="config.yaml"
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

Configure the image path:

```yaml title="config.yaml"
image_path: /path/to/image.jpg
```

Configure the map parameters:

```yaml title="config.yaml"
  - name: anypoint
    save_path: output/anypoint
    type: AnyPointM2
    alpha_offset: 0.0
    beta_offset: 0.0
    zoom: 1.0
```

Run the fisheye transform tool:

```bash
./fisheye_transformer -c config.yaml
```
