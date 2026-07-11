---
description: >-
  Meteo speakers - placeable speakers and vehicle casting from the meteo phone
  Music app, designed exclusively for the meteo fivem server.
---

# Meteo Speakers

This is a guide about testing the meteo fivem speakers script designed exclusively for meteo server. It replaces the old boombox and now connects with the [meteo phone](../meteo-phone/) Music app.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Meteo phone is running (needed for the Music app casting features)

***

## Testing Placeable Speakers

{% stepper %}
{% step %}
**Get an item**

There are two placeable items. Use `/giveitem yourid meteo_boombox 1` for the boombox, or `/giveitem yourid meteo_speaker 1` for the speaker (longer sound range). You can also grab them from the admin menu or the hardware store.
{% endstep %}

{% step %}
**Place it**

Open your inventory and use the item. Aim where you want it, then place it with LMB (left mouse button). Use RMB to cancel and scroll up/down to rotate.
{% endstep %}

{% step %}
**Play music**

Target the placed speaker and open the controls. Paste a direct audio URL to play, then use pause, resume, stop, seek and volume. Recently played links are saved so you can play them again.
{% endstep %}

{% step %}
**Pick it up**

Target the speaker and pick it up to return the item to your inventory. Admins get an extra delete option on the target. You can place up to 3 speakers per player.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Only direct audio file URLs are supported (mp3, ogg, wav, m4a, aac, flac, opus). YouTube and Spotify links do not work - use a direct file link, for example from fivemanage.
{% endhint %}

***

## Casting from the Phone Music App

Open the Music app on the meteo phone to cast audio to a speaker or your vehicle.

{% stepper %}
{% step %}
**Cast to a placed speaker**

Under "My Speakers" the phone lists your nearby placed speakers. Pick one and the music plays through that speaker instead of your phone.
{% endstep %}

{% step %}
**Cast to your vehicle**

Sit in a vehicle and cast to it to play music through the vehicle. You need keys to the vehicle. Cycles, boats, helis, planes and trains cannot be used as vehicle speakers.
{% endstep %}

{% step %}
**Disconnect**

While you are casting, the speaker shows as "in use" to other players. Disconnect from the phone (or drive off / lose the vehicle) to free it up again.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Sound distance, max speakers per player, default volume, placement settings, the vehicle keys requirement and blocked vehicle classes are all configurable in our config. You can change them once you get the server. We will guide you :)
{% endhint %}
