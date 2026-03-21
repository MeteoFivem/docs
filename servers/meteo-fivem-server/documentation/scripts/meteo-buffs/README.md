---
description: >-
  Meteo buffs - food addiction, substance addiction and status effects script
  designed exclusively for the meteo fivem server.
---

# Meteo Buffs

This is a guide about testing the meteo fivem buffs and status effects script designed exclusively for meteo server. This script tracks food addiction, substance addiction, stress, drunk level and more. It directly affects gym performance and player stats. Connected with meteo-gym, meteo-hud, meteo-misc consumables and more.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-buffs-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Performance Enhancers

These are items that boost your gym performance:

{% stepper %}
{% step %}
Spawn and use performance enhancer items:

* `/giveitem yourid creatine 1` - use before gym. Gives +20% stat gains, +30 instant energy for 15 minutes. Has 2 hour cooldown
* `/giveitem yourid steroids 1` - much stronger boost. +150% stat gains for 20 minutes but has side effects. 6 hour cooldown
* `/giveitem yourid painkillers 1` - removes limping, slowly heals +5 HP every 2s for 2 minutes. 5 min cooldown
* `/giveitem yourid adrenaline 1` - removes limping, 20% damage reduction, speed boost, cant be ragdolled for 1 minute. 10 min cooldown
{% endstep %}

{% step %}
After using them go to gym and workout or get into combat to see the difference
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Also please check out [meteo-medicaljob](../meteo-medicaljob/) test guide for more details on painkillers and adrenaline since they are medical items.
{% endhint %}

***

## Testing Food Addiction

Eating too much fast food and junk food builds up food addiction which hurts your gym performance.

### Fast Food Test

{% stepper %}
{% step %}
Spawn some fast food items and use them:

* `/giveitem yourid meteo_bleeder_burger 5`
* `/giveitem yourid meteo_burgershot_fries 5`
* `/giveitem yourid meteo_hotdog 5`
{% endstep %}

{% step %}
At 50+ combined addiction you get -50% stat gains in gym

At 90+ addiction exercise gets blocked completely
{% endstep %}
{% endstepper %}

### Junk Food Test

* `/giveitem yourid meteo_donut 5`
* `/giveitem yourid meteo_ice_cream 5`
* `/giveitem yourid meteo_junk_energy 3` (this one is stronger, +18 per use)

### Healthy Food Test

{% stepper %}
{% step %}
Eating healthy food builds a streak which gives bonuses:

* `/giveitem yourid meteo_roast_chicken 3`
* `/giveitem yourid water_bottle 3`
* `/giveitem yourid meteo_tunasandwich 3`
{% endstep %}

{% step %}
At 3+ healthy streak you get +25% stat gains in gym and 24h immunity to junk food addiction
{% endstep %}
{% endstepper %}

***

## Testing Substance Addiction

Drugs and alcohol also build addiction and hurt gym performance:

* `/giveitem yourid beer 5` - alcohol (+8 addiction each, penalty at 50+)
* `/giveitem yourid whiskey 3` - stronger alcohol (+12 each)
* `/giveitem yourid joint 5` - weed (+10 each, penalty at 50+)
* `/giveitem yourid cokebaggy 2` - cocaine (+15 each, penalty at 30+)
* `/giveitem yourid meth 2` - meth (+18 each, penalty at 25+)
* `/giveitem yourid xtcbaggy 3` - ecstasy (+12 each, penalty at 35+)
* `/giveitem yourid oxy 3` - oxycodone (+12 each, penalty at 40+)
* `/giveitem yourid crack_baggy 1` - crack cocaine (+20 each, strongest)

> Substances also have screen effects - drunk vision, speed boosts, ragdolls etc. Try them and see :)

***

## Testing Detox/Rehab Items

These items reduce addiction levels:

* `/giveitem yourid detox_pills 1` - reduces all substance addictions by 30 points
* `/giveitem yourid rehab_drink 1` - reduces alcohol addiction by 50 points
* `/giveitem yourid detox_tea 1` - reduces drug addictions by 40 points (weed, cocaine, meth, ecstasy, oxy - not alcohol)

***

## Test Commands

{% hint style="warning" %}
These commands are only available on our test server so you can quickly check things without grinding. Also check out [test-commands](test-commands.md) for full details.
{% endhint %}

* `/buffs food fastFood 80` - set food addiction (fastFood, junkFood, healthyFood, balancedMeals)
* `/buffs drug cocaine 60` - set substance addiction (alcohol, weed, cocaine, meth, oxy, ecstasy)
* `/buffs hunger 100` - set hunger level
* `/buffs thirst 100` - set thirst level
* `/buffs stress 50` - set stress level
* `/buffs drunk 50` - set drunk level
* `/buffs streak 5` - set healthy eating streak
* `/buffs reset all` - reset everything
* `/buffs reset food` - reset food addictions only
* `/buffs reset drug` - reset drug addictions only
* `/buffs info` - print all buff data to F8 console

***

## Good to Know

{% hint style="success" %}
All addiction thresholds, penalties, item effects, durations and detox amounts are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Addiction penalties stack - so being addicted to both junk food and cocaine at the same time makes gym much harder
* Substance addiction slowly decays over time (1 point per hour)
* Stress causes screen blur at 60+ and ragdoll chance at 100
