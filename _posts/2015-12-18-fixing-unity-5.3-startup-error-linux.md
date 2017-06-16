---
layout: post
title: Fixing the Unity3D 5.3 startup error on Linux
date: 2015-12-18 19:23:00 +0100
tags:
  - unity3d
  - tutorial
comments: true
---

If you experience this error with the newest Unity3D Build on Linux, just do this one simple step:

![Screenshot](/images/unity3d_startup_error.png){:width="500"}


- Create the folder `~/.local/share/unity3d` and you are good to go!

__Now have fun with Unity!__

In more detail, the "main" error message in `~/.config/unity3d/Editor.log` is

> CopyPackageFile failed, unable to copy /opt/Unity/Editor/Data/Resources/Packages/unity-editor-home-0.0.7.tgz to /home/luca/.local/share/unity3d/Packages/unity-editor-home-0.0.7.tgz
>
> CopyPackageFile failed, unable to copy /opt/Unity/Editor/Data/Resources/Packages/unityeditor-cloud-hub-0.0.1.tgz to /home/luca/.local/share/unity3d/Packages/unityeditor-cloud-hub-0.0.1.tgz
