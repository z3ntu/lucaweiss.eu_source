---
title: Projects
type: page
---

A non-exhaustive list of activities around open-source software. You can find links to some of the code forges I'm active on the [About](/about/) page.

## Embedded

### postmarketOS

postmarketOS is a Linux distribution for mobile devices and more. It's based on Alpine Linux and can be installed on smartphones and many other mobile devices.
I'm part of the 'Core Contributors' of the project, and part of the infrastructure team which manages the hosting of the website, wiki, Matrix server etc.
Amongst other things I've ported postmarketOS to many devices, including all generations of Fairphone (1, 2, 3, 4 & 5), several Qualcomm Snapdragon 801 devices, several Snapdragon 400-based smartwatches, and in the past I've also worked on the PINE64 family of devices (such as the PinePhone, PineTab, etc).

* [Project Website](https://postmarketos.org/)
* [Team Page](https://postmarketos.org/core-contributors/#luca-weiss-z3ntu)

### Linux kernel development

Currently most Android devices run a very outdated version of Linux which is modified by SoC manufacturers and OEMs and deviate from official Linux kernel releases quite a lot. Work has been work by different organisations, companies and people to upstream changes to mainline Linux so that a smartphone, tablet or smartwatch, which originally came with old and heavily modified Linux versions, can also boot a non-modified version of the Linux kernel. That way security and features come directly to a device without the SoC manufacturer or OEM being in the way.

My work is primarily focused around device and driver bringup for the various Fairphone devices but also devices from other OEMs using similar chipsets.

* [Commits in upstream Linux](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/?qt=author&q=Luca+Weiss)
* [SC7280-mainline repository](https://github.com/sc7280-mainline/linux)
* [SM6350-mainline repository](https://github.com/sm6350-mainline/linux)
* [MSM8974-mainline repository](https://github.com/msm8974-mainline/linux)
* [MSM8226-mainline repository](https://github.com/msm8226-mainline/linux)

### Official TWRP builds for Fairphone 2, 4 and 5

Team Win Recovery Project (TWRP) is a popular custom recovery for Android devices with touchscreen support. The Fairphone 2, Fairphone 4 and Fairphone 5 builds are maintained by me.

* [GitHub Link - Fairphone 2](https://github.com/TeamWin/android_device_fairphone_FP2)
* [Official download - Fairphone 2](https://twrp.me/fairphone/fairphone2.html)
* [GitHub Link - Fairphone 4](https://github.com/TeamWin/android_device_fairphone_FP4)
* [Official download - Fairphone 4](https://twrp.me/fairphone/fairphone4.html)
* [GitHub Link - Fairphone 5](https://github.com/TeamWin/android_device_fairphone_FP5)
* [Official download - Fairphone 5](https://twrp.me/fairphone/fairphone5.html)

## Razer

### OpenRazer

OpenRazer is an open-source driver and user-space daemon that allows you to manage your Razer peripherals on GNU/Linux. I'm the maintainer for the project - developing it, handling issues, reviewing changes and packaging the software for many different Linux distributions. Written in C and Python.

* [GitHub Link](https://github.com/openrazer/openrazer)
* [Project Website](https://openrazer.github.io/)

### RazerGenie

An open-source Qt-based application which is a UI for interacting with the [OpenRazer](#openrazer) daemon. Written in C++ and Qt.

* [GitHub Link](https://github.com/z3ntu/RazerGenie)

### razer_test

An experimental replacement for the [OpenRazer](#openrazer) project which aims to solve design issues present in OpenRazer. Works on Linux, FreeBSD, macOS and Windows. Written in C++.

* [GitHub Link](https://github.com/z3ntu/razer_test)

---

# Archive

These are some projects I've worked on in the past but due to various reasons do not maintain anymore.

## Embedded

### CWM v6.0.1.2 for the ZTE Racer II

ClockworkMod Recovery (CWM) is a custom recovery for Android devices, made by Koushik "Koush" Dutta. Ported to the ZTE Racer II.

* [GitHub Link](https://github.com/z3ntu/android_device_zte_racer2)

### EFIDroid for the Fairphone 2

An UEFI-based second-stage bootloader which supports multiboot. Ported to the Fairphone 2.

* [GitHub Link](https://github.com/efidroid/device/tree/fairphone/fp2)

## Android Apps

### Nextcloud News

An app which connects to the "News" app for Nextcloud. Written in Kotlin, uses the Android Jetpack libraries and the Nextcloud Single Sign-on API.

### Schaukuchl Android App

An app which displays the current menu for the restaurant "Schaukuchl" in Vienna.

* [GitHub Link](https://github.com/z3ntu/Schaukuchl)

### Spengergasse Timetable App

The timetables in our school were generated HTML pages that were not responsive and had other issues. We've developed an Android app that implemented a parser for the HTML tables using jsoup and displayed them in a nice format. The app was later abandoned because the school switched to a newer version of Untis (the timetable software) that had its own Android app.

## Python

### aaurbs

Automated Arch User Repository Build System is an automated builder for Arch Linux packages with a webinterface.

* [GitHub Link](https://github.com/z3ntu/aaurbs)

### DynDNS

A self-written DynDNS client & server. Works with the DigitalOcean DNS API.

* [GitHub Link](https://github.com/z3ntu/DynDNS)

### Honeypot

Web-based todo list, made as a school project with 3 others.

* [GitHub Link](https://github.com/MadeInSpengergasse/Honeypot)
* [Demo Video](https://youtu.be/8HdV2xxItIM)

### Monstercat Connect Notifier

A Telegram bot which sends new releases by the EDM Label "Monstercat" automatically to a Telegram channel.

* [GitHub Link](https://github.com/z3ntu/MonstercatConnectNotifier)

## Browser Extensions

### JavadocRedirector

This is a Chrome/Opera extension which automatically redirects you from Java 7 Javadoc pages to Java 8 Javadoc pages.

* [GitHub Link](https://github.com/z3ntu/JavadocRedirector)
* [Chrome Web Store](https://chrome.google.com/webstore/detail/javadoc-redirector/pkpckmephcfffdfjemgnekclglhpkcom)

### GriesmayerNoFlash

A WebExtension (compatible with Chrome and Firefox 57+) that adds a **Download** button to educational videos on [griesmayer.com](http://griesmayer.com/) which need Flash to play.

* [GitHub Link](https://github.com/z3ntu/GriesmayerNoFlash)

## Others

### RobotPi

RobotPi is a project for controlling a robot with both a server-side and a client-side component.

* [GitHub Server](https://github.com/z3ntu/robotpi_server)
* [GitHub Client](https://github.com/z3ntu/robotpi_client_android)
