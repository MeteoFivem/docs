---
description: >-
  Meteo transit job - bus transit job run through the phone Labor app with
  multi-stop routes, passenger boarding, rush hour, level-based route unlocks
  and in-game route creator designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-transitjob/
---

# Meteo Transit Job

This is a guide about testing the Meteo V2 transit job script designed exclusively for the Meteo V2 package. Solo bus transit job run through the Labor app on the phone, with 6 bus routes, passengers that walk on and off the bus at every stop, rush hour, level-based route and bus unlocks, night bonus, timed challenge runs and a bus deposit that depends on damage.

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
* Have your [phone](../meteo-phone/) ready - the job runs through the Labor app
* Some cash on you for the bus deposit

***

## Testing Transit Job

{% stepper %}
{% step %}
**Go to the transit dispatcher**

Go to the transit dispatcher at the bus depot (bus blip on the map, or use `/tp 449.5959, -650.5834, 28.4790, 240.2101`). Talk to the Transit Dispatcher and pick "Get me a bus". Choose a bus and pay the deposit - some buses need a higher job level
{% endstep %}

{% step %}
**Clock in from the phone**

Get in the driver seat of your job bus (required). Open your phone, go to the Labor app and open the transit job. Press "Clock in". Once clocked in you will see "Waiting for dispatch"
{% endstep %}

{% step %}
**Take a route**

Dispatch sends you a route offer on the phone. Press "Take the job" to accept or "Pass" to skip it (passing a lot makes the next offer take longer). If you do not answer in time the offer expires. Once accepted, the gps routes you to the first stop
{% endstep %}

{% step %}
**Pick up passengers at stops**

Drive to each marked stop. When you arrive, waiting passengers walk to the bus and get on. From the second stop on, some passengers on board get off at each stop. Wait for the boarding to finish and the next stop is marked
{% endstep %}

{% step %}
**Complete the route**

Follow the route to the last stop. Once you reach it the route is completed and you get paid in cash with a full breakdown on the phone. The payout is saved in the History tab of the Labor app. A new route is dispatched after a short cooldown
{% endstep %}

{% step %}
**Clock out and return the bus**

Press "Clock out" in the Labor app (or pick "End my shift" at the dispatcher). Then talk to the dispatcher and pick "Return my bus" to get your deposit back
{% endstep %}
{% endstepper %}

***

## Understanding Routes

Each route has several runs with different stop sequences and a task picks one at random. Routes unlock by job level and each route only allows certain buses.

* Downtown Express - level 1
* South Los Santos Loop - level 2
* West Side Hills - level 2
* Industrial District - level 3
* Coastal Scenic - level 3
* Airport Shuttle - level 4

***

## Understanding Buses

* Standard City Bus - level 1
* Dashound Tour Bus - level 1
* Brute Tour Bus - level 2
* Airport Shuttle - level 3
* you are only offered routes your current bus is allowed on (for example the Airport Shuttle route needs the coach or the airport bus)

***

## Understanding Earnings

* each route pays a base fare plus a rate for every metre of the trip
* every passenger who gets on adds a passenger bonus and extra XP
* level pay bonus, night bonus and challenge bonus are added on top
* a damaged bus reduces the route pay
* everything is paid in cash and shown with a breakdown on the phone

***

## Rush Hour Mechanics

The number of people waiting at a stop changes with the time of day. Morning (07:00-09:00) and evening (17:00-19:00) rush hours have more passengers, late night (22:00-05:00) has fewer. More passengers = higher passenger bonus

***

## Levels And Perks

* level 1 - Trainee Driver: base pay
* level 2 - City Bus Driver: +5% pay + night bonus
* level 3 - Professional Driver: +10% pay + 25% XP bonus
* level 4 - Expert Driver: +15% pay + 40% XP bonus
* level 5 - Master Driver: +20% pay + 60% XP bonus
* complete routes and earn XP to level up - your job level and XP show in the Labor app
* every route also gives reputation and civilian perk XP

***

## Achievements And Rankings

Transit achievements show in the Awards tab of the Labor app. Collect the reward once one is unlocked. Achievements include:

* first route, 10, 50 and 100 routes completed
* a master achievement for every route
* routes with no bus damage
* timed challenge runs completed
* night routes completed
* earn $50,000 and $200,000

Check the Rankings tab of the Labor app to see where you stand against other workers.

***

## Testing Challenges

Some routes are timed challenge runs (30% chance by default). The timer is based on the trip distance. Finish the route in time to get a 15-30% bonus on top of the pay

***

## Testing Night Bonus

Night bonus applies 22:00-06:00 in-game time and requires level 2 or higher. It adds a 1.1x-1.2x multiplier on top of route pay. Use the `/time` command to test different times (only for admins)

***

## Testing Vehicle Damage

If you damage the bus, the route pays less - the more damage, the bigger the cut. When you return the bus, the deposit refund also depends on how damaged it is (full refund only for an undamaged bus). Try completing routes with a clean vs damaged bus

***

## Good to Know

{% hint style="success" %}
transit job is solo only - it can not be run as a crew. you must be in the driver seat of your own job bus to clock in. you can only be clocked in to one job at a time. passenger peds are local entities (spawn and despawn per stop).
{% endhint %}

{% hint style="info" %}
Fares, passengers, buses and deposits, which buses run each route, the challenge and night bonuses, damage penalties, deposit refund, rewards and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit the depot and the bus runs, stop by stop, in-game with the Transit Job creator.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
