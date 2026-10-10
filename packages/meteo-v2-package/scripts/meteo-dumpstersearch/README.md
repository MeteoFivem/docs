---
description: >-
  Meteo dumpster search - search dumpsters for materials and rare blueprints
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-dumpstersearch/
---

# Meteo Dumpster Search

This is a guide about testing the Meteo V2 dumpster search script designed exclusively for the Meteo V2 package.

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

## Testing Dumpster Search

{% stepper %}
{% step %}
Go near any dumpster or bin in the city and point target and click on search
{% endstep %}

{% step %}
It will play a search animation with 5 second progress bar
{% endstep %}

{% step %}
After searching you will get crafting materials, items and sometimes rare blueprints
{% endstep %}
{% endstepper %}

* Each dumpster has a 30 minute cooldown after searching
* Also drops fingerprint (60% chance) unless wearing gloves

### Items You Can Get

* **common crafting materials** - plastic, metalscrap, rubber, steel, aluminum, copper, iron
* **uncommon items** - tablet, lockpick, oxy, meteo\_ecola\_syrup, meteo\_cough\_syrup
* **rare blueprints** - meteo\_blueprint\_flashlight, meteo\_blueprint\_grip, meteo\_blueprint\_suppressor, meteo\_blueprint\_extclip, meteo\_blueprint\_scope (1-3% chance)

### Dumpster Models That Work

* All standard dumpsters and bins around the city (prop\_dumpster\_01a, prop\_bin\_05a etc.)

### Using Materials

* Crafting materials can be used at crafting tables. check out [meteo-craftingtables](../meteo-craftingtables/) testing guide
* Blueprints are used for weapon attachment crafting

***

## Good to Know

{% hint style="success" %}
Loot table, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

> Connected with [meteo-perks](../meteo-perks/). Scavenging perk line: Sharp Eyes makes you search faster, Lucky Find gives a better chance for rare items, Dumpster Pro reduces dumpster cooldown, Gold Digger increases scavenge cash

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}
