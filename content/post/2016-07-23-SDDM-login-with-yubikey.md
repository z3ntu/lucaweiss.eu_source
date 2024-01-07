---
title: SDDM login with a Yubikey on Arch Linux
date: 2016-07-23 11:56:00 +0200
tags:
  - yubikey
  - login
  - tutorial
aliases:
  - /2016/07/23/SDDM-login-with-yubikey.html
---

If you are wondering how you can login with a Yubikey into your system with SDDM, here are the steps:

**Step 1:**
Install [yubico-pam](https://www.archlinux.org/packages/?name=yubico-pam) from [community].

**Step 2:** Edit the file `/etc/yubikeys` and insert text in the following format:
```
<username>:<yubikey_token_id>
# eg
luca:cclcclcclccl
```
If you don't know what the token ID from your yubikey is, just open a text editor and press the button on your yubikey to create a one time password (=OTP). Then take the **first twelve characters** from that string, which is your token id. If you are too lazy to count, you can also press the button multiple times and take the part that stays the same at the beginning.

**Step 3:** Edit the file `/etc/pam.d/system-auth` that it looks like the following. Note, that by editing this file you allow these users you specified in Step 2 to login nearly everywhere in your system with the yubikey.
```
#%PAM-1.0

auth sufficient pam_yubico.so debug id=1 authfile=/etc/yubikeys

auth required pam_unix.so try_first_pass nullok
# and more lines
```
**If you don't want fancy debug lines, remove the 'debug' parameter.
If you don't want the ability to just login with your yubikey, replace the 'sufficient' parameter with 'required'. But note, that you will be locked out of your system if you lose your yubikey or don't have it with you!**

**Step 4:** Now you should be able to use your Yubikey to login into your session, unlock the lockscreen and even use it for `sudo` access.
*If you don't want global Yubikey authentication, you can also not add the line in step 3 into the `system-auth` file but into the `sddm` file in the `/etc/pam.d/` directory. But also note, that you won't be able to use your Yubikey to unlock the lockscreen, just to login!*

I hope this was helpful. If you have any questions, don't hesitate to ask in the comments.
You can also take a look at the [Fedora wiki article about Yubikey authentication](https://fedoraproject.org/wiki/Using_Yubikeys_with_Fedora), which is much better than the Arch wiki at the moment.
