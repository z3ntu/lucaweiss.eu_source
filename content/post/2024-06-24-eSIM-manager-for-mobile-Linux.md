---
title: "An eSIM manager for Mobile Linux"
date: 2024-06-24T13:15:00+02:00
tags:
  - postmarketOS
  - Alpine Linux
  - Qualcomm
  - eSIM
---

For a while eSIM management on Mobile Linux, such as postmarketOS, was just a
dream. **Now it's real!**

## Background

Nowadays many smartphones and other devices have a so-called eSIM - or eUICC -
built-in to the device. This eSIM is essentially a chip on the PCB of the
device that allows an end user to download a SIM profile - essentially all the
data of a SIM card - to said chip and then the modem of the device can use that
chip the same way as it would use any physical SIM card you insert.

This allows for example convenient SIM swapping since you can just download a
profile from your new operator and use it immediately without waiting for a
physical SIM card to arrive by mail.

Similarly there's plenty of "travel eSIM" providers where you can buy e.g. a
30-day data-only eSIM for the country you are travelling to and you can
directly install it on your phone.

Sidenote, while the name might suggest otherwise, there's also removable eSIM
cards in the usual 2FF (mini-SIM), 3FF (micro-SIM), 4FF (nano-SIM) form factor
that you know, such as the ones from [eSIM.me](https://esim.me/),
[5ber](https://esim.5ber.com/) or
[sysmocom](https://shop.sysmocom.de/sysmoEUICC1-eUICC-for-consumer-eSIM-RSP/sysmoEUICC1).

## Time to introduce: eSIM Manager!

Over the past couple of months I've been working on enabling the management of
eSIMs on Qualcomm phones running postmarketOS, and today I'm happy to announce
that version 0.1 of my eSIM Manager is available!

This should work on any phone with Qualcomm SoC (unless it's very old and not
using QRTR) which has an eSIM chip built-in or with a removable eSIM card
inserted.

The source code can be found on
[Codeberg](https://codeberg.org/lucaweiss/lpa-gtk) and the package is now also
available in [Alpine Linux
edge](https://pkgs.alpinelinux.org/packages?name=lpa-gtk&branch=edge&repo=&arch=&maintainer=),
so you can install it on any device running postmarketOS edge today!

<div style="display: flex; flex-wrap: wrap; gap: 10px;">
{{< figure src="/images/lpa-gtk-overview.png" width="200" class="left" >}}
{{< figure src="/images/lpa-gtk-detail.png" width="200" class="left" >}}
{{< figure src="/images/lpa-gtk-download.png" width="200" class="left" >}}
</div>
<br>

In the backend this app is using a project called
[lpac](https://github.com/estkme-group/lpac) which is handling the
actual communication with the eSIM chip.

For lpac I have developed a driver so that lpac can work on Qualcomm phones
("QMI-over-QRTR"). These changes are included in lpac since version
[v2.0.2](https://github.com/estkme-group/lpac/releases/tag/v2.0.2).

The app is built using GTK4 and Libadwaita and uses the Blueprint markup
language for building the UI. The code is written in Python.

## Technical Details

I'm going to spare the details how SIM cards and eSIM cards work in general and
explain only the management-communication side of it since that's what's really
relevant for this project:

In order to do any operation e.g. enable a profile the steps done are the
following:

1. Open a communication channel ("logical channel") with the chip
2. Send a request APDU and receive response APDU
    * These request/response messages are defined in GSMA standards, so this is
      generic to any eSIM chip
    * The content of these APDUs and the message handling is handled by the
      lpac core
3. Close the communication channel

This works the same regardless to whether the eSIM chip is built-in or on a
removable SIM card, from a software-perspective there's no difference.

And for regular SIM card usage, once a profile is enabled via this "management
API" the eSIM can be used like any regular SIM card using the regular "APIs"
the modem uses for authenticating to the network and anything else that a SIM
card does.

## Thanks

This project couldn't have been possible without [Harald Welte
(LaForge)](https://chaos.social/@LaF0rge) getting me curious about eSIMs and
posting lots of useful information for understanding it.

Additionally everything is built on top of the [lpac
project](https://github.com/estkme-group/lpac) which is doing all the heavy
lifting in this, I've 'only' adapted it to work on Qualcomm devices and made a
GUI for it.

And of course thanks to [Fairphone](https://www.fairphone.com/), my employer,
for allowing me to spend time on this project, both for figuring out how eSIM
works in general on Qualcomm devices and spending many more hours adding
support to lpac and building this app.

If you have any questions or comments, feel free to send me an e-mail or
comment on [the Fediverse (Mastodon)
post](https://fosstodon.org/@z3ntu/112671374903329787)!
