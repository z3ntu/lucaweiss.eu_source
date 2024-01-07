---
title: Signing boot images for fastboot
date: 2017-06-16 08:55:00 +0200
tags:
  - android
  - fp2
comments: true
aliases:
  - /2017/06/16/Signing-boot-images.html
---
If you have ever seen the error `FAILED (remote: bootimage: incomplete or not signed)`, here's the solution (at least for the Fairphone 2 😉):

Download the `BootSignature.jar` file from my server (or compile it yourself from the LineageOS 14.1 tree with the command `mka BootSignature`).
```shell
curl -O https://public.lucaweiss.eu/BootSignature.jar
```

Download the `make_key` tool from the LineageOS GitHub.
```shell
curl -O https://raw.githubusercontent.com/LineageOS/android_development/cm-14.1/tools/make_key
```

Make the script executable
```shell
chmod +x make_key
```
Generate the key with
```shell
./make_key keystore '/C=US/ST=California/L=Mountain View/O=Android/OU=Android/CN=Android/emailAddress=android@android.com'
```
Put the `BootSignature.jar`, `keystore.pk8` and `keystore.x509.pem` in a directory of your choice.

Put the following script into a location in the PATH (`~/bin` or `/usr/local/bin` should be good) **and replace the first variable with the location you put the three files in**:

```shell
#!/bin/bash

KEYSTORE_TOOLS=/location/to/jar_and_certs

IMGFILE=$1

if [ ! -n "$1" ]; then
  echo "Usage: $0 <file.img>"
  exit 1
fi

java -jar $KEYSTORE_TOOLS/BootSignature.jar /boot $IMGFILE $KEYSTORE_TOOLS/keystore.pk8 $KEYSTORE_TOOLS/keystore.x509.pem $IMGFILE.signed
```
Don't forget to make that script executable! (`chmod +x`)

Now you can use the script to sign your images and then boot it
```shell
sign_img boot.img && fastboot boot boot.img.signed
```

Have fun!
