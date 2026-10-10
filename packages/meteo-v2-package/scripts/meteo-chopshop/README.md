---
description: >-
  Meteo chop shop - vehicle chopping with 4 contract tiers
  (easy/medium/premium/highend), part extraction, police dispatch chance and
  configurable rewards designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-chopshop/
---

# Meteo Chop Shop

This is a guide about testing the Meteo V2 chop shop script designed exclusively for the Meteo V2 package. Vehicle chopping with 4 contract tiers (easy, medium, premium, highend), part extraction mechanics, police dispatch chance and configurable rewards per tier.

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

## Contract Types

| Contract | Item                         | Vehicles              | Reward                          |
| -------- | ---------------------------- | --------------------- | ------------------------------- |
| Easy     | `meteo_chopcontract_easy`    | D-class, 1-2 vehicles | $600-1200 folded cash + scrap   |
| Medium   | `meteo_chopcontract_medium`  | C-class, 2-3 vehicles | $1800-3500 folded cash + scrap  |
| Premium  | `meteo_chopcontract_premium` | B-class, 2-3 vehicles | $3000-6000 folded cash + scrap  |
| Highend  | `meteo_chopcontract_highend` | A-class, 2-4 vehicles | $5000-10000 folded cash + scrap |

Players get these contracts from vehicle search and other crime activities. For testing you can spawn them with `/giveitem` or admin menu.

> Cash rewards are paid as `meteo_foldedcash` together with materials like metalscrap, steel, rubber and copper. Premium and highend contracts also have a small chance to give a `meteo_boostcontract`, and highend a very rare `meteo_vinscratch`. Folded cash can be washed into clean cash through the [hustling job](../meteo-hussling/)

***

## Testing Chop Shop

{% stepper %}
{% step %}
**Get a contract**

use `/giveitem yourid meteo_chopcontract_highend` to spawn a highend contract (or any tier you want to test)
{% endstep %}

{% step %}
**Go to a chop location**

go to sandy chop shop using `/tp 100.9369, 6616.7534, 32.4353`. there is also another one at `/tp 978.2922, -2227.1057, 31.6517`. you can customize these locations once you get the package
{% endstep %}

{% step %}
**Activate the contract**

point target to the ped and click on view contracts. you can see your available contracts there. tap to activate. it will show what vehicles you need to bring and chop
{% endstep %}

{% step %}
**Find the vehicles**

any vehicle of the contract class counts, so you can find them on roads with npcs driving them. you can not hand in the same model twice on one contract, and owned or job vehicles are blocked. for testing you can just use `/car vehiclename` to spawn them
{% endstep %}

{% step %}
**Chop the vehicle**

drive the vehicle to the chop location. point target to the vehicle and it will show to start chop. get the parts and drop them. repeat for all vehicles in the contract
{% endstep %}

{% step %}
**Get rewards**

after all vehicles are chopped you get the rewards. check the contract tier table above for reward amounts per tier
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All chop locations, contract tiers, vehicle classes, rewards and part drop rates are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

* There is a 30% chance chopping triggers a police dispatch alert on [meteo-mdt](../meteo-mdt/)
* Connected with [meteo-perks](../meteo-perks/). Chop Shop perk line: Chop Expert strips cars faster and needs 1 less vehicle per contract, Big Score increases chop cash, Empire increases chop cash and scrap and needs 1 less vehicle per contract

**Connected scripts:**

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-searchvehicles/" %}
[meteo-searchvehicles](../meteo-searchvehicles/)
{% endcontent-ref %}
