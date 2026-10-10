---
description: >-
  Meteo appearance - clothing stores, barber, tattoos and job outfits script
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-appearance/
---

# Meteo Appearance

This is a guide about testing the Meteo V2 appearance and clothing script designed exclusively for the Meteo V2 package. this is connected with [meteo-inventory](../meteo-inventory/) clothing section.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Appearance

{% stepper %}
{% step %}
**Character Creation**

Create a new character from the character selection screen. the appearance menu opens so you can build your look. creation is save only - you can't close it without saving, so a new character never spawns as the default ped. if you disconnect in the middle of creation, the creation menu opens again the next time you load that character
{% endstep %}

{% step %}
**Clothing Stores**

Go to any clothing store location on map. press e to open the shop menu. change clothing and save. it will deduct the cost ($100 per visit). each clothing item shows preview images so you can see it before picking

{% hint style="warning" %}
Make sure to check that clothing shops update the inventory clothing section too. refer to [meteo-inventory](../meteo-inventory/) testing guide for more info.
{% endhint %}

You can save outfits on clothing stores too and share them with other players using a share code. also check out other shops like barber ($50) and tattoos ($200 per tattoo) on map
{% endstep %}

{% step %}
**Take Off Clothing**

Use the clothing removal commands to take off a piece. the item goes back to your inventory so you can put it on again later. if your inventory is full you can't take it off

* `/removehat`, `/removeglasses`, `/removemask`, `/removeears`, `/removenecklace`
* `/removeshirt`, `/removevest`, `/removewatch`, `/removebag`
* `/removepants`, `/removeshoes`, `/removebracelet`, `/removedecal`
{% endstep %}

{% step %}
**Job Outfits**

Lets check job outfits. lets try police job. if you dont have police job use /setjob. make sure its a boss grade. `/tp -545.0594, -127.1616, 38.8002` to teleport. then first time as a police boss you can see add outfit click on that and give a name and save it. what this doing is saving your current outfit. but now this outfit can be used by all other police job players. you can check it by `/setjob yourid police 1`. and open the menu again now you can see it only has option to select that outfit. that it
{% endstep %}
{% endstepper %}

### Other Job Locker Locations

* **Police** - `/tp -545.0594, -127.1616, 38.8002`
* **Ambulance (Pillbox)** - `/tp 53.8490, -387.0211, 39.3781`
* **Ambulance (Blane County)** - `/tp 53.8490, -387.0211, 39.3781`
* **Mechanic** - `/tp -322.9909, -144.9560, 39.4344`

### Other Commands

* `/reloadskin` - reload your appearance if it looks wrong
* `/clearprops` - clear stuck props and accessories

***

## Good to Know

{% hint style="success" %}
Shop prices (clothing, barber, tattoo and plastic surgeon) and the starting outfit for new male and female characters are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. the starting outfit has a "Copy my outfit" button so you can dress up in game and use that look.

Add or edit clothing stores, barbers, tattoo shops, plastic surgeons and job lockers in-game with the Appearance creator. the plastic surgeon is switched off by default.
{% endhint %}

> Clothing preview images come from the image studio in [meteo-manage](../meteo-manage/). admins can also give a player a custom ped and restore their old look from the admin menu

**Connected scripts:**

{% content-ref url="../meteo-inventory/" %}
[meteo-inventory](../meteo-inventory/)
{% endcontent-ref %}
