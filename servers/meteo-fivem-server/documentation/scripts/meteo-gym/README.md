---
description: >-
  Meteo gym - workout script with stats, injuries and performance enhancers
  designed exclusively for the meteo fivem server.
---

# Meteo Gym

This is a guide about testing the meteo fivem gym script designed exclusively for meteo server. this gym script is connected with meteo-buffs. so when players use items like foods, water, alcohol, joints, drugs etc it will impact their performance and also their gym stats.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Gym

### Checking Your Stats

* open f1 menu and click on Character Stats
* you can see all the status from there. even if you get an injury it will show here with restricted energy regain and those things

### Working Out

* go to any gym location. the main gym is Muscle Sands Gym on the map (has a blip)
* or teleport: `/tp -1201.72, -1565.24, 4.61`
* there are also 2 prison gym locations for jailed players
* start working out on any equipment. there are 6 exercise types:
  * pull-ups and bench press (builds strength)
  * push-ups and treadmill (builds endurance)
  * barbell curls and dumbbell workout (builds dexterity)
* each exercise has a skill check minigame. doing well = better stat gains
* working out drains energy and also your hunger and thirst

### Performance Enhancers

* spawn `creatine` and use it before working out. it gives +20% stat gains and +30 instant energy for 15 minutes
* spawn `steroids` and use it for a much bigger boost. +150% stat gains and almost no energy cost for 20 minutes (but has side effects)
* players can find creatine and steroids from crime activities
* btw becareful. you might have side effects :)

### Injuries

* Note: if you have creatine or any performance enhancers. it will not show injuries.
* if you do badly on the skill check you might get an injury (sore muscles, pulled muscle, sprained wrist, back strain)
* injuries reduce your stat gains and some block certain exercises
* injuries heal over time (20 to 60 minutes depending on type)

### How Food and Substances Affect Gym

* eating healthy foods like `meteo_roast_chicken` builds a healthy eating streak which gives +25% stat gains
* eating too much junk food and fast food reduces your gym performance. at 90+ addiction it blocks exercise completely
* using alcohol, getting addicted to joints and drugs is reducing performance too
* check out [meteo-buffs](../meteo-buffs/) since its connected to this for more details and try its testing

***

## Test Commands

these commands are only available on our test server so you can quickly check things. also check out [test-commands](test-commands.md) for full details.

* `/setgymstats` - max out all gym stats instantly
* `/gym set strength 500` - set a specific stat (strength, dexterity, endurance)
* `/gym add strength 100` - add to a stat
* `/gym energy 250` - set energy level
* `/gym max` - max all stats to 1000
* `/cleargyminjury` - quick clear injury

***

## Good to Know

* all gym locations, exercises, stat gains, energy costs, injury settings and modifier values are configurable on our config. you can change them once you get the server. we will guide you :)
* stats max out at 1000. strength boosts melee damage, dexterity boosts movement speed, endurance boosts stamina regen
* stats slowly decay when players dont workout for a while
