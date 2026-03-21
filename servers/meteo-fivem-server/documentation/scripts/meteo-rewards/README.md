---
description: >-
  Meteo rewards - reward boxes and crates with rarity tiers script
  designed exclusively for the meteo fivem server.
---

# Meteo Reward Boxes & Crates

This is a guide about testing the meteo fivem rewards boxes script designed exclusively for meteo server. This script is made and optimized for meteo crime system and casino lucky wheel rewards.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-rewards-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Quick Test

{% stepper %}
{% step %}
To test just quickly get `meteo_casino_premium_crate` item using meteo admin or using `/giveitem yourid meteo_casino_premium_crate 1`
{% endstep %}

{% step %}
Use the item and spin it
{% endstep %}

{% step %}
See your luck :)

Rewards have 5 rarity tiers - common (gray), uncommon (green), rare (blue), epic (purple) and legendary (gold)
{% endstep %}
{% endstepper %}

***

## All Crate Types

There are 10 different crate and box types. Try them all:

**Basic rewards:**
* `meteo_reward_box` - basic rewards (water, sandwich, bandage, armor)
* `meteo_reward_crate` - standard crate (spray cans, armor, weapon blueprints)

**Crime system hunt rewards:**
* `meteo_seahunt_salvage` - sea hunt salvage (medical supplies)
* `meteo_seahunt_artifact` - sea hunt artifact (rare medical and chemicals)
* `meteo_foresthunt_supplies` - forest hunt supplies (military materials)
* `meteo_foresthunt_contraband` - forest hunt contraband (weapon blueprints and chemicals)
* `meteo_bargehunt_cargo` - barge hunt cargo (industrial materials)
* `meteo_bargehunt_contraband` - barge hunt contraband (blueprints and drug tables)

**Casino rewards:**
* `meteo_casino_crate` - casino crate (standard weapon tints)
* `meteo_casino_premium_crate` - casino premium crate (MK2 weapon tints)

> Players will get hunt crates by doing hunts on meteo crime system. Check out meteo crime scripts for more details.

***

## Good to Know

{% hint style="success" %}
All reward tables, rarity weights and items are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Each crate type has its own themed loot table with weighted drop chances
