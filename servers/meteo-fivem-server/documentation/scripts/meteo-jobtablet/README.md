---
description: >-
  Meteo job tablet - central hub for all civilian jobs, groups, achievements,
  rankings, tournaments, and task history designed exclusively for the meteo
  fivem server.
---

# Meteo Job Tablet

This is a guide about testing the meteo fivem job tablet script designed exclusively for meteo server. central hub for all civilian jobs, groups, achievements, rankings, tournaments, and task history. this tablet connects to 7 different jobs (more coming) and gives players a unified way to manage everything.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-testing-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Getting The Tablet

{% stepper %}
{% step %}
**Spawn it**

use `/giveitem id meteo_jobtablet` to spawn the item. or grab it from any job location (taxi, repo, etc). or use admin menu items section
{% endstep %}
{% endstepper %}

***

## Testing Individual Jobs - Quick Overview

for complete testing instructions for each job, check their individual guides:

* [Taxi Job](../meteo-taxijob/) - simple taxi driver job
* [Repo Job](../meteo-repojob/) - vehicle repossession job
* [Transit Job](../meteo-transitjob/) - advanced bus transit job
* [Electrician Job](../meteo-electricianjob/) - group electrician job with fuse box repairs
* [Cleaning Job](../meteo-cleaningjob/) - group cleaning job with minigame spots
* [Go Postal Job](../meteo-gopostaljob/) - group postal delivery job
* [Fishing Job](../meteo-fishingjob/) - relaxing passive fishing job

{% hint style="info" %}
each job has its own detailed testing guide with steppers. click any of the links above to see full instructions
{% endhint %}

***

## Testing Groups

{% stepper %}
{% step %}
**Create a group**

while in a job, click "create group" button. invite other players by their citizen id (find from your phone contacts)
{% endstep %}

{% step %}
**Work together**

group leader can assign tasks to whole group. members see shared dispatch state and timer. when leader completes task, all members get paid (with group bonus multiplier)
{% endstep %}

{% step %}
**Leader transfer**

when leader goes offline, leadership transfers to next member automatically. active task is cancelled and all members are reset but group stays with new leader
{% endstep %}

{% step %}
**Leave or disband**

leave group or disband it when done. vehicle return is available for ALL players in group, not just leader
{% endstep %}
{% endstepper %}

***

## Testing Achievements And Rankings

{% stepper %}
{% step %}
**Check achievements**

each job has unique achievements (e.g. "taxi: 100 trips", "repo: no damage repo", "electrician: 50 boxes"). achievements track progress and give bonuses to earnings. check the achievements tab to see all requirements. achievements reset if you create new character
{% endstep %}

{% step %}
**Check rankings**

rankings tab shows leaderboard for each job. top ranking players get higher pay multiplier on that job. complete multiple tasks to climb the rankings
{% endstep %}
{% endstepper %}

***

## Testing Tournaments

{% stepper %}
{% step %}
**Create a tournament**

open tablet and go to tournaments tab. if you have admin, click "create tournament" button. select job, entry fee, prize pool, and duration. tournament is now live and other players see it
{% endstep %}

{% step %}
**Join and compete**

players can click "join tournament" and pay entry fee. all earnings from tasks in that job count toward tournament score. must have progress > 0 to collect reward (at least 1 task completed)
{% endstep %}

{% step %}
**Rewards**

top 3 finishers get paid from prize pool. tournament countdown shows live time remaining. when time expires, rewards auto-distribute to top 3
{% endstep %}
{% endstepper %}

***

## Testing Task History

after completing tasks, check "task history" section. shows breakdown of each task: base pay + bonuses

breakdown includes: level%, night%, challenge%, perk% bonuses. total earned = base pay + all bonuses combined. search or filter history by job type. history saved per character and updated in real-time. each task shows: pay, time taken, distance, items earned

***

## Testing Different Earnings

try these different scenarios to see how bonuses stack:

* complete task with level 10 vs level 1 (shows level bonus multiplier)
* complete task at night vs daytime (night bonus applies)
* complete task with achievement bonus active
* complete task as group member (group multiplier applies)
* complete task with perk specialization active (if perk script connected)
* all bonuses are multiplicative on base pay

{% hint style="warning" %}
Check out [test-commands](test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
all 7 jobs (taxi, repo, transit, electrician, cleaning, go postal, fishing) are configured in Config.jobs with clockIn=true or false. job level requirements, base pay, bonuses, and achievement rewards are all configurable. group members see real-time elapsed time synced from server. rankings are persistent and tracked per job per character. once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-taxijob/" %}
[meteo-taxijob](../meteo-taxijob/)
{% endcontent-ref %}

{% content-ref url="../meteo-repojob/" %}
[meteo-repojob](../meteo-repojob/)
{% endcontent-ref %}

{% content-ref url="../meteo-transitjob/" %}
[meteo-transitjob](../meteo-transitjob/)
{% endcontent-ref %}

{% content-ref url="../meteo-electricianjob/" %}
[meteo-electricianjob](../meteo-electricianjob/)
{% endcontent-ref %}

{% content-ref url="../meteo-cleaningjob/" %}
[meteo-cleaningjob](../meteo-cleaningjob/)
{% endcontent-ref %}

{% content-ref url="../meteo-gopostaljob/" %}
[meteo-gopostaljob](../meteo-gopostaljob/)
{% endcontent-ref %}

{% content-ref url="../meteo-fishingjob/" %}
[meteo-fishingjob](../meteo-fishingjob/)
{% endcontent-ref %}

{% content-ref url="../meteo-cityhallv2/" %}
[meteo-cityhallv2](../meteo-cityhallv2/)
{% endcontent-ref %}

{% content-ref url="../meteo-dailyrewards/" %}
[meteo-dailyrewards](../meteo-dailyrewards/)
{% endcontent-ref %}
