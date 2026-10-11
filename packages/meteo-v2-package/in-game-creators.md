---
description: >-
  Set up your whole FiveM server in game with Meteo V2 in-game creators and
  script settings. Add locations, change prices and configure every script
  with no coding, no config files and no restarts.
icon: wand-magic-sparkles
---

# In-Game Creators and Settings

With the Meteo V2 package, you set up your server in game. You add new locations, change prices and configure every script from the admin menu. You don't need any coding, you don't edit config files and you don't restart scripts.

***

## The Old Way

Say you just added a new hospital map to your server. Normally you would:

1. Find the hospital script in your resources
2. Open its config file
3. Go in game and copy the coordinates for the check-in, the beds, the garage and the stash, one by one
4. Paste each one into the config and hope you didn't break the formatting
5. Restart the script, go back in game and check it
6. Repeat when something is a little off

That takes a lot of time. One missing comma breaks the whole script, and you need to know how config files work just to move a door.

***

## The Meteo Way

With Meteo V2 you do it all in game:

{% stepper %}
{% step %}
**Open the admin menu**

Press **F9** or type `/admin` and go to **Script Settings**
{% endstep %}

{% step %}
**Pick the script**

Pick Meteo Medical Job and open its creator
{% endstep %}

{% step %}
**Follow the steps**

Click **New** and the creator guides you step by step. Walk to each spot and place it right where you stand. Zones are drawn corner by corner in the world, and vehicles can be read straight from the one you are sitting in
{% endstep %}

{% step %}
**Save**

The review step shows anything you still need to fill in. Hit save and the new hospital is live for every player right away
{% endstep %}
{% endstepper %}

No restart, no config files and no coding.

***

## See It in Action

{% embed url="https://www.youtube.com/watch?v=GF35jR3R3g0" %}

{% embed url="https://www.youtube.com/watch?v=GQV6N6wErTU" %}

***

## In-Game Creators

47 Meteo scripts have their own in-game creator, including:

* **City** - garages, shops, vehicle rentals, fuel stations and chargers, banks and ATMs, clothing, barber and tattoo shops, Benny's, casino, pawn shop, furnishing, crafting tables and the gym
* **Jobs** - police stations, hospitals, mechanic shops, job garages, boss menus, evidence, the MDT, prison and every civilian job depot
* **Crime** - drugs, drug selling, hustling, house robbery, vault, sea, barge, forest and transport hunts, high speed drops, ATM skimming and the crime tablet
* **Player progression** - daily rewards, reward crates, buffs and racing

The first time a script starts, everything in its config is copied into its creator, so nothing is lost and all of it can be edited in game.

***

## Use Any Map You Want

Everything is placed in game, so the package fits any map or MLO you want. Bought a new police station or a new hospital? Open the creator, walk in and place the points. You never have to look for a script that matches your map.

***

## Script Settings

Every Meteo script puts its config in **Script Settings**. Prices, rewards, cooldowns, limits and much more can be changed from the admin menu.

* Search settings by name, or show only the ones you have changed
* Reset one setting or a whole section back to its default
* Settings that need a restart are marked, so you always know
* Your changes are saved in the database, so **they survive script updates**. Update a script and your setup stays the same

***

## Presets, Import and Export

* **Presets** - save your setup as a preset and apply it later to go back to that state
* **Export** - export the scripts, settings and creator records you want as JSON. You can export only what you changed
* **Import** - import a setup from any server running Meteo V2. You see every change before anything is saved and pick what to apply
* **Backups** - a backup is saved before every import, so you can always undo it

Share your setup with another server, or keep a backup before big changes.

***

## Safe for Your Staff

Script settings and creators are for the server owner (god) only by default. Everyone else can only view them. You can give the **Change script settings** or **Build and change creator records** permission to a staff role whenever you want.

***

{% hint style="success" %}
Try the creators and script settings yourself for free on our showcase server. [See here to get access](how-to/how-to-access-showcase-server.md). The showcase server runs in safe mode, so you can open everything, but nothing is saved.
{% endhint %}

{% content-ref url="scripts/meteo-manage/" %}
[Meteo Manage](scripts/meteo-manage/)
{% endcontent-ref %}
