---
description: >-
  Meteo medical job - injury system, treatment, hospitals with in-game creator
  and EMS script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-medicaljob/
---

# Meteo Medical Job

This is a guide about testing the Meteo V2 medical job and injury script designed exclusively for the Meteo V2 package. This script has advanced injury tracking (5 damage types, 13 body parts), hospital management, patient treatment, medical items and death states. Connected with [meteo-buffs](../meteo-buffs/), [meteo-gym](../meteo-gym/), [meteo-hud](../meteo-hud/), [meteo-inventory](../meteo-inventory/) and more.

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

## Testing as a Player (No Job Needed)

### Injury System

{% stepper %}
{% step %}
Get damaged by getting shot, punched, falling from height, or getting hit by fire
{% endstep %}

{% step %}
Your character will get injuries on specific body parts (head, chest, arms, legs etc.)
{% endstep %}

{% step %}
If your legs get injured your character will start limping
{% endstep %}

{% step %}
Open meteo inventory and check the skeleton display - injuries show on the body with details
{% endstep %}

{% step %}
Check f1 menu > Character Stats to see injury info too
{% endstep %}
{% endstepper %}

### Bleeding

* When you take damage there is a chance you start bleeding (levels 0 to 4)
* Bleeding drains your health over time. The higher the level the more damage
* Use these items to stop bleeding:

{% hint style="warning" %}
`/giveitem yourid bandage 3` - reduces bleeding by 1 level `/giveitem yourid gauze 3` - reduces bleeding by 1 level `/giveitem yourid tourniquet 1` - reduces bleeding by 2 levels `/giveitem yourid firstaid 1` - reduces bleeding by 2 levels `/giveitem yourid ifaks 1` - reduces bleeding by 3 levels (strongest)
{% endhint %}

### Healing Items

{% hint style="warning" %}
`/giveitem yourid bandage 3` - heals 15 HP, treats cuts and bruises `/giveitem yourid gauze 3` - heals 30 HP, treats cuts and gunshots `/giveitem yourid firstaid 1` - heals 100 HP (full heal) and treats the whole body `/giveitem yourid ifaks 1` - heals 100 HP, treats cuts, bruises and gunshots on entire limb
{% endhint %}

### Injury Treatment Items

{% hint style="warning" %}
`/giveitem yourid splint 1` - treats fractures (from falls and heavy impacts) `/giveitem yourid burnkit 1` - treats burns (from fire and explosions)
{% endhint %}

### Painkillers and Adrenaline

{% hint style="warning" %}
`/giveitem yourid painkillers 1` - removes limping, slowly heals +5 HP every 2s for 2 minutes. 5 min cooldown `/giveitem yourid adrenaline 1` - removes limping, 20% damage reduction, speed boost, cant be ragdolled for 1 minute. 10 min cooldown
{% endhint %}

* These also affect gym performance (check [meteo-buffs](../meteo-buffs/) testing guide)

### Death States

* When you take too much damage you go **KO** (knocked out) - you can crawl on the ground. Anyone can help you up. 120s timer before respawn
* If you take more damage while KO you go **BW** (black and white/critical) - you cant move. Only EMS can revive you with defibrillator or medicalkit. 5 min timer before respawn
* While KO you can hold **E** to give up and go straight to unconscious
* While downed hold **G** to alert on duty EMS. The call goes to the dispatch in [meteo-mdt](../meteo-mdt/) and when a medic replies you see the message on your death screen
* When the respawn timer runs out hold **E** to respawn at the nearest hospital

### Hospital Check-in

{% stepper %}
{% step %}
You can check yourself into hospital by going to the check-in desk at any hospital
{% endstep %}

{% step %}
It costs money ($500 at LS Medical, $300 at Blane County, free at Prison)
{% endstep %}

{% step %}
You get placed in a hospital bed and fully heal after 60 seconds
{% endstep %}

{% step %}
Hold **E** to get out of the bed when you are done
{% endstep %}
{% endstepper %}

***

## Testing as EMS

### Setup

{% hint style="warning" %}
`/setjob yourid ambulance 4`
{% endhint %}

* Lets go to Blane County Medical for testing

### Blane County Medical Locations

* **duty station** - `/tp 1101.0105, 2725.4763, 38.7121` go here and toggle on duty first
* **armory** - `/tp 1112.5284, 2742.7329, 38.7097` go here and buy medical supplies with job funds
* **personal locker (stash)** - `/tp 1121.4153, 2718.9778, 38.7097` go here to store your medical supplies
* **check-in desk** - `/tp 1100.3995, 2723.5591, 38.7097` this is where players check themselves in to heal
* **locker room (clothing)** - `/tp 53.8490, -387.0211, 39.3781` change into EMS uniform. Check out [meteo-appearance](../meteo-appearance/)
* **ems garage** - `/tp 1093.9653, 2741.2776, 38.6723` get ems vehicles. Check out [meteo-jobgarage](../meteo-jobgarage/)
* **boss menu** - `/tp 68.8365, -352.0688, 43.9347` access boss menu. Check out [meteo-bossmenu](../meteo-bossmenu/)

### Treating Patients

{% stepper %}
{% step %}
Point target at a player and select "Check Patient"
{% endstep %}

{% step %}
You can see their health, bleeding level, all injuries with body part and severity
{% endstep %}

{% step %}
From there you can treat bleeding, treat specific injuries, heal patient HP, help up KO players, and revive BW players
{% endstep %}
{% endstepper %}

### Hospital Beds

* Go near a hospital bed and use target. **Use Bed** lies you down on it
* If you are escorting a patient you get **Place Patient** to put them on the bed
* Healing patient HP with items needs the patient to be in a hospital bed

### Hospitals

The package ships with 3 hospitals. Each has duty station, armory and personal locker:

* **LS Medical Center** - `/tp 70.3482, -378.1653, 40.6636` (8 beds, $500 check-in)
* **Blane County Medical** - `/tp 1100.3995, 2723.5591, 38.7097` (3 beds, $300 check-in)
* **Prison Medical** - `/tp 1769.9105, 2571.7930, 45.7299` (6 beds, free, dead players do not respawn here)

### Hospital Creator

{% stepper %}
{% step %}
Open the admin menu with `/admin` and go to Script Settings > Medical. The Creator section lists every hospital
{% endstep %}

{% step %}
Add a hospital, give it a name, aim at the main entrance for the map blip and set the check-in fee (0 makes it free)
{% endstep %}

{% step %}
Place the beds - a body lies on the bed while you place it so you can line it up with the mattress. Then add check-in desks, duty spots, supply points and lockers
{% endstep %}

{% step %}
Turn on **Skip on respawn** for hospitals dead players should not wake up at, like the prison hospital
{% endstep %}
{% endstepper %}

* In the same menu you can change the medical armory, what each medical item does, and hospital options like wiping inventory on respawn or clearing stress after a bed heal

***

## Good to Know

{% hint style="success" %}
Hospital options, medical supplies in the armory and what each medical item does are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit hospitals, beds, check-in desks and fees, duty spots, supply points and lockers in-game with the Hospitals creator. Script Settings is god-tier only.
{% endhint %}

* Treatments have optional skill check minigames that can be enabled/disabled in config
* Defibrillator is reusable (not consumed on use) but medicalkit gets consumed

{% content-ref url="../meteo-buffs/" %}
[meteo-buffs](../meteo-buffs/)
{% endcontent-ref %}

{% content-ref url="../meteo-inventory/" %}
[meteo-inventory](../meteo-inventory/)
{% endcontent-ref %}
