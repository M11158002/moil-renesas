---
sidebar_position: 1
---

# AI SDK

## Build RZ/V AI Application

```bash
source /opt/poky/3.1.31/environment-setup-aarch64-poky-linux
```

```bash
git clone https://github.com/Ignitarium-Renesas/RZV2L_AiLibrary
```

```bash
cd RZV2L_AiLibrary/01_Head_count/Head_count_cam
```

```bash
make
```

check the output file `head_count_cam_app` in the exe folder.

```bash
head_count_cam_app
```

## Deploy RZ/V AI Application

```bash
scp -r exe/ root@<RZV_IP>:/home/root/demo
```
