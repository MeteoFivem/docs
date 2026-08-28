---
description: >-
  Meteo graveyard digging - dig up graves for buried valuables, designed
  exclusively for the meteo fivem server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-graveyarddig/
---

# Meteo Graveyard Dig

This is a guide about testing the meteo fivem graveyard digging script designed exclusively for meteo server.

Grab a shovel, find a fresh mound at the cemetery and dig it open. Whatever went in the ground with them is yours.

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
* You need a shovel - `/giveitem yourid meteo_shovel 1`

***

## Testing Graveyard Dig

### Digging a Grave

{% stepper %}
{% step %}
Head to the cemetery. Graves you can dig show as fresh dirt mounds
{% endstep %}

{% step %}
Target a mound and choose **Dig Grave**. The camera drops into the dig and you get a shovel in hand
{% endstep %}

{% step %}
There are 4 clumps of loose dirt on the mound. Aim at one and shovel it away - each one takes 5 hits
{% endstep %}

{% step %}
The mound sinks a little every time you clear a clump. The HUD counts your progress and **Backspace** stops the dig
{% endstep %}

{% step %}
Clear all 4 and you uncover a skeleton
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Only one person can dig a grave at a time, and you cannot dig one that has already been opened.
{% endhint %}

### Searching the Remains

* Target the uncovered skeleton and choose **Search Remains**
* You get between 1 and 3 item rolls, so some graves pay and some give you nothing worth carrying
* Common finds are cash, old coins and gold chains
* Better graves turn up gold teeth and diamond rings
* The rare pulls are a gold crucifix, an antique signet ring, a mourning brooch, a grave relic, a ruby or an antique pocket watch

Sell all of it at the [pawnshop](../meteo-pawnshop/).

{% hint style="warning" %}
A dug grave resets to a fresh mound after 40 minutes, so a cemetery is not an endless money printer. You also get 3 digs before a 10 minute cooldown kicks in.
{% endhint %}

### Getting Caught

* Finishing a dig has a 40% chance to send a suspicious activity alert to police through [meteo-dispatch](../meteo-dispatch/)
* The dig itself is slow and the camera locks you in place, so you are an easy target while you work

***

## Good to Know

{% hint style="success" %}
Graves are placed with an in game creator, so you decide which cemeteries have them and how many. Loot table, roll counts, search time, dispatch chance, reset time and cooldown are configurable. You can change them once you get the server. We will guide you :)
{% endhint %}

* Looting a grave gives [meteo-perks](../meteo-perks/) progress, and the Grave Robber perk adds an extra loot roll
* Digging adds stress, which ties into [meteo-buffs](../meteo-buffs/)
* Admins can use `/digcreator` to place, test and delete graves

{% content-ref url="../meteo-pawnshop/" %}
[meteo-pawnshop](../meteo-pawnshop/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-dispatch/" %}
[meteo-dispatch](../meteo-dispatch/)
{% endcontent-ref %}
