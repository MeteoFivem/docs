---
description: >-
  Meteo radio - radio with encrypted channels for jobs script designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-radio/
---

# Meteo Radio

This is a guide about testing the Meteo V2 unique radio script designed exclusively for the Meteo V2 package.

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

***

## Testing Radio

* There are 2 radio items - `radio` and `encrypted_radio`. You can use `/giveitem` command or use admin menu items section to get those items for testing
* **Radio** - civilian radio with channels 100 to 500 (public for everyone)
* **Encrypted\_radio** - encrypted radio for police and EMS. Its channels are managed from the [meteo-mdt](../meteo-mdt/) radio panel

### How to Use

{% stepper %}
{% step %}
Spawn a `radio` and use it from inventory (or press **=**) to open the radio UI
{% endstep %}

{% step %}
Select a channel between 100 and 500 and start transmitting. Use **.** and **,** to jump to the next or previous channel
{% endstep %}

{% step %}
Save channels to your favourites - favourites and recently used channels are saved per character
{% endstep %}

{% step %}
Volume control is built in - default is 80, you can adjust from 0 to 100 with step of 5
{% endstep %}
{% endstepper %}

{% hint style="info" %}
You can see all keybinds from FiveM keybind settings and change them to whatever you like.
{% endhint %}

### Testing Encrypted Radio

{% stepper %}
{% step %}
Set your job first: `/setjob yourid police 4` and spawn `encrypted_radio`
{% endstep %}

{% step %}
Use the encrypted radio from inventory. It connects you to the MDT radio board and you wait for a channel assignment
{% endstep %}

{% step %}
Open the [MDT](../meteo-mdt/) radio panel. Officers with the right MDT permissions can create channels and move people between them, and your radio follows whatever the MDT assigns
{% endstep %}

{% step %}
Use the encrypted radio again to disconnect. Opening the normal radio or dropping the encrypted radio also disconnects you from the board
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Radio brand name, volume settings, channels and job restrictions are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

> Has radio click sounds and animations that can be toggled
