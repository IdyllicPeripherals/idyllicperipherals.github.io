---
title: 'Enable VoLTE on the Honor 90 Lite'
date: 2024-05-24 00:00:00
description: Forcefully enabling VoLTE on Android.
featured_image: '/images/Photo_Blog/Honor_Apps.jpg'
---

### ENABLE VoLTE ON THE HONOR 90 LITE IN AUSTRALIA

<div class="gallery3" data-columns="1">
	<img src="/images/Photo_Blog/Honor_After_2.jpg">
</div>


Hopefuly this write up can help some people. 

I’ve been using Kogan Mobile for many years now because they offer a very good value 365 day mobile plan.

However, recently, 3G is no longer being supported by the Vodafone network and this has forced me to finally upgrade my Honor 8 to something new, the Honor 90 Lite.

I did some research and it looked like there wouldn’t be any issues using an Honor 90 Lite in Australia even though the phone is not sold here. GSMarena and the official Honor website showed this phone was able to use LTE-FDD/LTE-TDD networks.

The Honor 90 Lite I purchased was the CRT-NX1 Global version in Midnight Black and costed a total of 280AUD, including shipping and taxes, from Aliexpress.

When I installed the Kogan Sim card I was disappointed to find out I could not make any phone calls even though the Mobile Data was working. There was nothing in the settings that would fix this issue and I started to wonder if I should try a different mobile network like Optus or Telstra.

Fortunately, I found a relatively easy way to forcefully unlock VoLTE so that I could make calls over the 4G network. This fix seems permanent and VoLTE still shows after restarting. 

I don’t really understand much of the technical aspect but just followed some guides and it worked out. Normally I’d be a bit more hesitant to install random apps and APKs on my phone but I was desperate. 

### Applications to Install

<div class="gallery3" data-columns="1">
	<img src="/images/Photo_Blog/Honor_Apps.jpg">
</div>

The apps you will need to install can be downloaded from the Playstore or the APKs can be found online.

#### Shizuku

[https://shizuku.rikka.app/guide/setup/](https://shizuku.rikka.app/guide/setup/){:target="_blank"}

#### Pixel IMS

[https://github.com/kyujin-cho/pixel-volte-patch/blob/main/README.en.md](https://github.com/kyujin-cho/pixel-volte-patch/blob/main/README.en.md){:target="_blank"}

### How To Enable VoLTE

#### 1. Follow the steps in the **[Shizuku guide.](https://shizuku.rikka.app/guide/setup/){:target="_blank"}**

`[Settings > About Phone > Build Number > Press Multiple Times]`

`[Developer Options > Enable Wireless Debugging or USB Debugging]`

`[Open Shizuku > Pair with Honor 90 Lite]`

Initially I tried using the PC method, but it wasn’t working and my PC struggled to find the device. The wireless debugging fortunately worked and was hassle free. 

The most complex part was probably needing to enable Developer mode since most people have never needed to do this. To access the Developer Tab on the Honor 90 Lite you need to press the Build Number several times . 

---
#### 2. Open Pixel IMS and in the settings, enable VoLTE and VoWifi

`[Open Pixel > Sim Config > Enable VoLTE and Enable VoWiFi]`

There is a cogwheel icon that allows you to access Sim Config. 

<div class="gallery3" data-columns="1">
	<img src="/images/Photo_Blog/Honor_Pixel_2.jpg">
</div>

---
#### 3. Double check your settings and make sure everything relevant is enabled in Mobile Data.

`[Settings > Mobile Network > Mobile Data > Enable Wifi Calling]`

I’ve also set my preferred network to NR/LTE/WCDMA/GSM auto.

<div class="gallery" data-columns="2">
	<img src="/images/Photo_Blog/Honor_Before.jpg">
	<img src="/images/Photo_Blog/Honor_After.jpg">
</div>

---

VoLTE is now displayed at the top right and still shows even after I uninstalled Shizuku and Pixel IMS. 


Everything seems to still work fine but I don’t know if I’ll need to use these apps again if there are Honor software updates. 
 
### Disclaimer – No guarantee this will work for you. I’m just showing the method I used to get VoLTE working on my Honor 90 Lite in Australia.





---
