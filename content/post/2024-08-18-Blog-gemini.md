---
title: "My website and blog is available via Gemini"
date: 2024-08-18T22:45:00+02:00
tags:
  - Gemini
---

[Gemini](https://geminiprotocol.net/) is a neat piece of technology. The Gemini
protocol somewhat comparable to HTTP and the Gemtext file format comparable to
HTML. But it's simple. Like so simple that writing a client or server is
actually doable.

All popular web browsers (Chromium and its skins - and Firefox) have their
roots in the 1990's and there hasn't been any new web browser becoming usable
in many years. Not because people haven't tried - I'm sure many people have -
but because the standards around the modern web are so gigantic that it's just
not feasable to develop a web browser from scratch.

The best (and only?) attempt I've seen is [Ladybird](https://ladybird.dev/),
which is "an ongoing project to build a truly independent web browser from
scratch". And I'm very happy to see this project continuing to get better, but
it's still far from a usable web browser for everything you want to do in life.

So, back to Gemini!

Earlier in 2024 I've installed a Gemini server on the same host which is
running Apache2 for serving my website/blog and after a few commands for setup
it was running.

Since my website content is written in Markdown and built using Hugo, it was
not a difficult exercise to add "Gemtext generation" to the build pipeline and
using a few regex replacements we can generate a version of the website that
mostly resembles Gemtext.

Of course, that generated version is definitely not perfect and sometimes some
Markdown-isms or HTML bits slip through, but for being essentially zero
maintenance it's pretty great. Manually polishing a separate Gemtext version
would be better of course but for now this version will do.

For viewing Gemini pages you can find clients for most platforms, notably I
like "Lagrange" on Linux and "Buran" on Android. Of course there's plenty other
clients as well, including clients for your terminal and everything else.

Hope you enjoy!

![Screenshot of my website in the Lagrange client](/images/gemini-website.png)
