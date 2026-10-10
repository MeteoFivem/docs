---
description: >-
  Meteo taxi job - taxi driver job run from the phone with 5 levels,
  distance-based fares, tips, wealthy passengers, night bonus and challenge
  timers designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-taxijob/
---

# Meteo Taxi Job

This is a guide about testing the Meteo V2 taxi job script designed exclusively for the Meteo V2 package. Taxi driver job you run from the Labor app on your phone - grab a cab, take fares from dispatch, pick up npc passengers and drive them to their destination. 5 level progression, distance-based fares, tips, wealthy passengers, speed bonus, night bonus, challenge timers and using your own car at higher levels.

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
* Some cash on you for the cab deposit

***

## Testing Taxi Job

{% stepper %}
{% step %}
**Go to the dispatcher**

go to the taxi dispatcher (Taxi Job blip on the map, or use `/tp 898.0183, -175.0788, 73.8161, 254.0420`). talk to the npc and pick "Get me a vehicle". pick a cab and pay the deposit
{% endstep %}

{% step %}
**Clock in from your phone**

get in the driver seat of your cab (required). open the phone, go to the **Labor** app and open the taxi job. tap "Clock in". you are now on duty and waiting for dispatch
{% endstep %}

{% step %}
**Take a fare**

dispatch sends you a fare. the offer card shows the pickup and destination. tap "Take the job" to accept or "Pass" to turn it down (passing adds a short wait before the next offer). the offer expires if you do not answer in time. gps routes you to the pickup
{% endstep %}

{% step %}
**Pick up the passenger**

drive to the pickup. when you get within 30m an npc passenger appears. stop within 5m and they walk over and get in your cab. you get the "passenger on board" status and a new gps marker to the destination
{% endstep %}

{% step %}
**Drop off the passenger**

follow the gps to the destination. once you stop at the marker the passenger gets out by themselves and the fare completes. you get paid in cash, the breakdown shows in your Labor app and the next fare is dispatched after a short cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* every fare = a small drop charge ($3-5) + a rate for every metre driven
* short trips (up to 1km): $0.05-0.50 per metre
* medium trips (up to 5km): $0.05-0.10 per metre
* long trips (over 5km): $0.10-0.25 per metre, and the most XP
* level bonus, night bonus, challenge bonus, speed bonus, tips, wealthy passenger bonus and perk bonus are added on top
* damage to your cab lowers the fare
* pay goes to your cash, the full breakdown shows in the Labor app history

***

## Levels And Perks

the taxi job has its own levels, separate from your Labor reputation

* level 1 - Trainee Driver: base fares
* level 2 - Taxi Driver: +3% pay + night bonus + upgraded cabs
* level 3 - Professional Driver: +6% pay + 15% tip chance
* level 4 - Senior Driver: +9% pay + 25% tip chance + speed bonus + 50% bonus XP + wealthy passengers (15%) + use your own car
* level 5 - Elite Driver: +12% pay + 40% tip chance + speed bonus + 50% bonus XP + wealthy passengers (30%) + use your own car
* finish fares to earn taxi XP and level up
* check the Rankings tab in the Labor app to see where you rank vs other drivers

***

## Perks Explained

* **tips** - when a passenger tips they add 10-20% on top of the fare
* **wealthy passengers** - pay +25% on the fare
* **speed bonus** - finish the trip in under 80% of the estimated time for +20%
* **own car** - from level 4 you can clock in from the driver seat of a car you own instead of a job cab

***

## Cabs

* Panto - level 1, $500 deposit
* Vapid Stanier - level 1, $750 deposit
* Issi Classic - level 2, $1,000 deposit
* Dilettante - level 3, $1,500 deposit
* return the cab at the dispatcher ("Return my vehicle") to get your deposit back - you need to clock out first

***

## Achievements

taxi achievements show in the Awards tab of the Labor app. each one pays out reputation once you collect it

* First Fare - complete your first taxi ride
* Regular Driver - complete 25 taxi rides
* Veteran Cabbie - complete 100 taxi rides
* Taxi Legend - complete 500 taxi rides
* Night Rider - complete 50 rides during night hours
* Speed Demon - complete 25 challenge tasks on time
* Big Earner - earn $50,000 from taxi fares
* Taxi Tycoon - earn $200,000 from taxi fares
* Perfect Ride - complete 10 rides with zero vehicle damage
* Elite Driver - reach Elite taxi rank

***

## Testing Challenges

{% stepper %}
{% step %}
**Get a challenge fare**

30% of fares are challenge fares with a timer on screen. the timer is worked out from the trip distance
{% endstep %}

{% step %}
**Complete on time**

drop the passenger off before the timer runs out to get a 39-50% bonus on the fare
{% endstep %}
{% endstepper %}

***

## Testing Night Bonus

night bonus is unlocked at level 2. it applies 22:00-06:00 in-game time and multiplies the fare by 1.3x-1.5x

use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete a ride to see the bonus in the breakdown

***

## Testing Vehicle Damage

two things happen when you damage your cab:

* the fare is lowered (down to 50% at heavy damage)
* you get back less of the deposit when you return it (100% for no damage, 0% when wrecked)

try completing rides with a clean vs damaged cab to see the difference

***

## Good to Know

{% hint style="success" %}
the taxi job is solo only - it cannot be run as a crew. you can only be clocked in to one Labor job at a time. every finished fare also gives Labor reputation and civilian perk XP. if your passenger dies the fare is cancelled.
{% endhint %}

{% hint style="info" %}
Fares, bonuses (challenge, night, tips, speed), rewards (perk XP and reputation), cabs, damage and deposit refunds, and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit the depot (dispatcher, cab bays and map marker) and the pickup and drop-off places in-game with the Taxi Job creator.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}
