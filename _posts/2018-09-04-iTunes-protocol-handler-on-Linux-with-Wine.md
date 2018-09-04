---
layout: post
title: iTunes protocol handler on Linux with Wine
date: 2018-09-04 16:19:00 +0200
tags:
  - wine
comments: true
---
Today I have tried adding my PayPal account to my iTunes (installed with Wine) Account but discovered, that adding my PayPal account as a payment method didn't work. After inspecting the network traffic, I found that my browser (Firefox) was redirected to an `itmss://` URL, but Firefox didn't know how to handle that and did nothing. To get it working yourself, follow the next steps:

Assuming you already have iTunes installed and are using Firefox, open `about:config` in Firefox, accept the prompt, right-click and select New -> Boolean. In the dialog enter `network.protocol-handler.expose.itmss` as preference name and select `false` as value. After that, restart Firefox.

Next, create a new file somewhere (I chose `/usr/local/bin/`), called for example `itunes-url` and make it executable (`chmod +x filename`). Put the following content into the file while adjusting the paths to the Wine prefix and the installation directory.
```sh
#!/bin/sh

env WINEPREFIX="/home/luca/.wine_itunes" wine /home/luca/.wine_itunes/drive_c/Program\ Files/iTunes/iTunes.exe /url "$@"
```
I found this invocation with Wine regedit.exe under `HKEY_CLASSES_ROOT\itmss\shell\open\command`, based on [this website](https://support.shotgunsoftware.com/hc/en-us/articles/219031308-Launching-applications-using-custom-browser-protocols).

Then you can go into iTunes and add your PayPal payment method. Once you've logged in and accepted the PayPal prompts, you should get a popup from Firefox where you should select the application to handle the `itmss` URL. Select the `itunes-url` script, you created before and click "Open link". Now iTunes should get the URL from PayPal and you can confirm the new payment method in iTunes.

Have fun!
