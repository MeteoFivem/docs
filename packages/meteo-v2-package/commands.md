---
description: >-
  all server commands available in the Meteo V2 package. sorted by resource
  with permission levels.
icon: terminal
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/commands.md
---

# Server Commands

All registered commands across the Meteo V2 package scripts. commands are sorted by resource.

{% hint style="info" %}
Permission levels: **user** (everyone), **admin** (staff), **god** (server owners only) and **console** (server console only). some user commands also check your job.
{% endhint %}

***

## meteo-manage

The admin menu - player management, bans, vehicles, items, world control, dev tools and script settings. all admin actions get logged.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `admin` | open the admin menu (**F9** by default) | admin | - |
| `admincar` | save the vehicle you're sitting in to your garage | admin | - |
| `maxmods` | apply max upgrades to your current vehicle | admin | - |
| `reloadadmin` | reload the admin menu UI if it gets stuck | admin | - |

Noclip, coord copying, player blips and the rest of the dev tools are keybinds and toggles inside the menu - **F9** opens it, **F10** is noclip and **F11** copies your coords.

***

## meteo-mdt

The records terminal for police, EMS, judges and lawyers. dispatch lives in here too - meteo-dispatch is no longer a separate script.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `mdt` | open the MDT (**F5** by default) | user (job + on duty) | - |
| `reloadmdt` | reload the MDT UI if it gets stuck, then reopen it with `/mdt` | user | - |
| `911` | emergency call - goes to police and EMS | user (needs a phone) | `message` |
| `911e` | medical emergency call - works while you're downed | user (needs a phone) | `message` |
| `911a` | anonymous 911 call (no caller ID) | user (needs a phone) | `message` |
| `311` | non-emergency call to police | user (needs a phone) | `message` |
| `panic` | panic button - officer down alert | user (dispatch access) | - |
| `10-99` | officer down alert (same as `/panic`) | user (dispatch access) | - |
| `10-78` | officer needs assistance alert | user (dispatch access) | - |
| `dispatch` | open the full-screen dispatch console (**F6** by default) | user (`dispatch_console` permission) | - |
| `testalert` | send a test dispatch alert at your position | admin | `preset` (optional, random if empty) |

The call commands are loaded from config - the ones above are the defaults. **J** responds to the alert on screen and the **arrow keys** flip through the alert queue.

***

## meteo-chat

Custom chat script with 3D RP text, job chat channels, dice rolls, and announcements.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `say` | speak in character to nearby players | user | `message` |
| `ooc` | out of character chat | user | `message` |
| `me` | RP action - shows 3D text above your head | user | `action` |
| `do` | RP description - 3D text for environment stuff | user | `description` |
| `try` | RP attempt - random success/fail outcome | user | `action` |
| `roll` | roll a dice (default 1-6) | user | `max_number` (optional) |
| `clear` | clear your chat history | user | - |
| `chatsize` | adjust your chat font size, width or height | user | `setting` (font/width/height/reset) `value` (50-150, optional) |
| `resetchat` | reset chat size back to default | user | - |
| `announce` | send a server-wide announcement | admin | `message` |
| `police` | job chat - message all on-duty police | user (police only) | `message` |
| `ems` | job chat - message all on-duty EMS | user (EMS only) | `message` |
| `mechanic` | job chat - message all on-duty mechanics | user (mechanic only) | `message` |

Job chat commands are loaded from config - the ones above are the default channels.

***

## meteo-inventory

Custom inventory script with utility slots, backpacks, clothing, item quality, and weapon handling.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `giveitem` / `additem` | give an item to a player | admin | `id` `item` `count` (optional) `type` (optional) |
| `removeitem` | remove an item from a player | admin | `id` `item` `count` (optional) `type` (optional) |
| `setitem` | set how many of an item a player has | admin | `id` `item` `count` (optional) `type` (optional) |
| `clearinv` | wipe all items from an inventory | admin | `invId` |
| `viewinv` | look inside an inventory without touching it | admin | `invId` |
| `takeinv` | confiscate a player's inventory | admin | `id` |
| `restoreinv` / `returninv` | give back a confiscated inventory | admin | `id` |
| `saveinv` | save all pending inventory changes to the database | admin | `lock` (optional) |
| `clearevidence` | clear a police evidence locker | user (police boss) | `locker` |
| `steal` | open the inventory of the nearest player | user | - |

***

## meteo-phone

Phone script with apps for SMS, email, bank, garage, contacts, gallery, music, properties, and more.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `phone` | open or close the phone (**M** by default) | user | - |
| `reloadphone` | reload the phone UI if it gets stuck, then reopen it | user | - |

Phone, SIM and data management for staff is done from the admin menu now.

***

## meteo-garages

Vehicle garage and impound script with spawn point management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `impound` | impound a nearby vehicle | user (LEO on duty) | - |
| `depot` | send a nearby vehicle to the depot | user (LEO on duty) | - |

***

## meteo-vehiclekeys

Vehicle keys, locks, lockpicking and hotwiring. see the [testing guide](scripts/meteo-vehiclekeys/).

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `givekeys` | hand your vehicle keys to a nearby player. without an ID it gives to the closest person or everyone in the vehicle | user | `id` (optional) |
| `addkeys` | admin-give keys to a player | admin | `id` (optional) |

Keybinds: **L** toggles the locks, **G** toggles the engine and **H** searches the cabin for keys when you have none.

***

## meteo-vehiclecontrols

Vehicle control panel for doors, windows, seats and the engine.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `vehcontrol` | open the vehicle control panel while in a vehicle (no default key, bind it in your settings) | user | - |

***

## meteo-dealerships

Vehicle dealership script with financing, test drives, and showroom management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `dealermanage` | open the manage menu at a dealership you own or work at | user (owner/employee) | - |
| `reloaddealerships` | reload the dealership UI if it gets stuck | user | - |
| `dealeradmin` | open the dealership admin panel | admin | - |
| `checkfinances` | manually check for overdue finance payments | admin | - |
| `clearfinanceblacklist` | remove a player from the finance blacklist | admin | `citizenid` |

***

## meteo-properties

Housing, apartments and shell interiors.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `properties` | open the property admin panel | admin | - |
| `reloadproperties` | reload the property UI if it gets stuck | user | - |
| `propstats` | show property cache stats | god | - |
| `aptsweep` | run the apartment sweep now (rent, inactivity, purge) | god | - |
| `aptexpire` | expire a room now as if the tenant went inactive. no ID uses the room you stand in or your first room | god | `id` (optional) `purge` (optional) |
| `propdev` | property test tools - assign, vacate, recover, purge, rent, age, export and import | god | `scope` (room/transfer) `action` `id` (optional) `cid` (optional) |

***

## meteo-restaurants

Restaurant script with multi-step cooking, employees, ingredients, and orders.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `restmanage` | open the manage menu while inside a restaurant you own or manage | user (owner/manager) | - |
| `restdev` | open the restaurant dev/setup menu | admin | - |

***

## meteo-jail

Prison script with jailing, solitary, break-out minigames, alarm system, and prison jobs.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `jail` | jail a player - opens jail menu | user (jail jobs) | - |
| `unjail` | release a player from jail | user (jail jobs) | - |
| `updatejail` | change a jailed player's remaining time | user (jail jobs) | - |
| `solitary` | send a jailed player to solitary | user (jail jobs) | - |
| `unsolitary` | remove a player from solitary | user (jail jobs) | - |
| `updatesolitary` | update solitary time | user (jail jobs) | - |
| `stopalarm` | stop the prison alarm | user (jail jobs) | - |

Jail jobs are set in config - police by default.

{% hint style="warning" %}
`testalarm`, `testmeal` and `setjailrep` are showcase server only commands. check [test commands](test-commands.md) for those.
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
| `removehat` | take off your hat or helmet | user | - |
| `removeglasses` | take off your glasses | user | - |
| `removemask` | take off your mask | user | - |
| `removeears` | take off your ear accessory | user | - |
| `removenecklace` | take off your necklace | user | - |
| `removeshirt` | take off your top | user | - |
| `removevest` | take off your vest | user | - |
| `removewatch` | take off your watch | user | - |
| `removebag` | take off your bag | user | - |
| `removepants` | take off your pants | user | - |
| `removeshoes` | take off your shoes | user | - |
| `removebracelet` | take off your bracelet | user | - |
| `removedecal` | remove your decal | user | - |

The clothing removal commands are loaded from config and can be renamed or turned off. with the inventory clothing system on, the piece moves into your inventory.

***

## meteo-animations

Emotes, walk styles, moods, shared emotes, pointing and hands up.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `e` / `emote` | play an emote | user | `emotename` |
| `emotecancel` | cancel your current emote (**X** by default) | user | - |
| `emotemenu` | open the emote menu (**F3** by default) | user | - |
| `walk` | set your walk style | user | `style` |
| `mood` | set your facial expression | user | `mood` |
| `nearby` | request a shared emote with the closest player | user | `emotename` |
| `pointing` | point with your finger (**B** by default) | user | - |
| `handsup` | put your hands up (**X** by default) | user | - |

***

## meteo-hud

Player HUD, vehicle cluster, cruise control and speed limiter.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `hudsettings` | open the HUD settings panel | user | - |
| `hudedit` | move, scale and hide HUD elements | user | - |
| `cinematic` | hide the HUD and show black bars | user | - |
| `reloadhud` | reload the HUD UI if it gets stuck | user | - |

Keybinds: **Y** toggles cruise control and **U** the speed limiter. settings and cinematic have no default key - bind them in your settings.

***

## meteo-buffs

Hunger, thirst, stress, buffs and cravings.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `charstatus` | show your character status - effects and cravings (no default key, bind it in your settings) | user | - |

***

## meteo-scenes

3D text scene script - place persistent text in the world.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `scene` | place a 3D text scene in the world | admin | - |
| `deletescene` | delete the scene you're looking at | admin | - |
| `sceneadmin` | open the scene admin panel | admin | - |
| `hidescenes` | toggle scene visibility for yourself | user | - |

***

## meteo-crimetablet

Crime tablet script for criminals - crypto wallet, contacts, and achievements.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `addcrypto` | add crypto to your own wallet | admin | `amount` (optional, default 10000) |

***

## meteo-boosting

Vehicle boosting script with contracts, locations, AI guards, and achievements.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `boostcdreset` | reset a player's boosting cooldown | admin | `id` |

***

## meteo-banking

Bank accounts, cards, loans and the banking API for other scripts.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `bankapi` | test the banking API - balance, add, remove, transfer, history and more. only exists when `Config.testCommands` is on, keep it off on a live server | admin | `action` `...` (run it empty for the full list) |

***

## meteo-cityhall

City hall script for documents, job applications, and business registration.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `givedocument` | give a document to a player. bosses can only give their own job's documents | user (admin or boss) | `id` `document` |

***

## meteo-multichar

Multi-character selection script with character screen, spawn locations, and slot management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `charslots` | manage a player's character slots | admin | `action` (add/remove/view) `identifier` `amount` |
| `logout` | go back to the character selection screen | admin | - |
| `deletechar` | permanently delete a character | god | `citizenid` |

***

## meteo-reports

Player report script for submitting reports and staff management.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `report` | open the report menu | user | - |

***

## meteo-playtime

Tracks how long players have been on the server.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `playtime` | check your total playtime on the server | user | - |
| `import-txadmin-playtime` | import existing playtime from txAdmin | console | - |

***

## meteo-misc

Misc gameplay features - vehicle push, crouch, consumables, diving, trunk hiding and more.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `trunkadjust` | tune where a player lies inside the nearest vehicle's boot (saved and synced for everyone) | admin | - |

Hold **middle mouse** to zoom in.

***

## meteo-policeradar

Police vehicle radar.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `radarpos` | move the radar panel on your screen (saved for you) | user | - |

***

## meteo-welcome

Welcome screen for new players.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `welcome` | open the welcome screen again | user | - |

***

## meteo-imagestudio

Captures clean vehicle, clothing and furnishing images in game.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `imagestudio` | open the image studio | admin (`use_imagestudio` permission) | `model` (optional) |

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
| `optin` | toggle your admin opt-in (needed to run some admin commands) | admin | - |
| `id` | shows your server ID | user | - |

`ooc` and `me` are handled by [meteo-chat](scripts/meteo-chat/), and `logout` and `deletechar` by meteo-multichar.

***

## meteo-smallresources

Collection of small gameplay scripts - seatbelt, tackle, pointing and the clip recorder.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `toggleseatbelt` | put your seatbelt on or take it off (**B** by default) | user | - |
| `tackle` | tackle the player in front of you while running (**Left Alt** by default) | user | - |
| `point` | point with your finger (**B** by default) | user | - |
| `record` | start recording gameplay footage | user | - |
| `clip` | start recording a short clip | user | - |
| `saveclip` | save and stop the current recording | user | - |
| `delclip` | delete the current recording | user | - |

Cruise control lives in [meteo-hud](scripts/meteo-hud/) now.

***

## meteo-radialmenu

Radial menu with quick-access actions.

| Command | What it does | Permission | Arguments |
| ------- | ------------ | ---------- | --------- |
| `radialmenu` | open the radial menu (**F1** by default) | user | - |
| `seat` | move to another seat in the vehicle | user | `seat` (number) |
| `window` | roll a vehicle window up or down | user | `window` (number) |

Getting into a vehicle boot is handled by [meteo-misc](scripts/meteo-misc/) now - target the open boot instead of using a command.

***

## Quick Permission Reference

| Level | Who can use it |
| ----- | -------------- |
| **user** | everyone (some commands check your job, duty or a script permission too) |
| **admin** | staff with admin permission |
| **god** | highest level - server owners only |
| **console** | only from the server console (txAdmin live console), not in game |

Showcase server only commands are listed on the [test commands](test-commands.md) page.
