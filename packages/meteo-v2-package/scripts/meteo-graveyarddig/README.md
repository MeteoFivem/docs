---
description: >-
  Meteo graveyard digging - dig up graves for buried valuables, designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-graveyarddig/
---

# Meteo Graveyard Dig

This is a guide about testing the Meteo V2 graveyard digging script designed exclusively for the Meteo V2 package.

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
* Common finds are folded cash, old coins and gold chains
* Better graves turn up gold teeth and diamond rings
* The rare pulls are a gold crucifix, an antique signet ring, a mourning brooch, a grave relic, a ruby or an antique pocket watch

Sell all of it at the [pawnshop](../meteo-pawnshop/).

{% hint style="warning" %}
A dug grave resets to a fresh mound after 40 minutes, so a cemetery is not an endless money printer. You also get 3 digs before a 10 minute cooldown kicks in.
{% endhint %}

### Getting Caught

* Finishing a dig has a 40% chance to send a suspicious activity alert to police through [meteo-mdt](../meteo-mdt/)
* The dig itself is slow and the camera locks you in place, so you are an easy target while you work

***

## Good to Know

{% hint style="success" %}
Loot rolls, loot pool, perk XP and stress are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit cemeteries and their graves in-game with the Graveyards creator, so you decide which cemeteries have them and how many.
{% endhint %}

* Looting a grave gives XP on the Grave Robbing perk line of [meteo-perks](../meteo-perks/). Grave Robber gives a chance for an extra loot roll and Quick Dig makes you dig faster
* Digging adds stress, which ties into [meteo-buffs](../meteo-buffs/)
* Folded cash can be washed into clean cash through the [hustling job](../meteo-hussling/)

{% content-ref url="../meteo-pawnshop/" %}
[meteo-pawnshop](../meteo-pawnshop/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}
