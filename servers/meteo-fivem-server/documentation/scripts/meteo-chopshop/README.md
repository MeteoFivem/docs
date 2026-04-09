---
description: >-
  Meteo chop shop - vehicle chopping with 3 contract tiers (easy/medium/highend),
  part extraction, police dispatch chance and configurable rewards designed
  exclusively for the meteo fivem server.
---

# Meteo Chop Shop

This is a guide about testing the meteo fivem chop shop script designed exclusively for meteo server. vehicle chopping with 3 contract tiers (easy, medium, highend), part extraction mechanics, police dispatch chance and configurable rewards per tier.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-testing-server.md).
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-chopshop-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Contract Types

| Contract | Item | Vehicles | Reward |
| -------- | ---- | -------- | ------ |
| Easy | `meteo_chopcontract_easy` | D-class, 1-2 vehicles | $600-1200 |
| Medium | `meteo_chopcontract_medium` | C-class, 2-3 vehicles | $1800-3500 |
| Highend | `meteo_chopcontract_highend` | A-class, 2-4 vehicles | $5000-10000 |

Players get these contracts from vehicle search and other crime activities. For testing you can spawn them with `/giveitem` or admin menu.

***

## Testing Chop Shop

{% stepper %}
{% step %}
**Get a contract**

use `/giveitem yourid meteo_chopcontract_highend` to spawn a highend contract (or any tier you want to test)
{% endstep %}

{% step %}
**Go to a chop location**

go to sandy chop shop using `/tp 100.9369, 6616.7534, 32.4353`. there is also another one at `/tp 978.2922, -2227.1057, 31.6517`. you can customize these locations once you get the server
{% endstep %}

{% step %}
**Activate the contract**

point target to the ped and click on view contracts. you can see your available contracts there. tap to activate. it will show what vehicles you need to bring and chop
{% endstep %}

{% step %}
**Find the vehicles**

the vehicles are on roads with npcs driving them. all configured vehicles are ones that actually spawn on roads. for testing you can just use `/car vehiclename` to spawn them
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
all chop locations, contract tiers, vehicle lists, rewards and part drop rates are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

* there is a 30% chance chopping triggers a police dispatch alert

**Connected scripts:**

{% content-ref url="../meteo-dispatch/" %}
[meteo-dispatch](../meteo-dispatch/) - for police dispatch alerts during chopping
{% endcontent-ref %}

{% content-ref url="../meteo-searchvehicles/" %}
[meteo-searchvehicles](../meteo-searchvehicles/) - for finding chop contracts
{% endcontent-ref %}
