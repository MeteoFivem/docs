---
description: >-
  Meteo hud - status display, crosshair, voice and vehicle hud script designed
  exclusively for the meteo fivem server.
---

# Meteo HUD

This is a guide about testing the meteo fivem hud script designed exclusively for meteo server. this hud is connected with our scripts like meteo-dailyrewards (used for economy boosts), meteo-phone, meteo-buffs. you will be able to see all effects on hud when you use those items. check out [meteo-buffs](../meteo-buffs/) for more info.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing HUD

{% stepper %}
{% step %}
**Status Display**

Hud is only showing status on bottom left when necessary. use `/hudsettings` on chat to open the settings menu. you can enable things as you want from there and also enable fps mode if necessary

<div align="left"><figure><img src="../../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure></div>

<div align="left"><figure><img src="../../../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**Crosshair and Ammo**

Get `/giveitem yourid weapon_pistol 1` or any weapon and aim. you will be able to see a dot. that is crosshair. you can also disable it once you get the server. we will guide you :)

When you shoot and when it detected ammo change it will update the ammo count on top right
{% endstep %}

{% step %}
**Voice**

Use voice and enable it and the bottom right voice will animate with your voice. use **\`** (backtick) on keyboard to change voice modes. also connect to radio and see if its changing the voice icon to radio icon
{% endstep %}

{% step %}
**Vehicle HUD**

Spawn a vehicle using `/car adder` and then open and play music or use phone test commands and get a notification. the vehicle hud will update with phone peek and you can see all vehicle speed and other things without issues. that deep we optimized the server and connected scripts when building the meteo server
{% endstep %}

{% step %}
**Economy Boost**

For checking out meteo economy boost check [meteo-dailyrewards](../meteo-dailyrewards/) testing guide
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All hud settings, crosshair, voice modes and display options are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}
