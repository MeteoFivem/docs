---
description: >-
  Meteo taxi job - taxi driver job with 5 levels, distance-based earnings, tip
  chance, night bonus and challenge timers designed exclusively for the meteo
  fivem server.
---

# Meteo Taxi Job

This is a guide about testing the meteo fivem taxi job script designed exclusively for meteo server. taxi driver job with 5 level progression, distance-based earnings, tip chance at level 3+, night bonus at level 4+, challenge timers and per-ride achievements.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Have the [job tablet](../meteo-jobtablet/) ready

***

## Testing Taxi Job

{% stepper %}
{% step %}
**Get the tablet and go to dispatcher**

use `/giveitem id meteo_jobtablet` to spawn the tablet. go to any taxi stand location (or use `/tp 442.5959, -660.5834, 28.4790, 240.2101` for main taxi dispatcher). talk to the npc and pick up your taxi vehicle. get in the driver seat and open tablet
{% endstep %}

{% step %}
**Clock in**

open tablet and go to taxi job. click "clock in" button. make sure you are in the taxi vehicle driver seat (this is required). once clocked in you will see "waiting for task" status
{% endstep %}

{% step %}
**Accept a task**

server will dispatch a new task automatically. you will see pickup location and destination on map. click "accept task" button to start. gps will route you to pickup location. follow the gps marker
{% endstep %}

{% step %}
**Pick up passenger**

drive to the pickup location (30m radius). when you get close (30m) an npc passenger will spawn. drive closer until ped is within 5m and they will enter your taxi. you will see "passenger in vehicle" status and new gps marker to dropoff
{% endstep %}

{% step %}
**Drop off passenger**

follow gps to dropoff location. once you arrive passenger will exit vehicle automatically. you will see "task completed" message. payment is processed and shown in task history. new task will be dispatched after cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* base pay depends on distance traveled from pickup to dropoff
* you get bonus per kilometer traveled
* every completed ride adds to your ranking
* if you reject a task, there is a cooldown penalty
* payment shown with breakdown in tablet task history

***

## Levels And Perks

* level 1: base earn rate
* level 2: +10% pay bonus
* level 3: +20% pay + tip chance (random bonus per ride)
* level 4: +30% pay + night bonus (22:00-06:00 +15% pay)
* level 5: +40% pay + all previous bonuses
* to unlock higher levels, complete more rides and earn xp
* check tablet rankings to see where you rank vs other taxi drivers

***

## Achievements

* complete 10 rides
* complete 50 rides
* travel 100km total
* travel 500km total
* earn $50,000
* earn $250,000
* each achievement tracks progress and gives bonus xp

***

## Testing Challenges

{% stepper %}
{% step %}
**Get a challenge task**

sometimes you will get a "challenge" task (30% chance). challenges have a timer - complete the route within the time limit
{% endstep %}

{% step %}
**Complete on time**

if you complete challenge on time, you get bonus payment. bonus is calculated based on time left and distance. challenge timer shows in tablet
{% endstep %}
{% endstepper %}

***

## Testing Night Bonus

night bonus is unlocked at level 2. once you reach level 2, night bonus applies 22:00-06:00 in-game time. gives +15% bonus on top of base pay during night hours

use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete ride to see bonus applied

***

## Testing Vehicle Damage

if you damage the taxi too much, you lose part of your deposit. deposit refund calculation based on vehicle damage percent. very damaged vehicle = less refund = less profit. try completing rides with clean vs damaged vehicles to see difference

***

## Testing With Levels

to test all perks quickly, use `/setcivlevel taxi 5` (testing command). this gives you level 5 status immediately. now all perks are active - you can see bonus in earnings. complete rides with level 5 vs level 1 to compare payouts

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
taxi levels and perks are configured in Config.levels with payBonus, tipChance, nightBonus values. challenge timer is generated server-side and includes full route distance (pickup to dropoff). vehicle health tracked - Config.vehicleDamage has penalty thresholds. deposit refund uses Config.depositDamage percent calculations. cooldown between tasks set in Config.taskCooldown with reject penalty. passenger ped models configurable per taxi type. once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/)
{% endcontent-ref %}
