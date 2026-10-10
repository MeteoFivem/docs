---
description: >-
  Meteo repo job - vehicle repossession job run from the phone with 3 vehicle
  classes, neighbourhood based pickups, 6 rank progression, night bonus and
  challenge timers designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-repojob/
---

# Meteo Repo Job

This is a guide about testing the Meteo V2 repo job script designed exclusively for the Meteo V2 package. Vehicle repossession job you run from the Labor app on your phone - grab a tow truck, take recovery jobs from dispatch, hook the car, tow it to the drop-off and inspect it. 3 vehicle classes (normal, high end, exotic), neighbourhood based pickups, 6 repo ranks, night bonus, challenge timers and deposit based damage penalties.

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
* Have your [phone](../meteo-phone/) ready - the job runs through the **Labor** app
* Some cash on you for the tow truck deposit

***

## Testing Repo Job

{% stepper %}
{% step %}
**Go to the dispatcher**

go to the repo job dispatcher (Repo Job blip on the map, or use `/tp 498.4681, -1340.0299, 29.3143, 8.2895`). talk to the npc and pick "Get me a tow truck". pick a truck and pay the deposit
{% endstep %}

{% step %}
**Clock in from your phone**

get in the driver seat of your tow truck (required). open the phone, go to the **Labor** app and open the repo job. tap "Clock in". you are now on duty and waiting for dispatch
{% endstep %}

{% step %}
**Take a recovery job**

dispatch sends you a recovery job. the offer card shows the vehicle class, pickup and drop-off. tap "Take the job" to accept or "Pass" to turn it down (passing adds a short wait before the next offer). the offer expires if you do not answer in time. gps routes you to the vehicle
{% endstep %}

{% step %}
**Find the vehicle**

drive to the marked area. when you get close the repo vehicle spawns with its owner standing next to it. get closer and the owner spots you and runs off - the car is now free to tow
{% endstep %}

{% step %}
**Hook the vehicle**

reverse the back of your tow truck up to the car. it hooks on by itself (see [The Tow Hook](#the-tow-hook) below). you get the "vehicle hooked to tow truck" status and a new gps marker to the drop-off
{% endstep %}

{% step %}
**Tow to the drop-off**

follow the gps to the drop-off. drop-offs are always at least 1000m away from the pickup. drive carefully - damage to the towed car lowers your pay
{% endstep %}

{% step %}
**Detach and inspect**

at the drop-off, detach the car from your tow truck. once it is off the truck you get an "Inspect Vehicle" option on the car. inspect it and the job completes. you get paid in cash, the breakdown shows in your Labor app and the next job is dispatched after a short cooldown
{% endstep %}
{% endstepper %}

***

## The Tow Hook

This is the one thing people get stuck on, so here it is on its own.

{% hint style="success" %}
**There is no custom hook keybind.** Hooking happens on its own when you back up close enough - this is GTA's own tow truck behaviour.
{% endhint %}

### Picking the vehicle up

* Reverse the back of your tow truck up to the repo vehicle
* The vehicle hooks on by itself and you get the "vehicle hooked to tow truck" status
* A new GPS marker to the drop-off appears at that point

### Dropping it off

* Follow the GPS to the drop-off
* Detach the car from your truck at the marked spot
* Once it is off the truck the "Inspect Vehicle" option appears on the car - inspect it to finish the job

### If nothing is happening

Work down this list:

| Problem | What to check |
| ------- | ------------- |
| It will not hook | Get closer to the car first so the owner runs off - the car is locked in place until then |
| Still will not hook | Approach from the tow truck side - back the truck up towards the car, do not drive at it nose first |
| No inspect option at the drop-off | You have to be at the marked drop-off, and the car has to be off the truck |
| Cannot clock in | You need to be in the driver seat of your own tow truck from the dispatcher |

{% hint style="info" %}
If you have never used a tow truck in GTA 5 before, just reverse the back of the truck up to the front of the car and wait a second.
{% endhint %}

***

## Understanding Vehicle Classes

* normal vehicles: everyday cars (lowest pay)
* high end vehicles: sports and luxury cars (medium pay) - unlocked at rank 3
* exotic vehicles: supercars (highest pay) - unlocked at rank 5
* the neighbourhood of the pickup decides which class is waiting (residential, commercial, industrial, rural, wealthy)
* once you unlock a higher class you also get a chance of an upgraded car on regular pickups

***

## Understanding Earnings

* pay = base fare + distance towed, rolled per job
* normal: $50-80 base fare + $0.03-0.05 per metre towed
* high end: $100-150 base fare + $0.06-0.12 per metre towed
* exotic: $200-400 base fare + $0.10-0.25 per metre towed
* rank bonus, night bonus, challenge bonus and perk bonus are added on top
* damage to the towed car lowers the pay (a clean car pays the full fare)
* pay goes to your cash, the full breakdown shows in the Labor app history

***

## Levels And Perks

the repo job has its own ranks, separate from your Labor reputation

* rank 1 - Repo Trainee: normal vehicles only
* rank 2 - Recovery Agent: +3% pay + night bonus
* rank 3 - Vehicle Specialist: +6% pay + high end vehicles
* rank 4 - Senior Repo: +9% pay + Elite Recovery Truck
* rank 5 - Licensed Pro: +12% pay + exotic vehicles + 50% bonus XP
* rank 6 - Master Repossessor: +15% pay + 50% bonus XP
* finish jobs to earn repo XP and rank up
* check the Rankings tab in the Labor app to see where you stand

***

## Tow Trucks

* Heavy Duty Tow - rank 1, $1,000 deposit
* Elite Recovery Truck - rank 4, $2,000 deposit
* return the truck at the dispatcher ("Return my tow truck") to get your deposit back - you need to clock out first

***

## Achievements

repo achievements show in the Awards tab of the Labor app. each one pays out reputation once you collect it

* First Recovery - complete your first repossession
* Regular Repo - complete 25 repossessions
* Veteran Repo - complete 100 repossessions
* Repo Legend - complete 500 repossessions
* Night Recovery - complete 50 repos during night hours
* Speed Recovery - complete 25 challenge tasks on time
* High-End Hunter - recover 25 high end vehicles
* Exotic Collector - recover 25 exotic vehicles
* Perfect Condition - deliver 10 vehicles with zero damage
* Big Earner - earn $50,000 from repossessions
* Repo Tycoon - earn $200,000 from repossessions
* Master Repossessor - reach Master Repossessor rank

***

## Testing Challenges

30% of jobs are challenge recoveries with a timer on screen. the timer is worked out from the tow distance. finish in time to get a 15-30% bonus on the job

***

## Testing Night Bonus

night bonus is unlocked at rank 2. it applies 22:00-06:00 in-game time and multiplies the job pay by 1.3x-1.5x. use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night

***

## Testing Vehicle Damage

two kinds of damage are tracked:

* the towed car - a damaged car pays less (down to 40% of the fare at heavy damage)
* your tow truck - a damaged truck gets back less of the deposit when you return it (100% for no damage, 0% when wrecked)

try a clean tow vs a rough one and compare the breakdown

***

## Good to Know

{% hint style="success" %}
the repo job is solo only - it cannot be run as a crew. you can only be clocked in to one Labor job at a time. every finished job also gives Labor reputation and civilian perk XP.
{% endhint %}

{% hint style="info" %}
Car pay and pools, bonuses (challenge and night), rewards (perk XP and reputation), tow trucks, damage and deposit refunds, and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit the depot (dispatcher, truck bays and map marker), the pickup lists (one per neighbourhood) and the drop-off lists in-game with the Repo Job creator.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}
