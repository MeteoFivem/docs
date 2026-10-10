---
description: >-
  Meteo police job - cuffing with break minigame, ankle cuffs, escort system,
  headbag, search and seize, megaphone, shield, deployable objects, security
  cameras, in-game station creator and grade-locked armory designed exclusively
  for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-policejob/
---

# Meteo Police Job

This is a guide about testing the Meteo V2 police job script designed exclusively for the Meteo V2 package. full police job with cuff break minigame, ankle cuffs, escort system, headbag, search and seize, megaphone, ballistic shield, deployable objects, 43 security cameras, grade-locked armory and an in game creator for stations and cameras.

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
* Police job: `/setjob yourid police 4` (grade 4 gives full access to all armory items and boss features)
* Familiar with [getting started](../../getting-started.md) basics

***

## LSPD Locations

| Location                | Teleport                            | Notes                           |
| ----------------------- | ----------------------------------- | ------------------------------- |
| Duty station            | `/tp -567.1415, -129.7446, 38.4368` | toggle on duty here first       |
| Armory                  | `/tp -560.2541, -117.1234, 38.4380` | buy police supplies and weapons |
| Personal locker (stash) | `/tp -547.5211, -96.5643, 33.6112`  | store your items                |
| Security cameras        | `/tp -549.3578, -103.9652, 33.6111` | view 43 cameras around the city |
| Trash                   | `/tp -583.0117, -107.4969, 33.6112` | shared station trash            |
| Locker room (clothing)  | `/tp -545.0594, -127.1616, 38.8002` | change into police uniform      |
| Boss menu               | `/tp -558.51, -125.61, 43.89`       | requires grade 4                |
| Police garage           | `/tp -574.0596, -90.0103, 33.6111`  | get police vehicles             |
| Heli refuel             | `/tp -574.3735, -133.4248, 51.9894` | refuel helicopters, see [meteo-fuel](../meteo-fuel/) |

**Other stations:**

* **Blaine County Sheriff** - `/tp 1061.0233, 2724.7800, 38.6572` (duty, armory, stash, cameras, trash all inside)

{% hint style="info" %}
These are the stations the package ships with. Stations and cameras are now built in game, so you can add, move or remove them - see [Station and Camera Creator](#station-and-camera-creator) below.
{% endhint %}

***

## Testing Police Features

{% stepper %}
{% step %}
**Go on duty**

teleport to the duty station and toggle on duty first. open f1 menu and go to job options to see all police actions like cuff, escort, search and more
{% endstep %}

{% step %}
**Test cuffing**

get `handcuffs` from armory or spawn `/giveitem yourid handcuffs 1`. go near a player and use handcuffs on them. the player being cuffed will get a cuff break minigame - if they succeed they break free and you get knocked back. if they fail they get cuffed. to uncuff use `cuffkeys` - `/giveitem yourid cuffkeys 1`. the knock back animation can be turned off in the admin menu (Script Settings > Police) if your server does not want it
{% endstep %}

{% step %}
**Test ankle cuffs**

you can apply ankle cuffs to already cuffed players. ankle cuffs force them to walk very slowly and blocks vehicle entry completely. remove with cuff keys
{% endstep %}

{% step %}
**Test lockpick cuffs (criminal side)**

cuffed players can try to lockpick their cuffs with lockpick items:

* `lockpick` - hard difficulty
* `advancedlockpick` - medium difficulty

the better lockpick is used first. it plays a lockpick minigame from [meteo-minigames](../meteo-minigames/) and there is a chance the lockpick breaks on success or failure
{% endstep %}

{% step %}
**Test escort system**

you can escort cuffed players, dead players or regular players. escorted players are attached to you and move with you. you can put escorted players into vehicles and take them out. escorted players cant fight or use weapons
{% endstep %}

{% step %}
**Test headbag**

spawn `/giveitem yourid headbag 1` and use it on a player. it blinds them with a full screen overlay. if they try to sprint, jump or fight with headbag on they will ragdoll
{% endstep %}

{% step %}
**Test search and seize**

point target at a player and select search player to open their inventory. you can also seize their cash - it creates a moneybag item with the cash inside
{% endstep %}

{% step %}
**Test megaphone**

spawn `/giveitem yourid megaphone 1` and use it. it broadcasts your voice to 50 meters range with radio FX effects. press E to talk, X to put away
{% endstep %}

{% step %}
**Test police shield**

spawn `/giveitem yourid police_shield 1` and use it. your character holds the ballistic shield. you cant enter vehicles while shield is active, and the shield no longer shoves parked vehicles around when you walk into them. when you put it away it shows on your back (needs [meteo-weaponback](../meteo-weaponback/))
{% endstep %}

{% step %}
**Test deployable objects**

you can place these items from armory on the ground:

* `police_cone` - traffic cone
* `police_barrier` - work barrier
* `police_roadsign` - road sign
* `police_tent` - crime scene tent
* `police_light` - work light
* `police_chair` - chair
* `police_table` - table
* `police_spike` - tire spikes (max 5 per officer)

go near the placed object and pickup to remove it
{% endstep %}

{% step %}
**Test security cameras**

go to the security cameras terminal at the station. you can view 43 cameras around the city (LTD gas stations, 24/7 stores, banks, liquor stores). use controls to rotate the camera and switch between cameras
{% endstep %}
{% endstepper %}

### Station and Camera Creator

{% stepper %}
{% step %}
**Open the creator**

open the admin menu with `/admin` and go to Script Settings > Police. the Creator section lists every police station and security camera
{% endstep %}

{% step %}
**Build a station**

pick Police station, name it and aim at the front of the station for the map blip. then add its duty spots, armory points, lockers, evidence bins and camera desks wherever you want them
{% endstep %}

{% step %}
**Add a camera**

pick Security camera, aim where the camera hangs and click, then look through it and click again to save the view. you can choose if officers can turn it and if it shows as online or lost signal
{% endstep %}

{% step %}
**Tune the rest**

in the same menu you can change which jobs count as police, how hard breaking out of cuffs is, the cuff break animation, lockpicks, armory items and ranks, and what the deployable items place
{% endstep %}
{% endstepper %}

***

## Also Make Sure to Check

these are all connected with police job and have their own testing guides:

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}

{% content-ref url="../meteo-policeradar/" %}
[meteo-policeradar](../meteo-policeradar/)
{% endcontent-ref %}

{% content-ref url="../meteo-jobgarage/" %}
[meteo-jobgarage](../meteo-jobgarage/)
{% endcontent-ref %}

{% content-ref url="../meteo-jail/" %}
[meteo-jail](../meteo-jail/)
{% endcontent-ref %}

***

## Good to Know

{% hint style="success" %}
Who counts as police, cuff break difficulty and animation, lockpicks, armory items and ranks, deployable objects and the spike limit are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit police stations (duty spots, armory points, lockers, evidence bins, camera desks) and security cameras in-game with the Police creator. Script Settings is god-tier only.
{% endhint %}

* armory items are grade locked - higher grades unlock better weapons and equipment
* dispatch is now part of [meteo-mdt](../meteo-mdt/), so 911 calls and alerts are handled from the MDT
