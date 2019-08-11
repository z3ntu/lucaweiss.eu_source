---
title: Google Play Services with Android 6.0 Marshmallow and Genymotion
date: 2015-12-10 12:24:00 +0100
tags:
  - android
  - tutorial
aliases:
  - /2015/12/10/play-services-with-genymotion.html
---

So, I think you want to install the Google Play Store & Services with an Android 6.0 Marshmallow Emulator?

To do that, follow either the long or the short version.

You need the following three files:

- [Genymotion-ARM-Translation_v1.1.zip](http://www.mirrorcreator.com/files/0ZIO8PME/Genymotion-ARM-Translation_v1.1.zip_links)
- [gapps-L-4-21-15.zip](https://www.androidfilehost.com/?fid=96042739161891406)
- [benzo-gapps-M-20151011-signed-chroma-r3.zip](https://www.androidfilehost.com/?fid=24052804347835438).

__Short version:__

- Download all three files.
- Create an emulator with the `Nexus 5X` image and start it.
- Flash `Genymotion-ARM-Translation_v1.1.zip` and reboot.
- Flash `gapps-L-4-21-15.zip` and reboot.
- Sign into your Google Account.
- Flash `benzo-gapps-M-20151011-signed-chroma-r3.zip` and reboot.
- You are finished!

__Long version:__

Then start GenyMotion and add an emulator with the preset `!! PREVIEW - Google Nexus 5X - 6.0.0 - API 23 - 1080x1920`. Start it and wait until you see the homescreen.

The next step is to flash the `Genymotion-ARM-Translation_v1.1.zip`. To do that, just drap & drop the .zip file onto the emulator.

Turn the emulator off with the power button and wait until it is powered off. Then turn it on again.


Now repeat the last two steps with `gapps-L-4-21-15.zip` (flash, reboot).

If you are finished with that, sign into your Google account (you can do that when opening the Play Store). If you are successfully logged in, flash the `benzo-gapps-M-20151011-signed-chroma-r3.zip` file and reboot again.

Have fun with your working Google Play Store!


Source: [gist.github.com](https://gist.github.com/wbroek/9321145)
