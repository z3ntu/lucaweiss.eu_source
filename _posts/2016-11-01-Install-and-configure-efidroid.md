---
layout: post
title: Install and configure EFIDroid on the Fairphone 2
date: 2016-11-01 15:27:00 +0100
tags:
  - efidroid
  - fp2
comments: true
---
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>

### Table of contents:
* [About EFIDroid](#about-efidroid)
* [How to install (FP2)](#how-to-install-fp2)
* [Add a new ROM](#add-a-new-rom)
* [Add a system to the new ROM](#add-a-system-to-the-new-rom)
* [Booting into your new ROM](#booting-into-your-new-rom)

## About EFIDroid
EFIDroid is a relatively new multiboot solution for mobile devices. It is based on the EFI implementation by Intel (EDK2).  
For more information and support, please visit to the [Fairphone Forum thread](https://forum.fairphone.com/t/efidroid-multiboot-for-the-fairphone-2/23344).

## How to install (FP2)
* Download the EFIDroid Manager app from Google Play: [https://play.google.com/store/apps/details?id=org.efidroid.efidroidmanager](https://play.google.com/store/apps/details?id=org.efidroid.efidroidmanager).
* Go to **Install/Update**  
![](/images/efidroid/sidebar.png){:width="300" .toggle-image}
* Click **Install**:  
![](/images/efidroid/install.png){:width="300" .toggle-image}
* It should be successfully installed!  
![](/images/efidroid/installed.png){:width="300" .toggle-image}

## Add a new ROM
* Before you do any of this you should download a ROM .zip file (for example [FP Open 16.09](http://storage.googleapis.com/fairphone-updates/7114445d-6560-440c-9c9f-44639808f7a7/fp2-sibon-16.09.0-ota-userdebug.zip)) and put it on your SD card (`/storage/sdcard1/` and **!!NOT!!** `/sdcard`!).
* To add a ROM click the **FAB** (Floating Action Button)  
![](/images/efidroid/mgr_systems_empty.png){:width="300" .toggle-image}
* Choose in the screen `/data/media/0/multiboot` as location.  
![](/images/efidroid/mgr_rom_new.png){:width="300" .toggle-image}
* Enter a **name** for the ROM  
![](/images/efidroid/mgr_rom_configured.png){:width="300" .toggle-image}
* You can leave the partitions as they are (Schema `LoopSystem + BindOther`) and press the **tick** in the top right corner.  
![](/images/efidroid/mgr_rom_partitions_finished.png){:width="300" .toggle-image}
* Now you can see that your newly created ROM is in the list.  
![](/images/efidroid/mgr_systems_one.png){:width="300" .toggle-image}
* Then **reboot**  
![](/images/efidroid/reboot.png){:width="300" .toggle-image}

## Add a system to the new ROM
Once you are in the **UEFI**, you can navigate around with **volume down** to go down, **volume up** to go up and the **power** button to confirm your selection.

* To flash a ROM the empty slot, select **TWRP (Internal)** and press **power**.
![](/images/efidroid/uefi_twrp.png){:width="300" .toggle-image}
* Next select your newly created ROM  
![](/images/efidroid/uefi_twrp_os.png){:width="300" .toggle-image}
* You will land in **TWRP** and be greeted with a warning about keeping the system partition **readonly**. Swipe the slider at the bottom to acknowledge it.
* Click **Install**, select the **Micro SDcard** at the top.  
![](/images/efidroid/twrp_2.png){:width="300" .toggle-image}
* Select for example the file `fp2-sibon-16.09.0-ota-userdebug.zip`.  
![](/images/efidroid/twrp_3.png){:width="300" .toggle-image}
* Disable the **Zip file signature verification** and slide the confirmation bar.
![](/images/efidroid/twrp_4.png){:width="300" .toggle-image}
* Everything should be good and you can reboot!  
![](/images/efidroid/twrp_5.png){:width="300" .toggle-image}

## Booting into your new ROM
* **Select** your new ROM and press the **power** button. *Do not be put off because of the long "Booting \<romname>" screen as FP Open plays the boot animation very late (unfortunately).*  
![](/images/efidroid/boot_secondary.png){:width="300" .toggle-image}
* **Aaaand we are in!**  
![](/images/efidroid/booted.png){:width="300" .toggle-image}

**If you have questions, please ask in the Fairphone Forum thread linked at the top.**

<div style="position:fixed;right:0;bottom:0; user-select: none;">
<div style="background-color:gray; color:white; cursor: pointer; margin-right: 10px; margin-bottom: 10px; padding: 5px; border-radius: 10px" width="100" height="100" onclick="$('.toggle-image').css('display', 'none');">Disable images</div>
<div style="background-color:gray; color:white; cursor: pointer; margin-right: 10px; margin-bottom: 10px; padding: 5px; border-radius: 10px" width="100" height="100" onclick="$('.toggle-image').css('display', 'inline');">Enable images</div>
</div>
