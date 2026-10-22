---
description: >-
  Meteo electrician job - group fuse box repair job run through the phone, with
  fusebox minigame, shock damage on failure, challenge timers, night bonus and 5
  level progression designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-electricianjob/
---

# Meteo Electrician Job

This is a guide about testing the Meteo V2 electrician job script designed exclusively for the Meteo V2 package. group fuse box repair job that you clock in and out of through the Labor app on the phone, with a fusebox minigame, shock damage and ragdoll on failure, burning boxes that stop burning once fixed, per-box pay, challenge timers, night bonus, vehicle deposit damage system, crew support and 5 level progression.

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
* Have a [phone](../meteo-phone/) - the job runs through the Labor app

***

## Testing Electrician Job

{% stepper %}
{% step %}
**Go to the dispatcher and get a work van**

go to the Water & Power depot (marked on the map). talk to the LSDWP Dispatcher and pick "get me a work vehicle". pick a van from the list - each van needs a deposit and some are locked behind higher levels. the van spawns in one of the depot bays
{% endstep %}

{% step %}
**Clock in from the phone**

get in the driver seat of your work van. open the phone, open the Labor app and pick the electrician job. press "clock in". you must be the driver of your own work van or the clock in is refused. once clocked in you are waiting for dispatch
{% endstep %}

{% step %}
**Accept a repair task**

dispatch sends you a repair task on the phone. you have a short time to answer (30 seconds by default). press "take the job" to accept or "pass" to skip it. passing adds a small wait before the next offer. once accepted the gps routes you to the task area
{% endstep %}

{% step %}
**Find the burning boxes**

arrive at the task area. every box on the task is marked on the map and burns with an electric fire until it is fixed. walk up to a box and use the "fix electrical box" target option
{% endstep %}

{% step %}
**Repair with the minigame**

the fusebox minigame from meteo-minigames starts. success: the box is repaired, the fire goes out and you get paid for that box right away. failure: you get shocked (ragdoll, health damage and spark effect) and you can try the box again
{% endstep %}

{% step %}
**Watch out for shock damage**

every failed repair hurts. fail too many times in a row and you can go down. if you go down during a task, the task fails
{% endstep %}

{% step %}
**Complete the task**

after all boxes are repaired you get the completion payout with a breakdown of every bonus. the payout and xp show on the phone and the task is saved in the Labor app history. a new task is offered after a short cooldown
{% endstep %}

{% step %}
**Clock out and return the van**

press "clock out" in the Labor app, or talk to the dispatcher and pick "end my shift". once off duty, talk to the dispatcher and pick "return my vehicle" to get your deposit back
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* each repaired box pays right away ($80-120 per box by default)
* task completion pays a base reward ($200-350 by default) plus bonuses
* bonuses on completion: job level bonus, night shift bonus, challenge bonus and perk bonus
* higher levels get more boxes per task = more total pay
* every payout is cash

***

## Crews - Working Together

{% stepper %}
{% step %}
**Create or join a crew**

open the Groups app on the phone. create a crew and invite people by state id or from people around you, or accept a crew invite. the crew leader runs the job for everyone
{% endstep %}

{% step %}
**Leader clocks in**

only the leader gets the van, clocks in and accepts tasks. members follow the same task in their own Labor app. every member must be free (not on another job and not down) for the leader to clock in or accept
{% endstep %}

{% step %}
**Repair independently**

all members see the same task area and can repair different boxes at the same time. only one player can work on a box at a time - if someone is already on it you get "someone is already repairing this box"
{% endstep %}

{% step %}
**Crew payment**

when all boxes are repaired, every member gets the full completion payout (not split). each box still pays the player who repaired it
{% endstep %}

{% step %}
**Leave the crew**

leave the crew from the Groups app. if the leader clocks out or disconnects, the task ends for the whole crew
{% endstep %}
{% endstepper %}

***

## Levels And Perks

* level 1 Apprentice: 1-3 boxes per task
* level 2 Junior Electrician (800 xp): 3-5 boxes, +5% pay, night bonus unlocked
* level 3 Licensed Electrician (2,000 xp): 4-7 boxes, +10% pay
* level 4 Expert Electrician (4,000 xp): 5-9 boxes, +15% pay
* level 5 Master Electrician (7,000 xp): 7-12 boxes, +20% pay
* bigger vans unlock at levels 2, 3 and 4
* every task also gives civilian perk xp and labor reputation
* your level and xp progress are shown on the electrician job page in the Labor app

***

## Achievements

achievements show in the Awards tab of the Labor app. unlocked rewards are collected there for reputation

* First Fix - repair your first box
* Circuit Breaker / Power Restorer / Grid Guardian / Master of the Grid - repair 50 / 250 / 500 / 1000 boxes
* On the Job - complete your first task
* Reliable Worker / Seasoned Pro / Department Veteran / LSDWP Legend - complete 25 / 75 / 150 / 250 tasks
* Night Shift / After Hours Expert - complete 10 / 50 repairs at night
* Big Earner / Power Tycoon - earn a total of $50,000 / $200,000

***

## Rankings And History

the Labor app has a Rankings tab with leaderboards and a History tab with every task payout. open a receipt in history to see the full breakdown of that task

***

## Testing Challenges

some tasks are challenge tasks (35% chance by default). the offer shows the challenge bonus. finish all boxes before the timer runs out to get a +15-30% challenge bonus on completion. the timer is longer for tasks that are further away or have more boxes

***

## Testing Night Bonus

night bonus is unlocked at level 2. it applies 22:00-06:00 in-game time and adds +10-20% to your pay. use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete a task to see the night shift bonus in the breakdown

***

## Testing Vehicle Damage

if you return the work van damaged, you lose part of your deposit. no damage = full refund, light damage = 85%, more damage = 60% or 30%, wrecked = no refund. try returning a clean van vs a damaged van

***

## Testing Minigame Difficulty

minigame difficulty is the same for all levels (no scaling). failure rate depends on player skill, not level. more boxes at higher levels = more total earnings, not a harder minigame

***

## Good to Know

{% hint style="success" %}
electrician job runs through the Labor app on the phone - no tablet needed. crews come from the Groups app and the leader runs the job. all members get full payment on task completion (not split). multiple players on same box: the script tells you if the box is already being repaired. if the leader disconnects, the task is cancelled for the whole crew.

Add or edit the depot (dispatcher, map marker and van bays) and the repair box groups in-game with the **Electrician Job** creator.

Pay, challenge and night bonuses, perk xp and reputation rewards, work vans, deposit refund and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-minigames/" %}
[meteo-minigames](../meteo-minigames/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
