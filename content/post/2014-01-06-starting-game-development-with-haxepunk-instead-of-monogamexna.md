---
author: fritzvd
categories:
- development
- game
date: 2014-01-06T20:25:23Z
excerpt: Use Haxe and HaxePunk you will feel good.
guid: http://blog.technokrat.nl/?p=484
id: 484
tags:
- c#
- haxe
- haxepunk
- openfl
- xna
title: Starting Game Development with HaxePunk instead of MonoGame/XNA
url: /2014/01/06/starting-game-development-with-haxepunk-instead-of-monogamexna/
---

So I started venturing off in a direction in which I have no experience what so ever. Only on the consumer-side of things ;-). Game development. Of course I had no idea what I was doing. Still don&#8217;t.

To start with I had no idea where to start. Lately I have been looking into Unity 3D and Unreal engine, but then I realized I suck at drawing and have no idea how to start with 3d. So then I was searching around for 2d engines and started out with Cocos2D-x and some other C++ based engines (can&#8217;t remember which), but that was kind of a hassle to get started and my builds would not run on my phone. Also I did not really get there style of documentation.

### MonoGame

After looking through tutorials and stuff, I settled on the XNA framework, or at least the open source version &#8211;> <a title="monogame" href="http://monogame.net/" target="_blank">MonoGame</a>. It is pretty awesome, some of the most legendary indie games: <a title="Supergiant games" href="http://supergiantgames.com/index.php/media/" target="_blank">Bastion</a>, <a title="Fez" href="http://fezgame.com/" target="_blank">FEZ</a> and <a title="smb" href="http://supermeatboy.com/" target="_blank">Super Meat Boy</a> are created with the closed source variant. Which for me was reason enough to find out more. Moreover the Bastion team (supergiant games) used MonoGame to port it to the iPad/iPhone.
  
So starting out with some tutorials I was making quite some headway in a short amount of time. C# is a very approachable language and MonoDevelop a lightweight IDE. Especially after trying out the badly indented (illegible) examples I found of all these different C++ libraries.

After having a first version that featured some smooth running sprites I thought it interesting to test the performance in an iPad simulator. The built worked well on Linux and on the Mac Desktop, but building it for iOS gave me some problems. BECAUSE YOU CAN&#8217;T. Not for free anyways. Xamarin charges you $299,- a year for you to be able to build for Android and iOS.

### Haxe and OpenFL

I was pretty disheartened, because I remembered all the hassle and strange examples I found with the plethora of frameworks I tried out before and did not really want to go back to that. On some website I found an article on <a href="http://openfl.org/" title="openfl" target="_blank">OpenFL</a> an open source flash framework that compiles to *. HTML5, windows, mac, linux, android, ios, blackberry, tizen. You name it. Also used to make this little gem: <a href="http://rymdkapsel.com/" title="rymdkapsel" target="_blank">rymdkapsel</a> A port of FlashPunk in Haxe <a href="http://haxepunk.com/" title="HaxePunk" target="_blank">HaxePunk</a> had some proper tutorials, it is maintained and was ported chiefly by<a href="http://matttuttle.com/" title="Matt Tuttle" target="_blank">Matt Tuttle</a>. (thanks for that).
  
The setup of OpenFL and haxepunk is very easy and straightforward and I am easily building to all the promissed targets. I can test my ios builds in the simulator on my Mac and send *.swf links to friends and invite alpa-testers for my Android APK&#8217;s. It is awesome.

For those to lazy to open the links and find out how easy it really is do this:
  
`So I started venturing off in a direction in which I have no experience what so ever. Only on the consumer-side of things ;-). Game development. Of course I had no idea what I was doing. Still don&#8217;t.

To start with I had no idea where to start. Lately I have been looking into Unity 3D and Unreal engine, but then I realized I suck at drawing and have no idea how to start with 3d. So then I was searching around for 2d engines and started out with Cocos2D-x and some other C++ based engines (can&#8217;t remember which), but that was kind of a hassle to get started and my builds would not run on my phone. Also I did not really get there style of documentation.

### MonoGame

After looking through tutorials and stuff, I settled on the XNA framework, or at least the open source version &#8211;> <a title="monogame" href="http://monogame.net/" target="_blank">MonoGame</a>. It is pretty awesome, some of the most legendary indie games: <a title="Supergiant games" href="http://supergiantgames.com/index.php/media/" target="_blank">Bastion</a>, <a title="Fez" href="http://fezgame.com/" target="_blank">FEZ</a> and <a title="smb" href="http://supermeatboy.com/" target="_blank">Super Meat Boy</a> are created with the closed source variant. Which for me was reason enough to find out more. Moreover the Bastion team (supergiant games) used MonoGame to port it to the iPad/iPhone.
  
So starting out with some tutorials I was making quite some headway in a short amount of time. C# is a very approachable language and MonoDevelop a lightweight IDE. Especially after trying out the badly indented (illegible) examples I found of all these different C++ libraries.

After having a first version that featured some smooth running sprites I thought it interesting to test the performance in an iPad simulator. The built worked well on Linux and on the Mac Desktop, but building it for iOS gave me some problems. BECAUSE YOU CAN&#8217;T. Not for free anyways. Xamarin charges you $299,- a year for you to be able to build for Android and iOS.

### Haxe and OpenFL

I was pretty disheartened, because I remembered all the hassle and strange examples I found with the plethora of frameworks I tried out before and did not really want to go back to that. On some website I found an article on <a href="http://openfl.org/" title="openfl" target="_blank">OpenFL</a> an open source flash framework that compiles to *. HTML5, windows, mac, linux, android, ios, blackberry, tizen. You name it. Also used to make this little gem: <a href="http://rymdkapsel.com/" title="rymdkapsel" target="_blank">rymdkapsel</a> A port of FlashPunk in Haxe <a href="http://haxepunk.com/" title="HaxePunk" target="_blank">HaxePunk</a> had some proper tutorials, it is maintained and was ported chiefly by<a href="http://matttuttle.com/" title="Matt Tuttle" target="_blank">Matt Tuttle</a>. (thanks for that).
  
The setup of OpenFL and haxepunk is very easy and straightforward and I am easily building to all the promissed targets. I can test my ios builds in the simulator on my Mac and send *.swf links to friends and invite alpa-testers for my Android APK&#8217;s. It is awesome.

For those to lazy to open the links and find out how easy it really is do this:
  
` 

Now you can start being aweswome and build your crazy ideas for android.

(Next time I&#8217;ll give some code excerpts and a flash file to test out).

**UPDATE:**
  
I&#8217;ve written a follow up on <a href="http://blog.technokrat.nl/?p=522" title="Particle Emitters" target="_blank">particle emitters in haxepunk</a>