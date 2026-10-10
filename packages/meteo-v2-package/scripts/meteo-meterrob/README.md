---
description: >-
  Meteo meter rob - pick parking meter coin boxes with a tension lockpick
  minigame script designed exclusively for the Meteo V2 package.
---

# Meteo Meter Rob

This is a guide about testing the Meteo V2 parking meter rob script designed exclusively for the Meteo V2 package.

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

## Testing Meter Rob

{% stepper %}
{% step %}
You need `advancedlockpick` item. `/giveitem yourid advancedlockpick 1`
{% endstep %}

{% step %}
Go near any parking meter in the city, point target at it and click **Pick Coin Box**
{% endstep %}

{% step %}
Double meters have two coin boxes. You start on the one you are standing closest to, and once it opens the camera moves to the second lock automatically. Each box pays out when it opens
{% endstep %}

{% step %}
Only one person can work a meter at a time
{% endstep %}
{% endstepper %}

### How the Lockpick Works

{% stepper %}
{% step %}
Move your mouse to aim the pick around the lock
{% endstep %}

{% step %}
Hold **left click** to put tension on it
{% endstep %}

{% step %}
Wrong spot - the lock turns a bit and sticks, and the red bar fills. The deeper it turns, the closer you are
{% endstep %}

{% step %}
Right spot - the pin starts setting (green). The spot slowly moves while you hold, so follow it with small mouse moves
{% endstep %}

{% step %}
Set all the pins to open the box. Every lock has 2 to 4 pins, the top of the screen shows how many
{% endstep %}

{% step %}
Red bar full - your pick snaps. You get 2 to 4 picks per lock
{% endstep %}
{% endstepper %}

> Sweep slowly without tension and listen - the clicks get faster near the right spot. **Right click** to give up. Giving up after a pick already snapped counts as a fail

### What Happens

* Open the box and you get items and may leave a fingerprint (60% chance) unless wearing gloves
* Run out of picks and the lock jams for 1 minute and your lockpick loses durability (25 per fail, it breaks at 0)
* 40% chance police gets alerted either way
* You can rob 3 meters in a row, then you have to lay low for 5 minutes
* Each coin box refills 30 minutes after being robbed

### Items You Can Get

* **common** - meteo\_foldedcash ($15-60)
* **uncommon** - lockpick
* **rare** - goldchain, rolex

### Selling Items

* You can sell stolen items at the pawnshop. Check out [meteo-pawnshop](../meteo-pawnshop/) testing guide for more info

### Perks

* If you have the **Light Hands** specialization - Lock Sense gives an extra pick, Silent Entry reduces police alert chance, Premium Picks makes lockpicks last longer and Inside Job gives better loot

***

## Good to Know

{% hint style="success" %}
Loot, police alerts, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
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

{% content-ref url="../meteo-pawnshop/" %}
[meteo-pawnshop](../meteo-pawnshop/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
