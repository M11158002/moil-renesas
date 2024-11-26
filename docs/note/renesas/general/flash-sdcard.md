# Flash SD Card

Check the sd card device.

```bash
lsblk
```

if the sd card device is /dev/sdx, and sd card is mounted, unmount the sd card.

```bash
sudo umount /dev/sdx1
sudo umount /dev/sdx2
```

Wire the SD card to the host PC.

```bash
sudo bmaptool copy core-image-<target>-<borad>.wic.gz /dev/sdx
```

if you want to resize the sd card partition, follow the steps below.

Check the sd card partition.

```bash
sudo fdisk -l /dev/sdx
```

Select the ext4 partition to resize.

```bash
sudo growpart /dev/sdx 2
```

Resize the filesystem.

```bash
sudo resize2fs /dev/sdx2
```