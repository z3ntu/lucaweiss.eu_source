---
title: SSH on Android
date: 2015-11-03 10:40:00 +0100
tags:
  - android
  - ssh
  - tutorial
aliases:
  - /2015/11/03/SSH-on-Android.html
---
**Installing the SSH binary on Android (for use with adb shell):**

Install [SSHDroid](https://play.google.com/store/apps/details?id=berserker.android.apps.sshdroid)

Launch SSHDroid and accept the superuser request

Then make sure you have your Android device connected with access to adb!
{{< highlight shell >}}
$ adb shell
$ su
$ mount -o rw,remount /system
$ cp /data/data/berserker.android.apps.sshdroid/dropbear/ssh /system/bin/ssh
{{< / highlight >}}
