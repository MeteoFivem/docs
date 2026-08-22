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

## 2.11.1

### Changes

* Removed the fake "Stash" perk from Organizations
* Perk effects now apply correctly in crafting and casino scripts
* Fixed missing locale issues
* Fixed inventory swap issues when a phone SIM card is open, along with handling for characters that don't support clothing
* Police shield improvements. You can no longer use it inside vehicles or push vehicles with it. The shield now also shows on your back
* Added dynamic doors support for furnishing doors
* Improved Meteo Speakers vehicle drown detection
* Added Slovenian language support

### Modified Files

```diff
~ server.cfg > setr game_enableDynamicDoorCreation "true"

~ resources/[meteostudios]/meteo-animations/locales/*

~ resources/[meteostudios]/meteo-apartments/locales/*

~ resources/[meteostudios]/meteo-appearance/locales/*

~ resources/[meteostudios]/meteo-atmskimming/locales/*

~ resources/[meteostudios]/meteo-banking/locales/*

~ resources/[meteostudios]/meteo-bargehunt/locales/*

~ resources/[meteostudios]/meteo-bennys/locales/*

~ resources/[meteostudios]/meteo-blackjack/locales/*
~ resources/[meteostudios]/meteo-blackjack/server/sv_main.lua

~ resources/[meteostudios]/meteo-boosting/locales/*

~ resources/[meteostudios]/meteo-bossmenuv2/locales/*

~ resources/[meteostudios]/meteo-buffs/locales/*

~ resources/[meteostudios]/meteo-casinocashier/locales/*

~ resources/[meteostudios]/meteo-chat/locales/*

~ resources/[meteostudios]/meteo-chopshop/locales/*

~ resources/[meteostudios]/meteo-cityhallv2/locales/*

~ resources/[meteostudios]/meteo-cleaningjob/locales/*

~ resources/[meteostudios]/meteo-craftingtables/locales/*
~ resources/[meteostudios]/meteo-craftingtables/server/sv_main.lua
~ resources/[meteostudios]/meteo-craftingtables/server/sv_perks.lua

~ resources/[meteostudios]/meteo-crimetablet/locales/*
~ resources/[meteostudios]/meteo-crimetablet/web/*

~ resources/[meteostudios]/meteo-dailyrewards/locales/*

~ resources/[meteostudios]/meteo-dealerships/locales/*

~ resources/[meteostudios]/meteo-dialogue/locales/*

~ resources/[meteostudios]/meteo-dispatch/locales/*

~ resources/[meteostudios]/meteo-drugs/locales/*

~ resources/[meteostudios]/meteo-drugselling/locales/*

~ resources/[meteostudios]/meteo-dumpstersearch/locales/*

~ resources/[meteostudios]/meteo-electricianjob/locales/*

~ resources/[meteostudios]/meteo-evidence/locales/*

~ resources/[meteostudios]/meteo-fishingjob/locales/*

~ resources/[meteostudios]/meteo-foresthunt/locales/*

~ resources/[meteostudios]/meteo-fuelv2/locales/*

~ resources/[meteostudios]/meteo-furnishing/client/cl_cart.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_external.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_gizmo.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_main.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_nui.lua
~ resources/[meteostudios]/meteo-furnishing/fxmanifest.lua
~ resources/[meteostudios]/meteo-furnishing/locales/*
~ resources/[meteostudios]/meteo-furnishing/server/sv_main.lua
~ resources/[meteostudios]/meteo-furnishing/shared/config.lua
~ resources/[meteostudios]/meteo-furnishing/shared/utils.lua

~ resources/[meteostudios]/meteo-garages/locales/*

~ resources/[meteostudios]/meteo-gopostaljob/locales/*

~ resources/[meteostudios]/meteo-graveyarddig/locales/*

~ resources/[meteostudios]/meteo-gym/locales/*

~ resources/[meteostudios]/meteo-houserobbery/locales/*

~ resources/[meteostudios]/meteo-hsd/locales/*

~ resources/[meteostudios]/meteo-hud/locales/*

~ resources/[meteostudios]/meteo-inventory/client.lua
~ resources/[meteostudios]/meteo-inventory/init.lua
~ resources/[meteostudios]/meteo-inventory/locales/*
~ resources/[meteostudios]/meteo-inventory/modules/clothing/server.lua
~ resources/[meteostudios]/meteo-inventory/modules/inventory/server.lua
~ resources/[meteostudios]/meteo-inventory/modules/mysql/server.lua
~ resources/[meteostudios]/meteo-inventory/web/*

~ resources/[meteostudios]/meteo-jail/locales/*

~ resources/[meteostudios]/meteo-jobgarage/locales/*

~ resources/[meteostudios]/meteo-jobtablet/locales/*

~ resources/[meteostudios]/meteo-loadingscreen/locales/*

~ resources/[meteostudios]/meteo-loosechange/locales/*

~ resources/[meteostudios]/meteo-luckywheel/locales/*
~ resources/[meteostudios]/meteo-luckywheel/server/sv_main.lua
~ resources/[meteostudios]/meteo-luckywheel/server/sv_perks.lua

~ resources/[meteostudios]/meteo-mailboxrob/locales/*

~ resources/[meteostudios]/meteo-manage/locales/*

~ resources/[meteostudios]/meteo-mdt/locales/*

~ resources/[meteostudios]/meteo-mechanicjob/locales/*

~ resources/[meteostudios]/meteo-medicaljob/locales/*

~ resources/[meteostudios]/meteo-misc/fxmanifest.lua
~ resources/[meteostudios]/meteo-misc/locales/*

~ resources/[meteostudios]/meteo-multichar/locales/*

~ resources/[meteostudios]/meteo-organizations/locales/*

~ resources/[meteostudios]/meteo-pawnshop/locales/*

~ resources/[meteostudios]/meteo-perks/*

~ resources/[meteostudios]/meteo-phone/locales/*
~ resources/[meteostudios]/meteo-phone/server/apps/sv_askifruit.lua
~ resources/[meteostudios]/meteo-phone/shared/askifruit_config.lua

~ resources/[meteostudios]/meteo-pickpocket/locales/*

~ resources/[meteostudios]/meteo-policejob/client/cl_shield.lua
~ resources/[meteostudios]/meteo-policejob/locales/*
~ resources/[meteostudios]/meteo-policejob/shared/config.lua

~ resources/[meteostudios]/meteo-policeradar/locales/*

~ resources/[meteostudios]/meteo-properties/locales/*

~ resources/[meteostudios]/meteo-racing/locales/*

~ resources/[meteostudios]/meteo-radio/locales/*

~ resources/[meteostudios]/meteo-remotespikes/locales/*

~ resources/[meteostudios]/meteo-repojob/locales/*

~ resources/[meteostudios]/meteo-reports/locales/*

~ resources/[meteostudios]/meteo-restaurants/locales/*

~ resources/[meteostudios]/meteo-rewards/locales/*

+ resources/[meteostudios]/meteo-roulette/locales/*
~ resources/[meteostudios]/meteo-roulette/server/sv_main.lua
~ resources/[meteostudios]/meteo-roulette/server/sv_perks.lua

~ resources/[meteostudios]/meteo-scenes/dui/img/blood.png
+ resources/[meteostudios]/meteo-scenes/locales/*
+ resources/[meteostudios]/meteo-scenes/web/*

~ resources/[meteostudios]/meteo-seahunt/locales/*

~ resources/[meteostudios]/meteo-searchvehicles/locales/*

~ resources/[meteostudios]/meteo-shops/locales/*

+ resources/[meteostudios]/meteo-slots/locales/*
~ resources/[meteostudios]/meteo-slots/server/sv_main.lua

~ resources/[meteostudios]/meteo-speakers/client/cl_main.lua
~ resources/[meteostudios]/meteo-speakers/locales/*
~ resources/[meteostudios]/meteo-speakers/shared/config.lua

~ resources/[meteostudios]/meteo-taxijob/locales/*

~ resources/[meteostudios]/meteo-transitjob/locales/*

~ resources/[meteostudios]/meteo-transporthunt/locales/*

~ resources/[meteostudios]/meteo-vaultjob/locales/*

~ resources/[meteostudios]/meteo-vehiclekeys/fxmanifest.lua
+ resources/[meteostudios]/meteo-vehiclekeys/locales/*

~ resources/[meteostudios]/meteo-vehiclerental/locales/*

~ resources/[meteostudios]/meteo-weaponback/client/cl_main.lua
~ resources/[meteostudios]/meteo-weaponback/server/sv_main.lua
~ resources/[meteostudios]/meteo-weaponback/shared/config.lua

~ resources/[meteostudios]/meteo-weaponrepair/locales/*

+ resources/[meteostudios]/meteo-weapontints/locales/*

+ resources/[meteostudios]/meteo-whiteboard/locales/*

~ resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua

~ resources/[ox]/ox_doorlock/locales/*

~ resources/[qb]/meteo-core/locales/*

+ resources/[qb]/meteo-radialmenu/locales/*

~ resources/[qb]/meteo-smallresources/locales/*
```

***

## 2.11.0

### Changes

* New house robbery
* New graveyard digging
* New casino slot machines
* New vehicle keys script replacing the old one
* New manage menu, old admin menu removed
* Full MDT rewrite with new UI, in-game license creator, penal codes, warrants, tickets, wanted system and proper permissions
* Licenses are now handled through the MDT instead of items. Create any license you want, unlimited licenses supported
* Shops now check MDT licenses instead of license items. Revoked licenses lock the shelf and lending your card does nothing
* Guns sold in shops and taken from the PD armory are now added to the MDT weapon registry
* Police radar now reads BOLOs, wanted vehicles and stolen plates from the MDT and updates live
* Impounds and depots are logged to officer MDT activity with vehicle history
* Court, lab work, duty time, photos and audit logs are now handled through the MDT
* Evidence system rebuilt with CSI kit, station evidence lockers and new DNA swab support
* Casings, blood and prints now show properly in the world
* Prints from robberies, pickpockets, dumpsters, hunts and doors now go through the evidence system
* Blood drops when someone takes a bad hit
* Prints and swabs are sent to the MDT lab for results
* Fingerscanner script removed, MDT handles prints now
* Chopshop reworked around vehicle classes, no more model restrictions
* Premium chop contracts added
* Big furnishing script update with a cleaner menu and easier customization
* Furniture now goes into a cart while placing, purchase once you're happy with everything
* Added undo and redo while placing furniture
* Furnishing gizmo improved, moving and rotating props is much smoother
* Clone, hide and show added, with live position and rotation while placing
* Category search added for furniture
* Meteo Scenes major update with in-game creator, graffiti, image support and admin management
* Chat 3D text stacks properly, stays above the roof while driving, and size/duration can be customized
* /roll now plays a dice animation before showing the result
* Player ID and vehicle class overlay added, hold HOME to check
* Judge and lawyer are now single grade jobs, both with boss and bank access
* City Council job added for the mayor
* Job garages can now be shared between multiple jobs or gangs, with individual vehicles lockable to one group
* Job garages support multiple spawn points, using the first free one so vehicles stop stacking
* Job garage vehicles now use shared keys, any employee can drive them
* Jail now keeps sentence records including time served, time cut and time owed from breaking out
* Prison collect stash is take only, you can no longer store items in it
* Prison collect stash now handles extra items based on available inventory slots
* Pawnshop storage now only accepts pawnshop items
* Hospital check-in prompt now uses ox_lib text UI so it can be read while downed
* Downed players can no longer steer, honk, drive by or use nitrous
* Radio now keeps favourite and recent channels and cannot be used while downed
* Major Radio update with MDT multi-channel support
* Multichar now tells you when a character is already logged in somewhere else
* Extra character slots can now be set from the new manage menu
* Dealership sell-back price is now based on what the vehicle actually cost
* Dealership admin panel now opens from the manage menu
* Trunk offset adjuster now opens from the manage menu
* Perks, crime tablet, crafting and boosting now hook into the manage menu for XP, crypto and cooldowns
* Most scripts now show their settings in the new manage menu
* Weapons on back rewritten, redraws properly after death and revive
* Appearance makeup now supports secondary colors
* Added clothing removal commands like /removehat, /removeglasses, /removemask and more
* Circle pick now supports custom difficulty
* Fixed GSR issues with weapon holding
* Fixed missing head fade in appearance
* Fixed hair changes only affecting the fade
* Fixed inventory drop props not cleaning up after relog
* Fixed item stack issues
* Fixed gym stats decaying way too fast, decay also pauses while offline
* Fixed banking menu modals not closing with ESC
* Fixed restaurants invalid step issue
* Fixed medical job item usage and damage going to the wrong body part, including custom peds
* Fixed dead cuff animation
* Fixed property and apartment spawn heading when set from the creator
* Fixed Discord player count not updating
* Fixed weapons on back breaking after long loading screens
* Fixed nitrous working while downed
* Fixed a few vehicles being in the wrong vehicle class

### Images

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_10.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_09.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_07.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_06.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_03.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_02.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_01.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_05.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.11.0_04.webp)

### Modified Files

```diff
~ meteo-server/server-data/meteo.cfg

+ meteo-server/server-data/resources/[meteostudios]/meteo-graveyarddig/

+ meteo-server/server-data/resources/[meteostudios]/meteo-houserobbery/

+ meteo-server/server-data/resources/[meteostudios]/meteo-manage/

+ meteo-server/server-data/resources/[meteostudios]/meteo-slots/

+ meteo-server/server-data/resources/[meteostudios]/meteo-vehiclekeys/

- resources/[meteostudios]/meteo-adminmenu

~ resources/[meteostudios]/meteo-apartments/client/source/cl_functions.lua

~ resources/[meteostudios]/meteo-appearance/client/cl_appearance.lua
+ resources/[meteostudios]/meteo-appearance/client/cl_clothing.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_main.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_nui.lua
~ resources/[meteostudios]/meteo-appearance/fxmanifest.lua
~ resources/[meteostudios]/meteo-appearance/locales/*
~ resources/[meteostudios]/meteo-appearance/server/sv_main.lua
~ resources/[meteostudios]/meteo-appearance/shared/config.lua
~ resources/[meteostudios]/meteo-appearance/shared/constants.lua
~ resources/[meteostudios]/meteo-appearance/web/*

~ resources/[meteostudios]/meteo-atmskimming/client/cl_main.lua

~ resources/[meteostudios]/meteo-banking/web/*

~ resources/[meteostudios]/meteo-bargehunt/client/cl_main.lua

~ resources/[meteostudios]/meteo-bennys/server/sv_functions.lua
~ resources/[meteostudios]/meteo-bennys/server/sv_main.lua
~ resources/[meteostudios]/meteo-bennys/shared/config.lua
~ resources/[meteostudios]/meteo-bennys/shared/utils.lua

~ resources/[meteostudios]/meteo-boosting/client/cl_main.lua
~ resources/[meteostudios]/meteo-boosting/server/sv_main.lua

~ resources/[meteostudios]/meteo-bossmenuv2/shared/config.lua

~ resources/[meteostudios]/meteo-buffs/client/cl_status.lua

~ resources/[meteostudios]/meteo-casinoannounce/server.lua

~ resources/[meteostudios]/meteo-chat/client/cl_3dtext.lua
~ resources/[meteostudios]/meteo-chat/client/cl_main.lua
~ resources/[meteostudios]/meteo-chat/server/sv_commands.lua
~ resources/[meteostudios]/meteo-chat/shared/config.lua
~ resources/[meteostudios]/meteo-chat/web/*

~ resources/[meteostudios]/meteo-chopshop/client/cl_main.lua
~ resources/[meteostudios]/meteo-chopshop/locales/*
~ resources/[meteostudios]/meteo-chopshop/server/source/sv_functions.lua
+ resources/[meteostudios]/meteo-chopshop/server/source/sv_vehicles.lua
~ resources/[meteostudios]/meteo-chopshop/server/sv_main.lua
~ resources/[meteostudios]/meteo-chopshop/shared/config.lua
~ resources/[meteostudios]/meteo-chopshop/shared/utils.lua

~ resources/[meteostudios]/meteo-circlepick/client.lua

~ resources/[meteostudios]/meteo-cityhallv2/locales/*
~ resources/[meteostudios]/meteo-cityhallv2/server/sv_main.lua
~ resources/[meteostudios]/meteo-cityhallv2/shared/config.lua

~ resources/[meteostudios]/meteo-cleaningjob/server/sv_main.lua

~ resources/[meteostudios]/meteo-craftingtables/server/sv_main.lua

~ resources/[meteostudios]/meteo-crimetablet/server/sv_main.lua

~ resources/[meteostudios]/meteo-dealerships/client/cl_main.lua
~ resources/[meteostudios]/meteo-dealerships/locales/*
~ resources/[meteostudios]/meteo-dealerships/server/sv_admin.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_functions.lua
+ resources/[meteostudios]/meteo-dealerships/server/sv_settings.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_shop.lua
~ resources/[meteostudios]/meteo-dealerships/shared/config.lua

~ resources/[meteostudios]/meteo-drugselling/client/cl_open.lua

~ resources/[meteostudios]/meteo-dumpstersearch/client/cl_main.lua
~ resources/[meteostudios]/meteo-dumpstersearch/shared/config.lua

~ resources/[meteostudios]/meteo-electricianjob/server/sv_main.lua

+ resources/[meteostudios]/meteo-evidence/*

- resources/[meteostudios]/meteo-fingerscanner/

~ resources/[meteostudios]/meteo-fishingjob/server/sv_main.lua

~ resources/[meteostudios]/meteo-foresthunt/client/cl_main.lua

~ resources/[meteostudios]/meteo-fuelv2/fxmanifest.lua

+ resources/[meteostudios]/meteo-furnishing/client/cl_cart.lua
+ resources/[meteostudios]/meteo-furnishing/client/cl_external.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_freecam.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_functions.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_gizmo.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_main.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_nui.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_targets.lua
~ resources/[meteostudios]/meteo-furnishing/fxmanifest.lua
~ resources/[meteostudios]/meteo-furnishing/locales/*
~ resources/[meteostudios]/meteo-furnishing/server/sv_main.lua
~ resources/[meteostudios]/meteo-furnishing/shared/utils.lua
~ resources/[meteostudios]/meteo-furnishing/web/*

~ resources/[meteostudios]/meteo-garages/client/cl_main.lua
~ resources/[meteostudios]/meteo-garages/locales/*
~ resources/[meteostudios]/meteo-garages/server/sv_main.lua
~ resources/[meteostudios]/meteo-garages/shared/config.lua

~ resources/[meteostudios]/meteo-gopostaljob/server/sv_main.lua

~ resources/[meteostudios]/meteo-gym/server/sv_main.lua
~ resources/[meteostudios]/meteo-gym/shared/config.lua

~ resources/[meteostudios]/meteo-hsd/client/cl_main.lua
~ resources/[meteostudios]/meteo-hsd/shared/config.lua

~ resources/[meteostudios]/meteo-inventory/client.lua
~ resources/[meteostudios]/meteo-inventory/data/dropprops.lua
~ resources/[meteostudios]/meteo-inventory/data/items.lua
~ resources/[meteostudios]/meteo-inventory/data/rarity.lua
~ resources/[meteostudios]/meteo-inventory/locales/*
~ resources/[meteostudios]/meteo-inventory/modules/bridge/client.lua
~ resources/[meteostudios]/meteo-inventory/modules/clothing/server.lua
~ resources/[meteostudios]/meteo-inventory/modules/clothing/shared.lua
~ resources/[meteostudios]/meteo-inventory/modules/inventory/server.lua
~ resources/[meteostudios]/meteo-inventory/modules/items/client.lua
+ resources/[meteostudios]/meteo-inventory/web/*

~ resources/[meteostudios]/meteo-jail/fxmanifest.lua
~ resources/[meteostudios]/meteo-jail/locales/*
~ resources/[meteostudios]/meteo-jail/server/sv_escape.lua
~ resources/[meteostudios]/meteo-jail/server/sv_jobs.lua
~ resources/[meteostudios]/meteo-jail/server/sv_main.lua
+ resources/[meteostudios]/meteo-jail/server/sv_sentence.lua
~ resources/[meteostudios]/meteo-jail/shared/config.lua

~ resources/[meteostudios]/meteo-jobgarage/client/cl_main.lua
~ resources/[meteostudios]/meteo-jobgarage/server/sv_main.lua
~ resources/[meteostudios]/meteo-jobgarage/shared/config.lua
~ resources/[meteostudios]/meteo-jobgarage/shared/utils.lua

~ resources/[meteostudios]/meteo-jobtablet/server/sv_main.lua

~ resources/[meteostudios]/meteo-loosechange/client/cl_main.lua

~ resources/[meteostudios]/meteo-luckywheel/client/cl_main.lua
~ resources/[meteostudios]/meteo-luckywheel/fxmanifest.lua

~ resources/[meteostudios]/meteo-mailboxrob/client/cl_main.lua

~ resources/[meteostudios]/meteo-mdt/*

~ resources/[meteostudios]/meteo-mechanicjob/client/cl_nitrous.lua
~ resources/[meteostudios]/meteo-mechanicjob/locales/*
~ resources/[meteostudios]/meteo-mechanicjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-mechanicjob/shared/config.lua

~ resources/[meteostudios]/meteo-medicaljob/client/cl_checking.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_hospital.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_injuries.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_items.lua
~ resources/[meteostudios]/meteo-medicaljob/fxmanifest.lua
~ resources/[meteostudios]/meteo-medicaljob/locales/*
~ resources/[meteostudios]/meteo-medicaljob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_injuries.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_items.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_main.lua
~ resources/[meteostudios]/meteo-medicaljob/shared/config.lua
~ resources/[meteostudios]/meteo-medicaljob/shared/injuries.lua
+ resources/[meteostudios]/meteo-medicaljob/shared/items.lua
~ resources/[meteostudios]/meteo-medicaljob/shared/weapons.lua

~ resources/[meteostudios]/meteo-misc/client/consumables.lua
~ resources/[meteostudios]/meteo-misc/client/discord.lua
+ resources/[meteostudios]/meteo-misc/client/inspect.lua
~ resources/[meteostudios]/meteo-misc/client/trunk.lua
~ resources/[meteostudios]/meteo-misc/locales/*
+ resources/[meteostudios]/meteo-misc/server/inspect.lua
~ resources/[meteostudios]/meteo-misc/server/main.lua
+ resources/[meteostudios]/meteo-misc/server/sv_settings.lua
~ resources/[meteostudios]/meteo-misc/server/trunk.lua
~ resources/[meteostudios]/meteo-misc/shared/config.lua

~ resources/[meteostudios]/meteo-multichar/client/cl_main.lua
~ resources/[meteostudios]/meteo-multichar/locales/*
~ resources/[meteostudios]/meteo-multichar/server/sv_functions.lua
~ resources/[meteostudios]/meteo-multichar/server/sv_main.lua
~ resources/[meteostudios]/meteo-multichar/shared/config.lua
~ resources/[meteostudios]/meteo-multichar/web/*

~ resources/[meteostudios]/meteo-pawnshop/client/cl_main.lua
~ resources/[meteostudios]/meteo-pawnshop/locales/*
~ resources/[meteostudios]/meteo-pawnshop/server/sv_main.lua
~ resources/[meteostudios]/meteo-pawnshop/shared/config.lua

~ resources/[meteostudios]/meteo-phone/client/cl_main.lua
~ resources/[meteostudios]/meteo-phone/fxmanifest.lua
+ resources/[meteostudios]/meteo-phone/server/other/sv_manage_api.lua
~ resources/[meteostudios]/meteo-phone/server/sv_main.lua
~ resources/[meteostudios]/meteo-phone/shared/config.lua
~ resources/[meteostudios]/meteo-phone/web/*

~ resources/[meteostudios]/meteo-pickpocket/client/cl_main.lua
~ resources/[meteostudios]/meteo-pickpocket/shared/config.lua

~ resources/[meteostudios]/meteo-policejob/client/cl_cuff.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_escort.lua
~ resources/[meteostudios]/meteo-policejob/locales/*
+ resources/[meteostudios]/meteo-policejob/server/sv_armory.lua
~ resources/[meteostudios]/meteo-policejob/server/sv_main.lua
~ resources/[meteostudios]/meteo-policejob/shared/config.lua

~ resources/[meteostudios]/meteo-policeradar/server/sv_main.lua

~ resources/[meteostudios]/meteo-properties/client/cl_functions.lua
~ resources/[meteostudios]/meteo-properties/client/cl_zones.lua

~ resources/[meteostudios]/meteo-racing/fxmanifest.lua
~ resources/[meteostudios]/meteo-racing/locales/*
~ resources/[meteostudios]/meteo-racing/server/sv_main.lua

~ resources/[meteostudios]/meteo-radio/*

~ resources/[meteostudios]/meteo-repojob/server/sv_main.lua

~ resources/[meteostudios]/meteo-restaurants/client/cl_cooking.lua
~ resources/[meteostudios]/meteo-restaurants/fxmanifest.lua
~ resources/[meteostudios]/meteo-restaurants/locales/*
~ resources/[meteostudios]/meteo-restaurants/server/sv_dev.lua
+ resources/[meteostudios]/meteo-restaurants/server/sv_settings.lua
~ resources/[meteostudios]/meteo-restaurants/shared/types.lua

- resources/[meteostudios]/meteo-sceneeditor/*

+ resources/[meteostudios]/meteo-scenes/*

~ resources/[meteostudios]/meteo-seahunt/client/cl_main.lua

~ resources/[meteostudios]/meteo-searchvehicles/client/cl_main.lua
~ resources/[meteostudios]/meteo-searchvehicles/shared/config.lua

~ resources/[meteostudios]/meteo-shops/client/cl_main.lua
~ resources/[meteostudios]/meteo-shops/server/sv_main.lua
~ resources/[meteostudios]/meteo-shops/shared/config.lua

~ resources/[meteostudios]/meteo-transporthunt/client/cl_main.lua

~ resources/[meteostudios]/meteo-vaultjob/client/cl_main.lua

~ resources/[meteostudios]/meteo-weaponback/client/cl_main.lua
~ resources/[meteostudios]/meteo-weaponback/server/sv_main.lua

~ resources/[meteostudios]/meteo-weapontints/server/sv_main.lua

~ resources/[meteostudios]/meteo-whiteboard/server/sv_main.lua

~ resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua

~ resources/[qb]/meteo-core/shared/jobs.lua
~ resources/[qb]/meteo-core/shared/vehicles.lua

~ resources/[qb]/meteo-radialmenu/config.lua

~ resources/[qb]/meteo-smallresources/client/consumables.lua
~ resources/[qb]/meteo-smallresources/client/ignore.lua
~ resources/[qb]/meteo-smallresources/config.lua

- resources/[qb]/meteo-vehiclekeys/*

+ resources/[assets]/[common]/maps-vinewood-rooms
```

### Database Changes

{% hint style="danger" %}
**Run these in order.** Run step 1 first, then **start the server once** so the MDT, evidence, graveyard digging and house robbery scripts create their new tables. Only after that restart, run step 2. Running step 2 first will fail because the tables do not exist yet.
{% endhint %}

#### Step 1 - run this before you start the server

```sql
DROP TABLE IF EXISTS `meteo_mdt_announcements`;
DROP TABLE IF EXISTS `meteo_mdt_bolos`;
DROP TABLE IF EXISTS `meteo_mdt_citations`;
DROP TABLE IF EXISTS `meteo_mdt_citizen_notes`;
DROP TABLE IF EXISTS `meteo_mdt_logs`;
DROP TABLE IF EXISTS `meteo_mdt_notifications`;
DROP TABLE IF EXISTS `meteo_mdt_reports`;
DROP TABLE IF EXISTS `meteo_mdt_report_charges`;
DROP TABLE IF EXISTS `meteo_mdt_report_citizens`;
DROP TABLE IF EXISTS `meteo_mdt_report_evidence`;
DROP TABLE IF EXISTS `meteo_mdt_report_officers`;
DROP TABLE IF EXISTS `meteo_mdt_report_vehicles`;
DROP TABLE IF EXISTS `meteo_mdt_vehicle_flags`;
DROP TABLE IF EXISTS `meteo_mdt_vehicle_history`;
DROP TABLE IF EXISTS `meteo_mdt_vehicle_notes`;
DROP TABLE IF EXISTS `meteo_mdt_warrants`;
DROP TABLE IF EXISTS `meteo_evidence_fingerprints`;
DROP TABLE IF EXISTS `meteo_evidence_dna`;
```

#### Step 2 - restart the server, then run this

This loads the default MDT licenses, penal codes, ticket types and job roles, plus the default graveyard dig spots.

<details>

<summary>Default data</summary>

```sql
-- meteo-mdt default data
INSERT INTO `meteo_mdt_license_types` (`id`, `name`, `identifier`, `description`, `image`, `obtainable`, `price`, `sort_order`) VALUES
    (1, 'Driver''s License', 'LIC-DL-7K3M9', 'Legal authorization to operate motor vehicles in Los Santos. Required for driving any vehicle.', 'driver_license.png', 1, 350, 0),
    (2, 'Weapons License', 'LIC-WL-4Q8XR', 'Legal authorization to purchase and carry approved firearms in Los Santos. Requires a background check and safety course.', 'meteo_weaponlicense.png', 1, 750, 1);

INSERT INTO `meteo_mdt_penal_categories` (`name`, `color`, `sort_order`) VALUES
    ('Traffic', '#4B9BE8', 0),
    ('Public Order', '#8B97A6', 1),
    ('Theft & Property', '#E8A54B', 2),
    ('Robbery & Burglary', '#E8783C', 3),
    ('Violent Crimes', '#E84B5A', 4),
    ('Weapons', '#A664E8', 5),
    ('Narcotics', '#46C97A', 6),
    ('Fraud & Cybercrime', '#3FC7D4', 7),
    ('Vehicle Crimes', '#7A8BE8', 8),
    ('Obstruction of Justice', '#D9C24B', 9),
    ('Organized Crime', '#E84BA6', 10),
    ('Environmental & Maritime', '#6FA85C', 11),
    ('Public Corruption', '#9AA5B1', 12);

INSERT INTO `meteo_mdt_ticket_types` (`name`, `color`, `default_fine`, `max_fine`, `sort_order`) VALUES
    ('Parking Violation', '#4B9BE8', 250, 1000, 0),
    ('Moving Violation', '#E8A54B', 750, 3000, 1),
    ('Speeding', '#E8783C', 1000, 5000, 2),
    ('Equipment Violation', '#8B97A6', 350, 1500, 3),
    ('Registration & Licensing', '#7A8BE8', 500, 2500, 4),
    ('Public Nuisance', '#D9C24B', 500, 2000, 5),
    ('Littering', '#6FA85C', 750, 3000, 6),
    ('Commercial Violation', '#3FC7D4', 1500, 10000, 7),
    ('Impound Release Fee', '#A664E8', 1500, 5000, 8),
    ('Failure to Appear', '#E84B5A', 2500, 10000, 9),
    ('Court Fee', '#9AA5B1', 1000, 25000, 10),
    ('Written Warning', '#46C97A', 0, 0, 11);

INSERT INTO `meteo_mdt_penal_codes`
    (`code`, `title`, `category`, `class`, `description`, `burdens`, `modifiers`, `hidden`, `internal`)
VALUES
    -- Traffic
    ('1.01', 'Speeding (Up to 25 Over)', 'Traffic', 'Infraction', 'Operating a vehicle above the posted limit by no more than 25 mph.',
     '["The posted limit for that stretch of road", "A radar, laser or paced speed reading", "The reading was tied to this driver and vehicle"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 500, "months": 0}]', 0, 0),
    ('1.02', 'Speeding (26 to 50 Over)', 'Traffic', 'Infraction', 'Operating a vehicle between 26 and 50 mph above the posted limit.',
     '["The posted limit for that stretch of road", "A radar, laser or paced speed reading", "The reading was tied to this driver and vehicle"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1200, "months": 0}]', 0, 0),
    ('1.03', 'Excessive Speed (Over 50 Over)', 'Traffic', 'Misdemeanor', 'Operating a vehicle more than 50 mph above the posted limit.',
     '["A verified speed reading more than 50 mph over the limit", "The driver was identified at the wheel"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2500, "months": 5}]', 0, 0),
    ('1.04', 'Failure to Obey a Traffic Control Device', 'Traffic', 'Infraction', 'Ignoring a signal, stop sign or lane marking.',
     '["A working control device was in place", "The driver passed it without complying"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 400, "months": 0}]', 0, 0),
    ('1.05', 'Illegal U-Turn', 'Traffic', 'Infraction', 'Turning against a posted restriction or across a solid divider.',
     '["The turn was posted as prohibited or crossed a solid divider"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 300, "months": 0}]', 0, 0),
    ('1.06', 'Failure to Yield', 'Traffic', 'Infraction', 'Not giving way where another road user had right of way.',
     '["Another road user held the right of way", "The driver proceeded anyway"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 450, "months": 0}]', 0, 0),
    ('1.07', 'Unsafe Lane Change', 'Traffic', 'Infraction', 'Changing lanes without signalling or without clear space.',
     '["The lane change was made without signal or clear space", "It forced another road user to react"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 400, "months": 0}]', 0, 0),
    ('1.08', 'Driving Against Traffic', 'Traffic', 'Misdemeanor', 'Travelling the wrong way on a marked carriageway.',
     '["The carriageway was one way or divided", "The driver travelled against the marked flow"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 900, "months": 0}]', 0, 0),
    ('1.09', 'Illegal Parking', 'Traffic', 'Infraction', 'Leaving a vehicle in a restricted, blocking or reserved space.',
     '["The space was posted, reserved or obstructive", "The vehicle was left unattended there"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 250, "months": 0}]', 0, 0),
    ('1.10', 'Driving Without a Valid License', 'Traffic', 'Misdemeanor', 'Operating a motor vehicle with no license on record for that class.',
     '["No valid license of the required class on record", "The person was operating the vehicle"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1500, "months": 5}]', 0, 0),
    ('1.11', 'Driving With a Suspended License', 'Traffic', 'Misdemeanor', 'Operating a motor vehicle while the license is suspended or revoked.',
     '["A live suspension or revocation on record", "The person was operating the vehicle", "The person was on notice of the suspension"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 10}]', 0, 0),
    ('1.12', 'Unregistered or Unplated Vehicle', 'Traffic', 'Infraction', 'Operating a vehicle with no registration or with plates removed.',
     '["The vehicle has no registration on record, or no plate fitted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 750, "months": 0}]', 0, 0),
    ('1.13', 'Faulty Equipment', 'Traffic', 'Infraction', 'Operating a vehicle with broken lights, mirrors or other required equipment.',
     '["Required equipment was missing or not working"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 300, "months": 0}]', 0, 0),
    ('1.14', 'Illegal Window Tint', 'Traffic', 'Infraction', 'Window tint darker than the legal limit.',
     '["The tint level exceeds the legal limit"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 350, "months": 0}]', 0, 0),
    ('1.15', 'Failure to Wear a Seatbelt', 'Traffic', 'Infraction', 'Driver or passenger unrestrained in a moving vehicle.',
     '["The vehicle was in motion", "The occupant was unrestrained"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 250, "months": 0}]', 0, 0),
    ('1.16', 'Failure to Wear a Helmet', 'Traffic', 'Infraction', 'Riding a motorcycle or quad without a helmet.',
     '["The vehicle requires a helmet", "The rider was not wearing one"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 250, "months": 0}]', 0, 0),
    ('1.17', 'Distracted Driving', 'Traffic', 'Infraction', 'Using a phone or other device while driving.',
     '["The vehicle was in motion", "The driver was using a handheld device"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 500, "months": 0}]', 0, 0),
    ('1.18', 'Reckless Driving', 'Traffic', 'Misdemeanor', 'Driving with wilful disregard for the safety of others.',
     '["The manner of driving created a real risk to others", "The driver was aware of that risk and continued"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3500, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1750, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1750, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1750, "months": 5}]', 0, 0),
    ('1.19', 'Street Racing', 'Traffic', 'Misdemeanor', 'Competing for speed on a public road.',
     '["Two or more vehicles competing for speed or distance", "The contest took place on a public road"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('1.20', 'Organizing a Street Race', 'Traffic', 'Felony', 'Arranging, promoting or marshalling an illegal road race.',
     '["The person set up, promoted or marshalled the event", "The race was held or was about to be held on a public road"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 12000, "months": 25}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 6000, "months": 12}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 6000, "months": 12}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 6000, "months": 12}]', 0, 0),
    ('1.21', 'Driving Under the Influence', 'Traffic', 'Misdemeanor', 'Operating a vehicle while impaired by alcohol or narcotics.',
     '["The person was operating the vehicle", "Impairment shown by field test, breath test or observation"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 6000, "months": 20}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 3000, "months": 10}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 3000, "months": 10}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 3000, "months": 10}]', 0, 0),
    ('1.22', 'Hit and Run (Property)', 'Traffic', 'Misdemeanor', 'Leaving the scene of a collision that damaged property.',
     '["A collision caused damage to property", "The driver left without exchanging details or reporting it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 4000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2000, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2000, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2000, "months": 8}]', 0, 0),
    ('1.23', 'Hit and Run (Injury)', 'Traffic', 'Felony', 'Leaving the scene of a collision that injured a person.',
     '["A collision caused injury to a person", "The driver left without stopping or rendering aid"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 18}]', 0, 0),

    -- Public Order
    ('2.01', 'Disorderly Conduct', 'Public Order', 'Misdemeanor', 'Fighting, threatening or offensive behaviour in a public place.',
     '["The conduct took place in public or in view of the public", "It alarmed, threatened or disturbed others"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1000, "months": 5}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 500, "months": 2}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 500, "months": 2}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 500, "months": 2}]', 0, 0),
    ('2.02', 'Public Intoxication', 'Public Order', 'Infraction', 'Being drunk in public to the point of being a danger or a nuisance.',
     '["The person was intoxicated in a public place", "They were unable to care for themselves or were a nuisance"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 600, "months": 0}]', 0, 0),
    ('2.03', 'Disturbing the Peace', 'Public Order', 'Infraction', 'Excessive noise or commotion that disturbs others.',
     '["Noise or commotion beyond what is reasonable", "Others were actually disturbed by it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 500, "months": 0}]', 0, 0),
    ('2.04', 'Trespassing', 'Public Order', 'Misdemeanor', 'Entering or staying on property after being told to leave.',
     '["The property was private or posted", "The person entered or stayed without permission"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1200, "months": 5}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 600, "months": 2}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 600, "months": 2}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 600, "months": 2}]', 0, 0),
    ('2.05', 'Criminal Trespass (Secured Property)', 'Public Order', 'Misdemeanor', 'Entering fenced, locked or restricted property.',
     '["The property was fenced, locked or clearly restricted", "The person defeated or bypassed that barrier"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 5}]', 0, 0),
    ('2.06', 'Loitering', 'Public Order', 'Infraction', 'Remaining in a place with no lawful purpose after being moved on.',
     '["The person had no lawful reason to remain", "They stayed after being asked to move on"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 300, "months": 0}]', 0, 0),
    ('2.07', 'Littering', 'Public Order', 'Infraction', 'Discarding refuse outside a bin or designated site.',
     '["The person discarded refuse in a public place"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 750, "months": 0}]', 0, 0),
    ('2.08', 'Unlawful Refuse Scavenging', 'Public Order', 'Infraction', 'Rifling through bins or dumpsters on private or commercial property.',
     '["The container sits on private or commercial property", "The person searched it without permission"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 400, "months": 0}]', 0, 0),
    ('2.09', 'Public Indecency', 'Public Order', 'Misdemeanor', 'Exposure or lewd conduct in view of the public.',
     '["The conduct was in view of the public", "It would offend a reasonable person"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1500, "months": 5}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 750, "months": 2}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 750, "months": 2}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 750, "months": 2}]', 0, 0),
    ('2.10', 'Harassment', 'Public Order', 'Misdemeanor', 'A course of conduct that alarms or torments another person.',
     '["A repeated course of conduct directed at one person", "It served no legitimate purpose", "It caused real alarm or distress"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2000, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1000, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1000, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1000, "months": 5}]', 0, 0),
    ('2.11', 'Stalking', 'Public Order', 'Felony', 'Repeatedly following or watching a person so as to place them in fear.',
     '["A repeated pattern of following, watching or contacting", "The victim was placed in reasonable fear"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 8000, "months": 25}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 4000, "months": 12}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 4000, "months": 12}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 4000, "months": 12}]', 0, 0),
    ('2.12', 'Unlawful Assembly', 'Public Order', 'Misdemeanor', 'Refusing to disperse from a gathering ordered to break up.',
     '["A lawful dispersal order was given", "The person remained after the order"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2500, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1250, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1250, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1250, "months": 5}]', 0, 0),
    ('2.13', 'Rioting', 'Public Order', 'Felony', 'Taking part in a violent public disturbance.',
     '["A group acted together with violence or destruction", "This person took an active part"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 18}]', 0, 0),
    ('2.14', 'Inciting a Riot', 'Public Order', 'Felony', 'Urging or organizing others into a violent disturbance.',
     '["The person urged or organized others to act", "The urging was likely to produce imminent violence"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('2.15', 'Animal Cruelty', 'Public Order', 'Felony', 'Deliberately injuring, neglecting or killing an animal.',
     '["The animal was injured, neglected or killed", "The act was deliberate or grossly negligent"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 7500, "months": 20}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 3750, "months": 10}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 3750, "months": 10}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 3750, "months": 10}]', 0, 0),
    ('2.16', 'Desecration of Human Remains', 'Public Order', 'Felony', 'Disturbing, damaging or removing human remains.',
     '["The remains were disturbed, damaged or moved", "There was no lawful authority to do so"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 22}]', 0, 0),
    ('2.17', 'Grave Robbing', 'Public Order', 'Felony', 'Opening a grave or crypt to take property from it.',
     '["A grave, crypt or plot was opened or broken into", "Property or remains were taken or intended to be taken"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 25}]', 0, 0),

    -- Theft & Property
    ('3.01', 'Petty Theft', 'Theft & Property', 'Misdemeanor', 'Taking property worth less than $1,000.',
     '["The property belonged to someone else", "It was taken without consent", "The value is under $1,000"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1500, "months": 5}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 750, "months": 2}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 750, "months": 2}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 750, "months": 2}]', 0, 0),
    ('3.02', 'Grand Theft', 'Theft & Property', 'Felony', 'Taking property worth $1,000 to $10,000.',
     '["The property belonged to someone else", "It was taken without consent", "The value falls between $1,000 and $10,000"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 8000, "months": 20}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 4000, "months": 10}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 4000, "months": 10}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 4000, "months": 10}]', 0, 0),
    ('3.03', 'Grand Theft (Aggravated)', 'Theft & Property', 'Felony', 'Taking property worth more than $10,000.',
     '["The property belonged to someone else", "It was taken without consent", "The value exceeds $10,000"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('3.04', 'Pickpocketing', 'Theft & Property', 'Misdemeanor', 'Taking property directly from the person of another without their knowledge.',
     '["The property was taken from the victim or their clothing", "The victim did not consent and did not notice at the time"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2500, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1250, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1250, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1250, "months": 5}]', 0, 0),
    ('3.05', 'Theft from a Motor Vehicle', 'Theft & Property', 'Misdemeanor', 'Taking property out of a vehicle that is not yours.',
     '["The vehicle belonged to someone else", "Property was removed from inside it", "There was no permission to be in the vehicle"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 12}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 6}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 6}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 6}]', 0, 0),
    ('3.06', 'Tampering with a Motor Vehicle', 'Theft & Property', 'Misdemeanor', 'Opening, entering or interfering with a vehicle that is not yours.',
     '["The vehicle belonged to someone else", "The person opened, entered or interfered with it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2000, "months": 8}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1000, "months": 4}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1000, "months": 4}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1000, "months": 4}]', 0, 0),
    ('3.07', 'Mail Theft', 'Theft & Property', 'Felony', 'Taking mail or parcels addressed to another person.',
     '["The item was addressed to someone else", "It was taken from a mailbox, carrier or doorstep"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 9000, "months": 25}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 4500, "months": 12}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 4500, "months": 12}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 4500, "months": 12}]', 0, 0),
    ('3.08', 'Tampering with a Mailbox', 'Theft & Property', 'Misdemeanor', 'Forcing, prying or damaging a mailbox.',
     '["The mailbox belonged to someone else", "It was forced, pried or damaged"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2500, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1250, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1250, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1250, "months": 5}]', 0, 0),
    ('3.09', 'Possession of Stolen Property', 'Theft & Property', 'Misdemeanor', 'Holding property known or believed to be stolen.',
     '["The property was in fact stolen", "The person had it in their possession", "They knew or should have known it was stolen"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 4000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2000, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2000, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2000, "months": 8}]', 0, 0),
    ('3.10', 'Trafficking in Stolen Property', 'Theft & Property', 'Felony', 'Buying, selling or fencing stolen goods as a business.',
     '["The goods were stolen", "The person bought, sold or brokered them", "They did so knowingly and more than once"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('3.11', 'Possession of Burglary Tools', 'Theft & Property', 'Misdemeanor', 'Carrying lockpicks, drills, pry bars or similar with intent to use them on property.',
     '["The person carried tools suited to forced entry", "The circumstances show intent to use them unlawfully"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3500, "months": 12}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1750, "months": 6}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1750, "months": 6}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1750, "months": 6}]', 0, 0),
    ('3.12', 'Vandalism', 'Theft & Property', 'Misdemeanor', 'Defacing property that is not yours.',
     '["The property belonged to someone else", "It was defaced or marked without permission"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2000, "months": 8}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1000, "months": 4}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1000, "months": 4}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1000, "months": 4}]', 0, 0),
    ('3.13', 'Criminal Damage to Property', 'Theft & Property', 'Misdemeanor', 'Destroying or seriously damaging property that is not yours.',
     '["The property belonged to someone else", "It was destroyed or seriously damaged", "The act was deliberate or reckless"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 5}]', 0, 0),
    ('3.14', 'Arson', 'Theft & Property', 'Felony', 'Setting fire to a structure, vehicle or property.',
     '["A fire or explosion was set deliberately", "It damaged a structure, vehicle or property"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 28}]', 0, 0),

    -- Robbery & Burglary
    ('4.01', 'Burglary (Residential)', 'Robbery & Burglary', 'Felony', 'Entering a dwelling to commit theft or another crime inside.',
     '["The building was a dwelling", "Entry was made without permission", "The intent on entry was to commit a crime inside"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),
    ('4.02', 'Burglary (Commercial)', 'Robbery & Burglary', 'Felony', 'Entering a business or non-residential building to commit a crime inside.',
     '["The building was closed or off limits to the person", "Entry was made without permission", "The intent on entry was to commit a crime inside"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('4.03', 'Home Invasion', 'Robbery & Burglary', 'Felony', 'Forcing entry into an occupied dwelling.',
     '["The dwelling was occupied at the time", "Entry was forced or made under threat", "The occupants were confronted or put in fear"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),
    ('4.04', 'Robbery', 'Robbery & Burglary', 'Felony', 'Taking property from a person by force or threat.',
     '["Property was taken from a person or their immediate presence", "Force or the threat of force was used"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('4.05', 'Armed Robbery', 'Robbery & Burglary', 'Felony', 'Robbery committed while carrying or using a weapon.',
     '["The elements of robbery are met", "A weapon was carried, shown or used during it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 30}]', 0, 0),
    ('4.06', 'Robbery of a Retail Establishment', 'Robbery & Burglary', 'Felony', 'Robbing a store, gas station or similar business.',
     '["The premises were a retail business", "Staff or a register was targeted by force or threat", "Property or cash was taken or attempted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('4.07', 'Robbery of a Financial Institution', 'Robbery & Burglary', 'Felony', 'Robbing a bank, vault or other financial premises.',
     '["The premises were a bank or financial institution", "Force, threat or forced entry was used", "Cash or valuables were taken or attempted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 50000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 25000, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 25000, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 25000, "months": 32}]', 0, 0),
    ('4.08', 'Defeating a Security System', 'Robbery & Burglary', 'Felony', 'Bypassing, disabling or overriding alarms, cameras or door controls.',
     '["A security system protected the premises", "The person bypassed, disabled or overrode it", "They had no authority to do so"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('4.09', 'Safe Cracking', 'Robbery & Burglary', 'Felony', 'Drilling, cutting or forcing a safe, vault door or deposit box.',
     '["The container was a safe, vault or deposit box", "It was drilled, cut or forced open", "There was no authority to open it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('4.10', 'Armored Transport Robbery', 'Robbery & Burglary', 'Felony', 'Attacking or robbing an armored cash or valuables transport.',
     '["The target was an armored or secured transport", "Force, threat or a blocking manoeuvre was used", "Cargo was taken or attempted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 60000, "months": 70}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 30000, "months": 35}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 30000, "months": 35}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 30000, "months": 35}]', 0, 0),
    ('4.11', 'Cargo Theft', 'Robbery & Burglary', 'Felony', 'Taking freight, crates or containers in transit or in storage.',
     '["The goods were freight in transit or in a storage yard", "They were taken without authority"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('4.12', 'Maritime Robbery', 'Robbery & Burglary', 'Felony', 'Boarding and robbing a vessel or barge.',
     '["The target was a vessel or barge on the water", "The person boarded without authority", "Property was taken or attempted by force or threat"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 22500, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 30}]', 0, 0),
    ('4.13', 'Extortion', 'Robbery & Burglary', 'Felony', 'Obtaining money or property through threats.',
     '["A demand was made for money, property or an act", "It was backed by a threat of harm, exposure or damage"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('4.14', 'Blackmail', 'Robbery & Burglary', 'Felony', 'Threatening to reveal information unless paid.',
     '["A threat to reveal information was made", "It was tied to a demand for money, property or an act"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),

    -- Violent Crimes
    ('5.01', 'Simple Assault', 'Violent Crimes', 'Misdemeanor', 'Threatening or attempting unlawful force against another person.',
     '["An unlawful act placed the victim in fear of immediate harm", "The person meant to do it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 12}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 6}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 6}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 6}]', 0, 0),
    ('5.02', 'Battery', 'Violent Crimes', 'Misdemeanor', 'Unlawful physical contact with another person.',
     '["Physical contact was made with the victim", "The contact was unlawful and unwanted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 4000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2000, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2000, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2000, "months": 8}]', 0, 0),
    ('5.03', 'Aggravated Assault', 'Violent Crimes', 'Felony', 'Assault causing serious injury or committed with intent to cause it.',
     '["The elements of assault are met", "Serious injury resulted, or was intended"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 12000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 6000, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 6000, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 6000, "months": 15}]', 0, 0),
    ('5.04', 'Assault with a Deadly Weapon', 'Violent Crimes', 'Felony', 'Assault committed with a firearm, blade or other deadly weapon.',
     '["The elements of assault are met", "A deadly weapon was used or displayed"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 22000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 11000, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 11000, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 11000, "months": 22}]', 0, 0),
    ('5.05', 'Assault on a Peace Officer', 'Violent Crimes', 'Felony', 'Assaulting a police officer in the performance of their duties.',
     '["The victim was a peace officer on duty", "The person knew or should have known that", "The elements of assault are met"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 25}]', 0, 0),
    ('5.06', 'Assault on an Emergency Responder', 'Violent Crimes', 'Felony', 'Assaulting medical, fire or rescue personnel on a call.',
     '["The victim was an emergency responder on a call", "The person knew or should have known that", "The elements of assault are met"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 25}]', 0, 0),
    ('5.07', 'Criminal Threats', 'Violent Crimes', 'Misdemeanor', 'Threatening death or serious harm so as to place someone in sustained fear.',
     '["A specific threat of death or serious harm was made", "The victim was placed in sustained, reasonable fear"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('5.08', 'False Imprisonment', 'Violent Crimes', 'Felony', 'Confining a person against their will.',
     '["The victim was confined or restrained", "They did not consent", "There was no lawful authority for it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),
    ('5.09', 'Kidnapping', 'Violent Crimes', 'Felony', 'Seizing and moving a person against their will.',
     '["The victim was seized and moved a meaningful distance", "They did not consent", "Force, threat or deception was used"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 20000, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 22}]', 0, 0),
    ('5.10', 'Hostage Taking', 'Violent Crimes', 'Felony', 'Holding a person to force a third party to act.',
     '["A person was held against their will", "The purpose was to force a demand on someone else"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 55000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 27500, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 27500, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 27500, "months": 30}]', 0, 0),
    ('5.11', 'Torture', 'Violent Crimes', 'Felony', 'Inflicting severe pain on a restrained or captive person.',
     '["The victim was restrained or captive", "Severe pain or suffering was inflicted deliberately"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 60000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 30000, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 30000, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 30000, "months": 32}]', 0, 0),
    ('5.12', 'Vehicular Assault', 'Violent Crimes', 'Felony', 'Using a vehicle as a weapon against a person.',
     '["A vehicle was driven at or into a person", "The act was deliberate or grossly reckless", "Injury resulted or was intended"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 25}]', 0, 0),
    ('5.13', 'Attempted Murder', 'Violent Crimes', 'Felony', 'A direct act toward killing another person that falls short of death.',
     '["A direct act was taken toward killing the victim", "The person intended to kill", "Death did not result"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 50000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 25000, "months": 30}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 25000, "months": 30}]', 0, 0),
    ('5.14', 'Vehicular Manslaughter', 'Violent Crimes', 'Felony', 'Causing a death through reckless or impaired driving.',
     '["A person died", "The death was caused by the manner of driving", "The driving was reckless, impaired or grossly negligent"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 28}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 28}]', 0, 0),
    ('5.15', 'Manslaughter', 'Violent Crimes', 'Felony', 'Killing without premeditation, in the heat of the moment or by gross negligence.',
     '["A person died", "This person caused the death", "There was no premeditation"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 30}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 30}]', 0, 0),
    ('5.16', 'Murder (Second Degree)', 'Violent Crimes', 'Felony', 'Intentional killing without premeditation.',
     '["A person died", "This person caused the death", "The killing was intentional but not planned in advance"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 70000, "months": 80}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 35000, "months": 40}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 35000, "months": 40}]', 0, 0),
    ('5.17', 'Murder (First Degree)', 'Violent Crimes', 'Felony', 'Premeditated killing, or a killing during another serious felony.',
     '["A person died", "This person caused the death", "The killing was planned, or occurred during another serious felony"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 100000, "months": 100}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 50000, "months": 50}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 50000, "months": 50}]', 0, 0),
    ('5.18', 'Murder of a Peace Officer', 'Violent Crimes', 'Felony', 'Killing a police officer or emergency responder in the line of duty.',
     '["A peace officer or emergency responder died on duty", "This person caused the death", "They knew or should have known the victim was on duty"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 125000, "months": 120}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 62500, "months": 60}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 62500, "months": 60}]', 0, 0),

    -- Weapons
    ('6.01', 'Carrying a Concealed Weapon Without a Permit', 'Weapons', 'Misdemeanor', 'Carrying a hidden weapon with no permit on record.',
     '["The weapon was concealed from ordinary view", "No valid carry permit on record"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('6.02', 'Possession of an Unlicensed Firearm', 'Weapons', 'Felony', 'Holding a firearm with no weapon license on record.',
     '["The item was a working firearm", "No valid weapon license on record for this person"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 10000, "months": 25}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 5000, "months": 12}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 5000, "months": 12}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 5000, "months": 12}]', 0, 0),
    ('6.03', 'Possession of an Illegal Firearm', 'Weapons', 'Felony', 'Holding a firearm that cannot be licensed at all.',
     '["The firearm is of a type that cannot be licensed", "The person had it in their possession or control"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('6.04', 'Possession of a Class 3 Weapon', 'Weapons', 'Felony', 'Holding an automatic weapon, launcher or military ordnance.',
     '["The weapon falls in the restricted military class", "The person had it in their possession or control"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),
    ('6.05', 'Brandishing a Weapon', 'Weapons', 'Misdemeanor', 'Displaying a weapon in a threatening way.',
     '["A weapon was displayed in public or toward a person", "The display was threatening rather than defensive"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 6000, "months": 18}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 3000, "months": 9}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 3000, "months": 9}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 3000, "months": 9}]', 0, 0),
    ('6.06', 'Discharge of a Firearm in Public', 'Weapons', 'Felony', 'Firing a weapon in a public or built up area.',
     '["A firearm was discharged", "It happened in a public place or built up area", "There was no lawful justification"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 12000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 6000, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 6000, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 6000, "months": 15}]', 0, 0),
    ('6.07', 'Possession of a Stolen Firearm', 'Weapons', 'Felony', 'Holding a firearm known or believed to be stolen.',
     '["The firearm was reported stolen or flagged on the registry", "The person had it in their possession", "They knew or should have known its origin"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),
    ('6.08', 'Trafficking in Firearms', 'Weapons', 'Felony', 'Selling or supplying firearms outside the licensed trade.',
     '["Firearms were sold, supplied or brokered", "The person is not a licensed dealer", "This was more than a single transfer"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 22500, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 32}]', 0, 0),
    ('6.09', 'Manufacture of a Firearm', 'Weapons', 'Felony', 'Building or assembling firearms without a license.',
     '["Firearms or receivers were built or assembled", "No manufacturing license on record"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),
    ('6.10', 'Defacing a Firearm Serial Number', 'Weapons', 'Felony', 'Removing, grinding or altering the serial on a weapon.',
     '["The weapon carried a serial number", "The serial was removed, altered or made unreadable"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('6.11', 'Possession of Body Armor During a Felony', 'Weapons', 'Felony', 'Wearing armor while committing a felony.',
     '["The person was committing or fleeing a felony", "They were wearing body armor at the time"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 10000, "months": 25}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 5000, "months": 12}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 5000, "months": 12}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 5000, "months": 12}]', 0, 0),
    ('6.12', 'Possession of an Explosive Device', 'Weapons', 'Felony', 'Holding thermite, charges or any explosive device.',
     '["The item was an explosive or incendiary device", "The person had it in their possession or control", "There was no lawful permit for it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 20000, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 30}]', 0, 0),
    ('6.13', 'Unlawful Use of an Explosive', 'Weapons', 'Felony', 'Detonating an explosive or incendiary device.',
     '["An explosive or incendiary device was set off", "There was no lawful authority to do so"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 50000, "months": 70}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 25000, "months": 35}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 25000, "months": 35}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 25000, "months": 35}]', 0, 0),

    -- Narcotics
    ('7.01', 'Possession of Marijuana (Personal)', 'Narcotics', 'Infraction', 'Holding a small personal quantity of marijuana.',
     '["The substance was marijuana", "The quantity is consistent with personal use"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 750, "months": 0}]', 0, 0),
    ('7.02', 'Possession of a Controlled Substance', 'Narcotics', 'Misdemeanor', 'Holding a controlled substance for personal use.',
     '["The substance is on the controlled list", "The person had it in their possession", "The quantity is consistent with personal use"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 12}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 6}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 6}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 6}]', 0, 0),
    ('7.03', 'Possession with Intent to Distribute', 'Narcotics', 'Felony', 'Holding a controlled substance in a quantity or packaging that shows dealing.',
     '["The substance is on the controlled list", "The quantity, packaging or cash on hand points to sale rather than use"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 18}]', 0, 0),
    ('7.04', 'Sale of a Controlled Substance', 'Narcotics', 'Felony', 'Selling or supplying narcotics.',
     '["A controlled substance changed hands", "Payment or an exchange was involved"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('7.05', 'Sale of a Controlled Substance to a Minor', 'Narcotics', 'Felony', 'Selling or supplying narcotics to a person under age.',
     '["The elements of sale are met", "The buyer was under age", "The seller knew or should have known that"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 20000, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 30}]', 0, 0),
    ('7.06', 'Cultivation of Marijuana', 'Narcotics', 'Felony', 'Growing marijuana plants without a license.',
     '["Live plants were being grown or tended", "No cultivation license on record"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),
    ('7.07', 'Manufacture of Methamphetamine', 'Narcotics', 'Felony', 'Cooking or processing methamphetamine.',
     '["Meth was being produced or processed", "The person took an active part in the process"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),
    ('7.08', 'Processing of Cocaine', 'Narcotics', 'Felony', 'Refining or packaging cocaine.',
     '["Coca product was being refined, cut or packaged", "The person took an active part in the process"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),
    ('7.09', 'Operating a Drug Laboratory', 'Narcotics', 'Felony', 'Running or maintaining a site set up to produce narcotics.',
     '["The site was set up to produce narcotics", "The person ran, financed or maintained it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 22500, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 32}]', 0, 0),
    ('7.10', 'Trafficking in Controlled Substances', 'Narcotics', 'Felony', 'Moving narcotics in bulk or as part of an ongoing supply chain.',
     '["A large quantity was involved, or an ongoing supply chain", "The person moved, stored or directed the product"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 55000, "months": 70}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 27500, "months": 35}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 27500, "months": 35}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 27500, "months": 35}]', 0, 0),
    ('7.11', 'Possession of Drug Paraphernalia', 'Narcotics', 'Infraction', 'Holding pipes, scales, baggies or similar drug equipment.',
     '["The item is used to take, weigh or package narcotics"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 500, "months": 0}]', 0, 0),
    ('7.12', 'Possession of a Precursor Chemical', 'Narcotics', 'Felony', 'Holding chemicals used to produce narcotics.',
     '["The chemical is a listed narcotics precursor", "The quantity or context shows it was for production"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 12000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 6000, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 6000, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 6000, "months": 15}]', 0, 0),
    ('7.13', 'Under the Influence of a Controlled Substance', 'Narcotics', 'Misdemeanor', 'Being visibly impaired by narcotics in public.',
     '["The person was in a public place", "They were visibly impaired by a controlled substance"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2000, "months": 8}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1000, "months": 4}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1000, "months": 4}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1000, "months": 4}]', 0, 0),
    ('7.14', 'Transport of Narcotics', 'Narcotics', 'Felony', 'Moving narcotics by vehicle, boat or aircraft.',
     '["A controlled substance was being moved", "A vehicle, boat or aircraft was used to move it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),

    -- Fraud & Cybercrime
    ('8.01', 'Fraud', 'Fraud & Cybercrime', 'Felony', 'Obtaining money or property by deception.',
     '["A false statement or deception was made", "Someone relied on it", "Money or property was obtained as a result"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('8.02', 'Identity Theft', 'Fraud & Cybercrime', 'Felony', 'Using another person identity or documents.',
     '["Identifying details belonging to another person were used", "They were used without consent for gain or to deceive"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('8.03', 'Forgery', 'Fraud & Cybercrime', 'Felony', 'Making or altering a document so it passes as genuine.',
     '["A document was made or altered", "The change was meant to make it pass as genuine"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 12000, "months": 28}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 6000, "months": 14}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 6000, "months": 14}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 6000, "months": 14}]', 0, 0),
    ('8.04', 'Possession of Forged Documents', 'Fraud & Cybercrime', 'Misdemeanor', 'Holding licenses, permits or papers known to be fake.',
     '["The document is forged or altered", "The person had it in their possession", "They knew or should have known it was not genuine"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('8.05', 'Credit Card Fraud', 'Fraud & Cybercrime', 'Felony', 'Using card details that are not yours.',
     '["Card or account details belonging to another were used", "The use was without consent"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),
    ('8.06', 'Installation of a Card Skimming Device', 'Fraud & Cybercrime', 'Felony', 'Fitting a reader or overlay to an ATM or card terminal.',
     '["A skimming device was fitted to a terminal or ATM", "The person fitted it or arranged for it to be fitted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('8.07', 'Possession of a Card Skimming Device', 'Fraud & Cybercrime', 'Felony', 'Holding a card reader, overlay or cloner.',
     '["The item is built to capture or clone card data", "The person had it in their possession or control"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('8.08', 'Tampering with an ATM', 'Fraud & Cybercrime', 'Felony', 'Interfering with, forcing or modifying a cash machine.',
     '["The machine was opened, modified or forced", "The person had no authority to touch it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('8.09', 'Unauthorized Access to a Computer System', 'Fraud & Cybercrime', 'Felony', 'Breaking into a network, terminal or control system.',
     '["The system was protected against access", "The person got in without authority"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 22000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 11000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 11000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 11000, "months": 20}]', 0, 0),
    ('8.10', 'Possession of a Hacking Device', 'Fraud & Cybercrime', 'Felony', 'Holding a hacking drive, laptop or tool built to defeat computer security.',
     '["The item is built or configured to defeat computer security", "The person had it in their possession or control"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('8.11', 'Possession of Stolen Financial Data', 'Fraud & Cybercrime', 'Felony', 'Holding card dumps, account files or data taken from a business.',
     '["The data originated from a theft or breach", "The person held or moved it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 12000, "months": 28}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 6000, "months": 14}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 6000, "months": 14}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 6000, "months": 14}]', 0, 0),
    ('8.12', 'Money Laundering', 'Fraud & Cybercrime', 'Felony', 'Passing criminal proceeds through legitimate accounts or businesses.',
     '["The funds came from criminal activity", "They were moved, converted or mixed to hide that origin", "The person knew or should have known the source"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 20000, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 30}]', 0, 0),
    ('8.13', 'Embezzlement', 'Fraud & Cybercrime', 'Felony', 'Taking money or property entrusted to you.',
     '["The property was entrusted to the person", "They converted it to their own use"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('8.14', 'Counterfeiting Currency', 'Fraud & Cybercrime', 'Felony', 'Making or passing fake money.',
     '["The currency is counterfeit", "The person made, held or passed it knowing that"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('8.15', 'Wire Fraud', 'Fraud & Cybercrime', 'Felony', 'Running a fraud scheme over phone, radio or network.',
     '["A scheme to defraud existed", "Phone, radio or network communication was used to carry it out"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 22000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 11000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 11000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 11000, "months": 20}]', 0, 0),

    -- Vehicle Crimes
    ('9.01', 'Grand Theft Auto', 'Vehicle Crimes', 'Felony', 'Taking a motor vehicle that is not yours, permanently.',
     '["The vehicle belonged to someone else", "It was taken without consent", "The intent was to keep or dispose of it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('9.02', 'Vehicle Boosting', 'Vehicle Crimes', 'Felony', 'Stealing a vehicle to order under a contract.',
     '["A specific vehicle was targeted to order", "It was taken without consent", "The person was working to a list, contract or drop point"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('9.03', 'Carjacking', 'Vehicle Crimes', 'Felony', 'Taking a vehicle from a person by force or threat.',
     '["The vehicle was taken from an occupant or their immediate presence", "Force or the threat of force was used"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),
    ('9.04', 'Possession of a Stolen Vehicle', 'Vehicle Crimes', 'Felony', 'Driving or holding a vehicle known to be stolen.',
     '["The vehicle was reported stolen", "The person drove or held it", "They knew or should have known its origin"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('9.05', 'Operating a Chop Shop', 'Vehicle Crimes', 'Felony', 'Running a site that strips stolen vehicles for parts.',
     '["The site was used to strip or process stolen vehicles", "The person ran, financed or worked the site"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 22500, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 32}]', 0, 0),
    ('9.06', 'Dismantling a Stolen Vehicle', 'Vehicle Crimes', 'Felony', 'Stripping a stolen vehicle for parts.',
     '["The vehicle was stolen", "The person stripped or dismantled it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('9.07', 'VIN Tampering', 'Vehicle Crimes', 'Felony', 'Removing or altering a vehicle identification number.',
     '["The vehicle carried an identification number", "It was removed, altered or swapped"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),
    ('9.08', 'Possession of a Vehicle Hacking Device', 'Vehicle Crimes', 'Felony', 'Holding a relay, jammer or drive used to defeat vehicle security.',
     '["The item is built to defeat vehicle locks, alarms or immobilisers", "The person had it in their possession or control"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('9.09', 'Unauthorized Use of a Vehicle', 'Vehicle Crimes', 'Misdemeanor', 'Taking a vehicle temporarily without permission.',
     '["The vehicle belonged to someone else", "It was used without permission", "There was no intent to keep it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('9.10', 'Vehicle Tracker Tampering', 'Vehicle Crimes', 'Misdemeanor', 'Removing, jamming or disabling a vehicle tracker.',
     '["A tracker was fitted to the vehicle", "It was removed, jammed or disabled", "The person had no authority to do so"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 6000, "months": 18}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 3000, "months": 9}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 3000, "months": 9}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 3000, "months": 9}]', 0, 0),

    -- Obstruction of Justice
    ('10.01', 'Failure to Identify', 'Obstruction of Justice', 'Misdemeanor', 'Refusing to give your name to an officer during a lawful stop.',
     '["The stop or detention was lawful", "The person refused to identify themselves"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1500, "months": 5}]', 0, 0),
    ('10.02', 'Providing False Information to a Peace Officer', 'Obstruction of Justice', 'Misdemeanor', 'Giving an officer a false name, story or document.',
     '["The information given was false", "The person knew it was false", "It was given to an officer acting in their duties"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 5}]', 0, 0),
    ('10.03', 'Obstruction of Justice', 'Obstruction of Justice', 'Misdemeanor', 'Interfering with an officer carrying out their duties.',
     '["The officer was carrying out a lawful duty", "The person wilfully interfered with it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('10.04', 'Resisting Arrest', 'Obstruction of Justice', 'Misdemeanor', 'Physically resisting a lawful arrest or detention.',
     '["The arrest or detention was lawful", "The person physically resisted it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 6000, "months": 18}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 3000, "months": 9}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 3000, "months": 9}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 3000, "months": 9}]', 0, 0),
    ('10.05', 'Fleeing on Foot', 'Obstruction of Justice', 'Misdemeanor', 'Running from an officer after being told to stop.',
     '["A lawful order to stop was given", "The person ran instead of complying"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('10.06', 'Fleeing in a Vehicle', 'Obstruction of Justice', 'Felony', 'Driving away from an officer signalling you to stop.',
     '["Lights, siren or a clear signal to stop was given", "The person drove off instead of stopping"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('10.07', 'Reckless Evasion', 'Obstruction of Justice', 'Felony', 'Fleeing in a vehicle in a way that endangers others.',
     '["The elements of fleeing in a vehicle are met", "The driving created a real danger to other road users"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('10.08', 'Escape from Custody', 'Obstruction of Justice', 'Felony', 'Breaking out of restraints, a cell or a transport.',
     '["The person was lawfully in custody", "They left or broke out without release"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('10.09', 'Aiding an Escape', 'Obstruction of Justice', 'Felony', 'Helping someone break out of custody.',
     '["Another person was lawfully in custody", "This person helped them get out or stay out"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('10.10', 'Tampering with Evidence', 'Obstruction of Justice', 'Felony', 'Moving, planting or altering evidence.',
     '["The item was evidence in a live matter", "It was moved, altered or planted", "The purpose was to affect the outcome"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('10.11', 'Destruction of Evidence', 'Obstruction of Justice', 'Felony', 'Destroying or discarding evidence to defeat an investigation.',
     '["The item was evidence in a live matter", "It was destroyed, discarded or wiped", "The purpose was to defeat the investigation"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('10.12', 'Witness Intimidation', 'Obstruction of Justice', 'Felony', 'Threatening or pressuring a witness or victim.',
     '["The person was a witness or victim in a live matter", "They were threatened, pressured or bribed", "The purpose was to change or stop their account"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('10.13', 'Perjury', 'Obstruction of Justice', 'Felony', 'Lying under oath or in a sworn statement.',
     '["The statement was made under oath or sworn", "It was false on a material point", "The person knew it was false"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('10.14', 'Contempt of Court', 'Obstruction of Justice', 'Misdemeanor', 'Defying a judge, disrupting proceedings or ignoring a court direction.',
     '["A court order or direction was in force", "The person defied or disrupted it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}]', 0, 0),
    ('10.15', 'Failure to Appear', 'Obstruction of Justice', 'Misdemeanor', 'Missing a required court date.',
     '["A court date was set and notified", "The person did not attend", "There was no accepted excuse"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 4000, "months": 12}]', 0, 0),
    ('10.16', 'Violation of a Court Order', 'Obstruction of Justice', 'Misdemeanor', 'Breaching bail conditions, a restraining order or a probation term.',
     '["A court order was in force against the person", "They were on notice of its terms", "They breached a term of it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 6000, "months": 18}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 3000, "months": 9}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 3000, "months": 9}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 3000, "months": 9}]', 0, 0),
    ('10.17', 'Impersonating a Peace Officer', 'Obstruction of Justice', 'Felony', 'Passing yourself off as police, medical or another emergency service.',
     '["The person held themselves out as an officer or responder", "They were not one", "Someone was meant to act on that belief"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('10.18', 'Filing a False Police Report', 'Obstruction of Justice', 'Misdemeanor', 'Reporting a crime that did not happen.',
     '["A report was made to police", "The account was false", "The person knew it was false"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 4000, "months": 12}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2000, "months": 6}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2000, "months": 6}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2000, "months": 6}]', 0, 0),
    ('10.19', 'Unlawful Possession of a Police Radio', 'Obstruction of Justice', 'Misdemeanor', 'Holding a scanner or radio tuned to law enforcement channels.',
     '["The device receives law enforcement traffic", "The person had it in their possession", "They are not authorized to hold it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 5000, "months": 15}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2500, "months": 8}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2500, "months": 8}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2500, "months": 8}]', 0, 0),
    ('10.20', 'Harboring a Fugitive', 'Obstruction of Justice', 'Felony', 'Hiding or sheltering someone wanted by police.',
     '["The other person was wanted or had escaped custody", "This person hid, sheltered or moved them", "They knew that person was wanted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 18000, "months": 35}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 9000, "months": 18}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 9000, "months": 18}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 9000, "months": 18}]', 0, 0),

    -- Organized Crime
    ('11.01', 'Participation in a Criminal Organization', 'Organized Crime', 'Felony', 'Acting as a member of a group set up to commit crime.',
     '["The group exists to commit crime", "The person acted as a member of it", "They knew what the group does"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 0),
    ('11.02', 'Directing a Criminal Organization', 'Organized Crime', 'Felony', 'Leading, financing or giving orders within a criminal group.',
     '["The group exists to commit crime", "The person led, financed or gave orders in it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 60000, "months": 70}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 30000, "months": 35}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 30000, "months": 35}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 30000, "months": 35}]', 0, 0),
    ('11.03', 'Recruitment into a Criminal Organization', 'Organized Crime', 'Felony', 'Bringing new members into a criminal group.',
     '["The group exists to commit crime", "The person recruited or sponsored a new member"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('11.04', 'Racketeering', 'Organized Crime', 'Felony', 'A pattern of criminal activity run through an organization.',
     '["An enterprise or organization exists", "A pattern of at least two related offenses was committed through it", "This person took part in that pattern"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 50000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 25000, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 25000, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 25000, "months": 32}]', 0, 0),
    ('11.05', 'Conspiracy to Commit a Felony', 'Organized Crime', 'Felony', 'Agreeing with others to commit a felony.',
     '["An agreement was reached with at least one other person", "The plan was to commit a felony", "At least one step was taken toward it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),
    ('11.06', 'Solicitation of a Felony', 'Organized Crime', 'Felony', 'Asking, hiring or paying someone to commit a felony.',
     '["The person asked, hired or paid another", "The act sought was a felony"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('11.07', 'Accessory After the Fact', 'Organized Crime', 'Felony', 'Helping a felon avoid arrest after the crime.',
     '["A felony was committed by someone else", "This person helped them avoid arrest or punishment", "They knew about the felony"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('11.08', 'Criminal Enterprise Financing', 'Organized Crime', 'Felony', 'Funding or bankrolling criminal operations.',
     '["Funds or resources were provided", "They went to criminal operations", "The person knew what they were funding"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 20000, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 30}]', 0, 0),
    ('11.09', 'Turf Warfare', 'Organized Crime', 'Felony', 'Armed conflict between criminal groups over territory.',
     '["Two or more groups were in armed conflict", "The conflict was over territory or trade", "This person took an active part"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 0),

    -- Environmental & Maritime
    ('12.01', 'Hunting Without a License', 'Environmental & Maritime', 'Infraction', 'Taking game with no hunting license on record.',
     '["Game was taken or pursued", "No valid hunting license on record"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 1000, "months": 0}]', 0, 0),
    ('12.02', 'Poaching', 'Environmental & Maritime', 'Misdemeanor', 'Taking protected game, or hunting out of season or in a closed area.',
     '["The animal or area is protected, or the season is closed", "The person took or pursued game there"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 4000, "months": 12}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 2000, "months": 6}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 2000, "months": 6}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 2000, "months": 6}]', 0, 0),
    ('12.03', 'Illegal Trapping', 'Environmental & Maritime', 'Misdemeanor', 'Setting snares or traps outside what the law allows.',
     '["Traps or snares were set", "The method or location is not permitted"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3000, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1500, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1500, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1500, "months": 5}]', 0, 0),
    ('12.04', 'Illegal Fishing', 'Environmental & Maritime', 'Infraction', 'Fishing without a permit, out of season or over the limit.',
     '["Fish were taken", "No valid permit, or the season or limit was breached"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 800, "months": 0}]', 0, 0),
    ('12.05', 'Trespass on a Protected Reserve', 'Environmental & Maritime', 'Misdemeanor', 'Entering a closed reserve, park or conservation area.',
     '["The area is closed or protected", "The person entered without a permit"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 2500, "months": 8}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1250, "months": 4}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1250, "months": 4}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1250, "months": 4}]', 0, 0),
    ('12.06', 'Unlawful Salvage', 'Environmental & Maritime', 'Felony', 'Recovering wreck or cargo from the seabed without authority.',
     '["The material was wreck, cargo or property on the seabed", "It was recovered without a salvage permit"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 15000, "months": 30}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 7500, "months": 15}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 7500, "months": 15}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 7500, "months": 15}]', 0, 0),
    ('12.07', 'Diving in a Restricted Zone', 'Environmental & Maritime', 'Misdemeanor', 'Diving in a closed, marked or protected area of water.',
     '["The area is marked or gazetted as restricted", "The person dived there without a permit"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 3500, "months": 10}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 1750, "months": 5}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 1750, "months": 5}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 1750, "months": 5}]', 0, 0),
    ('12.08', 'Unlawful Boarding of a Vessel', 'Environmental & Maritime', 'Felony', 'Boarding a vessel or barge without permission.',
     '["The vessel belonged to someone else", "The person boarded it without permission"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 20000, "months": 40}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 10000, "months": 20}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 10000, "months": 20}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 10000, "months": 20}]', 0, 0),
    ('12.09', 'Illegal Dumping of Hazardous Waste', 'Environmental & Maritime', 'Felony', 'Discarding chemicals, fuel or hazardous material into the environment.',
     '["The material was hazardous", "It was discarded outside a licensed site"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 0),

    -- Public Corruption
    ('13.01', 'Bribery of a Public Official', 'Public Corruption', 'Felony', 'Offering money or favours to an official for an act or omission.',
     '["Something of value was offered or given", "The recipient is a public official", "It was tied to an official act or omission"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 40000, "months": 60}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 20000, "months": 30}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 20000, "months": 30}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 20000, "months": 30}]', 0, 0),
    ('13.02', 'Accepting a Bribe', 'Public Corruption', 'Felony', 'An official taking money or favours in exchange for an act or omission.',
     '["The person is a public official", "They accepted or solicited something of value", "It was tied to an official act or omission"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 22500, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 32}]', 0, 1),
    ('13.03', 'Official Misconduct', 'Public Corruption', 'Felony', 'An official using their position for an improper purpose.',
     '["The person is a public official", "They acted outside their lawful authority", "The act served an improper purpose"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 0, 1),
    ('13.04', 'Abuse of Authority', 'Public Corruption', 'Felony', 'Using the powers of the office to intimidate, punish or extort.',
     '["The person is a public official", "They used the powers of the office against someone", "The purpose was to intimidate, punish or extort"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 30000, "months": 50}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 15000, "months": 25}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 15000, "months": 25}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 15000, "months": 25}]', 0, 1),
    ('13.05', 'Unlawful Use of a Government Database', 'Public Corruption', 'Felony', 'Running searches or pulling records with no case reason.',
     '["The person accessed a restricted government system", "The lookup had no case or duty reason", "The record belonged to a real person"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 25000, "months": 45}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 12500, "months": 22}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 12500, "months": 22}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 12500, "months": 22}]', 1, 1),
    ('13.06', 'Excessive Use of Force', 'Public Corruption', 'Felony', 'Force beyond what the situation called for.',
     '["The person is a peace officer acting under authority", "Force was used", "The force went beyond what was reasonable and necessary"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 35000, "months": 55}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 17500, "months": 28}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 17500, "months": 28}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 17500, "months": 28}]', 0, 1),
    ('13.07', 'Dereliction of Duty', 'Public Corruption', 'Misdemeanor', 'Failing to act where the office required it.',
     '["The person held a duty to act", "They failed to act", "The failure was wilful or grossly negligent"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 8000, "months": 20}]', 0, 1),
    ('13.08', 'Evidence Tampering by an Officer', 'Public Corruption', 'Felony', 'An officer planting, altering or losing evidence.',
     '["The person is a peace officer", "Evidence was planted, altered, lost or destroyed", "The act was deliberate"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 45000, "months": 65}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 22500, "months": 32}, {"id": "m3", "label": "Attempt", "descriptor": "Set out to commit the offense but did not complete it.", "fine": 22500, "months": 32}, {"id": "m4", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 22500, "months": 32}]', 1, 1),
    ('13.09', 'Conspiracy Against Civil Rights', 'Public Corruption', 'Felony', 'Officials acting together to deny someone their rights.',
     '["Two or more officials acted together", "The purpose was to deny a person their rights", "A step was taken toward it"]',
     '[{"id": "m1", "label": "Principal", "descriptor": "The person who carried out the offense.", "fine": 50000, "months": 70}, {"id": "m2", "label": "Accessory", "descriptor": "Helped, drove, kept watch or covered for the principal.", "fine": 25000, "months": 35}, {"id": "m3", "label": "Conspiracy", "descriptor": "Planned or agreed to the offense with at least one other person.", "fine": 25000, "months": 35}]', 1, 1);

-- meteo-mdt default roles and permissions
INSERT IGNORE INTO `meteo_mdt_roles` (`label`, `color`, `job`, `grade`, `require_duty`, `permissions`) VALUES
    ('Everyone', '#8B97A6', '__everyone__', 0, 0, '[ "view_dashboard","view_settings","view_preferences", "view_announcements","view_penal_code","view_bolo","view_court" ]'),
    ('Recruit', '#7FB3E8', 'police', 0, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_criminal_record","view_officer_notes","view_person_photos","view_person_contacts","view_properties", "view_person_reports","view_person_vehicles","view_person_licenses","view_person_tickets","view_person_fines", "view_vehicles","view_vehicle_details","view_vehicle_owner","view_vehicle_impound","view_vehicle_notes","view_vehicle_photos", "view_weapons","view_weapon_notes", "view_reports","view_report_photos","create_report","post_case_chat", "view_warrants","view_bolo","view_penal_code","view_licenses","view_tickets","view_tags", "view_announcements","view_photo_reel","view_roster" ]'),
    ('Officer', '#4B9BE8', 'police', 1, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_criminal_record","view_officer_notes","view_person_photos","view_person_contacts","view_properties", "view_person_reports","view_person_vehicles","view_person_licenses","view_person_tickets","view_person_fines", "view_vehicles","view_vehicle_details","view_vehicle_owner","view_vehicle_impound","view_vehicle_notes","view_vehicle_photos", "view_weapons","view_weapon_notes", "view_reports","view_report_photos","create_report","post_case_chat", "view_warrants","view_bolo","view_penal_code","view_licenses","view_tickets","view_tags", "view_announcements","view_photo_reel","view_roster","view_court","view_court_parties","view_laboratory","print_documents", "edit_person_notes","add_person_photos","manage_person_contacts","book_suspect","mark_wanted", "edit_vehicle_notes","add_vehicle_photos","flag_vehicle_stolen", "register_weapon","flag_weapon_stolen","seize_weapon","edit_weapon_notes", "set_report_status","edit_report_description","manage_report_officers","add_report_suspect","add_charge", "add_report_party","edit_report_party","add_report_photos", "link_report","link_report_vehicle","link_report_property","link_report_weapon","link_report_locker","link_report_lab", "create_warrant","serve_warrant","create_bolo","edit_bolo","resolve_bolo", "issue_ticket","assign_tags","add_photo_reel","share_records" ]'),
    ('Sergeant', '#2F7FD1', 'police', 2, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_criminal_record","view_officer_notes","view_person_photos","view_person_contacts","view_properties", "view_person_reports","view_person_vehicles","view_person_licenses","view_person_tickets","view_person_fines", "view_vehicles","view_vehicle_details","view_vehicle_owner","view_vehicle_impound","view_vehicle_notes","view_vehicle_photos", "view_weapons","view_weapon_notes", "view_reports","view_report_photos","create_report","post_case_chat", "view_warrants","view_bolo","view_penal_code","view_licenses","view_tickets","view_tags", "view_announcements","view_photo_reel","view_roster","view_court","view_court_parties","view_laboratory","print_documents", "edit_person_notes","add_person_photos","manage_person_contacts","book_suspect","mark_wanted", "edit_vehicle_notes","add_vehicle_photos","flag_vehicle_stolen", "register_weapon","flag_weapon_stolen","seize_weapon","edit_weapon_notes", "set_report_status","edit_report_description","manage_report_officers","add_report_suspect","add_charge", "add_report_party","edit_report_party","add_report_photos", "link_report","link_report_vehicle","link_report_property","link_report_weapon","link_report_locker","link_report_lab", "create_warrant","serve_warrant","create_bolo","edit_bolo","resolve_bolo", "issue_ticket","assign_tags","add_photo_reel","share_records", "view_court_notes","view_court_photos","view_court_posts","manage_report_doj", "view_investigative_reports","create_investigative_report","view_fto_reports","create_fto_report", "view_master_files","create_master_file","edit_master_files", "view_hidden_penal_code","view_lab_report_notes","edit_lab_report_notes","rerun_lab_report", "mark_fine_paid","delete_person_photos","delete_vehicle_photos","edit_photo_reel", "edit_warrant","edit_ticket_price","void_ticket","suspend_license","revoke_license", "edit_announcement","pin_announcement", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_reports","view_roster_duty","view_roster_stats", "roster_manage_callsign","roster_manage_praises","radio_move_others" ]'),
    ('Lieutenant', '#2563B0', 'police', 3, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_criminal_record","view_officer_notes","view_person_photos","view_person_contacts","view_properties", "view_person_reports","view_person_vehicles","view_person_licenses","view_person_tickets","view_person_fines", "view_vehicles","view_vehicle_details","view_vehicle_owner","view_vehicle_impound","view_vehicle_notes","view_vehicle_photos", "view_weapons","view_weapon_notes", "view_reports","view_report_photos","create_report","post_case_chat", "view_warrants","view_bolo","view_penal_code","view_licenses","view_tickets","view_tags", "view_announcements","view_photo_reel","view_roster","view_court","view_court_parties","view_laboratory","print_documents", "edit_person_notes","add_person_photos","manage_person_contacts","book_suspect","mark_wanted", "edit_vehicle_notes","add_vehicle_photos","flag_vehicle_stolen", "register_weapon","flag_weapon_stolen","seize_weapon","edit_weapon_notes", "set_report_status","edit_report_description","manage_report_officers","add_report_suspect","add_charge", "add_report_party","edit_report_party","add_report_photos", "link_report","link_report_vehicle","link_report_property","link_report_weapon","link_report_locker","link_report_lab", "create_warrant","serve_warrant","create_bolo","edit_bolo","resolve_bolo", "issue_ticket","assign_tags","add_photo_reel","share_records", "view_court_notes","view_court_photos","view_court_posts","manage_report_doj", "view_investigative_reports","create_investigative_report","view_fto_reports","create_fto_report", "view_master_files","create_master_file","edit_master_files", "view_hidden_penal_code","view_lab_report_notes","edit_lab_report_notes","rerun_lab_report", "mark_fine_paid","delete_person_photos","delete_vehicle_photos","edit_photo_reel", "edit_warrant","edit_ticket_price","void_ticket","suspend_license","revoke_license", "edit_announcement","pin_announcement", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_reports","view_roster_duty","view_roster_stats", "roster_manage_callsign","roster_manage_praises","radio_move_others", "view_disciplinary_reports","create_disciplinary_report", "drop_charges","delete_report_photos","delete_warrant","delete_bolo","delete_fingerprint", "delete_photo_reel","manage_photo_categories","delete_master_file", "view_internal_penal_code","issue_license","create_ticket","edit_ticket","manage_tags", "delete_announcement","post_global_announcement", "roster_hire","roster_manage_strikes","view_roster_activity_logs", "view_logs","view_activity_logs","radio_manage_channels" ]'),
    ('Chief', '#16478A', 'police', 4, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_criminal_record","view_officer_notes","view_person_photos","view_person_contacts","view_properties", "view_person_reports","view_person_vehicles","view_person_licenses","view_person_tickets","view_person_fines", "view_vehicles","view_vehicle_details","view_vehicle_owner","view_vehicle_impound","view_vehicle_notes","view_vehicle_photos", "view_weapons","view_weapon_notes", "view_reports","view_report_photos","create_report","post_case_chat", "view_warrants","view_bolo","view_penal_code","view_licenses","view_tickets","view_tags", "view_announcements","view_photo_reel","view_roster","view_court","view_court_parties","view_laboratory","print_documents", "edit_person_notes","add_person_photos","manage_person_contacts","book_suspect","mark_wanted", "edit_vehicle_notes","add_vehicle_photos","flag_vehicle_stolen", "register_weapon","flag_weapon_stolen","seize_weapon","edit_weapon_notes", "set_report_status","edit_report_description","manage_report_officers","add_report_suspect","add_charge", "add_report_party","edit_report_party","add_report_photos", "link_report","link_report_vehicle","link_report_property","link_report_weapon","link_report_locker","link_report_lab", "create_warrant","serve_warrant","create_bolo","edit_bolo","resolve_bolo", "issue_ticket","assign_tags","add_photo_reel","share_records", "view_court_notes","view_court_photos","view_court_posts","manage_report_doj", "view_investigative_reports","create_investigative_report","view_fto_reports","create_fto_report", "view_master_files","create_master_file","edit_master_files", "view_hidden_penal_code","view_lab_report_notes","edit_lab_report_notes","rerun_lab_report", "mark_fine_paid","delete_person_photos","delete_vehicle_photos","edit_photo_reel", "edit_warrant","edit_ticket_price","void_ticket","suspend_license","revoke_license", "edit_announcement","pin_announcement", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_reports","view_roster_duty","view_roster_stats", "roster_manage_callsign","roster_manage_praises","radio_move_others", "view_disciplinary_reports","create_disciplinary_report", "drop_charges","delete_report_photos","delete_warrant","delete_bolo","delete_fingerprint", "delete_photo_reel","manage_photo_categories","delete_master_file", "view_internal_penal_code","issue_license","create_ticket","edit_ticket","manage_tags", "delete_announcement","post_global_announcement", "roster_hire","roster_manage_strikes","view_roster_activity_logs", "view_logs","view_activity_logs","radio_manage_channels", "roster_fire","delete_report","delete_ticket","delete_lab_report" ]'),
    ('Recruit', '#F08A93', 'ambulance', 0, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_person_photos","view_person_contacts", "view_beds","view_announcements","view_photo_reel","view_roster","view_tags" ]'),
    ('Paramedic', '#E84B5A', 'ambulance', 1, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_person_photos","view_person_contacts", "view_beds","view_announcements","view_photo_reel","view_roster","view_tags", "view_officer_notes","view_prescriptions","view_person_prescriptions","issue_prescription", "add_person_photos","add_photo_reel","assign_tags","share_records" ]'),
    ('Doctor', '#D13343', 'ambulance', 2, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_person_photos","view_person_contacts", "view_beds","view_announcements","view_photo_reel","view_roster","view_tags", "view_officer_notes","view_prescriptions","view_person_prescriptions","issue_prescription", "add_person_photos","add_photo_reel","assign_tags","share_records", "edit_person_notes","cancel_prescription","manage_person_contacts","edit_photo_reel" ]'),
    ('Surgeon', '#B02533', 'ambulance', 3, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_person_photos","view_person_contacts", "view_beds","view_announcements","view_photo_reel","view_roster","view_tags", "view_officer_notes","view_prescriptions","view_person_prescriptions","issue_prescription", "add_person_photos","add_photo_reel","assign_tags","share_records", "edit_person_notes","cancel_prescription","manage_person_contacts","edit_photo_reel", "delete_prescription","delete_person_photos","delete_photo_reel","manage_photo_categories", "view_reports","view_report_photos","view_fto_reports","create_fto_report", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_reports","view_roster_duty","view_roster_stats", "roster_manage_callsign","roster_manage_praises","edit_announcement","pin_announcement","radio_move_others" ]'),
    ('Chief', '#8A1926', 'ambulance', 4, 1, '[ "view_dashboard","view_radio","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_person_photos","view_person_contacts", "view_beds","view_announcements","view_photo_reel","view_roster","view_tags", "view_officer_notes","view_prescriptions","view_person_prescriptions","issue_prescription", "add_person_photos","add_photo_reel","assign_tags","share_records", "edit_person_notes","cancel_prescription","manage_person_contacts","edit_photo_reel", "delete_prescription","delete_person_photos","delete_photo_reel","manage_photo_categories", "view_reports","view_report_photos","view_fto_reports","create_fto_report", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_reports","view_roster_duty","view_roster_stats", "roster_manage_callsign","roster_manage_praises","edit_announcement","pin_announcement","radio_move_others", "view_disciplinary_reports","create_disciplinary_report", "roster_hire","roster_fire","roster_manage_strikes","view_roster_activity_logs", "delete_announcement","post_global_announcement","manage_tags", "view_logs","view_activity_logs","radio_manage_channels" ]'),
    ('Judge', '#C9A828', 'judge', 0, 1, '[ "view_dashboard","view_own_activity","use_search","view_settings","view_preferences", "view_persons","view_criminal_record","view_person_fines","view_person_reports","view_person_tickets", "view_person_licenses","view_person_contacts","view_person_photos", "view_vehicles","view_vehicle_details","view_vehicle_owner", "view_reports","view_report_photos","view_master_files", "view_court","view_court_notes","view_court_photos","view_court_parties","view_court_posts","create_court_filing","post_court_filing","add_court_photos", "view_warrants","view_penal_code","view_licenses","view_tickets", "view_announcements","view_photo_reel","view_roster","view_tags","share_records", "edit_court_filing","apply_sentence_reduction","assign_lawyer","mark_fine_paid", "view_hidden_penal_code","create_warrant","edit_warrant","view_bolo","print_documents", "drop_charges","delete_court_photos","view_internal_penal_code","delete_warrant","delete_fingerprint", "view_weapons","view_weapon_notes","view_laboratory","view_logs","view_activity_logs", "delete_court_filing","create_penal_code","edit_penal_code","delete_penal_code", "assign_tags","manage_tags", "edit_announcement","pin_announcement","delete_announcement","post_global_announcement", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_duty","view_roster_stats", "view_roster_activity_logs","roster_hire","roster_fire", "roster_manage_callsign","roster_manage_strikes","roster_manage_praises" ]'),
    ('Attorney', '#2AA9B5', 'lawyer', 0, 1, '[ "view_dashboard","view_own_activity","use_search","view_settings","view_preferences", "view_persons","view_criminal_record","view_person_fines","view_person_reports","view_person_tickets", "view_person_licenses","view_person_contacts","view_person_photos","view_person_vehicles", "view_vehicles","view_vehicle_details","view_vehicle_owner", "view_reports","view_report_photos","view_master_files", "view_court","view_court_notes","view_court_photos","view_court_parties","view_court_posts","post_court_filing", "view_warrants","view_penal_code","view_licenses","view_tickets", "view_announcements","view_photo_reel","view_roster","share_records", "create_court_filing","edit_court_filing","add_court_photos","assign_lawyer", "apply_sentence_reduction","view_hidden_penal_code","view_bolo","view_tags","assign_tags", "drop_charges","delete_court_photos","view_internal_penal_code","mark_fine_paid", "delete_court_filing", "view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_duty","view_roster_stats", "view_roster_activity_logs","roster_hire","roster_fire", "roster_manage_callsign","roster_manage_strikes","roster_manage_praises", "edit_announcement","pin_announcement","delete_announcement", "view_logs","view_activity_logs" ]'),
    ('Mayor', '#9B6BE8', 'mayor', 0, 1, '[ "view_dashboard","view_own_activity","use_search","view_settings","view_preferences","use_camera", "view_persons","view_criminal_record","view_person_fines","view_person_reports","view_person_vehicles", "view_person_licenses","view_person_tickets","view_person_photos","view_person_contacts","view_properties", "view_vehicles","view_vehicle_details","view_vehicle_owner", "view_reports","view_report_photos","view_master_files", "view_court","view_court_notes","view_court_photos","view_court_parties","view_court_posts", "view_warrants","view_bolo", "view_penal_code","view_hidden_penal_code","view_internal_penal_code", "create_penal_code","edit_penal_code","delete_penal_code", "view_licenses","create_license","edit_license","delete_license", "view_tickets","create_ticket","edit_ticket","delete_ticket", "view_tags","assign_tags","manage_tags", "view_announcements","edit_announcement","delete_announcement","pin_announcement","post_global_announcement", "view_photo_reel","add_photo_reel","edit_photo_reel","delete_photo_reel","manage_photo_categories", "view_roster","view_roster_strikes","view_roster_praises","view_roster_activity","view_roster_reports", "view_roster_duty","view_roster_stats","view_roster_activity_logs", "view_logs","view_activity_logs","share_records" ]');

-- meteo-graveyarddig default graves
INSERT IGNORE INTO `meteo_graveyard_graves` (`id`, `grave_id`, `label`, `coords`, `heading`, `created_at`, `updated_at`) VALUES
    (1, 'grave_1', 'Grave 1', '{"z":42.64584732055664,"y":-260.234130859375,"x":-1806.61572265625}', 130.263, '2026-07-17 13:28:34', '2026-07-17 13:28:34'),
    (2, 'grave_2', 'Grave 2', '{"z":42.80157089233398,"y":-261.4349060058594,"x":-1805.4229736328126}', 120.263, '2026-07-17 13:28:41', '2026-07-17 13:28:41'),
    (3, 'grave_3', 'Grave 3', '{"z":43.70181274414062,"y":-269.1777648925781,"x":-1795.9122314453126}', 127.693, '2026-07-17 13:29:44', '2026-07-17 13:29:44'),
    (4, 'grave_4', 'Grave 4', '{"z":43.76611328125,"y":-270.1882629394531,"x":-1794.6943359375}', 130.008, '2026-07-17 13:29:52', '2026-07-17 13:29:52'),
    (5, 'grave_5', 'Grave 5', '{"z":44.78593826293945,"y":-281.20477294921877,"x":-1780.843505859375}', 133.476, '2026-07-17 13:30:10', '2026-07-17 13:30:10'),
    (6, 'grave_6', 'Grave 6', '{"z":44.92576217651367,"y":-285.4799499511719,"x":-1775.6771240234376}', 126.108, '2026-07-17 13:30:25', '2026-07-17 13:30:25'),
    (7, 'grave_7', 'Grave 7', '{"z":44.89503860473633,"y":-286.5801696777344,"x":-1774.4361572265626}', 125.76, '2026-07-17 13:30:30', '2026-07-17 13:30:30'),
    (8, 'grave_8', 'Grave 8', '{"z":44.91205978393555,"y":-291.14300537109377,"x":-1769.91650390625}', 122.425, '2026-07-17 13:30:40', '2026-07-17 13:30:40'),
    (9, 'grave_9', 'Grave 9', '{"z":44.98366546630859,"y":-292.3433837890625,"x":-1768.74560546875}', 117.887, '2026-07-17 13:30:44', '2026-07-17 13:30:44'),
    (10, 'grave_10', 'Grave 10', '{"z":45.32509231567383,"y":-298.29266357421877,"x":-1763.23291015625}', 117.165, '2026-07-17 13:30:52', '2026-07-17 13:30:52'),
    (11, 'grave_11', 'Grave 11', '{"z":45.40874099731445,"y":-299.40887451171877,"x":-1762.1690673828126}', 122.911, '2026-07-17 13:30:59', '2026-07-17 13:30:59'),
    (12, 'grave_12', 'Grave 12', '{"z":46.13284301757812,"y":-307.3048400878906,"x":-1751.92724609375}', 147.679, '2026-07-17 13:31:13', '2026-07-17 13:31:13'),
    (13, 'grave_13', 'Grave 13', '{"z":46.18431091308594,"y":-308.14324951171877,"x":-1750.531494140625}', 143.192, '2026-07-17 13:31:17', '2026-07-17 13:31:17'),
    (14, 'grave_14', 'Grave 14', '{"z":47.11766052246094,"y":-295.0245361328125,"x":-1748.2860107421876}', 265.751, '2026-07-17 13:32:37', '2026-07-17 13:32:37'),
    (15, 'grave_15', 'Grave 15', '{"z":47.35558319091797,"y":-289.8580627441406,"x":-1749.5499267578126}', 267.681, '2026-07-17 13:32:43', '2026-07-17 13:32:43'),
    (16, 'grave_16', 'Grave 16', '{"z":47.35568618774414,"y":-291.20220947265627,"x":-1745.4268798828126}', 262.728, '2026-07-17 13:32:55', '2026-07-17 13:32:55'),
    (17, 'grave_17', 'Grave 17', '{"z":47.63167953491211,"y":-283.1173400878906,"x":-1751.4642333984376}', 272.608, '2026-07-17 13:33:09', '2026-07-17 13:33:09'),
    (18, 'grave_18', 'Grave 18', '{"z":47.64879608154297,"y":-278.12689208984377,"x":-1752.6182861328126}', 272.608, '2026-07-17 13:33:13', '2026-07-17 13:33:13'),
    (19, 'grave_19', 'Grave 19', '{"z":47.81060791015625,"y":-281.7328186035156,"x":-1747.784912109375}', 266.862, '2026-07-17 13:33:19', '2026-07-17 13:33:19'),
    (20, 'grave_20', 'Grave 20', '{"z":48.4310073852539,"y":-283.4214172363281,"x":-1742.5711669921876}', 90.7523, '2026-07-17 13:33:41', '2026-07-17 13:33:41'),
    (21, 'grave_21', 'Grave 21', '{"z":47.83292388916015,"y":-292.48541259765627,"x":-1740.453125}', 256.277, '2026-07-17 13:33:49', '2026-07-17 13:33:49'),
    (22, 'grave_22', 'Grave 22', '{"z":48.25151062011719,"y":-285.50244140625,"x":-1737.688232421875}', 252.271, '2026-07-17 13:33:54', '2026-07-17 13:33:54'),
    (23, 'grave_23', 'Grave 23', '{"z":49.83552169799805,"y":-252.57383728027345,"x":-1763.4063720703126}', 318.354, '2026-07-17 13:34:09', '2026-07-17 13:34:09'),
    (24, 'grave_24', 'Grave 24', '{"z":49.58568954467773,"y":-238.38784790039063,"x":-1782.6895751953126}', 302.88, '2026-07-17 13:34:17', '2026-07-17 13:34:17'),
    (25, 'grave_25', 'Grave 25', '{"z":49.62037658691406,"y":-229.91500854492188,"x":-1790.228515625}', 284.34, '2026-07-17 13:34:23', '2026-07-17 13:34:23'),
    (26, 'grave_26', 'Grave 26', '{"z":50.374267578125,"y":-231.78981018066407,"x":-1782.72509765625}', 129.945, '2026-07-17 13:34:32', '2026-07-17 13:34:32'),
    (27, 'grave_27', 'Grave 27', '{"z":50.9304084777832,"y":-241.11798095703126,"x":-1769.7823486328126}', 309.196, '2026-07-17 13:34:39', '2026-07-17 13:34:39'),
    (28, 'grave_28', 'Grave 28', '{"z":50.69261169433594,"y":-251.01190185546876,"x":-1754.806884765625}', 316.516, '2026-07-17 13:34:50', '2026-07-17 13:34:50'),
    (29, 'grave_29', 'Grave 29', '{"x":-1731.619140625,"z":49.15349197387695,"y":-282.4869384765625}', 267.886, '2026-07-17 13:36:00', '2026-07-17 13:36:00'),
    (30, 'grave_30', 'Grave 30', '{"x":-1771.09423828125,"z":48.40288543701172,"y":-256.6980895996094}', 312.073, '2026-07-17 13:36:20', '2026-07-17 13:36:20'),
    (31, 'grave_31', 'Grave 31', '{"x":-1777.26318359375,"z":48.37625503540039,"y":-252.6218719482422}', 312.16, '2026-07-17 13:36:27', '2026-07-17 13:36:27'),
    (32, 'grave_32', 'Grave 32', '{"x":-1790.1339111328126,"z":48.06972503662109,"y":-241.15731811523438}', 293.373, '2026-07-17 13:36:35', '2026-07-17 13:36:35'),
    (33, 'grave_33', 'Grave 33', '{"x":-1775.790283203125,"z":52.26465225219726,"y":-219.9923553466797}', 295.288, '2026-07-17 13:36:48', '2026-07-17 13:36:48'),
    (34, 'grave_34', 'Grave 34', '{"x":-1767.93701171875,"z":52.33283233642578,"y":-227.0327911376953}', 307.249, '2026-07-17 13:36:53', '2026-07-17 13:36:53'),
    (35, 'grave_35', 'Grave 35', '{"x":-1756.701904296875,"z":53.04539489746094,"y":-228.51795959472657}', 315.672, '2026-07-17 13:36:59', '2026-07-17 13:36:59'),
    (36, 'grave_36', 'Grave 36', '{"x":-1745.4700927734376,"z":53.21250915527344,"y":-232.53463745117188}', 329.566, '2026-07-17 13:37:05', '2026-07-17 13:37:05'),
    (37, 'grave_37', 'Grave 37', '{"x":-1764.949951171875,"z":54.12596130371094,"y":-211.7318878173828}', 125.337, '2026-07-17 13:37:17', '2026-07-17 13:37:17'),
    (38, 'grave_38', 'Grave 38', '{"x":-1753.2117919921876,"z":55.91647720336914,"y":-206.8828125}', 306.487, '2026-07-17 13:37:26', '2026-07-17 13:37:26'),
    (39, 'grave_39', 'Grave 39', '{"x":-1746.3673095703126,"z":55.8575325012207,"y":-211.8031463623047}', 305.649, '2026-07-17 13:37:31', '2026-07-17 13:37:31'),
    (40, 'grave_40', 'Grave 40', '{"x":-1729.1153564453126,"z":54.19399642944336,"y":-233.4958953857422}', 347.325, '2026-07-17 13:37:54', '2026-07-17 13:37:54'),
    (41, 'grave_41', 'Grave 41', '{"x":-1722.2613525390626,"z":54.20080184936523,"y":-233.84754943847657}', 341.494, '2026-07-17 13:38:02', '2026-07-17 13:38:02'),
    (42, 'grave_42', 'Grave 42', '{"x":-1710.4659423828126,"z":55.35671997070312,"y":-226.32276916503907}', 342.051, '2026-07-17 13:38:10', '2026-07-17 13:38:10'),
    (43, 'grave_43', 'Grave 43', '{"x":-1726.97216796875,"z":55.31715393066406,"y":-225.20982360839845}', 334.394, '2026-07-17 13:38:18', '2026-07-17 13:38:18'),
    (44, 'grave_44', 'Grave 44', '{"x":-1627.6546630859376,"z":56.28561019897461,"y":-148.87387084960938}', 284.016, '2026-07-17 13:38:37', '2026-07-17 13:38:37'),
    (45, 'grave_45', 'Grave 45', '{"x":-1623.152587890625,"z":55.91513061523437,"y":-154.2672882080078}', 285.185, '2026-07-17 13:38:42', '2026-07-17 13:38:42'),
    (46, 'grave_46', 'Grave 46', '{"x":-1634.10400390625,"z":55.96045303344726,"y":-162.92112731933595}', 17.7378, '2026-07-17 13:38:52', '2026-07-17 13:38:52'),
    (47, 'grave_47', 'Grave 47', '{"x":-1633.3482666015626,"z":55.38479614257812,"y":-172.4029998779297}', 22.7139, '2026-07-17 13:39:04', '2026-07-17 13:39:04'),
    (48, 'grave_48', 'Grave 48', '{"x":-1640.9237060546876,"z":55.33187484741211,"y":-177.86447143554688}', 23.535, '2026-07-17 13:39:10', '2026-07-17 13:39:10'),
    (49, 'grave_49', 'Grave 49', '{"x":-1629.78759765625,"z":54.63115692138672,"y":-184.72457885742188}', 17.4943, '2026-07-17 13:39:20', '2026-07-17 13:39:20'),
    (50, 'grave_50', 'Grave 50', '{"x":-1622.2874755859376,"z":55.05082321166992,"y":-174.96563720703126}', 14.4205, '2026-07-17 13:39:27', '2026-07-17 13:39:27'),
    (51, 'grave_51', 'Grave 51', '{"x":-1648.390380859375,"z":56.63780975341797,"y":-157.5270538330078}', 117.788, '2026-07-17 13:39:48', '2026-07-17 13:39:48'),
    (52, 'grave_52', 'Grave 52', '{"x":-1648.787353515625,"z":57.60223007202148,"y":-143.27442932128907}', 107.561, '2026-07-17 13:39:54', '2026-07-17 13:39:54'),
    (53, 'grave_53', 'Grave 53', '{"x":-1651.283935546875,"z":58.74893188476562,"y":-126.7347183227539}', 351.008, '2026-07-17 13:40:01', '2026-07-17 13:40:01'),
    (54, 'grave_54', 'Grave 54', '{"x":-1657.5479736328126,"z":59.09633636474609,"y":-126.35623931884766}', 343.254, '2026-07-17 13:40:06', '2026-07-17 13:40:06'),
    (55, 'grave_55', 'Grave 55', '{"x":-1663.690185546875,"z":59.2138786315918,"y":-126.24897766113281}', 349.17, '2026-07-17 13:40:11', '2026-07-17 13:40:11'),
    (56, 'grave_56', 'Grave 56', '{"y":-147.30682373046876,"z":57.8757209777832,"x":-1680.9105224609376}', 102.016, '2026-07-17 13:44:52', '2026-07-17 13:44:52'),
    (57, 'grave_57', 'Grave 57', '{"y":-153.53512573242188,"z":57.36404037475586,"x":-1678.3350830078126}', 96.5148, '2026-07-17 13:44:57', '2026-07-17 13:44:57'),
    (58, 'grave_58', 'Grave 58', '{"y":-159.38670349121095,"z":56.91061401367187,"x":-1682.9317626953126}', 99.7371, '2026-07-17 13:45:05', '2026-07-17 13:45:05'),
    (59, 'grave_59', 'Grave 59', '{"y":-172.6439208984375,"z":56.8214225769043,"x":-1669.490478515625}', 104.864, '2026-07-17 13:45:17', '2026-07-17 13:45:17'),
    (60, 'grave_60', 'Grave 60', '{"x":-1790.586669921875,"z":44.07426071166992,"y":-273.606689453125}', 126.805, '2026-07-25 03:36:44', '2026-07-25 03:36:44');

-- meteo-houserobbery default rooms
INSERT IGNORE INTO `meteo_houserobbery_rooms` (`id`, `room_id`, `label`, `doors`, `props`, `created_at`, `updated_at`, `zones`, `peds`) VALUES
    (1, 'vinewood_01', 'Vinewood 01', '[{"coords":{"z":105.1712875366211,"x":531.9129028320313,"y":222.0451202392578},"model":1067970260}]', '[{"coords":{"z":104.37702941894533,"x":535.9066162109375,"y":219.08511352539066},"door":1,"rotation":{"z":162.0534820556641,"x":0.0,"y":-0.0},"model":"p_lestersbed_s","label":"Worn Wooden Bed (Blanket)","decoration":true},{"coords":{"z":103.80979919433594,"x":534.1194458007813,"y":218.53042602539066},"door":1,"rotation":{"z":161.42218017578126,"x":0.0,"y":-0.0},"model":"prop_fbi3_coffee_table","label":"Modern Coffee Table (White Frame)","decoration":true},{"item":"meteo_hr_printer","door":1,"label":"Printer","model":"prop_printer_01","coords":{"z":104.2384033203125,"x":533.9341430664063,"y":218.54202270507813},"rotation":{"z":147.80784606933598,"x":0.0,"y":-0.0}},{"coords":{"z":103.74115753173828,"x":533.9498901367188,"y":222.4528961181641},"door":1,"rotation":{"z":-20.30019950866699,"x":0.0,"y":0.0},"model":"prop_tv_cabinet_04","label":"TV Cabinet (Bookshelf Style)","decoration":true},{"item":"meteo_hr_tv","door":1,"label":"Flat TV","model":"prop_tv_flat_03","coords":{"z":104.4715347290039,"x":534.021728515625,"y":222.50381469726563},"rotation":{"z":-20.90729904174804,"x":0.0,"y":0.0}},{"item":"meteo_hr_mp3dock","door":1,"label":"MP3 Dock","model":"prop_mp3_dock","coords":{"z":104.46278381347656,"x":533.556884765625,"y":222.50970458984376},"rotation":{"z":-20.9020767211914,"x":-0.0,"y":-0.0}},{"item":"meteo_hr_vcr","door":1,"label":"VCR","model":"prop_vcr_01","coords":{"z":103.81185150146485,"x":534.9378051757813,"y":222.13938903808595},"rotation":{"z":-20.2770709991455,"x":-0.0,"y":-0.0}},{"coords":{"z":104.14400482177735,"x":537.6503295898438,"y":217.36764526367188},"door":1,"rotation":{"z":160.02578735351563,"x":0.0,"y":-0.0},"model":"prop_table_04","label":"Dining Bench (Dark Frame)","decoration":true},{"item":"meteo_hr_microwave","door":1,"label":"Microwave","model":"prop_micro_02","coords":{"z":104.69402313232422,"x":538.1843872070313,"y":217.30096435546876},"rotation":{"z":-177.02142333984376,"x":0.0,"y":-0.0}},{"item":"meteo_hr_toaster","door":1,"label":"Toaster","model":"prop_toaster_02","coords":{"z":104.71978759765625,"x":537.7716674804688,"y":217.3896484375},"rotation":{"z":77.5573501586914,"x":0.0,"y":0.0}},{"item":"meteo_hr_kettle","door":1,"label":"Kettle","model":"prop_kettle_01","coords":{"z":104.71978759765625,"x":537.2765502929688,"y":217.74896240234376},"rotation":{"z":155.37136840820313,"x":0.0,"y":-0.0}},{"item":"meteo_hr_coffeemac","door":1,"label":"Coffee Machine","model":"prop_coffee_mac_02","coords":{"z":104.78108215332031,"x":536.9236450195313,"y":217.70657348632813},"rotation":{"z":159.47283935546876,"x":0.0,"y":-0.0}},{"coords":{"z":103.73945617675781,"x":539.5936889648438,"y":220.62925720214845},"door":1,"rotation":{"z":-109.39739227294922,"x":0.0,"y":-0.0},"model":"prop_watercooler","label":"Water Cooler (Plastic Jug)","decoration":true},{"coords":{"z":103.74079895019531,"x":531.837158203125,"y":219.54026794433595},"door":1,"rotation":{"z":71.61282348632813,"x":0.0,"y":0.0},"model":"v_ind_rc_lowtable","label":"Wooden Coffee Table (Low)","decoration":true},{"coords":{"z":103.74285888671875,"x":532.7536010742188,"y":219.21951293945313},"door":1,"rotation":{"z":-107.44708251953125,"x":0.0,"y":-0.0},"model":"prop_chair_01b","label":"Plastic Chair (Worn Red)","decoration":true}]', '2026-07-16 12:15:39', '2026-07-16 12:42:44', '[{"coords":{"z":104.09310150146485,"x":533.9639282226563,"y":222.18751525878907},"label":"Storage","door":1,"radius":0.39999999999999}]', NULL),
    (2, 'vinewood_02', 'Vinewood 02', '[{"coords":{"y":229.85769653320313,"x":518.7546997070313,"z":105.17138671875},"model":1067970260}]', '[{"door":1,"rotation":{"y":-0.0,"x":0.0,"z":-109.52312469482422},"label":"Wide Bed (Red Frame)","decoration":true,"coords":{"y":233.07424926757813,"x":522.7533569335938,"z":103.74554443359375},"model":"apa_mp_h_bed_wide_05"},{"door":1,"rotation":{"y":-0.0,"x":0.0,"z":-139.43389892578126},"label":"Dog Bed (Grey)","decoration":true,"coords":{"y":229.9090576171875,"x":521.1048583984375,"z":103.7432861328125},"model":"sf_prop_sf_bed_dog_01a"},{"door":1,"rotation":{"y":-0.0,"x":0.0,"z":-110.49694061279297},"label":"Modern Coffee Table (White Frame)","decoration":true,"coords":{"y":231.3105010986328,"x":521.774169921875,"z":103.80989837646485},"model":"prop_fbi3_coffee_table"},{"door":1,"item":"meteo_hr_printer","rotation":{"y":0.0,"x":0.0,"z":76.9390869140625},"label":"Printer","coords":{"y":231.36544799804688,"x":518.0774536132813,"z":103.74002838134766},"model":"prop_printer_01"},{"door":1,"item":"meteo_hr_tv","rotation":{"y":-0.0,"x":0.0,"z":-112.03282928466797},"label":"Flat TV","coords":{"y":231.30099487304688,"x":521.8232421875,"z":104.32160186767578},"model":"prop_tv_flat_03"},{"door":1,"item":"meteo_hr_kettle","rotation":{"y":-0.0,"x":0.0,"z":-108.13961029052735},"label":"Kettle","coords":{"y":231.0685272216797,"x":521.5330200195313,"z":104.29296112060547},"model":"prop_kettle_01"},{"door":1,"rotation":{"y":0.0,"x":0.0,"z":51.93239212036133},"label":"Dining Chair (Red Plastic)","decoration":true,"coords":{"y":232.0808563232422,"x":518.3716430664063,"z":103.7548828125},"model":"hei_heist_din_chair_02"},{"door":1,"item":"meteo_hr_microwave","rotation":{"y":-0.0,"x":0.0,"z":-107.4641342163086},"label":"Microwave","coords":{"y":236.19378662109376,"x":523.9703369140625,"z":103.88926696777344},"model":"prop_micro_02"}]', '2026-07-16 14:37:58', '2026-07-16 14:53:00', '[{"radius":0.3,"door":1,"coords":{"y":231.5032501220703,"x":521.6182861328125,"z":104.23976135253906},"label":"Tv stand"}]', NULL),
    (3, 'vinewood_03', 'Vinewood 03', '[{"coords":{"y":232.64686584472657,"x":511.1015625,"z":105.17457580566406},"model":1067970260}]', '[{"door":1,"rotation":{"y":-0.0,"x":0.0,"z":-109.1734848022461},"label":"Plastic Table (Square, White)","decoration":true,"coords":{"y":238.8241729736328,"x":515.6106567382813,"z":104.14266967773438},"model":"prop_table_03b"},{"door":1,"rotation":{"y":-0.0,"x":-0.0,"z":-17.96665382385254},"label":"Water Cooler (Plastic Jug)","decoration":true,"coords":{"y":240.40403747558595,"x":512.5263671875,"z":103.74153900146485},"model":"prop_watercooler"},{"door":1,"rotation":{"y":-0.0,"x":-0.0,"z":-18.49629783630371},"label":"Fridge (Double Door, Water Dispenser)","decoration":true,"coords":{"y":240.31549072265626,"x":513.3330688476563,"z":103.7430419921875},"model":"v_res_fridgemodsml"},{"door":1,"item":"meteo_hr_microwave","rotation":{"y":-0.0,"x":0.0,"z":-98.09933471679688},"label":"Microwave","coords":{"y":238.87991333007813,"x":515.7805786132813,"z":104.70120239257813},"model":"prop_micro_02"},{"door":1,"item":"meteo_hr_toaster","rotation":{"y":-0.0,"x":0.0,"z":-171.79066467285157},"label":"Toaster","coords":{"y":238.48011779785157,"x":515.6759033203125,"z":104.53362274169922},"model":"prop_toaster_02"},{"door":1,"item":"meteo_hr_kettle","rotation":{"y":-0.0,"x":0.0,"z":-104.47712707519531},"label":"Kettle","coords":{"y":239.2095947265625,"x":515.3884887695313,"z":104.58345031738281},"model":"prop_kettle_01"},{"door":1,"rotation":{"y":-0.0,"x":0.0,"z":-109.30101013183594},"label":"L-Shaped Sofa (Modern)","decoration":true,"coords":{"y":235.63296508789063,"x":513.9694213867188,"z":103.5797348022461},"model":"v_ilev_m_sofa"},{"door":1,"rotation":{"y":0.0,"x":0.0,"z":67.97772979736328},"label":"TV Cabinet (Curved Front)","decoration":true,"coords":{"y":235.92428588867188,"x":510.9898986816406,"z":103.7431640625},"model":"prop_tv_cabinet_05"},{"door":1,"item":"meteo_hr_tv","rotation":{"y":0.0,"x":0.0,"z":69.05181884765625},"label":"Flat TV","coords":{"y":235.8871612548828,"x":511.00726318359377,"z":104.5812759399414},"model":"prop_tv_flat_03"}]', '2026-07-16 14:49:22', '2026-07-16 14:49:22', '[]', NULL),
    (4, 'vinewood_04', 'Vinewood 04', '[{"coords":{"x":496.2473449707031,"y":238.0497283935547,"z":105.17134094238281},"model":1067970260}]', '[{"model":"ex_prop_exec_bed_01","label":"Executive Bed (Beige Upholstery)","rotation":{"x":0.0,"y":0.0,"z":-19.96169853210449},"coords":{"x":499.04034423828127,"y":242.33551025390626,"z":103.74124145507813},"decoration":true,"door":1},{"model":"h4_mp_h_yacht_strip_chair_01","label":"Yacht Lounge Chair (White)","rotation":{"x":0.0,"y":-0.0,"z":-110.58739471435547},"coords":{"x":498.7781066894531,"y":238.1154022216797,"z":103.67295837402344},"decoration":true,"door":1},{"model":"v_ind_rc_lowtable","label":"Wooden Coffee Table (Low)","rotation":{"x":0.0,"y":-0.0,"z":-108.68828582763672},"coords":{"x":495.9353942871094,"y":240.27340698242188,"z":103.74085235595703},"decoration":true,"door":1},{"item":"meteo_hr_printer","model":"prop_printer_01","label":"Printer","rotation":{"x":0.0,"y":0.0,"z":68.6980209350586},"coords":{"x":495.7928466796875,"y":240.21749877929688,"z":104.15320587158203},"door":1},{"model":"prop_toilet_01","label":"Toilet (Standard)","rotation":{"x":0.0,"y":-0.0,"z":159.3599853515625},"coords":{"x":500.8609619140625,"y":243.161376953125,"z":103.74185943603516},"decoration":true,"door":1},{"model":"prop_w_fountain_01","label":"Public Sink (Stainless, Wide)","rotation":{"x":0.0,"y":-0.0,"z":160.30416870117188},"coords":{"x":499.7397155761719,"y":243.2371063232422,"z":104.3492202758789},"decoration":true,"door":1},{"model":"prop_toilet_brush_01","label":"Toilet Brush (Holder)","rotation":{"x":0.0,"y":-0.0,"z":162.16586303710938},"coords":{"x":501.6004638671875,"y":244.52957153320313,"z":103.72090911865235},"decoration":true,"door":1},{"model":"prop_fan_01","label":"Oscillating Fan (Floor)","rotation":{"x":0.0,"y":-0.0,"z":152.9168701171875},"coords":{"x":499.407958984375,"y":240.03387451171876,"z":103.7313461303711},"decoration":true,"door":1},{"model":"v_res_fridgemodsml","label":"Fridge (Double Door, Water Dispenser)","rotation":{"x":-0.0,"y":-0.0,"z":-18.50069808959961},"coords":{"x":497.7752990722656,"y":245.63458251953126,"z":103.74101257324219},"decoration":true,"door":1},{"item":"meteo_hr_kettle","model":"prop_kettle_01","label":"Kettle","rotation":{"x":0.0,"y":0.0,"z":61.13012313842773},"coords":{"x":496.2731018066406,"y":240.46310424804688,"z":104.2076644897461},"door":1},{"item":"meteo_hr_toaster","model":"prop_toaster_02","label":"Toaster","rotation":{"x":-0.0,"y":-0.0,"z":-46.37736892700195},"coords":{"x":495.9228210449219,"y":240.55052185058595,"z":104.15413665771485},"door":1},{"item":"meteo_hr_vcr","model":"prop_vcr_01","label":"VCR","rotation":{"x":0.0,"y":-0.0,"z":-112.13453674316406},"coords":{"x":500.04779052734377,"y":240.86700439453126,"z":103.81190490722656},"door":1}]', '2026-07-16 15:06:37', '2026-07-16 15:06:37', '[]', '[]'),
    (5, 'vinewood_05', 'Vinewood 05', '[{"model":1067970260,"coords":{"y":192.7554473876953,"z":108.7378158569336,"x":508.8204040527344}}]', '[{"decoration":true,"label":"Wide Bed (Red Frame)","model":"apa_mp_h_bed_wide_05","rotation":{"y":0.0,"z":69.99659729003906,"x":0.0},"coords":{"y":189.47003173828129,"z":107.31197357177736,"x":504.58306884765627},"door":1},{"decoration":true,"label":"Low Sideboard (Dark Wood)","model":"apa_mp_h_str_sideboardl_11","rotation":{"y":-0.0,"z":-110.22469329833985,"x":0.0},"coords":{"y":189.87217712402345,"z":107.3077163696289,"x":509.3258056640625},"door":1},{"item":"meteo_hr_tv","label":"Flat TV","model":"prop_tv_flat_03","rotation":{"y":-0.0,"z":-109.59769439697266,"x":0.0},"coords":{"y":190.9561462402344,"z":108.2712173461914,"x":509.4023742675781},"door":1},{"item":"meteo_hr_tv","label":"Flat TV","model":"prop_tv_flat_03","rotation":{"y":-0.0,"z":-109.59768676757813,"x":0.0},"coords":{"y":188.9917907714844,"z":108.27120208740236,"x":508.7068481445313},"door":1},{"item":"meteo_hr_vcr","label":"VCR","model":"prop_vcr_01","rotation":{"y":-0.0,"z":-110.4745864868164,"x":0.0},"coords":{"y":190.1743621826172,"z":108.26004028320313,"x":509.2460021972656},"door":1},{"decoration":true,"label":"Modern Armchair (Mustard)","model":"apa_mp_h_stn_chairarm_01","rotation":{"y":0.0,"z":69.05265045166016,"x":0.0},"coords":{"y":192.8501892089844,"z":107.30960845947266,"x":506.3714599609375},"door":1},{"item":"meteo_hr_printer","label":"Printer","model":"prop_printer_01","rotation":{"y":0.0,"z":70.8667221069336,"x":0.0},"coords":{"y":192.0015106201172,"z":108.12337493896485,"x":505.7710266113281},"door":1},{"decoration":true,"label":"Tall Fridge (Closed)","model":"prop_fridge_03","rotation":{"y":-0.0,"z":159.91004943847657,"x":0.0},"coords":{"y":185.1030731201172,"z":107.29817199707033,"x":507.29254150390627},"door":1},{"decoration":true,"label":"Water Cooler (Plastic Jug)","model":"prop_watercooler","rotation":{"y":-0.0,"z":159.47119140625,"x":0.0},"coords":{"y":185.22796630859376,"z":107.30598449707033,"x":506.4132385253906},"door":1},{"decoration":true,"label":"Modern Dining Table (Metal Legs)","model":"prop_table_06","rotation":{"y":-0.0,"z":-111.31026458740236,"x":0.0},"coords":{"y":191.5302734375,"z":107.72268676757813,"x":505.7648315429688},"door":1},{"decoration":true,"label":"Yacht Table (Black Wicker)","model":"prop_yacht_table_03","rotation":{"y":0.0,"z":70.68507385253906,"x":0.0},"coords":{"y":186.94065856933598,"z":107.30818176269533,"x":504.1951904296875},"door":1},{"item":"meteo_hr_toaster","label":"Toaster","model":"prop_toaster_02","rotation":{"y":0.0,"z":-37.77169036865234,"x":0.0},"coords":{"y":186.933349609375,"z":108.24088287353516,"x":504.1181640625},"door":1},{"item":"meteo_hr_microwave","label":"Microwave","model":"prop_micro_02","rotation":{"y":0.0,"z":71.9842529296875,"x":0.0},"coords":{"y":186.3590087890625,"z":108.38919067382813,"x":503.8437194824219},"door":1},{"item":"meteo_hr_kettle","label":"Kettle","model":"prop_kettle_01","rotation":{"y":-0.0,"z":144.45358276367188,"x":0.0},"coords":{"y":186.74700927734376,"z":108.2944107055664,"x":503.9914245605469},"door":1},{"item":"meteo_hr_coffeemac","label":"Coffee Machine","model":"prop_coffee_mac_02","rotation":{"y":0.0,"z":71.98426055908203,"x":0.0},"coords":{"y":187.65158081054688,"z":108.47624969482422,"x":504.5193786621094},"door":1},{"item":"meteo_hr_mp3dock","label":"MP3 Dock","model":"prop_mp3_dock","rotation":{"y":-0.0,"z":-112.622314453125,"x":0.0},"coords":{"y":189.59698486328129,"z":108.26246643066406,"x":508.9358215332031},"door":1},{"decoration":true,"label":"Bin (Red)","model":"prop_bin_10b","rotation":{"y":-0.0,"z":-20.39474487304687,"x":-0.0},"coords":{"y":185.4398651123047,"z":107.30816650390624,"x":505.9103393554688},"door":1},{"decoration":true,"label":"Wall Clock (White Face)","model":"prop_game_clock_01","rotation":{"y":-0.0,"z":-108.66728973388672,"x":0.0},"coords":{"y":190.6201629638672,"z":109.30105590820313,"x":509.775390625},"door":1},{"decoration":true,"label":"Magazine Holder (Black)","model":"prop_folder_02","rotation":{"y":0.0,"z":-7.92612409591674,"x":0.0},"coords":{"y":191.12814331054688,"z":107.97233581542968,"x":505.4082336425781},"door":1},{"decoration":true,"label":"FIB Ashtray (Wall-Mounted)","model":"prop_fib_ashtray_01","rotation":{"y":0.0,"z":50.82219696044922,"x":0.0},"coords":{"y":191.0175018310547,"z":108.3304672241211,"x":505.8922729492188},"door":1},{"decoration":true,"label":"Stack of Folders","model":"v_res_paperfolders","rotation":{"y":0.0,"z":-23.42291069030761,"x":0.0},"coords":{"y":191.3544464111328,"z":108.2312240600586,"x":505.6125793457031},"door":1},{"decoration":true,"label":"Perfume Bottle (Green)","model":"v_res_r_perfume","rotation":{"y":0.0,"z":49.68045425415039,"x":0.0},"coords":{"y":191.56069946289066,"z":108.25289154052736,"x":505.774169921875},"door":1},{"decoration":true,"label":"Oscillating Fan (Floor)","model":"prop_fan_01","rotation":{"y":-0.0,"z":-53.93889999389648,"x":-0.0},"coords":{"y":192.14938354492188,"z":107.29782104492188,"x":509.04693603515627},"door":1},{"decoration":true,"label":"Vacuum Cleaner (Upright)","model":"v_res_vacuum","rotation":{"y":-0.0,"z":-115.67518615722656,"x":0.0},"coords":{"y":188.05474853515626,"z":107.30994415283205,"x":508.6344604492188},"door":1}]', '2026-07-16 15:31:32', '2026-07-16 15:40:10', '[]', '[{"heading":250.18173599243165,"coords":{"y":192.17324829101563,"z":107.3077163696289,"x":507.1417541503906},"door":1},{"heading":338.7807312011719,"coords":{"y":187.65618896484376,"z":107.3077163696289,"x":507.5866394042969},"door":1}]');
```

</details>

***

## 2.10.0

### Changes

* Major Crime Tablet racing update with in game track creator, ELO and leaderboards - <https://youtu.be/gv1yc5w_BBE>
* Crime Tablet UI/UX improvements (blackmarket, boosting etc etc)
* New adjustable vehicle trunks. Configure and save trunk positions for each vehicle - <https://youtu.be/AF_-KyZTXNg>
* Added in-game perks creator support. now you can adjust and create as you want - <https://youtu.be/k2mujV43Ot8>
* New apartment rooms
* Added dealership skip support for vehicle imports
* Improved dealership vehicle imports
* Added dealerships manage command to open management without going to the location
* Added restaurants manage command to open management without going to the location
* Major Phone banking app update with in app billing and easy money transfers to saved contacts
* Phone notes sharing support
* Added show only nearest meditation blip option
* Added auto disable to hide the seize player cash target when money as item is enabled
* Furnishing now supports selling instead of only deleting
* Hardened prison spawning and prison ped improvements
* Chopshop parts carrying now properly handles dead and cuffed player states
* Chopshop now displays vehicle images
* Improved medical job help up animations with CPR
* Improved appearance support for heavy clothing packs, eye colors and head overlay tints
* Appearance improvements with new outfit hover preview support
* Multichar spawn improvements
* Improved weapon on back
* Fixed police horns getting stuck
* Fixed animation flag issues on the QBX bridge. Medical job help up animations should now work correctly
* Fixed gym decay issues
* Fixed being able to change seats while dead or cuffed
* Added more Meteo convar support. check new meteo.cfg
```cfg
setr meteo:cryptoname, setr meteo:cryptosymbol, setr meteo:walletprefix, setr meteo:terminalprompt, setr meteo:chat_automessages, setr meteo:chat_welcome
```

### Images

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_03.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_04.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_05.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_06.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_07.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_01.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_02.webp)

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteofivem.net_v2.10.0_09.webp)

### Modified Files

```diff
~ meteo-server\server-data\meteo.cfg

~ resources/[meteostudios]/meteo-apartments/shared/complexes/wiwang_hotel.lua

~ resources/[meteostudios]/meteo-appearance/client/cl_appearance.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_camera.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_nui.lua
~ resources/[meteostudios]/meteo-appearance/server/sv_main.lua
~ resources/[meteostudios]/meteo-appearance/web/*

~ resources/[meteostudios]/meteo-atmskimming/client/cl_main.lua
~ resources/[meteostudios]/meteo-atmskimming/fxmanifest.lua
~ resources/[meteostudios]/meteo-atmskimming/server/sv_logs.lua
~ resources/[meteostudios]/meteo-atmskimming/server/sv_main.lua
+ resources/[meteostudios]/meteo-atmskimming/server/sv_perks.lua

~ resources/[meteostudios]/meteo-bargehunt/server/sv_logs.lua
~ resources/[meteostudios]/meteo-bargehunt/shared/achievements.lua

~ resources/[meteostudios]/meteo-bennys/fxmanifest.lua
+ resources/[meteostudios]/meteo-bennys/server/sv_perks.lua

~ resources/[meteostudios]/meteo-boosting/fxmanifest.lua
~ resources/[meteostudios]/meteo-boosting/server/sv_logs.lua
~ resources/[meteostudios]/meteo-boosting/server/sv_main.lua
+ resources/[meteostudios]/meteo-boosting/server/sv_perks.lua
~ resources/[meteostudios]/meteo-boosting/shared/achievements.lua

~ resources/[meteostudios]/meteo-buffs/fxmanifest.lua
+ resources/[meteostudios]/meteo-buffs/server/sv_perks.lua

~ resources/[meteostudios]/meteo-chat/shared/config.lua

~ resources/[meteostudios]/meteo-chopshop/client/cl_main.lua
~ resources/[meteostudios]/meteo-chopshop/locales/*
~ resources/[meteostudios]/meteo-chopshop/server/source/sv_functions.lua
~ resources/[meteostudios]/meteo-chopshop/server/sv_main.lua
+ resources/[meteostudios]/meteo-chopshop/server/sv_perks.lua

~ resources/[meteostudios]/meteo-craftingtables/fxmanifest.lua
+ resources/[meteostudios]/meteo-craftingtables/server/sv_perks.lua

~ resources/[meteostudios]/meteo-crimetablet/client/cl_main.lua
+ resources/[meteostudios]/meteo-crimetablet/client/cl_racing.lua
~ resources/[meteostudios]/meteo-crimetablet/fxmanifest.lua
~ resources/[meteostudios]/meteo-crimetablet/locales/*
~ resources/[meteostudios]/meteo-crimetablet/server/sv_blackmarket.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_functions.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_main.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_organizations.lua
+ resources/[meteostudios]/meteo-crimetablet/server/sv_racing.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_services.lua
~ resources/[meteostudios]/meteo-crimetablet/shared/apps.lua
~ resources/[meteostudios]/meteo-crimetablet/shared/config.lua
~ resources/[meteostudios]/meteo-crimetablet/web/*

~ resources/[meteostudios]/meteo-customapp-finance/fxmanifest.lua

+ resources/[meteostudios]/meteo-dailyrewards/server/sv_perks.lua

~ resources/[meteostudios]/meteo-dealerships/client/cl_main.lua
~ resources/[meteostudios]/meteo-dealerships/client/cl_targets.lua
~ resources/[meteostudios]/meteo-dealerships/locales/*
~ resources/[meteostudios]/meteo-dealerships/server/sv_admin.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_main.lua
~ resources/[meteostudios]/meteo-dealerships/shared/config.lua
~ resources/[meteostudios]/meteo-dealerships/web/*

~ resources/[meteostudios]/meteo-drugs/fxmanifest.lua
+ resources/[meteostudios]/meteo-drugs/server/sv_perks.lua

~ resources/[meteostudios]/meteo-drugselling/fxmanifest.lua
~ resources/[meteostudios]/meteo-drugselling/server/sv_main.lua
+ resources/[meteostudios]/meteo-drugselling/server/sv_perks.lua

~ resources/[meteostudios]/meteo-dumpstersearch/fxmanifest.lua
+ resources/[meteostudios]/meteo-dumpstersearch/server/sv_perks.lua

~ resources/[meteostudios]/meteo-foresthunt/server/sv_logs.lua
~ resources/[meteostudios]/meteo-foresthunt/shared/achievements.lua

~ resources/[meteostudios]/meteo-fuelv2/client/cl_main.lua

~ resources/[meteostudios]/meteo-furnishing/client/cl_main.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_nui.lua
~ resources/[meteostudios]/meteo-furnishing/locales/*
~ resources/[meteostudios]/meteo-furnishing/server/sv_main.lua
~ resources/[meteostudios]/meteo-furnishing/shared/config.lua
~ resources/[meteostudios]/meteo-furnishing/web/*

~ resources/[meteostudios]/meteo-gym/server/sv_main.lua
~ resources/[meteostudios]/meteo-gym/server/sv_stats.lua
~ resources/[meteostudios]/meteo-gym/web/*

~ resources/[meteostudios]/meteo-hsd/fxmanifest.lua
~ resources/[meteostudios]/meteo-hsd/server/sv_logs.lua
+ resources/[meteostudios]/meteo-hsd/server/sv_perks.lua
~ resources/[meteostudios]/meteo-hsd/shared/achievements.lua

~ resources/[meteostudios]/meteo-jail/client/cl_jobs.lua
~ resources/[meteostudios]/meteo-jail/client/cl_main.lua
~ resources/[meteostudios]/meteo-jail/client/cl_mugshot.lua
~ resources/[meteostudios]/meteo-jail/client/cl_zone.lua
~ resources/[meteostudios]/meteo-jail/locales/*
~ resources/[meteostudios]/meteo-jail/server/sv_escape.lua
~ resources/[meteostudios]/meteo-jail/server/sv_main.lua
~ resources/[meteostudios]/meteo-jail/shared/config.lua

~ resources/[meteostudios]/meteo-loosechange/fxmanifest.lua
~ resources/[meteostudios]/meteo-loosechange/server/sv_logs.lua
+ resources/[meteostudios]/meteo-loosechange/server/sv_perks.lua
~ resources/[meteostudios]/meteo-loosechange/shared/achievements.lua

+ resources/[meteostudios]/meteo-luckywheel/server/sv_perks.lua

~ resources/[meteostudios]/meteo-medicaljob/client/cl_checking.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_nui.lua
+ resources/[meteostudios]/meteo-medicaljob/server/sv_perks.lua
~ resources/[meteostudios]/meteo-medicaljob/web/*

~ resources/[meteostudios]/meteo-misc/client/equipment.lua
~ resources/[meteostudios]/meteo-misc/client/meditate.lua
~ resources/[meteostudios]/meteo-misc/client/noshuff.lua
+ resources/[meteostudios]/meteo-misc/client/trunk.lua
~ resources/[meteostudios]/meteo-misc/fxmanifest.lua
~ resources/[meteostudios]/meteo-misc/locales/*
+ resources\[meteostudios]\meteo-misc\server\trunk.lua
~ resources/[meteostudios]/meteo-misc/shared/config.lua

~ resources/[meteostudios]/meteo-multichar/client/cl_dui.lua
~ resources/[meteostudios]/meteo-multichar/client/cl_main.lua
~ resources/[meteostudios]/meteo-multichar/server/sv_spawn.lua

~ resources/[meteostudios]/meteo-organizations/server/sv_logs.lua
~ resources/[meteostudios]/meteo-organizations/server/sv_main.lua
~ resources/[meteostudios]/meteo-organizations/shared/config.lua

~ resources/[meteostudios]/meteo-pawnshop/fxmanifest.lua
+ resources/[meteostudios]/meteo-pawnshop/server/sv_perks.lua

~ resources/[meteostudios]/meteo-perks/client/cl_main.lua
~ resources/[meteostudios]/meteo-perks/fxmanifest.lua
+ resources/[meteostudios]/meteo-perks/server/sv_config.lua
+ resources/[meteostudios]/meteo-perks/server/sv_editor.lua
~ resources/[meteostudios]/meteo-perks/server/sv_functions.lua
~ resources/[meteostudios]/meteo-perks/server/sv_main.lua
+ resources/[meteostudios]/meteo-perks/server/sv_permissions.lua
+ resources/[meteostudios]/meteo-perks/server/sv_registry.lua
~ resources/[meteostudios]/meteo-perks/shared/perks.lua
~ resources/[meteostudios]/meteo-perks/web/*

~ resources/[meteostudios]/meteo-phone/client/apps/cl_bank.lua
~ resources/[meteostudios]/meteo-phone/client/apps/cl_notes.lua
~ resources/[meteostudios]/meteo-phone/client/other/cl_locale.lua
~ resources/[meteostudios]/meteo-phone/locales/*
~ resources/[meteostudios]/meteo-phone/server/apps/sv_bank.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_notes.lua
~ resources/[meteostudios]/meteo-phone/server/sv_logs.lua
~ resources/[meteostudios]/meteo-phone/server/sv_main.lua
~ resources/[meteostudios]/meteo-phone/stream/*
~ resources/[meteostudios]/meteo-phone/web/*

+ resources/[meteostudios]/meteo-pickpocket/server/sv_perks.lua

~ resources/[meteostudios]/meteo-policejob/client/cl_escort.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_main.lua
~ resources/[meteostudios]/meteo-policejob/locales/*
~ resources/[meteostudios]/meteo-policejob/server/sv_main.lua

+ resources/[meteostudios]/meteo-properties/server/sv_perks.lua

+ resources/[meteostudios]/meteo-racing/

~ resources/[meteostudios]/meteo-restaurants/client/cl_cooking.lua
~ resources/[meteostudios]/meteo-restaurants/client/cl_main.lua
~ resources/[meteostudios]/meteo-restaurants/fxmanifest.lua
~ resources/[meteostudios]/meteo-restaurants/locales/*
+ resources/[meteostudios]/meteo-restaurants/server/sv_perks.lua
~ resources/[meteostudios]/meteo-restaurants/shared/config.lua

~ resources/[meteostudios]/meteo-rewards/fxmanifest.lua
+ resources/[meteostudios]/meteo-rewards/server/sv_perks.lua

+ resources/[meteostudios]/meteo-roulette/server/sv_perks.lua

~ resources/[meteostudios]/meteo-seahunt/fxmanifest.lua
~ resources/[meteostudios]/meteo-seahunt/server/sv_logs.lua
+ resources/[meteostudios]/meteo-seahunt/server/sv_perks.lua
~ resources/[meteostudios]/meteo-seahunt/shared/achievements.lua

+ resources/[meteostudios]/meteo-searchvehicles/server/sv_perks.lua

~ resources/[meteostudios]/meteo-shops/fxmanifest.lua
+ resources/[meteostudios]/meteo-shops/server/sv_perks.lua
~ resources/[meteostudios]/meteo-shops/shared/config.lua

~ resources/[meteostudios]/meteo-transporthunt/fxmanifest.lua
~ resources/[meteostudios]/meteo-transporthunt/server/sv_logs.lua
+ resources/[meteostudios]/meteo-transporthunt/server/sv_perks.lua
~ resources/[meteostudios]/meteo-transporthunt/shared/achievements.lua

~ resources/[meteostudios]/meteo-vaultjob/fxmanifest.lua
~ resources/[meteostudios]/meteo-vaultjob/server/sv_logs.lua
+ resources/[meteostudios]/meteo-vaultjob/server/sv_perks.lua
~ resources/[meteostudios]/meteo-vaultjob/shared/achievements.lua

~ resources/[meteostudios]/meteo-weaponback/client/cl_main.lua

~ resources/[meteostudios]/meteo-weaponrepair/fxmanifest.lua
+ resources/[meteostudios]/meteo-weaponrepair/server/sv_perks.lua

~ resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua

~ resources/[ox]/ox_target/client/main.lua

~ resources/[qb]/meteo-core/bridge/qb/client/functions.lua

~ resources/[qb]/meteo-radialmenu//*

~ resources/[standalone]/sirens/client.lua
```

### Database update

```sql
CREATE TABLE IF NOT EXISTS `meteo_phone_bills` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `creator_citizenid` VARCHAR(50) NOT NULL,
    `creator_name` VARCHAR(255) NOT NULL,
    `creator_account_id` INT(11) NOT NULL,
    `creator_account_number` VARCHAR(50) DEFAULT NULL,
    `creator_account_name` VARCHAR(255) DEFAULT NULL,
    `recipient_citizenid` VARCHAR(50) NOT NULL,
    `recipient_name` VARCHAR(255) NOT NULL,
    `amount` INT(11) NOT NULL,
    `reason` VARCHAR(255) NOT NULL,
    `status` VARCHAR(20) NOT NULL DEFAULT 'pending',
    `paid_account_id` INT(11) DEFAULT NULL,
    `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP,
    `paid_at` DATETIME DEFAULT NULL,
    PRIMARY KEY (`id`),
    INDEX `creator_citizenid` (`creator_citizenid`),
    INDEX `recipient_citizenid` (`recipient_citizenid`),
    INDEX `status` (`status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `meteo_phone_note_shares` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `note_id` INT(11) NOT NULL,
    `owner_serial` VARCHAR(50) NOT NULL,
    `shared_by_name` VARCHAR(100) DEFAULT NULL,
    `shared_with_citizenid` VARCHAR(50) NOT NULL,
    `shared_with_name` VARCHAR(100) DEFAULT NULL,
    `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    UNIQUE KEY `note_recipient` (`note_id`, `shared_with_citizenid`),
    INDEX `shared_with_citizenid` (`shared_with_citizenid`),
    INDEX `note_id` (`note_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

***
## 2.9.0

### Changes

* New whiteboard added
* New lean drug added
* New inventory combine items support
* Added durability support for lockpicks and screwdrivers
* Added custom job support for Job Tablet - [Repo](https://github.com/MeteoStudios/meteo-tablet-customjobs-demo)
* Added config to remove realestate from property creator
* Major permissions system update. You can now create groups and configure permissions. Refer to the [docs](https://docs.meteofivem.net/servers/meteo-fivem-server/documentation/how-to/how-to-script-permissions)
* Added Renewed-Banking exports support
* New admin menu prop placement tools added to developer tools
* Improved job garage previews for slower systems
* Improvements to plant placement
* Improved lucky wheel dui loading
* Improved Meteo Phone UI and fixed screen getting stuck
* Improved overall permissions handling and configuration flow
* Attempted to fix weird siren issue
* Fixed major daily rewards collecting exploit
* Fixed taxi job ped scenarios sometimes getting stuck
* Fixed `cb_datamine` perk not giving extra items
* Fixed Q and E keys while inventory is open

### Images
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.9.0_02.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.9.0_01.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.9.0_03.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteo-jobtablet_02.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteo-jobtablet_01.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_meteo-jobtablet_03.png)

### Modified Files

```diff
+ meteo-server/server-data/resources/[meteostudios]/meteo-whiteboard/
~ resources/[meteostudios]/meteo-adminmenu/client/cl_devtools.lua
+ resources/[meteostudios]/meteo-adminmenu/client/cl_propplacer.lua
~ resources/[meteostudios]/meteo-adminmenu/locales/*
~ resources/[meteostudios]/meteo-adminmenu/server/sv_admintools.lua
~ resources/[meteostudios]/meteo-adminmenu/server/sv_functions.lua
+ resources/[meteostudios]/meteo-adminmenu/server/sv_permissions.lua
+ resources/[meteostudios]/meteo-adminmenu/server/sv_propplacer.lua
~ resources/[meteostudios]/meteo-adminmenu/shared/config.lua
~ resources/[meteostudios]/meteo-adminmenu/web/*
~ resources/[meteostudios]/meteo-atmskimming/server/sv_main.lua
~ resources/[meteostudios]/meteo-banking/server/sv_main.lua
~ resources/[meteostudios]/meteo-bennys/server/sv_functions.lua
+ resources/[meteostudios]/meteo-bennys/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-bossmenuv2/client/cl_main.lua
~ resources/[meteostudios]/meteo-chopshop/server/source/sv_functions.lua
~ resources/[meteostudios]/meteo-cityhallv2/server/sv_main.lua
+ resources/[meteostudios]/meteo-cityhallv2/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-craftingtables/server/sv_main.lua
+ resources/[meteostudios]/meteo-craftingtables/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_files.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_organizations.lua
+ resources/[meteostudios]/meteo-crimetablet/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-dailyrewards/locales/*
~ resources/[meteostudios]/meteo-dailyrewards/server/sv_main.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_main.lua
+ resources/[meteostudios]/meteo-dealerships/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-drugs/client/cl_coca.lua
~ resources/[meteostudios]/meteo-drugs/client/cl_main.lua
~ resources/[meteostudios]/meteo-drugs/client/cl_weed.lua
~ resources/[meteostudios]/meteo-drugs/locales/*
~ resources/[meteostudios]/meteo-drugs/shared/coca.lua
~ resources/[meteostudios]/meteo-drugs/shared/weed.lua
~ resources/[meteostudios]/meteo-drugselling/shared/config.lua
~ resources/[meteostudios]/meteo-dumpstersearch/shared/config.lua
~ resources/[meteostudios]/meteo-inventory/client.lua
+ resources/[meteostudios]/meteo-inventory/data/combine.lua
~ resources/[meteostudios]/meteo-inventory/data/items.lua
~ resources/[meteostudios]/meteo-inventory/data/rarity.lua
~ resources/[meteostudios]/meteo-inventory/locales/*
~ resources/[meteostudios]/meteo-inventory/server.lua
~ resources/[meteostudios]/meteo-inventory/web/*
~ resources/[meteostudios]/meteo-jobgarage/client/cl_main.lua
~ resources/[meteostudios]/meteo-luckywheel/client/cl_main.lua
~ resources/[meteostudios]/meteo-mailboxrob/server/sv_main.lua
~ resources/[meteostudios]/meteo-mailboxrob/shared/config.lua
~ resources/[meteostudios]/meteo-misc/client/consumables.lua
~ resources/[meteostudios]/meteo-misc/server/afk.lua
+ resources/[meteostudios]/meteo-misc/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-misc/shared/items.lua
~ resources/[meteostudios]/meteo-multichar/server/sv_functions.lua
~ resources/[meteostudios]/meteo-multichar/server/sv_main.lua
+ resources/[meteostudios]/meteo-multichar/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-phone/client/apps/cl_customapps.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_music.lua
~ resources/[meteostudios]/meteo-phone/server/source/sv_functions.lua
+ resources/[meteostudios]/meteo-phone/server/source/sv_permissions.lua
~ resources/[meteostudios]/meteo-phone/web/*
~ resources/[meteostudios]/meteo-properties/server/sv_creator.lua
~ resources/[meteostudios]/meteo-properties/server/sv_main.lua
+ resources/[meteostudios]/meteo-properties/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-properties/shared/config.lua
~ resources/[meteostudios]/meteo-reports/server/sv_functions.lua
+ resources/[meteostudios]/meteo-reports/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_functions.lua
+ resources/[meteostudios]/meteo-restaurants/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-scenes/server/sv_main.lua
+ resources/[meteostudios]/meteo-scenes/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-searchvehicles/client/cl_main.lua
~ resources/[meteostudios]/meteo-searchvehicles/server/sv_main.lua
~ resources/[meteostudios]/meteo-searchvehicles/shared/config.lua
~ resources/[meteostudios]/meteo-shops/shared/config.lua
~ resources/[meteostudios]/meteo-speakers/server/sv_main.lua
+ resources/[meteostudios]/meteo-speakers/server/sv_permissions.lua
~ resources/[meteostudios]/meteo-weaponback/client/cl_main.lua
~ resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua

~ resources/[meteostudios]/meteo-jobtablet/*
~ resources/[meteostudios]/meteo-transitjob/*
~ resources/[meteostudios]/meteo-fishingjob/*
~ resources/[meteostudios]/meteo-gopostaljob/*
~ resources/[meteostudios]/meteo-electricianjob/*
~ resources/[meteostudios]/meteo-cleaningjob/*
~ resources/[meteostudios]/meteo-taxijob/*
~ resources/[meteostudios]/meteo-transitjob/*
~ resources/[meteostudios]/meteo-repojob/*

~ resources/[qb]/meteo-smallresources/config.lua
~ resources/[qb]/meteo-smallresources/server/consumables.lua
~ resources/[qb]/meteo-vehiclekeys/client/functions.lua
~ resources/[qb]/meteo-vehiclekeys/client/main.lua
~ resources/[qb]/meteo-vehiclekeys/config/server.lua
~ resources/[qb]/meteo-vehiclekeys/locales/*
~ resources/[qb]/meteo-vehiclekeys/server/main.lua
~ resources/[standalone]/sirens/client.lua
~ resources/[standalone]/sirens/server.lua

~ resources/[meteostudios]/meteo-adminmenu\fxmanifest.lua
~ resources/[meteostudios]/meteo-bennys\fxmanifest.lua
~ resources/[meteostudios]/meteo-cityhallv2\fxmanifest.lua
~ resources/[meteostudios]/meteo-crimetablet\fxmanifest.lua
~ resources/[meteostudios]/meteo-craftingtables\fxmanifest.lua
~ resources/[meteostudios]/meteo-dealerships\fxmanifest.lua
~ resources/[meteostudios]/meteo-scenes\fxmanifest.lua
~ resources/[meteostudios]/meteo-properties\fxmanifest.lua
~ resources/[meteostudios]/meteo-jobtablet\fxmanifest.lua
~ resources/[meteostudios]/meteo-reports\fxmanifest.lua
~ resources/[meteostudios]/meteo-restaurants\fxmanifest.lua
~ resources/[meteostudios]/meteo-speakers\fxmanifest.lua
~ resources/[meteostudios]/meteo-misc\fxmanifest.lua
~ resources/[meteostudios]/meteo-multichar\fxmanifest.lua
```

***
## 2.8.0

### Changes

{% hint style="warning" %}
**Important:** This is a major update. Make sure to update everything and do not miss any changes.
{% endhint %}

* Major optimization improvements for civilian jobs
* Added support for custom Crime Tablet services and heists - https://github.com/MeteoStudios/meteo-crimesservice-demo
* Improved civilian jobs to better handle larger player counts
* Improved dispatch handling for larger data
* Improved vehicle spawning
* Improved dealership vehicle spawning
* Fixed search dumpsters showing twice
* Fixed fishing shop item limitations
* Fixed meditation issues
* Fixed admin menu revive
* Fixed admin menu item searching
* Fixed inmates not respawning inside prison hospital
* Fixed Sea Hunt progressbar issues
* Fixed syncing issues with electrician job boxes
* Fixed medicaljob state bag issues
* Medical job blip issues fixed
* Major medical job improvements
* Medical job dead/knock improvements with major in-water fixes
* New EMS notification flow when players go down. EMS can now notify and message players through dispatch
* Improved police job search animations
* Escort keybind is now available for all players, not only police
* Fixed clothing item duplication from drag-triggered appearance sync
* Fixed clothing default issues with multichar and appearance
* Fixed appearance ped skin issues
* Improved appearance camera
* Multichar now supports disabling starting apartments
* Apartments and properties now support storage limits and upgrades
* Mechanic job multi-job support added
* Mechanic tablet UI tweaks
* Major phone improvements
* Phone speaker improvements with nearby player hearing support for ringing phones
* Improved phone ownership checking
* Fixed phone companies app member section scrollbar styling
* Improved phone camera with zoom support and phone screen capture
* Crime Tablet wallet prefix config support
* Players can no longer create groups while on active Crime Tablet services
* Added config to disable NPC pickpocket guns
* Added remove give cash option when money as item is enabled
* Improved stash furniture lockpick
* Improved pickpocket notifications
* Drug selling improvements with NPC stealing, animations and counter offers
* Restaurants item usage improvements
* Improved meteo-buffs display
* Inventory improvements including other player utility slots and item notifications
* Added config for terminal name updates
* Added config for vehicle keys. NPCs can now fight back when attacking their vehicles
* Added config to disable addictions and stress
* Added vehicle rental image support
* Improved doorlock sounds for restaurants, apartments and properties
* Added gym animation position support to prevent players moving outside equipment
* Fixed casino lucky wheel notifications
* Hunts item labels fixed
* Improved hunt item notifications
* Report menu overhaul
* Updated ox_lib

### Images

![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.8.0_03.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.8.0_04.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.8.0_05.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.8.0_02.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.8.0_01.png)
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.8.0_06.png)

### Modified Files

```diff
- resources/[meteostudios]/meteo-reportmenuv2
+ meteo-server/server-data/resources/[meteostudios]/meteo-reports/
~ resources/[meteostudios]/meteo-adminmenu/server/sv_functions.lua
~ resources/[meteostudios]/meteo-adminmenu/web/*
~ resources/[meteostudios]/meteo-apartments/client/main/cl_nui.lua
~ resources/[meteostudios]/meteo-apartments/client/main/cl_zones.lua
~ resources/[meteostudios]/meteo-apartments/locales/*
~ resources/[meteostudios]/meteo-apartments/server/main/sv_callbacks.lua
~ resources/[meteostudios]/meteo-apartments/server/main/sv_exports.lua
~ resources/[meteostudios]/meteo-apartments/server/sv_logs.lua
~ resources/[meteostudios]/meteo-apartments/server/sv_main.lua
~ resources/[meteostudios]/meteo-apartments/shared/config.lua
~ resources/[meteostudios]/meteo-apartments/web/*
~ resources/[meteostudios]/meteo-appearance/client/cl_appearance.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_camera.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_main.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_nui.lua
~ resources/[meteostudios]/meteo-appearance/shared/config.lua
~ resources/[meteostudios]/meteo-appearance/shared/constants.lua
~ resources/[meteostudios]/meteo-appearance/web/*
~ resources/[meteostudios]/meteo-arrowtiming/web/*
~ resources/[meteostudios]/meteo-banking/client/cl_main.lua
~ resources/[meteostudios]/meteo-bargehunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-bargehunt/server/sv_main.lua
~ resources/[meteostudios]/meteo-bargehunt/shared/utils.lua
~ resources/[meteostudios]/meteo-bennys/server/sv_functions.lua
~ resources/[meteostudios]/meteo-bennys/server/sv_main.lua
~ resources/[meteostudios]/meteo-bennys/shared/config.lua
~ resources/[meteostudios]/meteo-boosting/client/cl_main.lua
~ resources/[meteostudios]/meteo-boosting/server/sv_logs.lua
~ resources/[meteostudios]/meteo-boosting/server/sv_main.lua
~ resources/[meteostudios]/meteo-boosting/shared/config.lua
~ resources/[meteostudios]/meteo-bossmenuv2/server/sv_main.lua
~ resources/[meteostudios]/meteo-buffs/client/cl_food.lua
~ resources/[meteostudios]/meteo-buffs/client/cl_status.lua
~ resources/[meteostudios]/meteo-buffs/client/cl_substances.lua
~ resources/[meteostudios]/meteo-buffs/shared/config.lua
~ resources/[meteostudios]/meteo-cleaningjob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-cleaningjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-cleaningjob/client/cl_minigame.lua
~ resources/[meteostudios]/meteo-cleaningjob/client/cl_vehicle.lua
~ resources/[meteostudios]/meteo-cleaningjob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-cleaningjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-cleaningjob/server/sv_vehicle.lua
~ resources/[meteostudios]/meteo-cleaningjob/shared/config.lua
~ resources/[meteostudios]/meteo-crimetablet/client/cl_main.lua
~ resources/[meteostudios]/meteo-crimetablet/client/cl_services.lua
~ resources/[meteostudios]/meteo-crimetablet/locales/*
~ resources/[meteostudios]/meteo-crimetablet/server/sv_crypto.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_groups.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_main.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_organizations.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_services.lua
~ resources/[meteostudios]/meteo-crimetablet/shared/config.lua
~ resources/[meteostudios]/meteo-crimetablet/web/*
~ resources/[meteostudios]/meteo-dealerships/client/cl_camera.lua
~ resources/[meteostudios]/meteo-dealerships/client/cl_main.lua
~ resources/[meteostudios]/meteo-dealerships/client/cl_showroom.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_finance.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_functions.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_shop.lua
~ resources/[meteostudios]/meteo-dispatch/client/cl_locale.lua
~ resources/[meteostudios]/meteo-dispatch/client/cl_nui.lua
~ resources/[meteostudios]/meteo-dispatch/locales/*
~ resources/[meteostudios]/meteo-dispatch/server/sv_calls.lua
~ resources/[meteostudios]/meteo-dispatch/server/sv_chat.lua
~ resources/[meteostudios]/meteo-dispatch/server/sv_database.lua
~ resources/[meteostudios]/meteo-dispatch/server/sv_main.lua
~ resources/[meteostudios]/meteo-dispatch/shared/config.lua
~ resources/[meteostudios]/meteo-dispatch/web/*
~ resources/[meteostudios]/meteo-drugselling/client/cl_main.lua
~ resources/[meteostudios]/meteo-drugselling/locales/*
~ resources/[meteostudios]/meteo-drugselling/server/sv_main.lua
~ resources/[meteostudios]/meteo-drugselling/shared/config.lua
~ resources/[meteostudios]/meteo-drugselling/web/*
~ resources/[meteostudios]/meteo-electricianjob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-electricianjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-electricianjob/client/cl_repairs.lua
~ resources/[meteostudios]/meteo-electricianjob/client/cl_vehicle.lua
~ resources/[meteostudios]/meteo-electricianjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-electricianjob/server/sv_vehicle.lua
~ resources/[meteostudios]/meteo-electricianjob/shared/config.lua
~ resources/[meteostudios]/meteo-fishingjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-foresthunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-foresthunt/server/sv_main.lua
~ resources/[meteostudios]/meteo-foresthunt/shared/utils.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_main.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_nui.lua
~ resources/[meteostudios]/meteo-furnishing/locales/*
~ resources/[meteostudios]/meteo-furnishing/server/sv_main.lua
~ resources/[meteostudios]/meteo-fuseboxfix/client/client.lua
~ resources/[meteostudios]/meteo-garages/client/cl_main.lua
~ resources/[meteostudios]/meteo-garages/server/sv_functions.lua
~ resources/[meteostudios]/meteo-garages/server/sv_main.lua
~ resources/[meteostudios]/meteo-gopostaljob/client/cl_delivery.lua
~ resources/[meteostudios]/meteo-gopostaljob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-gopostaljob/client/cl_main.lua
~ resources/[meteostudios]/meteo-gopostaljob/client/cl_packages.lua
~ resources/[meteostudios]/meteo-gopostaljob/locales/*
~ resources/[meteostudios]/meteo-gopostaljob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-gopostaljob/server/sv_main.lua
~ resources/[meteostudios]/meteo-gopostaljob/server/sv_vehicle.lua
~ resources/[meteostudios]/meteo-gopostaljob/shared/config.lua
+ resources/[meteostudios]/meteo-gym/client/cl_dev.lua
~ resources/[meteostudios]/meteo-gym/client/cl_main.lua
~ resources/[meteostudios]/meteo-gym/locales/*
+ resources/[meteostudios]/meteo-gym/server/sv_occupancy.lua
~ resources/[meteostudios]/meteo-gym/shared/config.lua
~ resources/[meteostudios]/meteo-gym/web/*
~ resources/[meteostudios]/meteo-hsd/client/cl_main.lua
~ resources/[meteostudios]/meteo-hsd/server/sv_main.lua
~ resources/[meteostudios]/meteo-hud/client/cl_main.lua
~ resources/[meteostudios]/meteo-hud/web/*
~ resources/[meteostudios]/meteo-inventory/modules/clothing/server.lua
~ resources/[meteostudios]/meteo-inventory/modules/inventory/client.lua
~ resources/[meteostudios]/meteo-inventory/modules/inventory/server.lua
~ resources/[meteostudios]/meteo-inventory/web/*
~ resources/[meteostudios]/meteo-jail/server/sv_main.lua
~ resources/[meteostudios]/meteo-jobgarage/client/cl_main.lua
~ resources/[meteostudios]/meteo-jobgarage/server/sv_main.lua
~ resources/[meteostudios]/meteo-loosechange/client/cl_main.lua
~ resources/[meteostudios]/meteo-loosechange/server/sv_main.lua
~ resources/[meteostudios]/meteo-luckywheel/server/sv_main.lua
~ resources/[meteostudios]/meteo-mechanicjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-mechanicjob/locales/*
~ resources/[meteostudios]/meteo-mechanicjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-mechanicjob/server/sv_notifications.lua
~ resources/[meteostudios]/meteo-mechanicjob/shared/config.lua
~ resources/[meteostudios]/meteo-mechanicjob/web/*
~ resources/[meteostudios]/meteo-medicaljob/client/cl_checking.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_hospital.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_injuries.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_main.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_nui.lua
~ resources/[meteostudios]/meteo-medicaljob/locales/*
~ resources/[meteostudios]/meteo-medicaljob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_injuries.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_main.lua
~ resources/[meteostudios]/meteo-medicaljob/shared/config.lua
~ resources/[meteostudios]/meteo-medicaljob/web/*
~ resources/[meteostudios]/meteo-misc/client/meditate.lua
- resources/[meteostudios]/meteo-misc/server/meditate.lua
~ resources/[meteostudios]/meteo-misc/shared/config.lua
~ resources/[meteostudios]/meteo-multichar/client/cl_main.lua
~ resources/[meteostudios]/meteo-multichar/server/sv_main.lua
~ resources/[meteostudios]/meteo-multichar/shared/config.lua
~ resources/[meteostudios]/meteo-phone/client/apps/cl_camera.lua
~ resources/[meteostudios]/meteo-phone/client/apps/cl_phone.lua
~ resources/[meteostudios]/meteo-phone/client/cl_main.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_phone.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_shop.lua
~ resources/[meteostudios]/meteo-phone/shared/config.lua
~ resources/[meteostudios]/meteo-phone/web/*
~ resources/[meteostudios]/meteo-pickpocket/client/cl_main.lua
~ resources/[meteostudios]/meteo-pickpocket/locales/*
~ resources/[meteostudios]/meteo-pickpocket/shared/config.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_escort.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_main.lua
~ resources/[meteostudios]/meteo-policejob/locales/*
~ resources/[meteostudios]/meteo-policejob/server/sv_main.lua
+ resources/[meteostudios]/meteo-policejob/stream/*
~ resources/[meteostudios]/meteo-properties/client/cl_mlo.lua
~ resources/[meteostudios]/meteo-properties/client/cl_nui.lua
~ resources/[meteostudios]/meteo-properties/locales/*
~ resources/[meteostudios]/meteo-properties/server/sv_callbacks.lua
~ resources/[meteostudios]/meteo-properties/server/sv_exports.lua
~ resources/[meteostudios]/meteo-properties/server/sv_logs.lua
~ resources/[meteostudios]/meteo-properties/server/sv_main.lua
~ resources/[meteostudios]/meteo-properties/shared/config.lua
~ resources/[meteostudios]/meteo-properties/web/*
~ resources/[meteostudios]/meteo-repojob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-repojob/client/cl_main.lua
~ resources/[meteostudios]/meteo-repojob/client/cl_vehicle.lua
~ resources/[meteostudios]/meteo-repojob/server/sv_main.lua
~ resources/[meteostudios]/meteo-repojob/server/sv_vehicle.lua
~ resources/[meteostudios]/meteo-repojob/shared/config.lua
~ resources/[meteostudios]/meteo-restaurants/client/cl_doors.lua
~ resources/[meteostudios]/meteo-restaurants/client/cl_items.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_functions.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_items.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_storage.lua
~ resources/[meteostudios]/meteo-restaurants/shared/config.lua
~ resources/[meteostudios]/meteo-seahunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-seahunt/server/sv_main.lua
~ resources/[meteostudios]/meteo-seahunt/shared/utils.lua
~ resources/[meteostudios]/meteo-taxijob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-taxijob/client/cl_main.lua
~ resources/[meteostudios]/meteo-taxijob/locales/*
~ resources/[meteostudios]/meteo-taxijob/server/sv_main.lua
~ resources/[meteostudios]/meteo-taxijob/server/sv_vehicle.lua
~ resources/[meteostudios]/meteo-taxijob/shared/config.lua
~ resources/[meteostudios]/meteo-transitjob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-transitjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-transitjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-transitjob/server/sv_vehicle.lua
~ resources/[meteostudios]/meteo-transitjob/shared/config.lua
~ resources/[meteostudios]/meteo-transporthunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-transporthunt/server/sv_main.lua
~ resources/[meteostudios]/meteo-transporthunt/shared/utils.lua
~ resources/[meteostudios]/meteo-vaultjob/client/cl_guards.lua
~ resources/[meteostudios]/meteo-vaultjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-vaultjob/client/cl_trolleys.lua
~ resources/[meteostudios]/meteo-vaultjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-vaultjob/shared/utils.lua
~ resources/[meteostudios]/meteo-vehiclerental/client/cl_main.lua
~ resources/[meteostudios]/meteo-vehiclerental/server/sv_functions.lua
~ resources/[meteostudios]/meteo-vehiclerental/shared/config.lua
~ resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua
~ resources/[ox]/ox_lib
+ resources/[qb]/meteo-vehiclekeys
```

### Database Changes

```sql
ALTER TABLE `meteo_phone_sim_ownership` ADD INDEX `citizenid` (`citizenid`);
```

***

## 2.7.0

### Changes

{% hint style="warning" %}
**Important:** A full reinstall with the database is recommended. If you have a lot of player data you can try updating instead, but you MUST take a full backup (including the database) before doing this.
{% endhint %}

* Fully migrated to qbx and ox_inventory
* Stage bag restrict mode updated to match latest ox security standards
* Updated ox_lib (security update)
* Added model timeout support for multichar to help prevent loading issues on slower HDDs
* Fixed apartment selector not allowing access to the second apartment complex
* Updated apartment spawn selector UI for higher resolution screens
* Added `/seat` and `/window` chat commands
* Expanded resource renaming support
* Notification improvements
* Improved server version checking
* Organization invitations now require confirmation instead of instantly adding players
* Fixed music account mismatch issues
* Improvements to the phone Bleeter feed
* Fixed admin menu player ID limitations
* Admin menu logo now supports `meteo:logo` convar
* Overall improvements to targets and inventory

### Update guide

* First replace, add, and remove all changes below. After that, you can install your third party scripts if you have any. Make sure to update inventory data/items and weapons if you have custom items. (make sure its ox inventory format. old format is wrong)
* Still do NOT start the server.
* Open HeidiSQL and export your current database.
* Then go to https://convert.meteofivem.net/ and upload your SQL file. Also upload inventory data/items and weapons only if you have custom items. Otherwise, just skip that part.
* Convert and download the new SQL.
* Drop your old database and import the new SQL with qbx compatible data. :)
* now clear server cache and start the server.

### Modified Files

```diff
- resources/[qb]/meteo-core (delete)
- resources/[qb]/qbx_vehiclekeys (delete)
- resources/[standalone]/progressbar (delete)

~ meteo-server/server-data/misc.cfg
~ meteo-server/server-data/ox.cfg
~ meteo-server/server-data/permissions.cfg
~ meteo-server/server-data/server.cfg
~ meteo-server/server-data/voice.cfg

~ resources/[meteostudios]/meteo-adminmenu/client/cl_main.lua
~ resources/[meteostudios]/meteo-adminmenu/server/sv_admintools.lua
~ resources/[meteostudios]/meteo-adminmenu/server/sv_controls.lua
~ resources/[meteostudios]/meteo-adminmenu/server/sv_functions.lua
~ resources/[meteostudios]/meteo-adminmenu/shared/config.lua
~ resources/[meteostudios]/meteo-adminmenu/web/*
~ resources/[meteostudios]/meteo-animations/client/cl_handsup.lua
~ resources/[meteostudios]/meteo-animations/client/cl_main.lua
~ resources/[meteostudios]/meteo-animations/server/sv_main.lua
~ resources/[meteostudios]/meteo-apartments/client/main/cl_garage.lua
~ resources/[meteostudios]/meteo-apartments/client/main/cl_npc.lua
~ resources/[meteostudios]/meteo-apartments/server/main/sv_doorlock.lua
~ resources/[meteostudios]/meteo-apartments/server/main/sv_exports.lua
~ resources/[meteostudios]/meteo-apartments/shared/config.lua
~ resources/[meteostudios]/meteo-apartments/shared/utils.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_appearance.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_job_outfits.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_nui.lua
~ resources/[meteostudios]/meteo-appearance/client/cl_outfits.lua
~ resources/[meteostudios]/meteo-appearance/server/sv_database.lua
~ resources/[meteostudios]/meteo-appearance/server/sv_main.lua
~ resources/[meteostudios]/meteo-atmskimming/client/cl_main.lua
~ resources/[meteostudios]/meteo-atmskimming/server/sv_main.lua
~ resources/[meteostudios]/meteo-atmskimming/shared/utils.lua
~ resources/[meteostudios]/meteo-bargehunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-bargehunt/server/sv_functions.lua
~ resources/[meteostudios]/meteo-bargehunt/shared/utils.lua
~ resources/[meteostudios]/meteo-bennys/client/cl_main.lua
~ resources/[meteostudios]/meteo-bennys/server/sv_main.lua
~ resources/[meteostudios]/meteo-buffs/client/cl_performance.lua
~ resources/[meteostudios]/meteo-buffs/client/cl_status.lua
~ resources/[meteostudios]/meteo-buffs/client/cl_substances.lua
~ resources/[meteostudios]/meteo-buffs/server/sv_performance.lua
~ resources/[meteostudios]/meteo-buffs/server/sv_substances.lua
~ resources/[meteostudios]/meteo-buffs/shared/config.lua
~ resources/[meteostudios]/meteo-buffs/shared/utils.lua
~ resources/[meteostudios]/meteo-chat/shared/config.lua
~ resources/[meteostudios]/meteo-chat/web/*
~ resources/[meteostudios]/meteo-chopshop/client/cl_main.lua
~ resources/[meteostudios]/meteo-chopshop/server/source/sv_functions.lua
~ resources/[meteostudios]/meteo-chopshop/server/sv_main.lua
~ resources/[meteostudios]/meteo-chopshop/shared/config.lua
~ resources/[meteostudios]/meteo-chopshop/shared/utils.lua
~ resources/[meteostudios]/meteo-cityhallv2/client/cl_main.lua
~ resources/[meteostudios]/meteo-cityhallv2/server/sv_main.lua
~ resources/[meteostudios]/meteo-cityhallv2/shared/config.lua
~ resources/[meteostudios]/meteo-cityhallv2/shared/utils.lua
~ resources/[meteostudios]/meteo-cleaningjob/client/cl_cleaning.lua
~ resources/[meteostudios]/meteo-cleaningjob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-cleaningjob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-cleaningjob/shared/utils.lua
~ resources/[meteostudios]/meteo-craftingtables/client/cl_main.lua
~ resources/[meteostudios]/meteo-craftingtables/server/sv_main.lua
~ resources/[meteostudios]/meteo-craftingtables/shared/config.lua
~ resources/[meteostudios]/meteo-crimetablet/client/cl_blackmarket.lua
~ resources/[meteostudios]/meteo-crimetablet/client/cl_main.lua
~ resources/[meteostudios]/meteo-crimetablet/client/cl_organizations.lua
~ resources/[meteostudios]/meteo-crimetablet/client/cl_peds.lua
~ resources/[meteostudios]/meteo-crimetablet/locales/*
~ resources/[meteostudios]/meteo-crimetablet/server/sv_blackmarket.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_files.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_functions.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_main.lua
~ resources/[meteostudios]/meteo-crimetablet/server/sv_organizations.lua
~ resources/[meteostudios]/meteo-crimetablet/shared/config.lua
~ resources/[meteostudios]/meteo-crimetablet/shared/utils.lua
~ resources/[meteostudios]/meteo-crimetablet/web/*
~ resources/[meteostudios]/meteo-dailyrewards/client/cl_main.lua
~ resources/[meteostudios]/meteo-dailyrewards/server/sv_main.lua
~ resources/[meteostudios]/meteo-dailyrewards/shared/config.lua
~ resources/[meteostudios]/meteo-dailyrewards/shared/utils.lua
~ resources/[meteostudios]/meteo-drugs/client/cl_coca.lua
~ resources/[meteostudios]/meteo-drugs/client/cl_main.lua
~ resources/[meteostudios]/meteo-drugs/client/cl_weed.lua
~ resources/[meteostudios]/meteo-drugs/server/sv_coca.lua
~ resources/[meteostudios]/meteo-drugs/server/sv_main.lua
~ resources/[meteostudios]/meteo-drugs/server/sv_meth.lua
~ resources/[meteostudios]/meteo-drugs/server/sv_weed.lua
~ resources/[meteostudios]/meteo-drugs/shared/config.lua
~ resources/[meteostudios]/meteo-drugs/shared/utils.lua
~ resources/[meteostudios]/meteo-drugselling/client/cl_main.lua
~ resources/[meteostudios]/meteo-drugselling/client/cl_open.lua
~ resources/[meteostudios]/meteo-drugselling/server/sv_main.lua
~ resources/[meteostudios]/meteo-drugselling/shared/config.lua
~ resources/[meteostudios]/meteo-drugselling/shared/utils.lua
~ resources/[meteostudios]/meteo-dumpstersearch/client/cl_main.lua
~ resources/[meteostudios]/meteo-dumpstersearch/locales/*
~ resources/[meteostudios]/meteo-dumpstersearch/server/sv_main.lua
~ resources/[meteostudios]/meteo-dumpstersearch/shared/config.lua
~ resources/[meteostudios]/meteo-electricianjob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-electricianjob/client/cl_repairs.lua
~ resources/[meteostudios]/meteo-electricianjob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-electricianjob/shared/utils.lua
~ resources/[meteostudios]/meteo-evidence/client/cl_main.lua
~ resources/[meteostudios]/meteo-evidence/server/sv_main.lua
~ resources/[meteostudios]/meteo-evidence/shared/config.lua
~ resources/[meteostudios]/meteo-evidence/shared/utils.lua
~ resources/[meteostudios]/meteo-fishingjob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-fishingjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-fishingjob/shared/utils.lua
~ resources/[meteostudios]/meteo-foresthunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-foresthunt/server/sv_functions.lua
~ resources/[meteostudios]/meteo-foresthunt/shared/utils.lua
~ resources/[meteostudios]/meteo-fuelv2/client/cl_main.lua
~ resources/[meteostudios]/meteo-fuelv2/server/sv_main.lua
~ resources/[meteostudios]/meteo-fuelv2/shared/config.lua
~ resources/[meteostudios]/meteo-fuelv2/shared/utils.lua
~ resources/[meteostudios]/meteo-furnishing/client/cl_main.lua
~ resources/[meteostudios]/meteo-furnishing/server/sv_main.lua
~ resources/[meteostudios]/meteo-furnishing/shared/crafting.lua
~ resources/[meteostudios]/meteo-gopostaljob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-gopostaljob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-gopostaljob/shared/utils.lua
~ resources/[meteostudios]/meteo-gym/client/cl_main.lua
~ resources/[meteostudios]/meteo-gym/shared/config.lua
~ resources/[meteostudios]/meteo-hsd/client/cl_main.lua
~ resources/[meteostudios]/meteo-hsd/server/sv_functions.lua
~ resources/[meteostudios]/meteo-hsd/shared/utils.lua
~ resources/[meteostudios]/meteo-jobgarage/client/cl_main.lua
~ resources/[meteostudios]/meteo-jobgarage/shared/config.lua
~ resources/[meteostudios]/meteo-loosechange/client/cl_main.lua
~ resources/[meteostudios]/meteo-loosechange/server/sv_functions.lua
~ resources/[meteostudios]/meteo-loosechange/shared/config.lua
~ resources/[meteostudios]/meteo-loosechange/shared/utils.lua
~ resources/[meteostudios]/meteo-mailboxrob/client/cl_main.lua
~ resources/[meteostudios]/meteo-mailboxrob/server/sv_main.lua
~ resources/[meteostudios]/meteo-mailboxrob/shared/config.lua
~ resources/[meteostudios]/meteo-mailboxrob/shared/utils.lua
~ resources/[meteostudios]/meteo-mdt/client/cl_citations.lua
~ resources/[meteostudios]/meteo-mdt/server/sv_callbacks.lua
~ resources/[meteostudios]/meteo-mdt/shared/utils.lua
~ resources/[meteostudios]/meteo-mechanicjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-mechanicjob/client/cl_nitrous.lua
~ resources/[meteostudios]/meteo-mechanicjob/server/sv_main.lua
~ resources/[meteostudios]/meteo-mechanicjob/shared/utils.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_checking.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_hospital.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_injuries.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_items.lua
~ resources/[meteostudios]/meteo-medicaljob/client/cl_main.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_injuries.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_items.lua
~ resources/[meteostudios]/meteo-medicaljob/server/sv_main.lua
~ resources/[meteostudios]/meteo-medicaljob/shared/config.lua
~ resources/[meteostudios]/meteo-medicaljob/shared/utils.lua
~ resources/[meteostudios]/meteo-misc/client/consumables.lua
~ resources/[meteostudios]/meteo-misc/client/equipment.lua
~ resources/[meteostudios]/meteo-misc/client/meditate.lua
~ resources/[meteostudios]/meteo-misc/client/vehshoot.lua
~ resources/[meteostudios]/meteo-misc/client/zoom.lua
~ resources/[meteostudios]/meteo-misc/server/consumables.lua
~ resources/[meteostudios]/meteo-misc/server/equipment.lua
~ resources/[meteostudios]/meteo-multichar/client/cl_main.lua
~ resources/[meteostudios]/meteo-multichar/server/sv_main.lua
~ resources/[meteostudios]/meteo-multichar/shared/config.lua
~ resources/[meteostudios]/meteo-multichar/web/*
~ resources/[meteostudios]/meteo-pawnshop/locales/*
~ resources/[meteostudios]/meteo-pawnshop/server/sv_main.lua
~ resources/[meteostudios]/meteo-pawnshop/shared/config.lua
~ resources/[meteostudios]/meteo-phone/client/apps/cl_phone.lua
~ resources/[meteostudios]/meteo-phone/client/apps/cl_security.lua
~ resources/[meteostudios]/meteo-phone/client/cl_main.lua
~ resources/[meteostudios]/meteo-phone/client/source/cl_ox_phone.lua
~ resources/[meteostudios]/meteo-phone/locales/*
~ resources/[meteostudios]/meteo-phone/server/apps/sv_bleeter.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_music.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_phone.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_shop.lua
~ resources/[meteostudios]/meteo-phone/server/source/sv_functions.lua
~ resources/[meteostudios]/meteo-phone/server/source/sv_inventory.lua
~ resources/[meteostudios]/meteo-phone/server/source/sv_ox_phone.lua
~ resources/[meteostudios]/meteo-phone/server/sv_main.lua
~ resources/[meteostudios]/meteo-phone/shared/config.lua
~ resources/[meteostudios]/meteo-phone/web/*
~ resources/[meteostudios]/meteo-pickpocket/client/cl_main.lua
~ resources/[meteostudios]/meteo-pickpocket/client/cl_open.lua
~ resources/[meteostudios]/meteo-pickpocket/server/sv_main.lua
~ resources/[meteostudios]/meteo-pickpocket/shared/config.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_cuff.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_escort.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_headbag.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_main.lua
~ resources/[meteostudios]/meteo-policejob/client/cl_objects.lua
~ resources/[meteostudios]/meteo-policejob/locales/*
~ resources/[meteostudios]/meteo-policejob/server/sv_main.lua
~ resources/[meteostudios]/meteo-policejob/server/sv_objects.lua
~ resources/[meteostudios]/meteo-policejob/shared/config.lua
~ resources/[meteostudios]/meteo-policejob/shared/utils.lua
~ resources/[meteostudios]/meteo-radio/client/cl_main.lua
~ resources/[meteostudios]/meteo-radio/server/sv_main.lua
~ resources/[meteostudios]/meteo-radio/shared/config.lua
~ resources/[meteostudios]/meteo-radio/shared/utils.lua
~ resources/[meteostudios]/meteo-remotespikes/client/cl_main.lua
~ resources/[meteostudios]/meteo-remotespikes/server/sv_main.lua
~ resources/[meteostudios]/meteo-remotespikes/shared/config.lua
~ resources/[meteostudios]/meteo-remotespikes/shared/utils.lua
~ resources/[meteostudios]/meteo-repojob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-repojob/client/cl_main.lua
~ resources/[meteostudios]/meteo-repojob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-repojob/shared/utils.lua
~ resources/[meteostudios]/meteo-restaurants/client/cl_zones.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_cooking.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_functions.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_ingredients_shop.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_items.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_shop.lua
~ resources/[meteostudios]/meteo-restaurants/server/sv_storage.lua
~ resources/[meteostudios]/meteo-restaurants/shared/config.lua
~ resources/[meteostudios]/meteo-restaurants/shared/utils.lua
~ resources/[meteostudios]/meteo-rewards/server/sv_main.lua
~ resources/[meteostudios]/meteo-seahunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-seahunt/server/sv_functions.lua
~ resources/[meteostudios]/meteo-seahunt/shared/utils.lua
~ resources/[meteostudios]/meteo-searchvehicles/client/cl_main.lua
~ resources/[meteostudios]/meteo-searchvehicles/locales/*
~ resources/[meteostudios]/meteo-searchvehicles/server/sv_main.lua
~ resources/[meteostudios]/meteo-searchvehicles/shared/config.lua
~ resources/[meteostudios]/meteo-shops/client/cl_main.lua
~ resources/[meteostudios]/meteo-shops/server/sv_main.lua
~ resources/[meteostudios]/meteo-shops/shared/config.lua
~ resources/[meteostudios]/meteo-shops/shared/utils.lua
~ resources/[meteostudios]/meteo-speakers/client/cl_main.lua
~ resources/[meteostudios]/meteo-speakers/server/sv_main.lua
~ resources/[meteostudios]/meteo-speakers/shared/config.lua
~ resources/[meteostudios]/meteo-speakers/shared/utils.lua
~ resources/[meteostudios]/meteo-taxijob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-taxijob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-taxijob/shared/utils.lua
~ resources/[meteostudios]/meteo-transitjob/client/cl_dispatcher.lua
~ resources/[meteostudios]/meteo-transitjob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-transitjob/shared/utils.lua
~ resources/[meteostudios]/meteo-transporthunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-transporthunt/server/sv_functions.lua
~ resources/[meteostudios]/meteo-transporthunt/shared/utils.lua
~ resources/[meteostudios]/meteo-vaultjob/client/cl_guards.lua
~ resources/[meteostudios]/meteo-vaultjob/client/cl_main.lua
~ resources/[meteostudios]/meteo-vaultjob/client/cl_trolleys.lua
~ resources/[meteostudios]/meteo-vaultjob/server/sv_functions.lua
~ resources/[meteostudios]/meteo-vaultjob/shared/utils.lua
~ resources/[meteostudios]/meteo-vehiclerental/client/cl_main.lua
~ resources/[meteostudios]/meteo-vehiclerental/server/sv_main.lua
~ resources/[meteostudios]/meteo-vehiclerental/shared/config.lua
~ resources/[meteostudios]/meteo-vehiclerental/shared/utils.lua
~ resources/[meteostudios]/meteo-weaponback/client/cl_main.lua
~ resources/[meteostudios]/meteo-weaponback/server/sv_main.lua
~ resources/[meteostudios]/meteo-weaponrepair/client/cl_main.lua
~ resources/[meteostudios]/meteo-weaponrepair/server/sv_main.lua
~ resources/[meteostudios]/meteo-weaponrepair/shared/utils.lua
~ resources/[meteostudios]/msv2-versioncheck/
~ resources/[ox]/ox_lib
~ resources/[qb]/meteo-radialmenu/
~ resources/[qb]/meteo-smallresources/client/consumables.lua
~ resources/[qb]/meteo-smallresources/client/fireworks.lua
~ resources/[qb]/meteo-smallresources/client/seatbelt.lua
~ resources/[qb]/meteo-smallresources/server/consumables.lua
~ resources/[qb]/meteo-smallresources/server/main.lua
~ resources/[standalone]/sirens/
~ resources/[standalone]/vehiclehandler
~ resources/[standalone]/vehiclemileage
~ resources/[voice]/pma-voice

+ resources/[qb]/meteo-core/
+ meteo-server/server-data/qbox.cfg
+ meteo-server/server-data/resources/[meteostudios]/meteo-weapontints/
+ meteo-server/server-data/resources/[qb]/meteo-vehiclekeys/
+ meteo-server/server-data/resources/[qb]/meteo-vehicles/
+ resources/[meteostudios]/meteo-inventory/
+ resources/[meteostudios]/meteo-misc/server/meditate.lua
```

### Images
![](https://r2.fivemanage.com/ND1ABtrhOCiEbMgp1LFCW/updates/update_v2.7.0_01.png)

### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.

> **Warning:** Please make sure to keep a backup if you are applying this to your main server, and be mindful if you made any custom changes before.

***

## 2.6.0

### Changes

* Escrow ignore added for meteo speakers config
* Fixed renaming issues between meteo phone and speakers
* Fixed renaming issues with the meteo finance app
* Attempted fixes for bargehunt sync issues
* Database Changes (I forgot to include this in the last update). Please run this.
```sql
CREATE TABLE IF NOT EXISTS `meteo_phone_music_song_plays` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `account_id` INT(11) NOT NULL,
    `song_id` INT(11) NOT NULL,
    `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    UNIQUE KEY `unique_play` (`account_id`, `song_id`),
    INDEX `account_id` (`account_id`),
    INDEX `song_id` (`song_id`),
    FOREIGN KEY (`account_id`) REFERENCES `meteo_phone_music_accounts`(`id`) ON DELETE CASCADE,
    FOREIGN KEY (`song_id`) REFERENCES `meteo_phone_music_songs`(`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```

**Optional - skip if you do not want these languages:**

* Added Finnish language support
* Added Romanian language support

### Modified Files

```diff
~ resources/[meteostudios]/msv2-versioncheck/fxmanifest.lua
~ resources/[meteostudios]/meteo-bargehunt/client/cl_main.lua
~ resources/[meteostudios]/meteo-bargehunt/client/cl_mission.lua
~ resources/[meteostudios]/meteo-bargehunt/server/sv_main.lua
~ resources/[meteostudios]/meteo-customapp-finance
~ resources/[meteostudios]/meteo-dealerships/client/cl_main.lua
~ resources/[meteostudios]/meteo-dealerships/server/sv_finance.lua
~ resources/[meteostudios]/meteo-phone/server/apps/sv_music.lua
~ resources/[meteostudios]/meteo-phone/server/source/sv_ox_phone.lua
~ resources/[meteostudios]/meteo-phone/server/sv_main.lua

## Optional. Skip if you do not want languages update
+ resources/[meteostudios]/meteo-adminmenu/locales/*
+ resources/[meteostudios]/meteo-animations/locales/*
+ resources/[meteostudios]/meteo-apartments/locales/*
+ resources/[meteostudios]/meteo-appearance/locales/*
+ resources/[meteostudios]/meteo-atmskimming/locales/*
+ resources/[meteostudios]/meteo-banking/locales/*
+ resources/[meteostudios]/meteo-bargehunt/locales/*
+ resources/[meteostudios]/meteo-bennys/locales/*
+ resources/[meteostudios]/meteo-blackjack/locales/*
+ resources/[meteostudios]/meteo-boosting/locales/*
+ resources/[meteostudios]/meteo-bossmenuv2/locales/*
+ resources/[meteostudios]/meteo-buffs/locales/*
+ resources/[meteostudios]/meteo-casinocashier/locales/*
+ resources/[meteostudios]/meteo-chat/locales/*
+ resources/[meteostudios]/meteo-chopshop/locales/*
+ resources/[meteostudios]/meteo-cityhallv2/locales/*
+ resources/[meteostudios]/meteo-craftingtables/locales/*
+ resources/[meteostudios]/meteo-crimetablet/locales/*
+ resources/[meteostudios]/meteo-dailyrewards/locales/*
+ resources/[meteostudios]/meteo-dealerships/locales/*
+ resources/[meteostudios]/meteo-dialogue/locales/*
+ resources/[meteostudios]/meteo-dispatch/locales/*
+ resources/[meteostudios]/meteo-drugs/locales/*
+ resources/[meteostudios]/meteo-drugselling/locales/*
+ resources/[meteostudios]/meteo-dumpstersearch/locales/*
+ resources/[meteostudios]/meteo-electricianjob/locales/*
+ resources/[meteostudios]/meteo-evidence/locales/*
+ resources/[meteostudios]/meteo-fingerscanner/locales/*
+ resources/[meteostudios]/meteo-fishingjob/locales/*
+ resources/[meteostudios]/meteo-foresthunt/locales/*
+ resources/[meteostudios]/meteo-fuelv2/locales/*
+ resources/[meteostudios]/meteo-furnishing/locales/*
+ resources/[meteostudios]/meteo-garages/locales/*
+ resources/[meteostudios]/meteo-gopostaljob/locales/*
+ resources/[meteostudios]/meteo-gym/locales/*
+ resources/[meteostudios]/meteo-hsd/locales/*
+ resources/[meteostudios]/meteo-hud/locales/*
+ resources/[meteostudios]/meteo-inventory/locales/*
+ resources/[meteostudios]/meteo-jail/locales/*
+ resources/[meteostudios]/meteo-jobgarage/locales/*
+ resources/[meteostudios]/meteo-jobtablet/locales/*
+ resources/[meteostudios]/meteo-loadingscreen/locales/*
+ resources/[meteostudios]/meteo-loosechange/locales/*
+ resources/[meteostudios]/meteo-luckywheel/locales/*
+ resources/[meteostudios]/meteo-mailboxrob/locales/*
+ resources/[meteostudios]/meteo-mdt/locales/*
+ resources/[meteostudios]/meteo-mechanicjob/locales/*
+ resources/[meteostudios]/meteo-medicaljob/locales/*
+ resources/[meteostudios]/meteo-misc/locales/*
+ resources/[meteostudios]/meteo-multichar/locales/*
+ resources/[meteostudios]/meteo-organizations/locales/*
+ resources/[meteostudios]/meteo-pawnshop/locales/*
+ resources/[meteostudios]/meteo-perks/locales/*
+ resources/[meteostudios]/meteo-phone/locales/*
+ resources/[meteostudios]/meteo-pickpocket/locales/*
+ resources/[meteostudios]/meteo-policejob/locales/*
+ resources/[meteostudios]/meteo-policeradar/locales/*
+ resources/[meteostudios]/meteo-properties/locales/*
+ resources/[meteostudios]/meteo-radio/locales/*
+ resources/[meteostudios]/meteo-remotespikes/locales/*
+ resources/[meteostudios]/meteo-repojob/locales/*
+ resources/[meteostudios]/meteo-reportmenuv2/locales/*
+ resources/[meteostudios]/meteo-restaurants/locales/*
+ resources/[meteostudios]/meteo-rewards/locales/*
+ resources/[meteostudios]/meteo-roulette/locales/*
+ resources/[meteostudios]/meteo-scenes/locales/*
+ resources/[meteostudios]/meteo-seahunt/locales/*
+ resources/[meteostudios]/meteo-searchvehicles/locales/*
+ resources/[meteostudios]/meteo-shops/locales/*
+ resources/[meteostudios]/meteo-speakers/locales/*
+ resources/[meteostudios]/meteo-taxijob/locales/*
+ resources/[meteostudios]/meteo-transitjob/locales/*
+ resources/[meteostudios]/meteo-transporthunt/locales/*
+ resources/[meteostudios]/meteo-vaultjob/locales/*
+ resources/[meteostudios]/meteo-vehiclerental/locales/*
+ resources/[meteostudios]/meteo-weaponrepair/locales/*
+ resources/[qb]/meteo-core/locales/*
+ resources/[qb]/meteo-radialmenu/locales/*
+ resources/[qb]/meteo-smallresources/locales/*
```

***

## 2.5.0

### Changes

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

### Modified Files

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

### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.

> **Warning:** Please make sure to keep a backup if you are applying this to your main server, and be mindful if you made any custom changes before.

***
## 2.4.0

### Changes

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
AFTER `is_locked`;

ALTER TABLE `meteo_phone_sim_ownership`
ADD COLUMN IF NOT EXISTS `disabled_at` DATETIME DEFAULT NULL
AFTER `locked_at`;
```

### Modified Files

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

### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.

> **Warning:** Please make sure to keep a backup if you are applying this to your main server, and be mindful if you made any custom changes before.

## 2.3.0

### Changes

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

### Modified Files

* `resources/*`
* `server.cfg`

### How to Install

Use `/myorder` slash command on our Discord server and get the new updated link for server files. download full files and you must replace the full resources folder and server.cfg. otherwise rename won’t work. Refer to [how-to-rename-meteo-scripts.md](how-to/how-to-rename-meteo-scripts.md "mention") to rename scripts to your name :)

## 2.2.0

### Changes

* meteo-appearance: texture now resets when drawable changes
* restaurant shops: fixed item price editing, now only shows enabled categories
* improved phone close animation
* updated clothing
* chat updates for text-based RP servers
* added GetAccountBalance export support for qb-banking
* circlepick minigame: improved difficulty and added fight ped block

### Modified Files

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

## 2.1.0

### Changes

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

### Modified Files

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

### How to Install

Download the server again from the same link you originally received and replace all modified files listed above.

***

## Notes

{% hint style="info" %}
The only official place to get the meteo fivem server is [meteofivem.net/meteo-fivem-server](https://meteofivem.net/meteo-fivem-server). Copies sold anywhere else (resellers or "leaked" downloads) do not get updates, support or security patches from us.
{% endhint %}
