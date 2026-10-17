---
description: >-
  Meteo drug selling - sell drugs to NPCs with territory bonuses script designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-drugselling/
---

# Meteo Drug Selling

This is a guide about testing the Meteo V2 drug selling script designed exclusively for the Meteo V2 package.

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

## Testing Drug Selling

### Alrighttt..

* Now make sure you have `cokebaggy`, `meth`, `joint`, `weed_brick` - any of these items. If you know what im talking about if you already did the [meteo-drugs](../meteo-drugs/) script testing guide.

{% hint style="warning" %}
Make sure to check the [meteo-drugs](../meteo-drugs/) testing guide if you haven't
{% endhint %}

### Selling Drugs

{% stepper %}
{% step %}
#### Get Drugs to Sell

Lets spawn `weed_brick`. You can use /giveitem or admin menu to spawn
{% endstep %}

{% step %}
#### Offer Drugs to NPC

Find NPC and now when you point target on them it will show offer drugs new option. Click on that and offer drugs
{% endstep %}

{% step %}
#### Set Price

After that use **arrow left** and **right** to adjust a price and press **E** to confirm
{% endstep %}

{% step %}
#### Collect Cash

After you sell you will get `meteo_foldedcash` :) there is also a chance police gets alerted on [meteo-mdt](../meteo-mdt/) and you can leave a fingerprint
{% endstep %}

{% step %}
#### Wash Money

Folded cash can be washed into clean cash through the [hustling job](../meteo-hussling/)
{% endstep %}
{% endstepper %}

### Organization Territory

* If you are in an organization and selling drugs on your org territory you will gain more XP for your org and earn more cash
* Check out [meteo-organizations](../meteo-organizations/) testing guide for more info about territories

***

## Good to Know

{% hint style="success" %}
Deals, counter-offers, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit the drugs players can sell and their prices in-game with the Sellable Drugs creator.
{% endhint %}

> Connected with [meteo-perks](../meteo-perks/). Dealing perk line: Turf Control gives more org rep from drug sales. Smooth Talker and Connections from the Pawn line and Pure Product from the Growing line also boost your sales

{% content-ref url="../meteo-drugs/" %}
[meteo-drugs](../meteo-drugs/)
{% endcontent-ref %}

{% content-ref url="../meteo-organizations/" %}
[meteo-organizations](../meteo-organizations/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}
