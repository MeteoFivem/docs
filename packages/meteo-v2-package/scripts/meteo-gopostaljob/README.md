---
description: >-
  Meteo go postal job - group package delivery job run through the phone, with
  van loading, multi-drop routes, challenge timers, night bonus and 5 level
  progression designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-gopostaljob/
---

# Meteo Go Postal Job

This is a guide about testing the Meteo V2 go postal job script designed exclusively for the Meteo V2 package. group package delivery job that you clock in and out of through the Labor app on the phone, with package loading at the depot, packages carried in the back of your van, recipients waiting at every drop, per-delivery pay, challenge timers, night bonus, vehicle deposit damage system, crew support and 5 level progression.

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

## Testing Go Postal Job

{% stepper %}
{% step %}
**Go to the dispatcher and get a postal van**

go to the Go Postal depot (marked on the map). talk to the Go Postal Manager and pick "get me a delivery vehicle". pick a van from the list - each van needs a deposit and some are locked behind higher levels. the van spawns in one of the depot bays
{% endstep %}

{% step %}
**Clock in from the phone**

get in the driver seat of your postal van. open the phone, open the Labor app and pick the go postal job. press "clock in". you must be the driver of your own work van or the clock in is refused. once clocked in you are waiting for dispatch
{% endstep %}

{% step %}
**Accept a delivery route**

dispatch sends you a delivery route on the phone. you have a short time to answer (30 seconds by default). press "take the job" to accept or "pass" to skip it. passing adds a small wait before the next offer. once accepted, head to the package pickup zone at the depot
{% endstep %}

{% step %}
**Load the packages**

at the pickup zone use "pick up package" to grab a package, carry it to your van and use "store package" to load it. repeat until all packages for the route are loaded. the packages show in the back of the van
{% endstep %}

{% step %}
**Deliver packages**

drive to each drop marked on the map. a recipient waits at every drop. at the drop, use "take package" on your van, carry it to the recipient and use "deliver package". you get paid for that delivery right away
{% endstep %}

{% step %}
**Complete the route**

after every package is delivered you get the completion payout with a breakdown of every bonus. the payout and xp show on the phone and the route is saved in the Labor app history. a new route is offered after a short cooldown
{% endstep %}

{% step %}
**Clock out and return the van**

press "clock out" in the Labor app, or talk to the manager and pick "end my shift". once off duty, talk to the manager and pick "return my vehicle" to get your deposit back
{% endstep %}
{% endstepper %}

***

## Understanding Earnings

* each delivered package pays right away ($80-120 per package by default)
* route completion pays a base reward ($100-200 by default) plus bonuses
* bonuses on completion: job level bonus, night shift bonus, challenge bonus and perk bonus
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

only the leader gets the van, clocks in and accepts routes. members follow the same route in their own Labor app. every member must be free (not on another job and not down) for the leader to clock in or accept
{% endstep %}

{% step %}
**Split the work**

all members see the same route. members can load packages and deliver to different drops at the same time. if someone is already delivering at a drop you get "someone is already delivering here"
{% endstep %}

{% step %}
**Crew payment**

when every package is delivered, every member gets the full completion payout (not split). each delivery still pays the player who delivered it
{% endstep %}

{% step %}
**Leave the crew**

leave the crew from the Groups app. if the leader clocks out or disconnects, the route ends for the whole crew
{% endstep %}
{% endstepper %}

***

## Levels And Perks

* level 1 Package Handler
* level 2 Courier (800 xp): +5% pay, night bonus unlocked
* level 3 Professional Courier (2,000 xp): +10% pay
* level 4 Expert Courier (4,000 xp): +15% pay
* level 5 Master Courier (7,000 xp): +20% pay
* bigger vans unlock at levels 2, 3 and 4
* every route also gives civilian perk xp and labor reputation
* your level and xp progress are shown on the go postal job page in the Labor app

***

## Achievements

achievements show in the Awards tab of the Labor app. unlocked rewards are collected there for reputation

* First Route - complete your first route
* Route Runner / Experienced Driver / Master Driver / Legendary Driver - complete 25 / 75 / 150 / 250 routes
* First Delivery - deliver your first package
* Delivery Handler / Delivery Pro / Delivery Expert / Delivery Legend - deliver 50 / 250 / 500 / 1000 packages
* Night Owl / Night Shift Master - deliver 10 / 50 packages at night

***

## Rankings And History

the Labor app has a Rankings tab with leaderboards and a History tab with every route payout. open a receipt in history to see the full breakdown of that route

***

## Testing Challenges

some routes are challenge routes (35% chance by default). the offer shows the challenge bonus. deliver everything before the timer runs out to get a +15-30% challenge bonus on completion. the timer is longer for routes with a longer drive

***

## Testing Night Bonus

night bonus is unlocked at level 2. it applies 22:00-06:00 in-game time and adds +15-25% to your pay. use `/time` command to test different times (only for admins). example: `/time 12` for day, `/time 1` for night. to test: get level 2, set time to night, complete a route to see the night shift bonus in the breakdown

***

## Testing Vehicle Damage

if you return the postal van damaged, you lose part of your deposit. no damage = full refund, light damage = 85%, more damage = 60% or 30%, wrecked = no refund. try returning a clean van vs a damaged van

***

## Good to Know

{% hint style="success" %}
go postal job runs through the Labor app on the phone - no tablet needed. crews come from the Groups app and the leader runs the job. postal vans: Boxville Truck, Post OP Boxville, Go Postal NSpeedo and Go Postal Stockade (level-based unlock). all members get full payment on route completion (not split). if the leader disconnects, the route is cancelled for the whole crew.

Add or edit the depot (manager, package pickup, map marker and van bays) and the delivery rounds in-game with the **Go Postal Job** creator.

Pay, challenge and night bonuses, perk xp and reputation rewards, postal vans, deposit refund and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
