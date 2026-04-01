---
description: >-
  Meteo electrician job - group electrician job with fuse box repairs designed
  exclusively for the meteo fivem server.
---

# Meteo Electrician Job

This is a guide about testing the meteo fivem electrician job script designed exclusively for meteo server. group electrician job. repair electrical fuse boxes with minigame, earn money per box repaired. works solo or with group. harder than cleaning, better pay.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-electricianjob-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Have the [job tablet](../meteo-jobtablet/) ready

***

## Testing Electrician Job

{% stepper %}
{% step %}
**Get the tablet and go to dispatcher**

use `/giveitem id meteo_jobtablet` to spawn the tablet. go to electrician dispatcher location. talk to the npc and pick up a work van. get in the vehicle and open tablet
{% endstep %}

{% step %}
**Clock in**

open tablet and go to electrician job. click "clock in" button. once clocked in u will see "waiting for task" status
{% endstep %}

{% step %}
**Accept an electrical task**

server will dispatch a new electrical task automatically. u will see task location with number of fuse boxes to repair. click "accept task" to start. gps will route u to the task location. follow the gps marker
{% endstep %}

{% step %}
**Find electrical boxes**

arrive at task location (within area radius). u will see electrical fuse boxes marked on map. boxes are networked entities spawned when task starts. boxes have fire particle effects (unrepaired boxes are burning). approach each box and interact with ox_target/qb-target
{% endstep %}

{% step %}
**Repair with minigame**

select "repair box" option on the box. fuse box minigame starts (meteo-fuseboxfix) - minigame is a sequence puzzle. success: box repaired, fire effect removed, u get paid. failure: u get electrocuted (shock animation + damage), need to retry. each successful repair = immediate payment
{% endstep %}

{% step %}
**Watch out for shock damage**

if u fail the minigame, u get shocked. shock causes: ragdoll animation + health damage + shock particle effect. can happen multiple times if u keep failing. careful with failures - take too much damage and u die
{% endstep %}

{% step %}
**Complete the task**

after all boxes are repaired at the location, u will see "task completed" message. payment processed for all repaired boxes + completion bonus. earnings show in task history. new task dispatched after cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* payment based on boxes repaired per location
* each box = base pay (Config.perRepairPay)
* more boxes per location = more total earnings
* completion bonus added when all boxes done
* earnings = (boxes repaired x per-box pay) + completion bonus
* higher levels have more boxes to repair = more total pay

***

## Groups - Working Together

{% stepper %}
{% step %}
**Create or join a group**

open tablet and go to electrician job. click "create group" to start a group. or u can see existing groups and ask to join one. group leader can invite friends. members see the same task location and can help repair boxes
{% endstep %}

{% step %}
**Repair independently**

when in a group, all members see the same task location. each member can repair different boxes independently. all repaired boxes count toward task completion. only one player can repair a box at a time - if another player tries to repair same box, u get notified "box busy"
{% endstep %}

{% step %}
**Group payment**

when all boxes are repaired, entire group gets paid. all members get full payment (Config.memberCompletionPercent = 100%). solo: u repair 8 boxes = 8 x box pay + bonus. group of 3: combined 8 boxes = all 3 get (8 x box pay + bonus)
{% endstep %}

{% step %}
**Leave group**

click "leave group" in tablet. u are removed from group. group continues without u (if other members still there). if last member leaves, group is disbanded
{% endstep %}
{% endstepper %}

***

## Levels And Perks

* level 1: access to basic electrical tasks (4-5 boxes)
* level 2: unlock more locations and +10% pay + night bonus access
* level 3: access harder jobs (+20% pay)
* level 4: +30% pay bonus
* level 5: +40% pay + all perks + hardest jobs unlocked
* complete more tasks and earn xp to level up

***

## Achievements

* complete 10 electrical tasks
* complete 50 electrical tasks
* repair 100 boxes total
* repair 500 boxes total
* earn $100,000
* earn $500,000
* complete perfect task (all boxes repaired, no failures)

***

## Testing Challenges

some electrical tasks have challenge timers (30% chance). complete all boxes within time limit to get bonus. bonus calculated by time remaining and difficulty. challenge timer shown in tablet

***

## Testing Night Bonus

night bonus is unlocked at level 2. once u reach level 2, night bonus applies 22:00-06:00 in-game time. gives +15% bonus on top of base pay during night hours. use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete task to see bonus

***

## Testing Vehicle Damage

if u damage work van too much, u lose part of your deposit. deposit refund based on vehicle damage percent. damaged van = reduced earnings. try completing tasks with clean vs damaged van

***

## Testing All Levels And Boxes

to see all electrical locations and perks instantly, use `/setcivlevel electrician 5` (testing command). this gives u level 5 status immediately. now u have access to all electrical task locations. test level 1 vs level 5 to see difference in pay and boxes per task

***

## Testing Minigame Difficulty

minigame difficulty is same for all levels (no scaling). just do the fuse box repair sequence correctly. failure rate depends on player skill, not level. more boxes at higher levels = more total earnings, not harder minigame

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
electrician job supports groups - leader spawns vehicle and accepts tasks. all group members can repair boxes independently at same location. box locations configured with multiple variants per level. minigame is same difficulty for all levels (no scaling by level). boxes have fire particle effects while unrepaired. shock effect on minigame failure: ragdoll + damage + particle effect. challenge timer chance set in Config.challenge (30% default). night bonus requires level 2+ and applies 22:00-06:00 in-game time. vehicle damage tracked - deposit refund uses Config.depositDamage percent. all members get full payment on task completion (not split). multiple players on same box: script notifies if box already being repaired (box busy). once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet, groups, achievements, rankings
{% endcontent-ref %}
