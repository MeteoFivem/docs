---
description: >-
  Meteo weapon tints - recolour your weapons with tint items designed
  exclusively for the meteo fivem server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-weapontints/
---

# Meteo Weapon Tints

This is a guide about testing the meteo fivem weapon tints script designed exclusively for meteo server.

Tints are items. Use one while holding a weapon and the colour sticks to that weapon, not to you - so it stays on when you store it, sell it or hand it over.

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
* Get a weapon with `/giveitem yourid weapon_pistol 1`

***

## Testing Weapon Tints

{% stepper %}
{% step %}
Spawn a tint with `/giveitem yourid weapontint_2 1` for gold
{% endstep %}

{% step %}
Take your weapon out and hold it
{% endstep %}

{% step %}
Use the tint from your inventory. Your character sprays it on and the tint is consumed
{% endstep %}

{% step %}
Put the weapon away and take it out again - the colour is still there
{% endstep %}
{% endstepper %}

### Normal Weapon Tints

| Item | Colour |
| ---- | ------ |
| `weapontint_0` | Default / black |
| `weapontint_1` | Green |
| `weapontint_2` | Gold |
| `weapontint_3` | Pink |
| `weapontint_4` | Army |
| `weapontint_5` | LSPD |
| `weapontint_6` | Orange |
| `weapontint_7` | Platinum |

### MK2 Weapon Tints

MK2 weapons use their own set - `weapontint_mk2_0` through `weapontint_mk2_11`. That covers classic black, gray, two-tone, white, beige, green, blue, earth, brown and black, plus red, blue and yellow contrast.

{% hint style="warning" %}
The two sets do not mix. An MK2 tint on a normal weapon and a normal tint on an MK2 weapon are both rejected, and so is applying a tint the weapon already has - so you never waste one by accident.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Whether tints are consumed, the apply time and the animation are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* The tint is saved on the weapon item, so it travels with the weapon between players and through storage
* Everything is checked on the server, so a tint cannot be applied without actually holding the item

{% content-ref url="../meteo-inventory/" %}
[meteo-inventory](../meteo-inventory/)
{% endcontent-ref %}

{% content-ref url="../meteo-weaponrepair/" %}
[meteo-weaponrepair](../meteo-weaponrepair/)
{% endcontent-ref %}
