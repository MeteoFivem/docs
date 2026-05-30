---
description: >-
  Changelogs for the meteo fivem server. All updates, new features, fixes and
  improvements in one place.
icon: clock-rotate-left
---

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

{% hint style="info" %}
**Reading the Modified Files list.** Some updates show changed files as a colored diff. Here is what the symbols mean:

* `+` (green) - file was **added** in this update
* `~` - file was **modified** / changed
* `-` (red) - file was **deleted** / removed
{% endhint %}

***

### 2.5.0

#### Changes

* Apartments elevator improvements
* ATM skim target improvements
* Banking ATM locale missing fix
* Missing translations added for crimetablet, dailyrewards, gym and cityhall
* Chat distance improvements
* Circlepick minigame UI improvements
* Progressbar UI overhaul
* Improved animation handling. Emotes, hands up and police actions now cancel each other properly instead of conflicting each other
* Hands up moved to meteo-animations instead of smallresources
* Police job player search, rob player logout and disconnect handling hardened more
* Taxi job sync issues fixed
* Taxi job location fixes
* Job garages should now properly give vehicle keys
* Vehiclehandler simple error fixed
* Fixed medicaljob help up progressbar error
* Attempted fixes for vehicle spawning issues with higher player counts
* Attempted crafting UI bug fixes
* Consumable items no longer go missing on cancel. Item now refunds if progress gets canceled
* Appearance clothing image improvements
* Added clothing image disable support with `Config.showClothingImages`
* Appearance head overlays are now loaded dynamically instead of being capped at 10
* Missing appearance features added including chest and makeup colors
* Appearance now uses CDN images instead of local images
* Dealerships now use CDN images instead of local  images  
* Dealership finance disable support added per dealership
* Dealership financed vehicles improvements
* Vehicle transfer improvements with sale price support (Phone)
* New Meteo Phone finance app integration hooks added for dealerships
* Inventory bank/cash support
* Improved inventory item drop pickups
* Phone contact sharing update
* Phone music app unique play count support added
* Phone text typing animation added
* Music casting support added for speakers and vehicles
* Loading screen now uses CDN video instead of local video
* New coke_bricks making support
* server.cfg update required. Missing core ACE permission added

* Just add this to your server.cfg
```cfg
add_ace resource.meteo-core command allow # Allow meteo-core to execute commands
```

#### Modified Files

* `meteo-server/server-data/resources/[meteostudios]/meteo-customapp-finance/`
* `meteo-server/server-data/resources/[meteostudios]/meteo-speakers/`
* `meteo-server/server-data/server.cfg`
* `resources/[meteostudios]/meteo-animations/client/*`
* `resources/[meteostudios]/meteo-animations/shared/config.lua`
* `resources/[meteostudios]/meteo-apartments/client/main/cl_elevator.lua`
* `resources/[meteostudios]/meteo-apartments/server/main/sv_callbacks.lua`
* `resources/[meteostudios]/meteo-appearance/client/cl_appearance.lua`
* `resources/[meteostudios]/meteo-appearance/client/cl_nui.lua`
* `resources/[meteostudios]/meteo-appearance/shared/config.lua`
* `resources/[meteostudios]/meteo-appearance/web/*`
* `resources/[meteostudios]/meteo-atmskimming/client/cl_main.lua`
* `resources/[meteostudios]/meteo-banking/client/cl_main.lua`
* `resources/[meteostudios]/meteo-bennys/client/cl_main.lua`
* `resources/[meteostudios]/meteo-bennys/server/sv_main.lua`
* `resources/[meteostudios]/meteo-bennys/shared/pricing.lua`
* `resources/[meteostudios]/meteo-bennys/shared/utils.lua`
* `resources/[meteostudios]/meteo-boombox/client/cl_main.lua`
* `resources/[meteostudios]/meteo-boombox/locales/*`
* `resources/[meteostudios]/meteo-boombox/server/sv_main.lua`
* `resources/[meteostudios]/meteo-boombox/shared/config.lua`
* `resources/[meteostudios]/meteo-boombox/shared/rename.lua`
* `resources/[meteostudios]/meteo-boombox/shared/utils.lua`
* `resources/[meteostudios]/meteo-boombox/web/*`
* `resources/[meteostudios]/meteo-chat/server/sv_commands.lua`
* `resources/[meteostudios]/meteo-chat/shared/config.lua`
* `resources/[meteostudios]/meteo-circlepick/web/*`
* `resources/[meteostudios]/meteo-cityhallv2/client/cl_main.lua`
* `resources/[meteostudios]/meteo-cityhallv2/locales/*`
* `resources/[meteostudios]/meteo-cityhallv2/web/*`
* `resources/[meteostudios]/meteo-cleaningjob/client/cl_vehicle.lua`
* `resources/[meteostudios]/meteo-cleaningjob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-cleaningjob/server/sv_vehicle.lua`
* `resources/[meteostudios]/meteo-cleaningjob/shared/config.lua`
* `resources/[meteostudios]/meteo-craftingtables/web/*`
* `resources/[meteostudios]/meteo-crimetablet/client/cl_main.lua`
* `resources/[meteostudios]/meteo-crimetablet/locales/*`
* `resources/[meteostudios]/meteo-crimetablet/server/sv_main.lua`
* `resources/[meteostudios]/meteo-crimetablet/shared/config.lua`
* `resources/[meteostudios]/meteo-crimetablet/web/*`
* `resources/[meteostudios]/meteo-dailyrewards/client/cl_main.lua`
* `resources/[meteostudios]/meteo-dailyrewards/locales/*`
* `resources/[meteostudios]/meteo-dailyrewards/server/sv_main.lua`
* `resources/[meteostudios]/meteo-dailyrewards/web/*`
* `resources/[meteostudios]/meteo-dealerships/client/cl_main.lua`
* `resources/[meteostudios]/meteo-dealerships/client/cl_targets.lua`
* `resources/[meteostudios]/meteo-dealerships/locales/*`
* `resources/[meteostudios]/meteo-dealerships/server/sv_finance.lua`
* `resources/[meteostudios]/meteo-dealerships/server/sv_functions.lua`
* `resources/[meteostudios]/meteo-dealerships/server/sv_manage.lua`
* `resources/[meteostudios]/meteo-dealerships/server/sv_shop.lua`
* `resources/[meteostudios]/meteo-dealerships/shared/config.lua`
* `resources/[meteostudios]/meteo-dealerships/web/*`
* `resources/[meteostudios]/meteo-dispatch/web/*`
* `resources/[meteostudios]/meteo-drugs/client/cl_coca.lua`
* `resources/[meteostudios]/meteo-drugs/locales/*`
* `resources/[meteostudios]/meteo-drugs/server/sv_coca.lua`
* `resources/[meteostudios]/meteo-drugs/shared/coca.lua`
* `resources/[meteostudios]/meteo-drugselling/shared/config.lua`
* `resources/[meteostudios]/meteo-electricianjob/client/cl_vehicle.lua`
* `resources/[meteostudios]/meteo-electricianjob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-electricianjob/server/sv_vehicle.lua`
* `resources/[meteostudios]/meteo-electricianjob/shared/config.lua`
* `resources/[meteostudios]/meteo-furnishing/client/cl_targets.lua`
* `resources/[meteostudios]/meteo-furnishing/shared/config.lua`
* `resources/[meteostudios]/meteo-furnishing/shared/targets.lua`
* `resources/[meteostudios]/meteo-garages/client/cl_main.lua`
* `resources/[meteostudios]/meteo-garages/server/sv_functions.lua`
* `resources/[meteostudios]/meteo-garages/shared/config.lua`
* `resources/[meteostudios]/meteo-gopostaljob/client/cl_main.lua`
* `resources/[meteostudios]/meteo-gopostaljob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-gopostaljob/server/sv_vehicle.lua`
* `resources/[meteostudios]/meteo-gopostaljob/shared/config.lua`
* `resources/[meteostudios]/meteo-gym/client/cl_main.lua`
* `resources/[meteostudios]/meteo-gym/locales/*`
* `resources/[meteostudios]/meteo-gym/web/*`
* `resources/[meteostudios]/meteo-hsd/client/cl_main.lua`
* `resources/[meteostudios]/meteo-hsd/server/sv_main.lua`
* `resources/[meteostudios]/meteo-hud/client/cl_main.lua`
* `resources/[meteostudios]/meteo-hud/web/*`
* `resources/[meteostudios]/meteo-inventory/client/drops.lua`
* `resources/[meteostudios]/meteo-inventory/client/main.lua`
* `resources/[meteostudios]/meteo-inventory/server/main.lua`
* `resources/[meteostudios]/meteo-inventory/server/other.lua`
* `resources/[meteostudios]/meteo-inventory/server/sv_logs.lua`
* `resources/[meteostudios]/meteo-inventory/shared/config.lua`
* `resources/[meteostudios]/meteo-inventory/shared/throwable_props.lua`
* `resources/[meteostudios]/meteo-inventory/web/*`
* `resources/[meteostudios]/meteo-jobgarage/client/cl_main.lua`
* `resources/[meteostudios]/meteo-jobgarage/server/sv_main.lua`
* `resources/[meteostudios]/meteo-jobgarage/shared/config.lua`
* `resources/[meteostudios]/meteo-loadingscreen/server.lua`
* `resources/[meteostudios]/meteo-loadingscreen/web/*`
* `resources/[meteostudios]/meteo-medicaljob/client/cl_checking.lua`
* `resources/[meteostudios]/meteo-misc/client/consumables.lua`
* `resources/[meteostudios]/meteo-misc/server/consumables.lua`
* `resources/[meteostudios]/meteo-phone/client/*`
* `resources/[meteostudios]/meteo-phone/locales/*`
* `resources/[meteostudios]/meteo-phone/server/*`
* `resources/[meteostudios]/meteo-phone/shared/config.lua`
* `resources/[meteostudios]/meteo-phone/web/*`
* `resources/[meteostudios]/meteo-phone/fxmanifest.lua`
* `resources/[meteostudios]/meteo-policejob/client/cl_cuff.lua`
* `resources/[meteostudios]/meteo-policejob/client/cl_escort.lua`
* `resources/[meteostudios]/meteo-policejob/client/cl_main.lua`
* `resources/[meteostudios]/meteo-policejob/client/cl_megaphone.lua`
* `resources/[meteostudios]/meteo-policejob/client/cl_shield.lua`
* `resources/[meteostudios]/meteo-policejob/locales/*`
* `resources/[meteostudios]/meteo-policejob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-repojob/client/cl_vehicle.lua`
* `resources/[meteostudios]/meteo-repojob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-repojob/server/sv_vehicle.lua`
* `resources/[meteostudios]/meteo-repojob/shared/config.lua`
* `resources/[meteostudios]/meteo-taxijob/client/cl_main.lua`
* `resources/[meteostudios]/meteo-taxijob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-taxijob/server/sv_vehicle.lua`
* `resources/[meteostudios]/meteo-taxijob/shared/config.lua`
* `resources/[meteostudios]/meteo-taxijob/shared/job/locations.lua`
* `resources/[meteostudios]/meteo-transitjob/client/cl_main.lua`
* `resources/[meteostudios]/meteo-transitjob/server/sv_main.lua`
* `resources/[meteostudios]/meteo-transitjob/server/sv_vehicle.lua`
* `resources/[meteostudios]/meteo-transitjob/shared/config.lua`
* `resources/[meteostudios]/meteo-vehiclerental/client/cl_main.lua`
* `resources/[meteostudios]/meteo-vehiclerental/server/sv_functions.lua`
* `resources/[meteostudios]/meteo-vehiclerental/shared/config.lua`
* `resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua`
* `resources/[qb]/meteo-core/shared/items.lua`
* `resources/[qb]/meteo-core/shared/weapons.lua`
* `resources/[qb]/meteo-smallresources/client/handsup.lua`
* `resources/[qb]/meteo-smallresources/client/seatbelt.lua`
* `resources/[qb]/meteo-smallresources/config.lua`
* `resources/[standalone]/progressbar/*`
* `resources/[standalone]/vehiclehandler/client.lua`
* `resources/[standalone]/xsound`

#### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.

> **Warning:** Please make sure to keep a backup if you are applying this to your main server, and be mindful if you made any custom changes before.

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

* `resources/[meteostudios]/meteo-adminmenu`
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
* `resources/[meteostudios]/meteo-blackjack`
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
* `resources/[meteostudios]/meteo-jail`
* `resources/[meteostudios]/meteo-jobgarage/locales/*`
* `resources/[meteostudios]/meteo-jobtablet/locales/*`
* `resources/[meteostudios]/meteo-loadingscreen/locales/*`
* `resources/[meteostudios]/meteo-loosechange/locales/*`
* `resources/[meteostudios]/meteo-luckywheel`
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
* `resources/[meteostudios]/meteo-phone/client/*`
* `resources/[meteostudios]/meteo-phone/locales/*`
* `resources/[meteostudios]/meteo-phone/server/*`
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
* `resources/[meteostudios]/meteo-roulette`
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
