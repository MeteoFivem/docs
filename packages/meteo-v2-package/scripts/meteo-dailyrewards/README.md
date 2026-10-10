---
description: >-
  Meteo daily rewards - daily job tasks with milestone rewards and economy
  boost script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-dailyrewards/
---

# Meteo Daily Rewards

This is a guide about testing the Meteo V2 daily rewards script designed exclusively for the Meteo V2 package.

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

***

## Testing Daily Rewards

{% stepper %}
{% step %}
`/tp -1288.70, -561.74, 31.68` to the Daily Grind Board (also has a blip on the map)
{% endstep %}

{% step %}
Point the target and click on view daily rewards
{% endstep %}

{% step %}
On the menu you can see all your tasks for today. All these tasks are connected with our civilian jobs

This is also connected with our [perks](../meteo-perks/) script. The **Dailies** perk line gives a bigger economy boost target and more milestone cash
{% endstep %}

{% step %}
Toggle economy boost and get 2x or 3x payment when completing job tasks until you reach the bonus target
{% endstep %}

{% step %}
Go do one task and see if its updating the progress

There are milestones at 2, 5 and 7 tasks completed with money and item rewards
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Civilian jobs are clocked in and out from the **Labor** app on the phone. Check out [meteo-phone](../meteo-phone/) and the job guides like [meteo-taxijob](../meteo-taxijob/) to learn more.
{% endhint %}

***

## Testing the Creator

Admins can open the admin menu with **F9** and go to **Script Settings** > **Creator** > **Daily Rewards**. There are two kinds of entries:

* **Milestone** - how many tasks are needed, a cash range and the reward items
* **Job board** - where a board stands, whether it shows on the map and the target size. Add more boards around the city if you want

***

## Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server so you can quickly check things without waiting. Also check out [test-commands](test-commands.md) for full details.
{% endhint %}

* `/dailycomplete 1` - complete one task by its number
* `/dailycompleteall` - complete every task
* `/dailyreset` - reset today's progress
* `/dailyboostreset` - reset your economy boost

***

## Good to Know

{% hint style="success" %}
Milestones and job boards are editable in-game with the **Daily Rewards** creator, and the perk XP per task is editable from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

* Tasks reset daily and are randomly picked from the civilian job pools (electrician, bus, cleaning, delivery, repo, taxi and fishing)
* Want to connect your own job? Check out the [exports](exports.md)
