---
description: >-
  Changelogs for the meteo fivem server. All updates, new features, fixes and
  improvements in one place.
icon: clock-rotate-left
---

# Changelogs

All updates, new features, fixes and improvements to the meteo fivem server.

{% hint style="info" %}
We push updates regularly. All updates are included with your purchase - no extra fees.
{% endhint %}

{% hint style="danger" %}
**Watch out for scammers.** The only legitimate place to purchase the meteo fivem server is [meteofivem.net/meteo-fivem-server](https://meteofivem.net/meteo-fivem-server). Scammers often copy our changelogs to make their fake versions look real. If you bought it anywhere else (random Discord servers, third-party resellers, "leaked" downloads), you did not get the real product - and you will not get updates, support, or security patches from us.
{% endhint %}

{% hint style="success" %}
**Need help with an update or have a question?** Open a ticket on our official Discord at [discord.meteofivem.net](https://discord.meteofivem.net). Our team is there to help every customer with installation, updates and any issues.
{% endhint %}

***
### 2.4.0

#### Changes

* Fixed restaurant shop items failing to purchase
* Fixed restaurant order box usage failing
* Fixed multi-slot stack handling when transferring shop items from stash
* Phone fix: hiring employees in core companies no longer fails with "player not online" caused by an undefined `targetCitizenId` variable
* Added SIM card copy support
* Added Thai `th` locale translation
* Fixed player crashes when moving items into backpacks
* Fixed scenes dui errors
* Fully rewrote the box spawn system for `bargehunt` and `foresthunt` to improve sync reliability
* Fixed furnishing objects not spawning after renaming
* smallresources improvements
* Fixed taxijob and electrician job location issues after renaming
* Chat update now registers exports under both `meteo-chat` and the default `chat`
* Admin menu spectate improvements
* Casino improvements
* Translation improvements
* Prison improvements
* Appearance ui improvements
* `crime tablet/app.lua` is now open, allowing you to translate app names if needed
* Updated Meteo rights watermark removal support with `setr meteo:acknowledge false`

* Database Changes
run this
```sql
ALTER TABLE `meteo_phone_sim_ownership`
ADD COLUMN IF NOT EXISTS `is_disabled` TINYINT(1) NOT NULL DEFAULT 0
COMMENT 'Permanent disable (1=copied to new number, cannot be reactivated)'
AFTER `is_locked`;

ALTER TABLE `meteo_phone_sim_ownership`
ADD COLUMN IF NOT EXISTS `disabled_at` DATETIME DEFAULT NULL
COMMENT 'When permanently disabled'
AFTER `locked_at`;
```

#### Modified Files

* `resources/[meteostudios]/meteo-adminmenu/client/cl_admintools.lua`
* `resources/[meteostudios]/meteo-adminmenu/client/cl_main.lua`
* `resources/[meteostudios]/meteo-adminmenu/locales/*`
* `resources/[meteostudios]/meteo-adminmenu/server/sv_admintools.lua`
* `resources/[meteostudios]/meteo-adminmenu/server/sv_functions.lua`
* `resources/[meteostudios]/meteo-adminmenu/server/sv_logs.lua`
* `resources/[meteostudios]/meteo-adminmenu/shared/config.lua`
* `resources/[meteostudios]/meteo-adminmenu/shared/debug.lua`
* `resources/[meteostudios]/meteo-adminmenu/web/*`
* `resources/[meteostudios]/meteo-animations/locales/*`
* `resources/[meteostudios]/meteo-apartments/locales/*`
* `resources/[meteostudios]/meteo-appearance/client/cl_nui.lua`
* `resources/[meteostudios]/meteo-appearance/locales/*`
* `resources/[meteostudios]/meteo-appearance/web/*`
* `resources/[meteostudios]/meteo-atmskimming/locales/*`
* `resources/[meteostudios]/meteo-banking/locales/*`
* `resources/[meteostudios]/meteo-bargehunt/client/cl_main.lua`
* `resources/[meteostudios]/meteo-bargehunt/client/cl_mission.lua`
* `resources/[meteostudios]/meteo-bargehunt/locales/*`
* `resources/[meteostudios]/meteo-bennys/locales/*`
* `resources/[meteostudios]/meteo-blackjack/client/cl_main.lua`
* `resources/[meteostudios]/meteo-blackjack/locales/*`
* `resources/[meteostudios]/meteo-blackjack/shared/config.lua`
* `resources/[meteostudios]/meteo-boombox/locales/*`
* `resources/[meteostudios]/meteo-boosting/locales/*`
* `resources/[meteostudios]/meteo-bossmenuv2/locales/*`
* `resources/[meteostudios]/meteo-buffs/locales/*`
* `resources/[meteostudios]/meteo-casinoannounce`
* `resources/[meteostudios]/meteo-chopshop`
* `resources/[meteostudios]/meteo-cityhallv2/locales/*`
* `resources/[meteostudios]/meteo-cleaningjob/locales/*`
* `resources/[meteostudios]/meteo-craftingtables/client/cl_main.lua`
* `resources/[meteostudios]/meteo-craftingtables/locales/*`
* `resources/[meteostudios]/meteo-craftingtables/shared/config.lua`
* `resources/[meteostudios]/meteo-crimetablet/locales/*`
* `resources/[meteostudios]/meteo-crimetablet/shared/apps.lua`
* `resources/[meteostudios]/meteo-dailyrewards/locales/*`
* `resources/[meteostudios]/meteo-dealerships/locales/*`
* `resources/[meteostudios]/meteo-dialogue/locales/*`
* `resources/[meteostudios]/meteo-dispatch/locales/*`
* `resources/[meteostudios]/meteo-drugs/locales/*`
* `resources/[meteostudios]/meteo-drugselling/locales/*`
* `resources/[meteostudios]/meteo-dumpstersearch/locales/*`
* `resources/[meteostudios]/meteo-electricianjob/locales/*`
* `resources/[meteostudios]/meteo-electricianjob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-evidence/locales/*`
* `resources/[meteostudios]/meteo-fingerscanner/locales/*`
* `resources/[meteostudios]/meteo-fishingjob/locales/*`
* `resources/[meteostudios]/meteo-foresthunt/client/cl_main.lua`
* `resources/[meteostudios]/meteo-foresthunt/client/cl_mission.lua`
* `resources/[meteostudios]/meteo-foresthunt/locales/*`
* `resources/[meteostudios]/meteo-fuelv2/locales/*`
* `resources/[meteostudios]/meteo-furnishing/locales/*`
* `resources/[meteostudios]/meteo-furnishing/web/*`
* `resources/[meteostudios]/meteo-garages/locales/*`
* `resources/[meteostudios]/meteo-gopostaljob/locales/*`
* `resources/[meteostudios]/meteo-gym/locales/*`
* `resources/[meteostudios]/meteo-hsd/locales/*`
* `resources/[meteostudios]/meteo-hud/config.lua`
* `resources/[meteostudios]/meteo-hud/locales/*`
* `resources/[meteostudios]/meteo-inventory/client/other.lua`
* `resources/[meteostudios]/meteo-inventory/locales/*`
* `resources/[meteostudios]/meteo-inventory/shared/throwable_props.lua`
* `resources/[meteostudios]/meteo-jail/client/cl_escape.lua`
* `resources/[meteostudios]/meteo-jail/client/cl_main.lua`
* `resources/[meteostudios]/meteo-jail/client/cl_mugshot.lua`
* `resources/[meteostudios]/meteo-jail/client/cl_zone.lua`
* `resources/[meteostudios]/meteo-jail/client/source/`
* `resources/[meteostudios]/meteo-jail/locales/*`
* `resources/[meteostudios]/meteo-jail/server/source/`
* `resources/[meteostudios]/meteo-jail/server/sv_escape.lua`
* `resources/[meteostudios]/meteo-jail/server/sv_main.lua`
* `resources/[meteostudios]/meteo-jail/shared/config.lua`
* `resources/[meteostudios]/meteo-jail/shared/config_jobs.lua`
* `resources/[meteostudios]/meteo-jail/shared/jobs.lua`
* `resources/[meteostudios]/meteo-jail/shared/traders.lua`
* `resources/[meteostudios]/meteo-jail/shared/utils.lua`
* `resources/[meteostudios]/meteo-jail/web/*`
* `resources/[meteostudios]/meteo-jobgarage/locales/*`
* `resources/[meteostudios]/meteo-jobtablet/locales/*`
* `resources/[meteostudios]/meteo-loadingscreen/locales/*`
* `resources/[meteostudios]/meteo-loosechange/locales/*`
* `resources/[meteostudios]/meteo-luckywheel/client/cl_main.lua`
* `resources/[meteostudios]/meteo-luckywheel/locales/*`
* `resources/[meteostudios]/meteo-luckywheel/shared/config.lua`
* `resources/[meteostudios]/meteo-mailboxrob/locales/*`
* `resources/[meteostudios]/meteo-mdt/locales/*`
* `resources/[meteostudios]/meteo-mechanicjob/locales/*`
* `resources/[meteostudios]/meteo-medicaljob/locales/*`
* `resources/[meteostudios]/meteo-misc`
* `resources/[meteostudios]/meteo-multichar/locales/*`
* `resources/[meteostudios]/meteo-multichar/shared/config.lua`
* `resources/[meteostudios]/meteo-organizations/locales/*`
* `resources/[meteostudios]/meteo-pawnshop/locales/*`
* `resources/[meteostudios]/meteo-perks/locales/*`
* `resources/[meteostudios]/meteo-phone/client/other/cl_locale.lua`
* `resources/[meteostudios]/meteo-phone/client/other/cl_shop.lua`
* `resources/[meteostudios]/meteo-phone/install/images/motion_sensor.png`
* `resources/[meteostudios]/meteo-phone/install/images/phone.png`
* `resources/[meteostudios]/meteo-phone/install/images/sim_card.png`
* `resources/[meteostudios]/meteo-phone/install/images/spy_camera.png`
* `resources/[meteostudios]/meteo-phone/locales/*`
* `resources/[meteostudios]/meteo-phone/server/apps/sv_companies.lua`
* `resources/[meteostudios]/meteo-phone/server/apps/sv_properties.lua`
* `resources/[meteostudios]/meteo-phone/server/apps/sv_shop.lua`
* `resources/[meteostudios]/meteo-phone/server/source/properties/`
* `resources/[meteostudios]/meteo-phone/server/source/sv_functions.lua`
* `resources/[meteostudios]/meteo-phone/server/sv_main.lua`
* `resources/[meteostudios]/meteo-phone/shared/askifruit_config.lua`
* `resources/[meteostudios]/meteo-phone/shared/config.lua`
* `resources/[meteostudios]/meteo-phone/web/*`
* `resources/[meteostudios]/meteo-pickpocket/locales/*`
* `resources/[meteostudios]/meteo-policejob/locales/*`
* `resources/[meteostudios]/meteo-policeradar/locales/*`
* `resources/[meteostudios]/meteo-properties/locales/*`
* `resources/[meteostudios]/meteo-radio/locales/*`
* `resources/[meteostudios]/meteo-remotespikes/locales/*`
* `resources/[meteostudios]/meteo-repojob/locales/*`
* `resources/[meteostudios]/meteo-reportmenuv2/locales/*`
* `resources/[meteostudios]/meteo-restaurants/locales/*`
* `resources/[meteostudios]/meteo-restaurants/server/sv_orders.lua`
* `resources/[meteostudios]/meteo-restaurants/server/sv_shop.lua`
* `resources/[meteostudios]/meteo-restaurants/server/sv_storage.lua`
* `resources/[meteostudios]/meteo-rewards/locales/*`
* `resources/[meteostudios]/meteo-roulette/client/cl_main.lua`
* `resources/[meteostudios]/meteo-roulette/locales/*`
* `resources/[meteostudios]/meteo-roulette/shared/config.lua`
* `resources/[meteostudios]/meteo-roulette/shared/utils.lua`
* `resources/[meteostudios]/meteo-scenes/dui/*`
* `resources/[meteostudios]/meteo-scenes/locales/*`
* `resources/[meteostudios]/meteo-seahunt/locales/*`
* `resources/[meteostudios]/meteo-searchvehicles/locales/*`
* `resources/[meteostudios]/meteo-shops/locales/*`
* `resources/[meteostudios]/meteo-taxijob/locales/*`
* `resources/[meteostudios]/meteo-taxijob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-transitjob/locales/*`
* `resources/[meteostudios]/meteo-transporthunt/locales/*`
* `resources/[meteostudios]/meteo-vaultjob/locales/*`
* `resources/[meteostudios]/meteo-vehiclerental/locales/*`
* `resources/[meteostudios]/meteo-weaponrepair/locales/*`
* `resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua`
* `resources/[ox]/ox_lib/web/*`
* `resources/[qb]/meteo-core/locales/*`
* `resources/[qb]/meteo-radialmenu/locales/*`
* `resources/[qb]/meteo-smallresources/client/hudcomponents.lua`
* `resources/[qb]/meteo-smallresources/client/ignore.lua`
* `resources/[qb]/meteo-smallresources/locales/*`
* `resources/[qb]/qbx_vehiclekeys/locales/*`

#### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.

> **Warning:** Please make sure to keep a backup if you are applying this to your main server, and be mindful if you made any custom changes before.

### 2.3.0

#### Changes

* server rename support. now you can change all of our meteo- names to yourname-
* added 100 million cap to /givemoney and /setmoney
* added croatian (hr) locale
* updated oxmysql and ox\_doorlock to latest
* added phone music app domain + mp3 validation
* added toggle for youtube support in boombox (fivem tos)
* fixed repair kits not being removed on use
* fixed dead players respawning at prison hospital (can exclude with excludeFromRespawn)
* fixed phone labor app custom jobs rendering after ui redesign
* changed inventory weapon.lua to open
* changed addcrypto to admin command

#### Modified Files

* `resources/*`
* `server.cfg`

#### **How to Install**

Use `/myorder` slash command on our Discord server and get the new updated link for server files. download full files and you must replace the full resources folder and server.cfg. otherwise rename won’t work. Refer to [how-to-rename-meteo-scripts.md](how-to/how-to-rename-meteo-scripts.md "mention") to rename scripts to your name :)

### 2.2.0

#### Changes

* meteo-appearance: texture now resets when drawable changes
* restaurant shops: fixed item price editing, now only shows enabled categories
* improved phone close animation
* updated clothing
* chat updates for text-based RP servers
* added GetAccountBalance export support for qb-banking
* circlepick minigame: improved difficulty and added fight ped block

#### Modified Files

* `resources/[meteostudios]/meteo-appearance/web/*`
* `resources/[meteostudios]/meteo-banking/server/sv_main.lua`
* `resources/[meteostudios]/meteo-chatv2/client/cl_3dtext.lua`
* `resources/[meteostudios]/meteo-chatv2/locales/*`
* `resources/[meteostudios]/meteo-chatv2/server/sv_commands.lua`
* `resources/[meteostudios]/meteo-chatv2/server/sv_logs.lua`
* `resources/[meteostudios]/meteo-chatv2/server/sv_main.lua`
* `resources/[meteostudios]/meteo-chatv2/shared/config.lua`
* `resources/[meteostudios]/meteo-chatv2/web/*`
* `resources/[meteostudios]/meteo-circlepick/client.lua`
* `resources/[meteostudios]/meteo-circlepick/config.lua`
* `resources/[meteostudios]/meteo-circlepick/web/*`
* `resources/[meteostudios]/meteo-dealerships/server/sv_logs.lua`
* `resources/[meteostudios]/meteo-phone/client/other/cl_anim.lua`
* `resources/[meteostudios]/meteo-restaurants/server/sv_functions.lua`
* `resources/[meteostudios]/meteo-restaurants/server/sv_owner.lua`
* `resources/[meteostudios]/meteo-restaurants/server/sv_shop.lua`
* `resources/[standalone]/meteo-server-v2/fxmanifest.lua`

### 2.1.0

#### Changes

* added Config.meditateMinStress
* added Config.meditateBlipEnabled
* added new keybind for escort
* added daily limits support for lucky spins
* added missing `meteo_fish_steelhead` inventory image
* added missing locales to core scripts
* added missing beanbagshotgun assets
* added lucky wheel email when winning the vehicle
* added lucky wheel vehicle livery when retrieving from depot
* fixed inventory clothing issue
* fixed hospital issues
  * players can now enable voice while in bed.
  * fixed bed queue
* fixed job system group blips syncing issue
* fixed dealership custom classes not showing
* fixed dumpers being looted by multiple people
* fixed garage custom vehicle disappearing issue
* fixed boosting completion issue
* fixed "GetNetworkObject: no object by ID X" spam when spawning vehicles as admin
* fixed appearance issues (eye color, makeup inconsistency, improved clothing texture buttons)
* fixed phone music app new releases not refreshing on main page
* fixed phone music app new releases horizontal scroll not working
* attempted fix fuel issue
* attempted fix random phone screen bug
* changed Config.bedResetStress (can now be enabled)
* changed core vehicles.lua for lucky wheel vehicle le7b

#### Modified Files

* `meteo-server-v2/fxmanifest.lua`
* `meteo-adminmenu/client/cl_vehicle.lua`
* `meteo-adminmenu/server/sv_functions.lua`
* `meteo-appearance/client/cl_appearance.lua`
* `meteo-appearance/client/cl_nui.lua`
* `meteo-appearance/locales/*`
* `meteo-appearance/web/*`
* `meteo-boosting/client/cl_main.lua`
* `meteo-dealerships/web/*`
* `meteo-dumpstersearch/server/sv_main.lua`
* `meteo-electricianjob/client/cl_repairs.lua`
* `meteo-fuelv2/client/cl_main.lua`
* `meteo-garages/server/sv_main.lua`
* `meteo-inventory/client/clothing.lua`
* `meteo-inventory/server/clothing.lua`
* `meteo-inventory/web/*`
* `meteo-luckywheel/client/cl_main.lua`
* `meteo-luckywheel/locales/*`
* `meteo-luckywheel/server/sv_main.lua`
* `meteo-luckywheel/shared/config.lua`
* `meteo-medicaljob/client/cl_hospital.lua`
* `meteo-medicaljob/server/sv_main.lua`
* `meteo-medicaljob/shared/config.lua`
* `meteo-misc/client/meditate.lua`
* `meteo-misc/locales/*`
* `meteo-misc/shared/config.lua`
* `meteo-phone/web/*`
* `meteo-policejob/client/cl_escort.lua`
* `meteo-policejob/shared/config.lua`
* `qb-core/locales/*`
* `qb-radialmenu/locales/*`
* `qb-smallresources/locales/*`
* `qbx_vehiclekeys/locales/*`
* `[cfx-maps]/beanbagshotgun`
* `qb-core/shared/vehicles.lua`

#### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.
