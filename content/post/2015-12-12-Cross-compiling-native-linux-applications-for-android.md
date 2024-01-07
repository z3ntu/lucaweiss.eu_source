---
title: Cross-compiling native Linux applications for Android
date: 2015-12-12 20:23:00 +0100
tags:
  - android
  - tutorial
comments: true
aliases:
  - /2015/12/12/Cross-compiling-native-linux-applications-for-android.html
---

Here's how you can cross-compile "normal" Linux applications for Android!

**Note, that I cannot give you any help in following this. It worked(tm) when I wrote this but don't know about now.**

* For the `android_configure` script download [this script](https://gist.github.com/z3ntu/57b95b02ebe8e153d5a8), place it in your `~/bin` folder and (if not already) add `~/bin` to your `PATH` variable.
* To create a standalone toolchain use something like the following command (run from your NDK root-dir):
{{< gist z3ntu 4285eb6fd4327caa6fd8 >}}

### Ncurses
Add `ac_cv_header_locale_h=no` to your `android_configure` script to the line `export CC` (example: `export CC=${CROSS_PATH}/${CROSS_COMPILE}-gcc ac_cv_header_locale_h=no`)
```shell
android_configure --enable-widec
make
make install
```

### Htop
```shell
android_configure
make
make install
```

### GnuTLS
```shell
android_configure --without-p11-kit
make
make install
```

### Wget
```shell
android_configure
patch src/gnutls.c < ../TOOLS/gnutls.c.patch
make
make install
```

### Curl
```shell
android_configure
make
make install
```

### Libiconv
```shell
android_configure --host=arm-linux
make
make install
```

### Git
Comment out the parts in `configure.ac` with `ac_cv_fread_reads_directories` and `ac_cv_snprintf_returns_bogus`. Currently on Line 854.
```shell
make configure
android_configure
make NO_NSEC=1
```

### Binutils
```shell
android_configure
make
make install
```

### Python (not complete)
```shell
android_configure --host=arm-linux --build=arm
not complete!
```

---

## GCC

### GMP
```shell
android_configure --host=arm-linux
make
make install
```

### MPFR
```shell
android_configure --host=arm-linux
make
make install
```

### MPC
```shell
android_configure --host=arm-linux
make
make install
```

### GCC
Add `-I<YOUR_NDK_ROOT>/sources/android/support/include` to your CFLAGS (android_configure script)
```shell
android_configure
make
make install
```

Thanks for reading!
