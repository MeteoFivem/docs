---
description: >-
  Meteo rewards - reward boxes and crates with rarity tiers script designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-rewards/
---

# Meteo Rewards

This is a guide about testing the Meteo V2 rewards boxes script designed exclusively for the Meteo V2 package. This script is made and optimized for meteo crime system and casino lucky wheel rewards.

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

These are the crate and box types that come with the package. Try them all:

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
* `meteo_transporthunt_loot` - transport hunt loot

**Casino rewards:**

* `meteo_casino_crate` - casino crate (standard weapon tints)
* `meteo_casino_premium_crate` - casino premium crate (MK2 weapon tints)

> Players will get hunt crates by doing hunts on meteo crime system. Check out meteo crime scripts for more details.

***

## Testing the Creator

{% stepper %}
{% step %}
Open the admin menu with **F9** and go to **Script Settings** > **Creator** > **Reward Boxes**
{% endstep %}

{% step %}
Add a record and pick the item to open. The item must already exist in your inventory items
{% endstep %}

{% step %}
Pick the opening style - **Crate** (spinner) or **Box** (reveal)
{% endstep %}

{% step %}
Add the possible rewards with the item, amount, rarity and weight. The chance of each reward shows next to its weight
{% endstep %}

{% step %}
Save, spawn the item and open it
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Every reward box, crate and its loot is editable in-game with the **Reward Boxes** creator, and the perk XP per opened reward is editable from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

* Each crate type has its own themed loot table with weighted drop chances
* Opening rewards gives XP on the **Crates** line in [meteo-perks](../meteo-perks/), which unlocks better reward box drops and a higher legendary chance
