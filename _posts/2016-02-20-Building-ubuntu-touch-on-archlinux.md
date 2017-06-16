---
layout: post
title: Building Ubuntu Touch on Arch Linux
date: 2016-02-20 21:37:00 +0100
tags:
  - arch-linux
  - ubuntu-touch
  - tutorial
comments: true
published: false
---
For building Ubuntu Touch on Arch Linux we need a virtual environment (chroot), because building Ubuntu Touch requires gcc 4.8 right now.

__Requirements:__
* `devtools`
```
mkdir <somewhere>
CHROOT=<somewhere>
mkarchroot -C /path/to/pacman.mkarchroot.conf $CHROOT/root base-devel
# Go into the chroot environment with:
arch-nspawn $CHROOT/root /bin/bash
```
The `pacman.mkarchroot.conf`:
<script src="https://gist.github.com/z3ntu/d557ea8ea54c84dbd2ef.js"></script>
Explanation:
`SigLevel = Never` because many of the archive packages' packager PGP signatures are now invalid.
The `Server` entries are a link to the archive from the 1st May of 2014.
The `vps` entry is my personal server which runs my personal program [aaurbs](https://github.com/z3ntu/aaurbs) to build AUR packages, which is used for downloading `phablet-tools`.

__Requirements in the chroot:__

_From personal repository:_
* `phablet-tools`
* `esound`
* `dpkg`
* `launchpadlib` (manually install `python2-keyring` from [the mirror](http://seblu.net/a/archive/repos/2014/09/10/community/os/x86_64/python2-keyring-4.0-2-any.pkg.tar.xz) and then do some hacking... //TODO: DOCUMENT!)

_From normal repositories:_
* `python2`
* `zip`
* `gcc-multilib`
* `lib32-glibc`
* `libxml2`
* `libx11`
* `libxext`
* `alsa-lib`
* `libpulse`
* `mesa`
* `mesa-libgl`
* `lib32-libx11`
* `cpio`
* Manually install [oauth](https://pypi.python.org/pypi/oauth/1.0.1) (will probably make an AUR package for that)

__Guide__
* Symlink some programs to work correctly with Ubuntu Touch
```
ln -s /usr/bin/python2 /usr/bin/python
ln -s /usr/bin/gcc /usr/bin/gcc-4.8
ln -s /usr/bin/g++ /usr/bin/g++-4.8
```
* Change the working directory somewhere (I just used `/home`)
```
cd <somewhere>
```
* Create a `phablet` directory and do the initial bootstrap (__NOTE: This will take a LONG time and download/use up about 17GB of storage.__)
```
mkdir phablet
phablet-dev-bootstrap phablet
```
* Enable caching and source the envsetup.sh file
```
#export USE_CCACHE=1 # doesn't work right now
source build/envsetup.sh
```
* Choose the lunch combo (you can test your environment by using the `aosp_mako_userdebug` combo).
```
lunch
```
* Finally compile Ubuntu Touch with the wanted number of threads (eg `-j4`)
```
make -j7
```
And then get coffee and pray :)

```
'/home/phablet/out/target/product/generic/ubuntu/kernel/boot/vmlinuz-3.4.0-4-goldfish' -> '/home/phablet/out/target/product/generic/ubuntu/kernel/vmlinuz'
```

**For Fairphone 2**
Clone device repo into devices/fairphone/fp2/
Clone kernel repo into kernel/fairphone/fp2/
Clone devices/qcom repo into devices/qcom/common/

__Reference:__
* [ArchWiki (Building Android)](https://wiki.archlinux.org/index.php/Android#Building_Android)
* [Ubuntu Touch (Porting new device)](https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/)
