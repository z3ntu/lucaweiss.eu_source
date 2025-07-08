---
title: Mounting Android Retrofit Dynamic Partition images
date: 2023-03-30 22:50:00 +0200
tags:
  - android
---
Android devices launching with Android 10 and newer use a feature called [Dynamic Partitions](https://source.android.com/docs/core/ota/dynamic_partitions) which essentially combines the `system_a`, `vendor_a` and `product_a` (and all the `_b`) variants into a single partition simplifying the actual partition layout while making it more flexible. Think of it like a single physical partition which contains multiple logical partitions, like with LVM.

This feature is available on newly launched devices, devices launched with earlier Android versions still have to cope with the rigid partition layout on-disk. For this Android has introduced a way to [retrofit dynamic partitions](https://source.android.com/docs/core/ota/dynamic_partitions/implement#upgrading-devices) onto exiting the existing partition layout.

Unfortunately this also makes it a bit more tricky to extract an image that has already been split into separate images that will be flashed on the `system_*`, `vendor_*` and `product_*` partitions, normally called `super_system.img`, `super_vendor.img` and `super_product.img`.

First, convert all sparse files into raw image files.
```shell
$ simg2img super_system.img super_system.raw.img
$ simg2img super_vendor.img super_vendor.raw.img
$ simg2img super_product.img super_product.raw.img
```

Then you can start setting up the loopback devices. Make sure to remember the loop device being printed by the command for later.
```shell
$ sudo losetup --read-only --find --show super_system.raw.img
/dev/loop0
$ sudo losetup --read-only --find --show super_vendor.raw.img
/dev/loop1
$ sudo losetup --read-only --find --show super_product.raw.img
/dev/loop2
```

Next, grab the sources for the `make-dynpart-mappings` tool from GitLab and compile it with the `USERSPACE` flag.
```shell
$ git clone https://gitlab.com/flamingradian/make-dynpart-mappings.git
$ cd make-dynpart-mappings/
$ make -B USERSPACE=1
```

Then you can run the tool against the loopback devices you set up before. Make sure you use the correct paths!
```shell
$ sudo ./make-dynpart-mappings /dev/loop0 0 /dev/loop1 /dev/loop2
```

Finally you should be able to mount the partitions and do what you please with it!
```shell
$ sudo mount -o ro /dev/mapper/system_a /mnt/android/system
$ sudo mount -o ro /dev/mapper/system_ext_a /mnt/android/system_ext
$ sudo mount -o ro /dev/mapper/vendor_a /mnt/android/vendor
$ sudo mount -o ro /dev/mapper/product_a /mnt/android/product
$ sudo mount -o ro /dev/mapper/odm_a /mnt/android/odm
```
