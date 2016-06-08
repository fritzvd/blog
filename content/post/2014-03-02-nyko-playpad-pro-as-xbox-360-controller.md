---
author: fritzvd
categories:
- game
date: 2014-03-02T19:15:06Z
guid: http://blog.technokrat.nl/?p=520
id: 520
tags:
- linux
- mapping nyko playpad
- mapping xbox controller
- nyko playpad pro
title: Nyko Playpad Pro or * as Xbox 360 controller on linux
url: /2014/03/02/nyko-playpad-pro-as-xbox-360-controller/
---

This is basically a fancy note to self. Last year in my pre vacation spending spree, I boughy myself (and my brother) a <a href="http://www.nyko.com/products/product-detail/?name=PlayPad+Pro" title="nyko" target="_blank">NYKO Playpad Pro.</a> A pretty cool gamepad for Android. I had lots of fun playing GTA Vice CIty on my trip to Italy. Playing SNES games etc.

However I tried to hook it up to my Linux pc and thought I would be able to use it with my new go to MetroidVania platformer: <a href="http://guacamelee.com/" title="guacamelee" target="_blank">Guacamelee</a>. Especially with Co-Op because I only have one Xbox 360 controller. In comes <a href="http://pingus.seul.org/~grumbel/xboxdrv/" title="xboxdrv" target="_blank">xboxdrv</a>.

Basically I need to enter this into my terminal and it runs (be sure to install 0.8.5 version (and up I guess) of xboxdrv)
  
Of course depending on what input event devices it is mapped to.

<pre><code class="syntax bash">sudo xboxdrv --evdev /dev/input/event13 --evdev-absmap ABS_X=x1,ABS_Y=y1,ABS_GAS=RT,ABS_BRAKE=LT,ABS_Z=X2,ABS_RZ=y2 --evdev-keymap BTN_A=A,BTN_B=b,BTN_X=x,BTN_Y=y,BTN_START=start,BTN_SELECT=back,BTN_THUMBL=tl,BTN_THUMBR=tr,BTN_TL=LB,BTN_TR=RB

</code></pre>