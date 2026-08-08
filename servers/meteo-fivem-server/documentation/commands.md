---
description: >-
  all server commands available on the meteo fivem server. sorted by resource
  with permission levels.
icon: terminal
---

# Server Commands

All registered commands across our meteo server scripts. commands are sorted by resource.

{% hint style="info" %}
Permission levels: **user** (everyone), **admin** (staff), **god** (server owners only). some user commands also check your job.
{% endhint %}

***

## meteo-manage

The admin menu - player management, bans, vehicles, items, world control, dev tools and script settings. all admin actions get logged.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `admin` | open the admin menu | admin | - |
| `admincar` | save the vehicle you're sitting in to your garage | admin | - |
| `maxmods` | apply max upgrades to your current vehicle | admin | - |
| `reloadadmin` | reload the admin menu | admin | - |

Noclip, coord copying, player blips and the rest of the dev tools are keybinds and toggles inside the menu now - **F9** opens it, **F10** is noclip and **F11** copies your coords.

***

## meteo-mdt

The records terminal for police, EMS, judges and lawyers.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `mdt` | open the MDT (**F5** by default) | user (job + on duty) | - |
| `reloadmdt` | reload the MDT | admin | - |

***

## meteo-chat

Custom chat script with 3D RP text, job chat channels, dice rolls, and announcements.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `ooc` | out of character chat | user | `message` |
| `me` | RP action - shows 3D text above your head | user | `action` |
| `do` | RP description - 3D text for environment stuff | user | `description` |
| `try` | RP attempt - random success/fail outcome | user | `action` |
| `roll` | roll a dice (default 1-6) | user | `max_number` (optional) |
| `clear` | clear your chat history | user | - |
| `chatsize` | adjust your chat font size and width | user | `setting` `value` (optional) |
| `resetchat` | reset chat size back to default | user | - |
| `announce` | send a server-wide announcement | admin | `message` |
| `police` | job chat - message all on-duty police | user (police only) | `message` |
| `ems` | job chat - message all on-duty EMS | user (EMS only) | `message` |
| `mechanic` | job chat - message all on-duty mechanics | user (mechanic only) | `message` |

Job chat commands are loaded from config - the ones above are the default channels.

***

## meteo-dispatch

Dispatch script for 911/311 calls, callsigns, panic buttons, and a dispatch panel for LEO/EMS jobs.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `911` | emergency call - notifies police and EMS | user | `message` |
| `911e` | EMS-only emergency call | user | `message` |
| `911a` | anonymous 911 call (no caller ID) | user | `message` |
| `311` | non-emergency call | user | `message` |
| `dispatch` | open the dispatch panel | user (LEO/EMS only) | - |
| `setcallsign` | assign a callsign to a player | user (boss only) | `id` `callsign` |
| `clearcallsign` | remove a player's callsign | user (boss only) | `id` |
| `10-78` | panic button - officer needs backup | user (LEO/EMS only) | - |
| `10-99` | officer down emergency alert | user (LEO/EMS only) | - |

***

## meteo-inventory

Custom inventory script with utility slots, backpacks, clothing, item quality, and weapon handling.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `giveitem` | give an item to a player | admin | `id` `item` `amount` |
| `clearinv` | clear a player's inventory | admin | `id` (optional, clears yours if empty) |
| `repairweapon` | set your weapon's durability | god | `hp` (0-100) |
| `randomitems` | fill your inventory with random items (testing) | god | - |

***

## meteo-phone

Phone script with apps for SMS, email, bank, garage, contacts, gallery, music, properties, and more.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `getphone` | give yourself a phone with a specific serial | admin | `serial` |
| `getsim` | give yourself a SIM card | admin | `number` (optional) |
| `resetphone` | wipe all data tied to a phone serial | admin | `serial` |
| `resetsim` | wipe all data tied to a SIM number | admin | `number` |
| `deletephone` | delete a phone and all its data | admin | `serial` |
| `deletesim` | delete a SIM and all its data | admin | `number` |

***

## meteo-garages

Vehicle garage and impound script with spawn point management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `impound` | impound a nearby vehicle (stores it) | user (LEO on duty) | - |
| `depot` | send a vehicle to the depot | user (LEO on duty) | - |

***

## meteo-jail

Prison script with jailing, solitary, break-out minigames, alarm system, and prison jobs.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `jail` | jail a player - opens jail menu | user (LEO on duty) | - |
| `unjail` | release a player from jail | user (LEO on duty) | - |
| `updatejail` | change a jailed player's remaining time | user (LEO on duty) | - |
| `solitary` | send a jailed player to solitary | user (LEO on duty) | - |
| `unsolitary` | remove a player from solitary | user (LEO on duty) | - |
| `updatesolitary` | update solitary time | user (LEO on duty) | - |
| `stopalarm` | stop the prison alarm | user (LEO on duty) | - |

{% hint style="warning" %}
`testalarm` and `testmeal` are showcase server only commands. check [test commands](test-commands.md) for those.
{% endhint %}

***

## meteo-medicaljob

EMS job script with injury tracking, hospital beds, and patient treatment.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `kill` | kill a player (sets HP to 0) | admin | `id` (optional, kills yourself if empty) |
| `revive` | revive a downed player | admin | `id` (optional, revives yourself if empty) |

***

## meteo-appearance

Character customization script - ped models, tattoos, clothing, outfits, and job uniforms.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `reloadskin` | reload your appearance from the database | user | - |
| `clearprops` | remove stuck props/accessories from your ped | user | - |

***

## meteo-scenes

3D text scene script - place persistent text in the world.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `scene` | place a 3D text scene in the world | admin | - |
| `deletescene` | delete a placed scene | admin | - |
| `hidescenes` | toggle scene visibility for yourself | user | - |
| `clearscenes` | remove all scenes from the server | admin | - |

***

## meteo-dealerships

Vehicle dealership script with financing, test drives, and showroom management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `dealeradmin` | open the dealership admin panel | admin | - |
| `checkfinances` | manually check for overdue finance payments | admin | - |
| `clearfinanceblacklist` | remove a player from the finance blacklist | admin | `citizenid` |

***

## meteo-crimetablet

Crime tablet script for criminals - crypto wallet, contacts, and achievements.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `addcrypto` | add crypto to a player's wallet | admin | `id` `amount` |

***

## meteo-multichar

Multi-character selection script with character screen, spawn locations, and slot management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `charslots` | manage a player's character slots | admin | `action` (add/remove/view) `identifier` `amount` |
| `logout` | go back to the character selection screen | admin | - |
| `deletechar` | permanently delete a character | god | `citizenid` |

***

## meteo-cityhallv2

City hall script for documents, job applications, and business registration.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `givedocument` | give a document to a player | user (admin or boss) | `id` `document` |

***

## meteo-reports

Player report script for submitting reports and staff management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `report` | open the report menu | user | - |

***

## meteo-boosting

Vehicle boosting script with contracts, locations, AI guards, and achievements.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `boostcdreset` | reset a player's boosting cooldown | admin | `id` |

***

## meteo-playtime

Tracks how long players have been on the server.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `playtime` | check your total playtime on the server | user | - |

***

## meteo-restaurants

Restaurant script with multi-step cooking, employees, ingredients, and orders.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `restdev` | open the restaurant dev/setup menu | admin | - |

***

## meteo-misc

Misc gameplay features - vehicle push, crouch, consumables, diving, trunk hiding and more.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `trunkadjust` | tune where a player lies inside the nearest vehicle's boot (saved and synced for everyone) | admin | - |

***

## meteo-core

The core framework. handles player data, jobs, gangs, money, permissions, and vehicle spawning.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `tp` | teleport to coordinates or a player | admin | `x y z` or player ID |
| `tpm` | teleport to your map marker | admin | - |
| `car` | spawn a vehicle by model name | admin | `model` `keepcurrent` (optional) |
| `dv` | delete the vehicle you're in, or nearby ones | admin | `radius` (optional) |
| `givemoney` | give money to a player | admin | `id` `type` `amount` |
| `setmoney` | set a player's money | admin | `id` `type` `amount` |
| `job` | check your current job info | user | - |
| `setjob` | set a player's active job and grade | admin | `id` `job` `grade` (optional) |
| `changejob` | change a player's primary job | admin | `id` `job` |
| `addjob` | add a job to a player | admin | `id` `job` `grade` (optional) |
| `removejob` | remove a job from a player | admin | `id` `job` |
| `gang` | check your current gang info | user | - |
| `setgang` | set a player's gang | admin | `id` `gang` `grade` (optional) |
| `togglepvp` | toggle PVP on/off server-wide | admin | - |
| `openserver` | open the server to all players | admin | - |
| `closeserver` | close the server (whitelist only) | admin | `reason` (optional) |
| `addpermission` | give a player a permission level | admin | `id` `permission` |
| `removepermission` | remove a player's permission level | admin | `id` `permission` |
| `optin` | toggle your admin opt-in (needed to run admin commands) | admin | - |
| `id` | shows your server ID | user | - |
| `deletechar` | delete one of your characters | user | - |
| `logout` | log out to the character selection screen | user | - |

`ooc` and `me` are disabled here - handled by [meteo-chat](scripts/meteo-chat/) instead.

***

## meteo-smallresources

Collection of small gameplay scripts - seatbelt, crouch, cruise control, tackle and the clip recorder.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `toggleseatbelt` | put your seatbelt on or take it off | user | - |
| `togglecruise` | toggle cruise control | user | - |
| `togglecrouch` | toggle crouch | user | - |
| `shuff` | shuffle to the other front seat | user | - |
| `tackle` | tackle the player in front of you | user | - |
| `point` | point with your finger | user | - |
| `record` | start recording a clip | user | - |
| `saveclip` | save the clip you just recorded | user | - |
| `clip` | play back a saved clip | user | - |
| `delclip` | delete a saved clip | user | - |

***

## meteo-vehiclekeys

Vehicle keys, locks, lockpicking and hotwiring. see the [testing guide](scripts/meteo-vehiclekeys/).

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `givekeys` | hand your vehicle keys to a nearby player. without an ID it gives to the closest person or everyone in the vehicle | user | `id` (optional) |
| `addkeys` | admin-give keys to a player | admin | `id` (optional) |
| `vehdoors` | open the vehicle door menu | user | - |

Keybinds: **L** toggles the locks, **H** searches the cabin for keys when you have none.

***

## meteo-radialmenu

Radial menu with quick-access actions.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `radialmenu` | open the radial menu | user | - |
| `seat` | move to another seat in the vehicle | user | - |
| `window` | roll a vehicle window up or down | user | - |

Getting into a vehicle boot is handled by [meteo-misc](scripts/meteo-misc/) now - target the open boot instead of using a command.

***

## Quick Permission Reference

| Level | Who can use it |
| ----- | -------------- |
| **user** | everyone (some commands check your job too) |
| **admin** | staff with admin permission |
| **god** | highest level - server owners only |
