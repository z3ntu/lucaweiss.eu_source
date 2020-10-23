---
title: Projects
type: page
---

## Embedded

#### postmarketOS

postmarketOS is a touch-optimized, pre-configured Alpine Linux that can be installed on smartphones and other mobile devices. I have ported postmarketOS to the Fairphone 1, Fairphone 2 and worked on a port for the Pine64 family of devices. Additionally I have contributed many packages and patches to the project. **[Project Website](https://postmarketos.org/)**

#### Fairphone 2 mainline kernel

Currently most Android devices run a very outdated version of Linux which is modified by SoC manufacturers and OEMs and deviate from official Linux kernel releases quite a lot. Work has been work by different organisations, companies and people to upstream these changes to mainline Linux so a smartphone or tablet, which originally came with e.g. Linux 3.4, can also boot a non-modified version of the Linux kernel. That way security and features come directly to a device without the OEM being in the way.
For the Fairphone 2 currently only a limited amount of hardware works but that hopefully can be improved in the future. **[GitHub Link](https://github.com/z3ntu/linux)** - **[kernel.org Patchwork (initial support)](https://patchwork.kernel.org/bundle/z3ntu/FP2-initial/?archive=both&state=*)** - **[kernel.org Patchwork (gpio vibra)](https://patchwork.kernel.org/bundle/z3ntu/gpio-vibra/?state=%2A&archive=both)**

#### TWRP 3.X for Fairphone 2 with `/data` decryption support

Team Win Recovery Project (TWRP) is a popular custom recovery for Android devices with touchscreen support. Ported to the Fairphone 2, included crypto support and submitted it to upstream (now getting official builds as they are released). **[GitHub Link](https://github.com/TeamWin/android_device_fairphone_fp2)** - **[Official download](https://twrp.me/devices/fairphone2.html)**

#### CWM v6.0.1.2 for the ZTE Racer II

ClockworkMod Recovery (CWM) is a custom recovery for Android devices, made by Koushik "Koush" Dutta. Ported to the ZTE Racer II. **[GitHub Link](https://github.com/z3ntu/android_device_zte_racer2)**

#### EFIDroid for the Fairphone 2

An UEFI-based second-stage bootloader which supports multiboot. Ported to the Fairphone 2. **[GitHub Link](https://github.com/efidroid/device/tree/fairphone/fp2)**

## Razer

#### OpenRazer

OpenRazer is an open-source driver and user-space daemon that allows you to manage your Razer peripherals on GNU/Linux. I am developing it, handling issues and packaging the software for many different Linux distributions. Written in C and Python **[GitHub Link](https://github.com/openrazer/openrazer)** - **[Project Website](https://openrazer.github.io/)**

#### RazerGenie

An open-source Qt-based application which is UI for interacting with the [OpenRazer](#openrazer) daemon. Written in C++ and Qt. **[GitHub Link](https://github.com/z3ntu/RazerGenie)**

#### razer_test

A work-in-progress replacement for the [OpenRazer](#openrazer) project which aims to solve design issues present in OpenRazer. Works on Linux, FreeBSD, macOS and Windows. Written in C++. **[GitHub Link](https://github.com/z3ntu/razer_test)**

## Android Apps

#### Nextcloud News

An app which connects to the "News" app for Nextcloud. Written in Kotlin, uses the Android Jetpack libraries and the Nextcloud Single Sign-on API.

#### Schaukuchl Android App

An app which displays the current menu for the restaurant "Schaukuchl" in Vienna. **[GitHub Link](https://github.com/z3ntu/Schaukuchl)**

#### Spengergasse Timetable App

The timetables in our school were generated HTML pages that were not responsive and had other issues. We've developed an Android app that implemented a parser for the HTML tables using jsoup and displayed them in a nice format. The app was later abandoned because the school switched to a newer version of Untis (the timetable software) that had its own Android app.

## Python

#### aaurbs

**a**utomated **a**rch **u**ser **r**epository **b**uild **s**ystem is an automated builder for Arch Linux packages with a webinterface. **[GitHub Link](https://github.com/z3ntu/aaurbs)**

#### DynDNS

A self-written DynDNS client & server. Works with the DigitalOcean DNS API. **[GitHub Link](https://github.com/z3ntu/DynDNS)**

#### Honeypot

Web-based todo list, made as a school project with 3 others. **[GitHub Link](https://github.com/MadeInSpengergasse/Honeypot)** - **[Demo Video](https://youtu.be/8HdV2xxItIM)**

#### Monstercat Connect Notifier

A Telegram bot which sends new releases by the EDM Label "Monstercat" automatically to a Telegram channel. **[GitHub Link](https://github.com/z3ntu/MonstercatConnectNotifier)**

## Browser Extensions

#### JavadocRedirector

This is a Chrome/Opera extension which automatically redirects you from Java 7 Javadoc pages to Java 8 Javadoc pages. **[GitHub Link](https://github.com/z3ntu/JavadocRedirector)** - **[Chrome Web Store](https://chrome.google.com/webstore/detail/javadoc-redirector/pkpckmephcfffdfjemgnekclglhpkcom)**

#### GriesmayerNoFlash

A WebExtension (compatible with Chrome and Firefox 57+) that adds a **Download** button to educational videos on [griesmayer.com](http://griesmayer.com/) which need Flash to play. **[GitHub Link](https://github.com/z3ntu/GriesmayerNoFlash)** - **[Chrome Web Store](https://chrome.google.com/webstore/detail/griesmayernoflash/hcaikojphmgkkdcpcohmmnloolhkjihp)** - **[Firefox Add-on](https://addons.mozilla.org/en-US/firefox/addon/griesmayernoflash/)**

## Others

#### RobotPi

RobotPi is a project for controlling a robot with both a server-side and a client-side component. **[GitHub Server](https://github.com/z3ntu/robotpi_server)** - **[GitHub Client](https://github.com/z3ntu/robotpi_client_android)**
