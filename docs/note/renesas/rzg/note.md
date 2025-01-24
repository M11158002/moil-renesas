# Note

show the layers information.

```bash
bitbake-layers show-layers
```

show the appends information.

```bash
bitbake-layers show-appends
```

check the wic file partition.

```bash
cp tmp/deploy/images/smarc-rzg2ul/core-image-weston-smarc-rzg2ul.wic.gz ./
gunzip -f core-image-weston-smarc-rzg2ul.wic.gz
fdisk -l core-image-weston-smarc-rzg2ul.wic
```

create a swap file.

```bash
dd if=/dev/zero of=/mnt/swap bs=1M count=1024
chmod 600 /mnt/swap
mkswap /mnt/swap
swapon /mnt/swap
echo "/mnt/swap none swap sw 0 0" >> /etc/fstab
```
