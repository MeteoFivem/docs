---
description: >-
  Meteo job tablet - central hub for all civilian jobs, groups, achievements, rankings, tournaments, and task history.
---

# Meteo Job Tablet

Central hub for all civilian jobs, groups, achievements, rankings, tournaments, and task history. This tablet connects to 7 different jobs (more coming) and gives players a unified way to manage everything.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-jobtablet-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Job Tablet

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the item. Or grab it from any job location (taxi, repo, etc). Or use admin menu items section.
{% endstep %}

{% step %}
**Open and explore**

Open the tablet to see all available jobs. U will see: taxi, repo, transit, electrician, cleaning, go postal, fishing. Each job has its own section with detailed information.
{% endstep %}

{% step %}
**Test taxi job**

Open tablet and clock in to taxi job. Accept a task and follow the route on your gps. Drop off passenger at destination to complete. Earnings show in task history with base pay breakdown. Check achievements: trips completed, distance traveled, passenger count. Check your ranking against other taxi drivers.
{% endstep %}

{% step %}
**Test repo job**

Clock in to repo job. Accept a task to repossess a vehicle from an npc. Drive to location and interact with the vehicle. Tow it back to the repo lot. Earnings include base pay + bonus for condition. Check achievements: vehicles repoed, speed bonus, no damage bonus.
{% endstep %}

{% step %}
**Test transit job**

Clock in to transit job. Spawn a bus/coach at designated location. Pick up passengers at marked stops. Drop them off at destination stops. Longer routes = more earnings and distance traveled bonus. Check achievements: total passengers transported, route completion time.
{% endstep %}

{% step %}
**Test electrician job**

Need to be in a group for this job. Clock in and accept a task. Drive to location and do electrical work (skill check). Complete multiple spots on the same route. Earnings higher than solo jobs. Check achievements: boxes delivered, total earnings, perfect completion (no damage).
{% endstep %}

{% step %}
**Test cleaning job**

Group job same as electrician. Clock in and accept task. Drive to location and clean spots (simple action). Multiple locations per route. Earnings + group multiplier. Check achievements: spots cleaned, total earnings, completion time.
{% endstep %}

{% step %}
**Test go postal job**

Group job with delivery routes. Clock in and accept delivery task. Pick up packages from postal office. Deliver to multiple addresses across map. Each delivery = money, group members can divide packages. Check achievements: total packages delivered, total earnings, on-time deliveries.
{% endstep %}

{% step %}
**Test fishing job**

Doesn't require clocking in (clockIn=false). Just open tablet, select fishing job. Go to any water location and cast line. Catch fish over time (passive income). Earnings based on time fished and rarity of catches. Check achievements: total fish caught, total weight, rare catches.
{% endstep %}

{% step %}
**Test groups**

While in a job, click "create group" button. Invite other players by their citizen id (find from your phone contacts). Group leader can assign tasks to whole group. Members see shared dispatch state and timer. When leader completes task, all members get paid (with group bonus multiplier). Leave group or disband it when done.
{% endstep %}

{% step %}
**Test achievements**

Each job has unique achievements (e.g. "taxi: 100 trips", "repo: no damage repo", "electrician: 50 boxes"). Achievements track progress and give bonuses to earnings. Check the achievements tab to see all requirements. Achievements reset if you create new character.
{% endstep %}

{% step %}
**Test rankings**

Rankings tab shows leaderboard for each job. Top ranking players get higher pay multiplier on that job. Complete multiple tasks to climb the rankings. Check your current ranking and compare with other players.
{% endstep %}

{% step %}
**Test tournaments**

Open tablet and go to tournaments tab. If u have admin, click "create tournament" button. Select job, entry fee, prize pool, and duration. Tournament is now live and other players see it. Players can click "join tournament" and pay entry fee. All earnings from tasks in that job count toward tournament score. Top 3 finishers get paid from prize pool. Tournament countdown shows live time remaining.
{% endstep %}

{% step %}
**Test task history**

After completing tasks, check "task history" section. Shows breakdown of each task: base pay + bonuses. Breakdown includes: level%, night%, challenge%, perk% bonuses. Total earned = base pay + all bonuses combined. Search or filter history by job type. History saved per character and updated in real-time.
{% endstep %}

{% step %}
**Test different earnings**

Complete task with level 10 vs level 1 (shows level bonus multiplier). Complete task at night vs daytime (night bonus applies). Complete task with achievement bonus active. Complete task as group member (group multiplier applies). Complete task with perk specialization active (if perk system connected). All bonuses are multiplicative on base pay.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All job configurations, earnings, level bonuses, group settings, tournament rules, achievements, and rankings are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-taxijob/" %}
[meteo-taxijob](../meteo-taxijob/) - simple taxi driver job
{% endcontent-ref %}

{% content-ref url="../meteo-repojob/" %}
[meteo-repojob](../meteo-repojob/) - vehicle repossession job
{% endcontent-ref %}

{% content-ref url="../meteo-transitjob/" %}
[meteo-transitjob](../meteo-transitjob/) - advanced bus transit job
{% endcontent-ref %}

{% content-ref url="../meteo-electricianjob/" %}
[meteo-electricianjob](../meteo-electricianjob/) - group electrician job
{% endcontent-ref %}

{% content-ref url="../meteo-cleaningjob/" %}
[meteo-cleaningjob](../meteo-cleaningjob/) - group cleaning job
{% endcontent-ref %}

{% content-ref url="../meteo-gopostaljob/" %}
[meteo-gopostaljob](../meteo-gopostaljob/) - group postal delivery job
{% endcontent-ref %}

{% content-ref url="../meteo-fishingjob/" %}
[meteo-fishingjob](../meteo-fishingjob/) - relaxing passive fishing job
{% endcontent-ref %}
