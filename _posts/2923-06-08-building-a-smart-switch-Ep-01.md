---
layout: post
tags: nerd electronics diy
cat: post
date: 2023-06-08
description: Smart Switch - from the scratch
---

Some of the ideas that we get, does not live longer, but if it does, it is worth implementing. Smart Switch is one of them. I thought I'll use this space to mark my progress in building a Smart Switch. Perhaps I would fail in building one eventually, but what's more important is the journey of knowledge. This, ladies and gentlemen, is episode 1 of 'Building a Smart Switch'

### Where did it start
So this is how the idea sprung. When we built a office cabin in our garden, I thought it would be great to switch on the heater remotely to make the room warm before I could start work. I checked for smart heaters which connect to the home network and noticed that they were quite expensive. While a normal heater is around £30-50, a smart heater started at around £200s. That is when, I decided to purchase a smart plug point - a plug socket which connects to the home network and any appliance, which is plugged into this smart plug point, becomes a smart appliance. I looked for options - there were plenty which works on Android, but I could hardly find one which will work on iOS. Finally I found Meross. Well, Meross is good I'd say at the beginning. And then I realized that it wasn't reliable at all. There were days I thought the heater was ON for over an hour, but I ended up shivering in the office later.

### The plan
So, now, the plan is to build one all by myself. I'm pretty sure that the final product that I'd end up building would be a little bigger that the products sold in the market. No, not like this :)
<p style="text-align:center;"> 
    <img src="/blog/assets/images/SmartSwitch_01_BigComputer.jpeg" width="40%"/> 
</p>

In my free time, I jotted some designs on what features it must have and how potentially it could look. I also had to weigh my skill on what could be possible with the limited resources I have. Base on that, here are few designs.

<p style="text-align:center;"> 
    <img src="/blog/assets/images/SmartSwitch_01_Plug01.jpeg" width="30%"/> 
    <img src="/blog/assets/images/SmartSwitch_01_Plug02.jpeg" width="30%"/> 
    <img src="/blog/assets/images/SmartSwitch_01_Plug03.jpeg" width="30%"/> 
</p>
<p style="text-align:center;"> 
    <img src="/blog/assets/images/SmartSwitch_01_Plug04.jpeg" width="80%"/> 
</p>

### Features
As I said before, I did list some of the features that the Smart Switch must have. But again, I might add or drop of the features based on what I will learn eventually in this process.
- **Timer** : It should allow the user to set the duration of how long the appliance should be ON.
- **Display** : It should, at any point, let the user see the running timer countdown.
- **Wifi** : The Smart Switch must be accessible via the home network.
- **Sensors** : When a sensor is attached to the Smart Switch, it must publish the results to the display/mobile. For example, if a temperature sensor is attached, the display must show the temperature. The temperature must be published to the home network too. This will help the user to take a decision on whether to switch ON the appliance or not.
- **Programmable** : If required, a skilled user must be able to reprogram to his/her needs.

### What's next
In the days to come, the plan is to make a simple block diagram and then a detailed circuit diagram to check what is achievable. I'm also planning to keep a track on what I purchase and the amount I'd be spending towards making this Smart Switch.

Do keep an eye around here...