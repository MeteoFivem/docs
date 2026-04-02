---
description: >-
  Meteo cleaning job - group cleaning job with minigame spots designed
  exclusively for the meteo fivem server.
---

# Meteo Cleaning Job

This is a guide about testing the meteo fivem cleaning job script designed exclusively for meteo server. group cleaning job. clean multiple spots in a location, use minigame for each spot, earn money per spot completed. works solo or with group.

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

## Testing Cleaning Job

{% stepper %}
{% step %}
**Get the tablet and go to dispatcher**

use `/giveitem id meteo_jobtablet` to spawn the tablet. go to cleaning job dispatcher location (or use `/tp -105.7079, -69.0300, 58.8590, 281.9016`). talk to the npc and pick up a cleaning van. get in the vehicle and open tablet
{% endstep %}

{% step %}
**Clock in**

open tablet and go to cleaning job. click "clock in" button. once clocked in you will see "waiting for task" status
{% endstep %}

{% step %}
**Accept a cleaning task**

server will dispatch a new cleaning task automatically. you will see task location with number of cleaning spots. click "accept task" to start. gps will route you to the task location. follow the gps marker
{% endstep %}

{% step %}
**Find cleaning spots**

arrive at task location (within area radius). you will see cleaning spots marked on map (trash piles, dirty areas, etc). approach each spot and interact with ox\_target/qb-target
{% endstep %}

{% step %}
**Clean the spot**

select "clean spot" option. minigame starts - complete the cleaning action. complete the sequence to clean the spot. fail and you get nothing for that spot (but can retry). each spot completion = money in your pocket. minigame difficulty same for all levels
{% endstep %}

{% step %}
**Complete the task**

after all spots are cleaned at the location, you will see "task completed" message. payment processed for all cleaned spots + completion bonus. earnings show in task history. new task dispatched after cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* payment based on spots cleaned per location
* each spot = base pay (Config.perSpotPay)
* more spots per location = more total earnings
* completion bonus added when all spots done
* earnings = (spots cleaned x per-spot pay) + completion bonus

***

## Groups - Working Together

{% stepper %}
{% step %}
**Create or join a group**

open tablet and go to cleaning job. click "create group" to start a group. or you can see existing groups and ask to join one. group leader can invite friends. members see the same task location and can help clean spots
{% endstep %}

{% step %}
**Clean independently**

when in a group, all members see the same task location. each member can clean different spots independently. all cleaned spots count toward task completion
{% endstep %}

{% step %}
**Group payment**

when all spots are cleaned, entire group gets paid. payment split: all members get full payment (Config.memberCompletionPercent = 100%). solo: you clean 5 spots = 5 x spot pay + bonus. group of 3: combined 5 spots = all 3 get (5 x spot pay + bonus). all members get paid equally on task completion
{% endstep %}

{% step %}
**Leave group**

click "leave group" in tablet. you are removed from group. group continues without you (if other members still there). if last member leaves, group is disbanded
{% endstep %}
{% endstepper %}

***

## Levels And Perks

* level 1: access to basic cleaning tasks (3-4 spots)
* level 2: unlock more spot locations and +10% pay
* level 3: access harder locations (+20% pay)
* level 4: +30% pay bonus + night bonus (22:00-06:00)
* level 5: +40% pay + all perks + hardest locations unlocked
* complete more tasks and earn xp to level up

***

## Achievements

* complete 10 tasks
* complete 50 tasks
* clean 100 spots total
* clean 500 spots total
* earn $50,000
* earn $250,000
* complete perfect task (all spots cleaned, no fails)

***

## Testing Challenges

some cleaning tasks have challenge timers (30% chance). complete all spots within time limit to get bonus. bonus calculated by time remaining. challenge timer shown in tablet

***

## Testing Night Bonus

night bonus is unlocked at level 2. once you reach level 2, night bonus applies 22:00-06:00 in-game time. gives +15% bonus on top of base pay during night hours. use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete task to see bonus

***

## Testing Vehicle Damage

if you damage cleaning van too much, you lose part of your deposit. deposit refund based on vehicle damage percent. damaged van = reduced earnings. try completing tasks with clean vs damaged van

***

## Testing All Levels And Spots

to see all spot locations and perks instantly, use `/setcivlevel cleaning 5` (testing command). this gives you level 5 status immediately. now you have access to all cleaning spot locations. test level 1 vs level 5 to see difference in pay and available locations

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
cleaning job supports groups - leader spawns vehicle and accepts tasks. all group members can clean spots independently at same location. spot locations configured with multiple variants per level. minigame is same difficulty for all levels (no scaling). challenge timer chance set in Config.challenge (30% default). night bonus requires level 2+ and applies 22:00-06:00 in-game time. vehicle damage tracked - deposit refund uses Config.depositDamage percent. all members get full payment on task completion (not split). group stays active even if member clocks out mid-task. if leader disconnects, task cancelled and all members reset. once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/)
{% endcontent-ref %}
