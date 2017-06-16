---
layout: post
title: Cross-compiling native Linux applications for Android
date: 2015-12-12 20:23:00 +0100
tags:
  - android
  - tutorial
comments: true
---

# Here's how you can cross-compile "normal" Linux applications for Android!

### _This post will be updated sometimes!_

- For the `android_configure` script download [this script](https://gist.github.com/z3ntu/57b95b02ebe8e153d5a8), place it in your `~/bin` folder and (if not already) add `~/bin` to your `PATH` variable.
- To create a standalone toolchain use something like the following command (run from your NDK root-dir):
<script src="https://gist.github.com/z3ntu/4285eb6fd4327caa6fd8.js"></script>

### Ncurses
Add `ac_cv_header_locale_h=no` to your `android_configure` script to the line `export CC` (example: `export CC=${CROSS_PATH}/${CROSS_COMPILE}-gcc ac_cv_header_locale_h=no`)
{% highlight shell %}
android_configure --enable-widec
make
make install
{% endhighlight %}

### Htop
{% highlight shell %}
android_configure
make
make install
{% endhighlight %}

### GnuTLS
{% highlight shell %}
android_configure --without-p11-kit
make
make install
{% endhighlight %}

### Wget
{% highlight shell %}
android_configure
patch src/gnutls.c < ../TOOLS/gnutls.c.patch
make
make install
{% endhighlight %}

### Curl
{% highlight shell %}
android_configure
make
make install
{% endhighlight %}

### Libiconv
{% highlight shell %}
android_configure --host=arm-linux
make
make install
{% endhighlight %}

### Git
Comment out the parts in `configure.ac` with `ac_cv_fread_reads_directories` and `ac_cv_snprintf_returns_bogus`. Currently on Line 854.
{% highlight shell %}
make configure
android_configure
make NO_NSEC=1
{% endhighlight %}

### Binutils
{% highlight shell %}
android_configure
make
make install
{% endhighlight %}

### Python (not complete)
{% highlight shell %}
android_configure --host=arm-linux --build=arm
not complete!
{% endhighlight %}

---

## GCC

### GMP
{% highlight shell %}
android_configure --host=arm-linux
make
make install
{% endhighlight %}

### MPFR
{% highlight shell %}
android_configure --host=arm-linux
make
make install
{% endhighlight %}

### MPC
{% highlight shell %}
android_configure --host=arm-linux
make
make install
{% endhighlight %}

### GCC
Add `-I<YOUR_NDK_ROOT>/sources/android/support/include` to your CFLAGS (android_configure script)
{% highlight shell %}
android_configure
make
make install
{% endhighlight %}

Thanks for reading!
