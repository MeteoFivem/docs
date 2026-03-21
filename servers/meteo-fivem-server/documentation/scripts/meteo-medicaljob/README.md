---
description: >-
  Meteo medical job - injury system, treatment, hospitals and EMS script
  designed exclusively for the meteo fivem server.
---

# Meteo Medical Job

This is a guide about testing the meteo fivem medical job and injury script designed exclusively for meteo server. this script has advanced injury tracking (5 damage types, 13 body parts), hospital management, patient treatment, medical items and death states. connected with [meteo-buffs](../meteo-buffs/), [meteo-gym](../meteo-gym/), [meteo-hud](../meteo-hud/), [meteo-inventory](../meteo-inventory/) and more.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing as a Player (No Job Needed)

### Injury System

* get damaged by getting shot, punched, falling from height, or getting hit by fire
* your character will get injuries on specific body parts (head, chest, arms, legs etc.)
* if your legs get injured your character will start limping
* open meteo inventory and check the skeleton display - injuries show on the body with details
* check f1 menu > Character Stats to see injury info too

### Bleeding

* when you take damage there is a chance you start bleeding (levels 0 to 4)
* bleeding drains your health over time. the higher the level the more damage
* use these items to stop bleeding:
  * `/giveitem yourid bandage 3` - reduces bleeding by 1 level
  * `/giveitem yourid gauze 3` - reduces bleeding by 1 level
  * `/giveitem yourid tourniquet 1` - reduces bleeding by 2 levels
  * `/giveitem yourid ifaks 1` - reduces bleeding by 3 levels (strongest)

### Healing Items

* `/giveitem yourid bandage 3` - heals 15 HP, treats cuts and bruises
* `/giveitem yourid gauze 3` - heals 30 HP, treats cuts and gunshots
* `/giveitem yourid firstaid 1` - heals 100 HP (full heal)
* `/giveitem yourid ifaks 1` - heals 100 HP, treats cuts, bruises and gunshots on entire limb

### Injury Treatment Items

* `/giveitem yourid splint 1` - treats fractures (from falls and heavy impacts)
* `/giveitem yourid burnkit 1` - treats burns (from fire and explosions)

### Painkillers and Adrenaline

* `/giveitem yourid painkillers 1` - removes limping, slowly heals +5 HP every 2s for 2 minutes. 5 min cooldown
* `/giveitem yourid adrenaline 1` - removes limping, 20% damage reduction, speed boost, cant be ragdolled for 1 minute. 10 min cooldown
* these also affect gym performance (check [meteo-buffs](../meteo-buffs/) testing guide)

### Death States

* when you take too much damage you go **KO** (knocked out) - you can crawl on the ground. anyone can help you up. 120s timer before respawn
* if you take more damage while KO you go **BW** (black and white/critical) - you cant move. only EMS can revive you with defibrillator or medicalkit. 5 min timer before respawn

### Hospital Check-in

* you can check yourself into hospital by going to the check-in desk at any hospital
* it costs money ($500 at LS Medical, $300 at Blane County, free at Prison)
* you get placed in a hospital bed and fully heal after 60 seconds

***

## Testing as EMS

### Setup

* set your job to ambulance: `/setjob yourid ambulance 4`
* lets go to Blane County Medical for testing

### Blane County Medical Locations

* **duty station** - `/tp 1101.0105, 2725.4763, 38.7121` go here and toggle on duty first
* **armory** - `/tp 1112.5284, 2742.7329, 38.7097` go here and buy medical supplies with job funds
* **personal locker (stash)** - `/tp 1121.4153, 2718.9778, 38.7097` go here to store your medical supplies
* **check-in desk** - `/tp 1100.3995, 2723.5591, 38.7097` this is where players check themselves in to heal
* **locker room (clothing)** - `/tp 53.8490, -387.0211, 39.3781` change into EMS uniform. check out [meteo-appearance](../meteo-appearance/)
* **ems garage** - `/tp 1093.9653, 2741.2776, 38.6723` get ems vehicles. check out [meteo-jobgarage](../meteo-jobgarage/)
* **boss menu** - `/tp 68.8365, -352.0688, 43.9347` access boss menu. check out [meteo-bossmenuv2](../meteo-bossmenuv2/)

### Treating Patients

* point target at a player and select "Check Patient"
* you can see their health, bleeding level, all injuries with body part and severity
* from there you can treat bleeding, treat specific injuries, heal patient HP, help up KO players, and revive BW players

### Hospitals

there are 3 hospital locations. each has duty station, armory and personal locker:

* **LS Medical Center** - `/tp 70.3482, -378.1653, 40.6636` (8 beds, $500 check-in)
* **Blane County Medical** - `/tp 1100.3995, 2723.5591, 38.7097` (3 beds, $300 check-in)
* **Prison Medical** - `/tp 1769.9105, 2571.7930, 45.7299` (6 beds, free)

***

## Good to Know

* all hospital locations, bed positions, healing times, item effects, check-in prices, bleeding damage and injury settings are configurable on our config. you can change them once you get the server. we will guide you :)
* treatments have optional skill check minigames that can be enabled/disabled in config
* defibrillator is reusable (not consumed on use) but medicalkit gets consumed
* connected with [meteo-buffs](../meteo-buffs/) for painkillers and adrenaline performance effects
* connected with [meteo-inventory](../meteo-inventory/) for injury skeleton display
