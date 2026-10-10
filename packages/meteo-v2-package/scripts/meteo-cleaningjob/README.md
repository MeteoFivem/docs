---
description: >-
  Meteo cleaning job - group spot-based cleaning job run from the phone Labor
  app, with a broom sweeping minigame, challenge timers, night bonus and 5 level
  progression designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-cleaningjob/
---

# Meteo Cleaning Job

This is a guide about testing the Meteo V2 cleaning job script designed exclusively for the Meteo V2 package. Group spot-based cleaning job run from the Labor app on your phone, with a broom sweeping minigame per spot, per-spot immediate payment, challenge timers, night bonus at level 2+, vehicle deposit damage system, crew task sharing and 5 level progression.

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
* Have a [phone](../meteo-phone/) - the job runs from the Labor app, which is installed by default

***

## Testing Cleaning Job

{% stepper %}
{% step %}
**Go to the dispatcher**

go to the Sunset Bleach depot marked on the map and talk to the dispatcher. the dispatcher can give you a work vehicle, a broom, take your vehicle back and end your shift
{% endstep %}

{% step %}
**Get a broom and a work vehicle**

choose "Get a broom" to receive a `meteo_broom`. you need it out in your hands to clean spots. then choose "Get me a work vehicle" and pick a van. each van needs a deposit in cash and some vans unlock at higher levels
{% endstep %}

{% step %}
**Clock in from the phone**

sit in the driver seat of your work van, open your phone and go to the Labor app. open the cleaning job and press "Clock in". you are now on duty and waiting for dispatch
{% endstep %}

{% step %}
**Accept a cleaning task**

dispatch sends you a task offer on the phone. press "Take the job" to accept or "Pass" to skip it. the offer only stands for a short time. once accepted, the work area is marked on the map. drive to it
{% endstep %}

{% step %}
**Find cleaning spots**

arrive at the work area. litter spots are marked on the map. use your `meteo_broom` from the inventory to take it out, walk to a spot and use the target option "Clean this spot"
{% endstep %}

{% step %}
**Clean the spot**

the sweeping minigame starts. shake your mouse to sweep until the spot is clean. press backspace to stop. each cleaned spot pays you straight away
{% endstep %}

{% step %}
**Complete the task**

after all spots in the area are cleaned, the task completes and the completion bonus is paid. the payout shows in the Labor app and in your task history. the next task is dispatched after a short cooldown
{% endstep %}

{% step %}
**End your shift**

press "Clock out" in the Labor app or choose "End my shift" at the dispatcher. then drive the van back and choose "Return my vehicle" to get your deposit back
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* every spot pays immediately to the player who cleaned it
* per-spot pay is rolled once per task, then paid for every spot
* a completion bonus is paid when all spots are done
* higher levels get more spots per task and a pay bonus on top
* earnings = (spots cleaned x per-spot pay) + completion bonus
* all payouts are paid in cash
* every task also gives cleaning XP, reputation in the Labor app and perk XP

***

## Crews - Working Together

{% stepper %}
{% step %}
**Create or join a crew**

open the Groups app on your phone and create a crew, or join one you are invited to. the crew leader can invite players by state ID
{% endstep %}

{% step %}
**Leader runs the shift**

only the crew leader takes the work van, clocks in and accepts tasks. every member needs to be free - not on another job and not incapacitated
{% endstep %}

{% step %}
**Clean independently**

all crew members see the same work area. each member can clean different spots. all cleaned spots count toward task completion and each spot pays the member who cleaned it
{% endstep %}

{% step %}
**Crew payment**

when all spots are cleaned, every member gets the full completion bonus - it is not split
{% endstep %}

{% step %}
**Leaving a crew**

leave the crew from the Groups app. if the leader clocks out, the crew shift ends for everyone
{% endstep %}
{% endstepper %}

***

## Levels And Perks

* level 1 (Cleaner Trainee): up to 3 spots per task
* level 2 (Junior Cleaner, 800 XP): up to 5 spots, +5% pay, +10% XP, night bonus unlocked
* level 3 (Professional Cleaner, 2,000 XP): up to 7 spots, +10% pay, +25% XP
* level 4 (Expert Cleaner, 4,000 XP): up to 9 spots, +15% pay, +40% XP
* level 5 (Master Cleaner, 7,000 XP): up to 12 spots, +20% pay, +60% XP
* better vans unlock at levels 2, 3 and 4
* clean more spots and finish more tasks to earn XP and level up

***

## Achievements

achievements show in the Awards tab of the Labor app. collect them there to get the reputation reward

* complete your first cleaning task
* complete 25, 75, 150 and 250 cleaning tasks
* clean your first spot
* clean 50, 250, 500 and 1000 spots
* clean 10 and 50 spots at night

***

## Testing Challenges

some cleaning tasks come with a challenge timer (35% chance). finish all spots before the timer runs out to get a bonus of 15-30% extra pay. the time limit is based on how far you have to drive

***

## Testing Night Bonus

night bonus is unlocked at level 2. once you reach level 2, night bonus applies 22:00-06:00 in-game time. it multiplies the pay by 1.15x-1.25x during night hours. use the `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night

***

## Testing Vehicle Damage

if you damage the cleaning van, you lose part of your deposit when you return it. a clean van gives the full deposit back, and the refund drops the more damaged it is. try returning a clean van vs a damaged one

***

## Good to Know

{% hint style="success" %}
cleaning job supports crews - the leader takes the van, clocks in and accepts tasks. all crew members can clean spots independently at the same area. you need a `meteo_broom` out to clean. a task fails if you are incapacitated while solo, or if every crew member is down.
{% endhint %}

{% hint style="info" %}
Pay per task and per spot, XP, the challenge and night bonuses, perk XP, reputation, work vans and deposits, the deposit refund steps and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit the depot (dispatcher, van bays and map marker) and the cleaning areas in-game with the Cleaning Job creator.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
