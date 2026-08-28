---
description: >-
  Meteo Manage - admin management menu with in game script settings designed
  exclusively for the meteo fivem server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-manage/
---

# Meteo Manage

This is a guide about testing the meteo fivem admin menu script designed exclusively for meteo server.

This replaces the old admin menu. It is a full staff panel now - player management, bans, vehicles, items, world control, moderation for the phone apps, and a script settings page that lets you edit any meteo script's config in game without touching a file.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Staff access. On the showcase server you already have it
* Open the menu with **F9** or `/admin`

{% hint style="info" %}
There are two staff tiers. **Admin** covers everyday staff actions. **God** is for server owners and adds bans, staff management and script settings on top.
{% endhint %}

***

## Testing Admin Menu

### Home

* Server snapshot - current players, staff online, active bans and uptime
* Player activity graph over the last 1, 6 or 24 hours with peak and low
* Admins online and a live feed of recent staff actions

### Characters

{% stepper %}
{% step %}
Go to characters to see everyone online. Filter by staff, police, EMS or civilians
{% endstep %}

{% step %}
Click a player to open their full profile - State ID, license, phone, DOB, playtime, cash, bank, job and gang
{% endstep %}

{% step %}
Try the live actions - teleport to, bring, spectate, freeze, revive, kill, open their inventory, open their clothing menu
{% endstep %}

{% step %}
Send them a message. Tick **Important** and it shows as a fullscreen alert instead of a notification
{% endstep %}

{% step %}
Give money, give an item, set their job or set their gang
{% endstep %}
{% endstepper %}

A profile also has tabs for the other meteo systems:

| Tab | What you can do |
| --- | --------------- |
| Perks | Set level, give points, reset a specialization, reset daily limits |
| Crime Tablet | Give XP or crypto, see level and reputation |
| Jail | Jail, release, set time, put in or take out of solitary |
| Crafting | Give crafting XP |
| Vehicle Boosting | Reset the boost cooldown |
| Character Slots | Add or remove extra character slots |

### Players

* This is the account level view - one row per player license, not per character
* Search by license, name, discord or State ID
* Open an account to see discord, steam, first seen, last seen, total playtime and every character under that license

### Bans

* Active bans list with reason, who banned them, when and when it expires
* Ban an offline player by license, with durations from 1 hour up to permanent
* Revoke a ban and the player can reconnect right away
* Expired bans drop off on their own

### Vehicles

{% stepper %}
{% step %}
**Spawner** - browse the full vehicle catalog, search by name, model or brand and spawn any of them
{% endstep %}

{% step %}
**Featured** - star vehicles in the spawner to pin them to your own quick spawn list, then reorder them
{% endstep %}

{% step %}
**Player Vehicles** - search every owned vehicle by plate, model, owner or State ID. See its state (garaged, out, impound), garage and condition. Delete, give or clone one
{% endstep %}

{% step %}
While sitting in a vehicle use the vehicle options panel - fix, wash, customize, max mods, save to database, change plate or delete
{% endstep %}
{% endstepper %}

### Items

* Browse every registered item with its weight, stacking and full details
* Give an item to any online player, or spawn one straight into your own inventory
* Copy an item id for use in commands

### Weather and Time

* Set any weather from extra sunny through to blizzard, christmas and halloween
* Jump to morning, noon, evening or night, or set an exact time
* Freeze the clock so it holds at the current time
* Toggle blackout to kill every street and building light citywide

All of it broadcasts to every player through the weather sync.

### Jobs

* Every job and gang registered in the core, with member counts and the boss grade
* Copy a job id to use when assigning one from a player profile

### Announcements

* Send a server wide announcement
* Recent announcements are kept in a history list
* Bans and kicks can auto broadcast a public banner with the reason

### Script Settings

This is the big one. Every meteo script registers its config here, so you can change how a script behaves in game and the change survives a script update.

{% stepper %}
{% step %}
Go to script settings and pick a script from the list on the left
{% endstep %}

{% step %}
Search settings by name, or filter to just the ones that have been modified
{% endstep %}

{% step %}
Change a value and hit save. Settings marked **Caution** ask you to confirm, and settings marked **Restart** only take effect after the resource restarts
{% endstep %}

{% step %}
Reset a single setting or a whole section back to its shipped default
{% endstep %}

{% step %}
For location settings use **Add my position** to drop a new entry where you are standing
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Script settings is god tier only. Everyone else sees it read-only. Your changes are stored in the database, which is why they survive updates - the config file only holds the shipped defaults.
{% endhint %}

### Dev Tools

Client side tools that only affect you.

| Tool | What it does |
| ---- | ------------ |
| NoClip | Free camera flight, **F10** in game |
| God Mode | You take no damage |
| Invisible | Other players cannot see you |
| Infinite Ammo | Your equipped weapon never runs out |
| Vehicle God Mode | The vehicle you are in takes no damage |
| Revive self | Full heal and clear death state |
| Player blips | Everyone on the map with vehicle icons |
| Names overhead | Floating names above players |
| Coords display | Live x/y/z/heading overlay |
| Entity view | Raycast entity inspector - **H** copy, **G** freeze, **E** delete |

**Coordinates** - press **F11** to copy your position. Pick vec2, vec3 or vec4 and choose vector or raw format, and it copies in exactly that shape.

**Entity spawner** - type a prop model, place it with left click, scroll to rotate. Placed props are synced to everyone. The list shows every placed prop with who placed it, and you can teleport to one, remove one or clear them all.

**Pull stash** - enter a stash id like `society_police` to open it in game.

### Staff

* Shows currently online staff, their tier, status and how many actions they took this week
* Grant session admin to an online player by State ID
* Remove someone's admin access

{% hint style="warning" %}
Grants here are temporary - they last for that player's current session only and clear on restart. Permanent staff go in `permissions.cfg`.
{% endhint %}

### Audit Logs

* Every staff action is recorded
* Search by staff, target, action or details
* Filter by category - players, economy, bans, jobs, vehicles, world, settings, staff, phone - or by denied attempts
* Filter by date range

### Phone

* Look up SIM cards and phone devices by number, serial or owner
* Open a device to see its notes, emails, photos, messages and calls
* Factory reset a phone (wipes its data but keeps it registered) or delete it entirely

### Bleeter

* Review and moderate Bleeter accounts from the [meteo phone](../meteo-phone/)
* Suspend or ban an account for 1, 3, 7 or 30 days with a reason shown to the owner
* Unsuspend and unban

### Music Artists

* Review music artist applications from the phone Music app
* Approve or reject a pending application

### Search

* One search box across players, characters, vehicles, items and bans

***

## Good to Know

{% hint style="success" %}
Keybinds, staff tiers and permissions, ban durations, announcement limits, page sizes and the weather list are all configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Every action is logged, including the ones that were denied
* Sensitive fields like licenses are hidden behind a click to reveal
* `/reloadadmin` reloads the menu without restarting the resource

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-jail/" %}
[meteo-jail](../meteo-jail/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/)
{% endcontent-ref %}
