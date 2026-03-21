---
description: >-
  Meteo gym - workout script with stats, injuries and performance enhancers
  designed exclusively for the meteo fivem server.
---

# Meteo Gym

This is a guide about testing the meteo fivem gym script designed exclusively for meteo server. This gym script is connected with meteo-buffs. So when players use items like foods, water, alcohol, joints, drugs etc it will impact their performance and also their gym stats.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Gym

### Checking Your Stats

{% stepper %}
{% step %}
Open f1 menu and click on Character Stats
{% endstep %}

{% step %}
You can see all the status from there. Even if you get an injury it will show here with restricted energy regain and those things
{% endstep %}
{% endstepper %}

### Working Out

{% stepper %}
{% step %}
Go to any gym location. The main gym is Muscle Sands Gym on the map (has a blip)

Or teleport: `/tp -1201.72, -1565.24, 4.61`

There are also 2 prison gym locations for jailed players
{% endstep %}

{% step %}
Start working out on any equipment. There are 6 exercise types:
* pull-ups and bench press (builds strength)
* push-ups and treadmill (builds endurance)
* barbell curls and dumbbell workout (builds dexterity)
{% endstep %}

{% step %}
Each exercise has a skill check minigame. Doing well = better stat gains

Working out drains energy and also your hunger and thirst
{% endstep %}
{% endstepper %}

### Performance Enhancers

* Spawn `creatine` and use it before working out. It gives +20% stat gains and +30 instant energy for 15 minutes
* Spawn `steroids` and use it for a much bigger boost. +150% stat gains and almost no energy cost for 20 minutes (but has side effects)
* Players can find creatine and steroids from crime activities
* btw becareful. You might have side effects :)

### Injuries

{% hint style="warning" %}
If you have creatine or any performance enhancers. It will not show injuries.
{% endhint %}

* If you do badly on the skill check you might get an injury (sore muscles, pulled muscle, sprained wrist, back strain)
* Injuries reduce your stat gains and some block certain exercises
* Injuries heal over time (20 to 60 minutes depending on type)

### How Food and Substances Affect Gym

* Eating healthy foods like `meteo_roast_chicken` builds a healthy eating streak which gives +25% stat gains
* Eating too much junk food and fast food reduces your gym performance. At 90+ addiction it blocks exercise completely
* Using alcohol, getting addicted to joints and drugs is reducing performance too

{% content-ref url="../meteo-buffs/" %}
[meteo-buffs](../meteo-buffs/)
{% endcontent-ref %}

***

## Test Commands

{% hint style="warning" %}
These commands are only available on our test server so you can quickly check things. Also check out [test-commands](test-commands.md) for full details.
{% endhint %}

* `/setgymstats` - max out all gym stats instantly
* `/gym set strength 500` - set a specific stat (strength, dexterity, endurance)
* `/gym add strength 100` - add to a stat
* `/gym energy 250` - set energy level
* `/gym max` - max all stats to 1000
* `/cleargyminjury` - quick clear injury

***

## Good to Know

{% hint style="success" %}
All gym locations, exercises, stat gains, energy costs, injury settings and modifier values are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Stats max out at 1000. Strength boosts melee damage, dexterity boosts movement speed, endurance boosts stamina regen
* Stats slowly decay when players dont workout for a while
