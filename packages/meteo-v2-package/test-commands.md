---
description: >-
  All showcase server commands available on the Meteo V2 showcase server.
  These commands help you test features quickly without grinding.
icon: terminal
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/test-commands.md
---

# Test Commands

These commands are only available on our showcase server. Use them to quickly test features without grinding.

{% hint style="warning" %}
These commands will NOT work on your production server. They are only for testing purposes on our showcase server.
{% endhint %}

***

## General Commands

| Command | What it does |
| ------- | ------------ |
| `/id` | Shows your server ID |
| `/tp x y z` | Teleport to coordinates |
| `/tpm` | Teleport to your map marker |
| `/car vehiclename` | Spawn a vehicle |
| `/giveitem yourid itemname amount` | Give yourself an item |
| `/setmoney yourid bank amount` | Set bank money |
| `/setjob yourid jobname grade` | Set your job |
| `/admincar` | Register current vehicle as owned |
| `/dv` | Delete current vehicle |

These are normal admin commands - check [server commands](commands.md) for the full list.

***

## Minigames

| Command | What it does |
| ------- | ------------ |
| `/minigame lockopen` | Play a minigame |
| `/minigame fusebox hard` | Play a minigame at a set difficulty |

Games: `arrowtiming`, `circlepick`, `etiming`, `fusebox`, `gymtrain`, `keymash`, `lockopen`, `reelzone`. run `/minigame` on its own to print the list in F8.

***

## Crime Tablet

| Command | What it does |
| ------- | ------------ |
| `/addcrypto 10000` | Add crypto to your wallet |
| `/setachievement all` | Complete all achievements |
| `/setachievement reset` | Reset all achievements |

{% content-ref url="scripts/meteo-crimetablet/test-commands.md" %}
[Crime Tablet - All Test Commands](scripts/meteo-crimetablet/test-commands.md)
{% endcontent-ref %}

***

## Buffs & Status

| Command | What it does |
| ------- | ------------ |
| `/buffs use beer` | Run an item's effects without using it |
| `/buffs crave cocaine` | Get hooked on a craving right away |
| `/buffs clear` | Clear all effects and cravings |
| `/buffs item joint` | Print an item's buff setup to the server console |
| `/buffs list` | Show how many items and cravings are set up |

{% content-ref url="scripts/meteo-buffs/test-commands.md" %}
[Buffs - All Test Commands](scripts/meteo-buffs/test-commands.md)
{% endcontent-ref %}

***

## Gym

| Command | What it does |
| ------- | ------------ |
| `/gym info` | Show your stats and energy |
| `/gym set strength 50` | Set a specific stat (0-100) |
| `/gym energy 100` | Set your energy |
| `/gym max` | Max all stats and energy |
| `/gym reset` | Reset all stats |

{% content-ref url="scripts/meteo-gym/test-commands.md" %}
[Gym - All Test Commands](scripts/meteo-gym/test-commands.md)
{% endcontent-ref %}

***

## Boosting

| Command | What it does |
| ------- | ------------ |
| `/testboost S` | Create a test boost contract |
| `/boostlevel 5` | Set boosting level |

{% content-ref url="scripts/meteo-boosting/test-commands.md" %}
[Boosting - All Test Commands](scripts/meteo-boosting/test-commands.md)
{% endcontent-ref %}

***

## Perks

| Command | What it does |
| ------- | ------------ |
| `/perks lines` | List every perk line and your level |
| `/perks xp pickpocket 200` | Award XP on a line |
| `/perks level pawn 7` | Set your level on a line |
| `/perks max` | Max every line |
| `/perks reset` | Reset every line |

{% content-ref url="scripts/meteo-perks/test-commands.md" %}
[Perks - All Test Commands](scripts/meteo-perks/test-commands.md)
{% endcontent-ref %}

***

## Organizations

| Command | What it does |
| ------- | ------------ |
| `/setorglevel xp 2000` | Add org XP |
| `/setorglevel upkeep` | Force upkeep due |
| `/setorglevel reset` | Delete your org |

{% content-ref url="scripts/meteo-organizations/test-commands.md" %}
[Organizations - All Test Commands](scripts/meteo-organizations/test-commands.md)
{% endcontent-ref %}

***

## Daily Rewards

| Command | What it does |
| ------- | ------------ |
| `/dailycompleteall` | Complete all tasks |
| `/dailyreset` | Reset progress |
| `/dailynewtasks` | Get new random tasks |

{% content-ref url="scripts/meteo-dailyrewards/test-commands.md" %}
[Daily Rewards - All Test Commands](scripts/meteo-dailyrewards/test-commands.md)
{% endcontent-ref %}

***

## Crafting

| Command | What it does |
| ------- | ------------ |
| `/setcraftxp 1 5000` | Set crafting XP |

{% content-ref url="scripts/meteo-craftingtables/test-commands.md" %}
[Crafting - All Test Commands](scripts/meteo-craftingtables/test-commands.md)
{% endcontent-ref %}

***

## Phone

| Command | What it does |
| ------- | ------------ |
| `/phonetest call 555-0199` | Ring yourself from a number |
| `/phonetest video 555-0199` | Get a test video call |
| `/phonetest notify` | Send a test notification |
| `/phonetest info` | Show your phone info |

{% content-ref url="scripts/meteo-phone/test-commands.md" %}
[Phone - All Test Commands](scripts/meteo-phone/test-commands.md)
{% endcontent-ref %}

***

## Jail

| Command | What it does |
| ------- | ------------ |
| `/setjailrep 1 500` | Set jail reputation |
| `/testalarm` | Toggle prison alarm |
| `/testmeal` | Trigger meal notification |

{% content-ref url="scripts/meteo-jail/test-commands.md" %}
[Jail - All Test Commands](scripts/meteo-jail/test-commands.md)
{% endcontent-ref %}
