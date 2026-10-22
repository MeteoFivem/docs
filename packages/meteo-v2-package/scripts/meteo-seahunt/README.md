---
description: >-
  Meteo sea hunt - underwater wreck diving and salvage script designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-seahunt/
---

# Meteo Sea Hunt

This is a guide about testing the Meteo V2 sea hunt script designed exclusively for the Meteo V2 package. Dive into the ocean, find sunken wrecks, and salvage valuable loot - solo or with your crew.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

{% hint style="warning" %}
Make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) guide before following this.
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Sea Hunt

{% stepper %}
{% step %}
**Purchase the service**

Open tablet and go to services app. You can see the Sea Hunt service. Purchase it (costs 175 MTC) and start

If you do not have crypto use `/addcrypto 200` and get crypto

{% hint style="info" %}
This is a testing command and only works on our showcase server
{% endhint %}

You can do this with a group too. follow group guide on [crimetablet](../meteo-crimetablet/) guide and add group members too
{% endstep %}

{% step %}
**Get ready**

Go to marked location on the map. also if you are in a group all group members can see this too

Make sure to get diving items from `/tp -1687.03, -1072.18, 13` and get both `diving_gear` and `diving_fill`. or you can just use /giveitem or admin menu to get these items

Also you need a boat. You can get one from boat rentals or just spawn one with `/car seashark`
{% endstep %}

{% step %}
**Do the hunt**

Go to the marked location, go deep in the sea, find the wrecks and search them

Make sure you have space in your inventory, otherwise items will not get to you

Find all wrecks and search them. Each search has a 25% chance to alert police on [meteo-mdt](../meteo-mdt/) and you can leave a fingerprint

You have 30 minutes to finish the hunt
{% endstep %}

{% step %}
**Collect rewards**

You will get items like `meteo_seahunt_salvage`, `meteo_seahunt_artifact`, reward boxes, meteo\_foldedcash and more. Use the salvage and artifact crates and see your luck :)

After you complete it open the tablet and see the logs and the crypto you got (190 MTC). Group members get a share too
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Rewards, the loot table, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit dive sites in-game with the Dive Sites creator.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/) - for service purchasing and groups
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/) - Sea Hunt perk line: Recon reduces hunt cooldown, Sea Legs gives more time on sea missions, War Machine increases all hunt loot
{% endcontent-ref %}

{% content-ref url="../meteo-rewards/" %}
[meteo-rewards](../meteo-rewards/) - for opening salvage and artifact crates
{% endcontent-ref %}

{% content-ref url="../meteo-misc/" %}
[meteo-misc](../meteo-misc/) - for diving gear oxygen system
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/) - for police alerts
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
