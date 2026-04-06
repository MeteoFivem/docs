---
description: >-
  Meteo go postal job - group package delivery job with multi-address routes,
  package splitting across group members, challenge timers and 5 level
  progression designed exclusively for the meteo fivem server.
---

# Meteo Go Postal Job

This is a guide about testing the meteo fivem go postal job script designed exclusively for meteo server. group package delivery job with multi-address routes (small to large), package splitting across group members, per-delivery immediate payment, challenge timers, night bonus, vehicle deposit damage system and 5 level progression.

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

## Testing Go Postal Job

{% stepper %}
{% step %}
**Get the tablet and go to dispatcher**

use `/giveitem id meteo_jobtablet` to spawn the tablet. go to postal office dispatcher location. talk to the npc and pick up a postal van (boxville or work vehicle). get in the vehicle and open tablet
{% endstep %}

{% step %}
**Clock in**

open tablet and go to go postal job. click "clock in" button. once clocked in you will see "waiting for task" status
{% endstep %}

{% step %}
**Accept a delivery task**

server will dispatch a new postal route automatically. you will see delivery route with multiple packages and addresses. click "accept task" to start. gps will route you to first delivery address. follow the gps marker
{% endstep %}

{% step %}
**Pick up packages**

at postal office, you start with packages for the route. packages are loaded in your postal van. each route has different number of packages (4-7 packages typical). you can see package count in task info. all packages start in van at beginning of route
{% endstep %}

{% step %}
**Deliver packages**

drive to each marked delivery address. you will see gps marker for each delivery point. stop near building/house entrance. approach the delivery spot (gps marker). interact with ox\_target/qb-target. select "deliver package" option. simple delivery action completes. you get paid immediately for that delivery
{% endstep %}

{% step %}
**Complete the route**

after all packages are delivered at all addresses, you will see "route completed" message. payment processed for all deliveries + completion bonus. earnings show in task history. new route dispatched after cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* payment based on packages delivered on route
* each package = base pay (Config.perDeliveryPay)
* more packages per route = more total earnings
* completion bonus added when all deliveries done
* earnings = (packages delivered x per-delivery pay) + completion bonus
* longer routes across map = more earnings

***

## Groups - Working Together

{% stepper %}
{% step %}
**Create or join a group**

open tablet and go to go postal job. click "create group" to start a group. or you can see existing groups and ask to join one. group leader can invite friends. members see the same delivery route and can help deliver packages
{% endstep %}

{% step %}
**Divide packages**

when in a group, all members see the same delivery route. packages shared across group members. leader can distribute packages or all grab their own. group can split up and deliver different packages simultaneously. faster to work in parallel on different deliveries
{% endstep %}

{% step %}
**Group payment**

when all packages delivered, entire group gets paid. all members get full payment (Config.memberCompletionPercent = 100%). solo: you deliver 6 packages = 6 x delivery pay + bonus. group of 3: combined 6 packages = all 3 get (6 x delivery pay + bonus). all members get paid equally on route completion
{% endstep %}

{% step %}
**Leave group**

click "leave group" in tablet. you are removed from group. group continues without you (if other members still there). if last member leaves, group is disbanded
{% endstep %}
{% endstepper %}

***

## Levels And Perks

* level 1: access to small routes (4-5 packages)
* level 2: unlock medium routes (+10% pay)
* level 3: unlock larger routes (+20% pay)
* level 4: +30% pay bonus + access to special routes
* level 5: +40% pay + all perks + longest routes unlocked
* complete more routes and earn xp to level up

***

## Achievements

* complete 10 postal routes
* complete 50 postal routes
* deliver 100 packages total
* deliver 500 packages total
* earn $100,000
* earn $500,000
* complete perfect route (all packages delivered on time)

***

## Testing Challenges

some postal routes have challenge timers (30% chance). complete all deliveries within time limit to get bonus. bonus calculated by time remaining. challenge timer shown in tablet

***

## Testing Night Bonus

night bonus is unlocked at level 2. once you reach level 2, night bonus applies 22:00-06:00 in-game time. gives +15% bonus on top of base pay during night hours. use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete route to see bonus

***

## Testing Vehicle Damage

if you damage postal van too much, you lose part of your deposit. deposit refund based on vehicle damage percent. damaged van = reduced earnings. try completing routes with clean vs damaged van

***

## Testing All Levels And Routes

to see all postal routes and perks instantly, use `/setcivlevel gopostal 5` (testing command). this gives you level 5 status immediately. now you have access to all postal delivery routes. test level 1 vs level 5 to see difference in pay and packages per route

***

## Testing Different Route Lengths

* small routes: 4-5 packages, quick completion, basic pay
* medium routes: 5-6 packages, moderate distance, better pay
* large routes: 7-8 packages, across map, highest pay
* longer routes = more total earnings but take more time
* test all route types to understand earning differences

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
go postal job supports groups - leader spawns vehicle and accepts tasks. all group members can deliver packages independently on same route. delivery locations configured with multiple variants per level. packages are divided among group members (not physically in van, just assigned). challenge timer chance set in Config.challenge (30% default). night bonus requires level 2+ and applies 22:00-06:00 in-game time. vehicle damage tracked - deposit refund uses Config.depositDamage percent. all members get full payment on route completion (not split). group members can work in parallel on different delivery addresses. postal van types: boxville2, boxville4, msciva41, msciva7 (level-based unlock). once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/)
{% endcontent-ref %}
