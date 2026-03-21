---
description: >-
  all test server commands available on the meteo fivem test server.
  these commands help you test features quickly without grinding.
icon: terminal
---

# Test Commands

these commands are only available on our test server. use them to quickly test features without grinding.

{% hint style="warning" %}
these commands will NOT work on your production server. they are only for testing purposes on our test server.
{% endhint %}

***

## General Commands

| Command | What it does |
| ------- | ------------ |
| `/id` | shows your server ID |
| `/tp x, y, z` | teleport to coordinates |
| `/car vehiclename` | spawn a vehicle |
| `/giveitem yourid itemname amount` | give yourself an item |
| `/setmoney yourid bank amount` | set bank money |
| `/setjob yourid jobname grade` | set your job |
| `/admincar` | register current vehicle as owned |
| `/dv` | delete current vehicle |

***

## Crime Tablet

| Command | What it does |
| ------- | ------------ |
| `/addcrypto amount` | add crypto to your account |
| `/setachievement all` | complete all achievements |
| `/setachievement reset` | reset all achievements |

[Full details](scripts/meteo-crimetablet/test-commands.md)

***

## Buffs & Status

| Command | What it does |
| ------- | ------------ |
| `/buffs food fastFood 80` | set food addiction |
| `/buffs drug cocaine 60` | set drug addiction |
| `/buffs hunger/thirst/stress value` | set basic needs |
| `/buffs reset all` | reset everything |
| `/buffs info` | print debug info to F8 |

[Full details](scripts/meteo-buffs/test-commands.md)

***

## Gym

| Command | What it does |
| ------- | ------------ |
| `/setgymstats` | max all gym stats |
| `/gym set strength 500` | set a specific stat |
| `/gym max` | max all stats to 1000 |
| `/cleargyminjury` | clear active injury |

[Full details](scripts/meteo-gym/test-commands.md)

***

## Boosting

| Command | What it does |
| ------- | ------------ |
| `/testboost S` | create a test boost contract |
| `/boostlevel 5` | set boosting level |

[Full details](scripts/meteo-boosting/test-commands.md)

***

## Perks

| Command | What it does |
| ------- | ------------ |
| `/perksetlevel 1 crime 5` | set perk level |
| `/perkaddxp 1 crime 1000` | add perk XP |
| `/perkgrant 1 perkId` | unlock specific perk |
| `/perkreset 1 crime` | reset perk progress |

[Full details](scripts/meteo-perks/test-commands.md)

***

## Organizations

| Command | What it does |
| ------- | ------------ |
| `/setorglevel xp 2000` | add org XP |
| `/setorglevel upkeep` | force upkeep due |
| `/setorglevel reset` | delete your org |

[Full details](scripts/meteo-organizations/test-commands.md)

***

## Daily Rewards

| Command | What it does |
| ------- | ------------ |
| `/dailycompleteall` | complete all tasks |
| `/dailyreset` | reset progress |
| `/dailynewtasks` | get new random tasks |

[Full details](scripts/meteo-dailyrewards/test-commands.md)

***

## Crafting

| Command | What it does |
| ------- | ------------ |
| `/setcraftxp 1 5000` | set crafting XP |

[Full details](scripts/meteo-craftingtables/test-commands.md)

***

## Job Tablet

| Command | What it does |
| ------- | ------------ |
| `/givecivxp electrician 500` | give job XP |
| `/setcivlevel electrician 5` | set job level |

[Full details](scripts/meteo-jobtablet/test-commands.md)

***

## Phone

| Command | What it does |
| ------- | ------------ |
| `/testnotification normal message` | send test notification |
| `/sendemail Ifruit_123456` | send test email |

[Full details](scripts/meteo-phone/test-commands.md)

***

## Jail

| Command | What it does |
| ------- | ------------ |
| `/setjailrep 1 500` | set jail reputation |
| `/testalarm` | toggle prison alarm |
| `/testmeal` | trigger meal notification |

[Full details](scripts/meteo-jail/test-commands.md)
