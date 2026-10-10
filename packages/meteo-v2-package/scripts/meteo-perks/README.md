---
description: >-
  Meteo perks - activity based perk lines that level up as you play, shown
  right inside the inventory, designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-perks/
---

# Meteo Perks

This is a guide about testing the Meteo V2 perks script designed exclusively for the Meteo V2 package. The perks system is fully rebuilt. There are no more separate perk menus or specializations to pick - every activity on the server (pickpocketing, pawning, crafting, fishing, the gym and many more) is its own perk line that levels up while you play it, and you see all of it inside the inventory.

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

## How Perks Work

* Each script brings its own perk line. For example `meteo-pickpocket` adds the **Pickpocket** line and `meteo-pawnshop` adds the **Pawn** line
* Lines are grouped under **Outlaw**, **Hustler**, **Worker**, **Lifestyle** and **Other**
* Doing the activity gives XP on that line only. Every line levels from 1 to 10
* Each line has perks that unlock automatically when the line reaches the perk's level. Nothing to spend or pick
* There is a daily XP cap per line (1500 XP by default), so players cannot grind one line in a single day
* When you earn XP a small toast shows up with the line, the XP gained and your progress. Reaching a new level shows a level up toast

***

## Testing Perks

### Viewing Your Perks

{% stepper %}
{% step %}
Open your inventory with **TAB**
{% endstep %}

{% step %}
Use **Q** / **E** to switch the right side tabs until you reach the **Perks** tab
{% endstep %}

{% step %}
You can see every group, your total level, and each line with its level and XP bar. Open a line to see its perks, what they give and the level they unlock at
{% endstep %}
{% endstepper %}

### Testing an Unlock

{% stepper %}
{% step %}
Lets test the **Pawn** line. Its **After Hours** perk unlocks at level 7 and lets the pawnshop accept deals 24/7 instead of only during open hours
{% endstep %}

{% step %}
Use `/perks level pawn 7` on chat

{% hint style="warning" %}
Note these commands are only available on our showcase server so you can check the features quickly. Also check out [test-commands](test-commands.md) for more details.
{% endhint %}
{% endstep %}

{% step %}
Open the inventory Perks tab again and see the Pawn line is now level 7 and After Hours shows as unlocked
{% endstep %}

{% step %}
Now go to the pawnshop outside its open hours and see if it still accepts your deals
{% endstep %}
{% endstepper %}

### Testing XP and Toasts

{% stepper %}
{% step %}
Use `/perks xp pickpocket 200` to earn XP the normal way. You will see the XP toast pop up
{% endstep %}

{% step %}
Or just go and do the activity. Pickpocket some locals and watch the Pickpocket line fill up
{% endstep %}

{% step %}
Keep earning on the same line and you will hit the daily cap. After that the line stops taking XP until the next daily reset
{% endstep %}
{% endstepper %}

> Every connected script has its own line, so try a few jobs and crime activities and see them show up in the Perks tab :)

***

## Admin Tools

Admins can open the admin menu with **F9** and go to a player's profile. The **Perks** section shows every line for that character (even when they are offline), and you can set a level, give XP, reset a line, reset today's cap, max every line or reset everything.

***

## Good to Know

{% hint style="success" %}
The level curve, the daily XP limit and reset hour, the XP toast and the reward of every single perk are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

* Perks integrate with crime scripts, civilian jobs, shops, crafting, the gym, buffs, daily rewards and more
* If a script is stopped its perk line disappears with it, and comes back when the script starts again
