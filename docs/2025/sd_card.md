# Flash SD Card

```bash
sudo apt install bmap-tools
sudo apt install gparted
```

```bash
sudo bmaptool copy --bmap core-image-weston-smarc-rzg2l.wic.bmap core-image-weston-smarc-rzg2l.wic /dev/sdX
```

```bash
sudo gparted /dev/sdX 2
```
