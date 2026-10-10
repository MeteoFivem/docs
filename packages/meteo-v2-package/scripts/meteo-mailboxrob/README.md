---
description: >-
  Meteo mailbox rob - rob mailboxes with lockpick script designed exclusively
  for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-mailboxrob/
---

# Meteo Mailbox Rob

This is a guide about testing the Meteo V2 mailbox rob script designed exclusively for the Meteo V2 package.

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

## Testing Mailbox Rob

{% stepper %}
{% step %}
You need `advancedlockpick` item. `/giveitem yourid advancedlockpick 1`
{% endstep %}

{% step %}
Go near any mailbox in the city and point target and click to rob
{% endstep %}

{% step %}
Complete the lockopen lockpick minigame from [meteo-minigames](../meteo-minigames/) (press E as the dot passes each pin, medium difficulty by default)
{% endstep %}

{% step %}
If you succeed you get items and may leave a fingerprint (60% chance) unless wearing gloves
{% endstep %}
{% endstepper %}

> Every failed attempt wears down your lockpick (25 durability per fail) and it breaks at 0. There is a 40% chance police gets alerted on each attempt

* 1 minute cooldown between robberies
* Each mailbox has a 30 minute reset timer after being robbed

### Items You Can Get

* **common** - meteo\_foldedcash ($20-100), lockpick, tablet, fitbit
* **uncommon** - goldchain, laptop, radioscanner, oxy
* **rare** - diamond\_ring, tenkgoldchain, rolex

### Selling Items

* You can sell stolen items at the pawnshop. Check out [meteo-pawnshop](../meteo-pawnshop/) testing guide for more info

***

## Good to Know

{% hint style="success" %}
Lockpicking (minigame difficulty and lockpick wear), loot, police alerts, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-minigames/" %}
[meteo-minigames](../meteo-minigames/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
