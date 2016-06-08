---
author: fritzvd
categories:
- android
date: 2014-01-05T20:37:13Z
guid: http://blog.technokrat.nl/?p=501
id: 501
tags:
- adb
- android
- cyanogenmod
- lg optimus 2x
- oops
- recovery
title: Unbricking my LG Optimus 2x with adb
url: /2014/01/05/good-golly-i-almost-bricked-my-phone/
---

So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
``So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
`` 

Then if you accidentally did this to the wrong mmc. Download busybox and also push it to your phone with adb push. Then you have to repartition the disk with fdisk and make a filesystem with mkfs.vfat:
  
```So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
``So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
`` 

Then if you accidentally did this to the wrong mmc. Download busybox and also push it to your phone with adb push. Then you have to repartition the disk with fdisk and make a filesystem with mkfs.vfat:
  
``` 
  
Open fdisk and enter following keys:

fdisk /dev/block/mmcblk0p9
  
n
  
p
  
1 <press enter for defaults> <press enter for defaults> a
  
1

Now make new filesystem with busybox:
  
````So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
``So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
`` 

Then if you accidentally did this to the wrong mmc. Download busybox and also push it to your phone with adb push. Then you have to repartition the disk with fdisk and make a filesystem with mkfs.vfat:
  
```So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
``So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

`So just before new year&#8217;s eve started, I started a (cyanogenmod) update for my phone (lg optimus 2x). Wiped data/cache/dalvik and did not get to flashing the new zip. But then the guests started to arrive and I left it, without having it hooked up to a power supply. Big mistake. There are a number of recovery images out there, (amongst the most well-known: [Clockwork Mod](http://www.clockworkmod.com/ "Clockworkmod") and [TeamWin Recovery Project](http://teamw.in/project/twrp2 "Team Win Recovery Project")). I was on TWRP but it just hung and could not get out of recovery mode. I tried a bunch of stuff. In a nutshell this is what you shouldn&#8217;t do.

Don&#8217;t blindly do anything xda-developers. I accidentally wiped my internal sdcard. (Firstly because I&#8217;m an idiot, and desperate people do stupid things. Desperate idiots the more so.) In stead of overwriting /dev/block/mmcblk0p7 I overwrote 9. Don&#8217;t do that.

So you should also not follow blindly what I say. But in my case (very specific random strange case). I needed to flash the recovery image because for some reason my TWRP was broken. So what I should have done was download a new recovery and flash the /dev/block/mmcbkl0p7.
  
My advice would thus be. Download ADK and startup adb with usb in your phone.

` 
  
Whatever your fstab says behind recovery should be the right block of memory you need to overwrite. Then do this:
  
`` 

Then if you accidentally did this to the wrong mmc. Download busybox and also push it to your phone with adb push. Then you have to repartition the disk with fdisk and make a filesystem with mkfs.vfat:
  
``` 
  
Open fdisk and enter following keys:

fdisk /dev/block/mmcblk0p9
  
n
  
p
  
1 <press enter for defaults> <press enter for defaults> a
  
1

Now make new filesystem with busybox:
  
```` 

Now reboot by pulling out battery or something and start with power and volume up buttons held simultaneously.
  
In recovery mode push the cyanogenmod.zip to your new empty sdcard. And install the zip.

BOOM. You now officialy unsuck