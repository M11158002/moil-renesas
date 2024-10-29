---
sidebar_position: 1
---
# 2.1 x86 Platform

## 2.1.1 Hardware Requirements

[Intel® Processor N200](https://www.intel.com/content/www/us/en/products/sku/231804/intel-processor-n200-6m-cache-up-to-3-70-ghz/specifications.html)  
[Intel® Core™ i5-1135G7 Processor](https://www.intel.com/content/www/us/en/products/sku/208658/intel-core-i51135g7-processor-8m-cache-up-to-4-20-ghz/specifications.html)

## 2.1.2 Software Requirements

- Ubuntu 22.04.5 LTS
- Mesa 24.3.0
- OpenGL 4.6
- VA-API 1.22 (libva 2.22.0)
- GStreamer 1.20.1

## 2.1.3 Environment Setup

If use SSH to connect to the x86 platform, you need to set the DISPLAY environment variable.

```bash
export DISPLAY=:0
# or
export DISPLAY=:1
```

Check the display number by running the following command:

```bash
for n in 0 1 2; do
    export DISPLAY=:$n
    xdpyinfo >/dev/null 2>&1 && echo "Display :$n is available"
done
```

## 2.1.4 Dependencies Installation
