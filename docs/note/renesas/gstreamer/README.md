# README

To use vspmfilter with USB cameras, you need to add option allocators=1 to uvcvideo kernel.

```bash
rmmod uvcvideo
# RZ/G2L
insmod /lib/modules/5.10.201-cip41-yocto-standard/kernel/drivers/media/usb/uvc/uvcvideo.ko allocators=1
# RZ/V2H
insmod /lib/modules/5.10.145-cip17-yocto-standard/kernel/drivers/media/usb/uvc/uvcvideo.ko allocators=1
```
