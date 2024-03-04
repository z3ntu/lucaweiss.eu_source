---
title: "The little NAS under my bed"
date: 2024-03-04T11:00:00+01:00
---

In April 2023 I've built myself a new NAS box to replace a rather old HPE
ProLiant MicroServer Gen8 at my parents place. Since I don't really have any
good space in my apartment it needed to fit under my bed and be reasonably
quiet.

After hearing good things about the ODROID H3+ I've decided to order one with a
case, hard drives and everything else necessary to fulfil this purpose.

# Hardware specs

* ODROID H3+ (Intel Celeron N6005)
* 32 GB SODIMM RAM
* 1 TB NVMe
* 2x 8 TB HDD
* ODROID-H3 Case Type 1
* 19V/7A Power Supply

(and I've also ordered 2x SATA cable for the HDDs; plus an RTC backup battery
but this was unnecessary because one was already included with the ODROID)

# Software

From software side I've installed Debian Linux on the NVMe as boot drive and
the HDDs are in a RAID1 using ZFS which host all the data.

The Debian install is managed using Ansible using some playbooks I've written
which installs the necessary packages and does a little bit of setup where
required.

To run the services like Jellyfin, Nextcloud, Immich, etc. I'm using
docker-compose with a Traefik reverse proxy in front.

The whole box is only accessible via Tailscale (I'm not 100% fan of it, some
components are surprisingly buggy but it works well enough, and it has some
useful features like custom DNS entries which I like).

So all the services can only be accessed from the VPN network, and for the
custom subdomains you can easily get LetsEncrypt certificates using the DNS
challenge. That way the browser is always happy with a green lock, no matter
what device you're accessing it from.

# My review

The box is working really well, I haven't had any problems with it since I
started using it. The only real downtime it had was once when I was travelling
there was a power outage at home so after the power came back the box was still
off and I couldn't turn it on remotely. After coming back home I enabled the
turn-on-after-power-outage feature in the BIOS so this shouldn't happen again.

I cannot complain about the performance at all, Jellyfin is streaming even 4K
content well - even when it has to transcode it thanks for Intel QuickSync.
Immich has no problems even when uploading a bunch of photos and when it's
doing its machine learning tasks on them.

The fan from the case is not really noticable, the only thing that's bothering
me a bit is that the hardware drives make some noise when the drive head is
seeking (I think?) but it's not really solvable I think apart from buying
pricey SSDs. But it's very quickly drowned out by any other sounds - either by
sounds from inside the room or from outside, and it's also never been a problem
while sleeping.

# Conclusion

For about €800 you can get a very capable NAS that is reasonably quiet, doesn't
consume a lot of power and is generally nice to have around.

I definitely recommend this for others, especially if they can put it in a
closet somewhere where the hard drive noise doesn't matter. Or keep less data
and buy some SATA SSDs instead, then it's nearly quiet.
