---
description: >-
  Configure Meteo Apartments for your server. Translations, furniture limits, security settings.
---

# Configuration Guide

All configuration is in `meteo-apartments/shared/config.lua`

***

## QBX Integration

If you're using QBX with qbx_garages or want starter apartments for new characters, follow these integration guides:

| Feature | Guide |
|---------|-------|
| **QBX Garages** | [QBX Garages Setup](for-developers/qbx-garages.md) - Required if using qbx_garages |
| **QBX Starter Apartments** | [QBX Starter Apartments Setup](for-developers/qbx-starter-apartments.md) - Optional for starter apartment system |

{% hint style="info" %}
**QBX Garages integration is required** if you're using qbx_garages. Starter apartments are optional.
{% endhint %}

***

## Adding New Apartments Complexes & Rooms

Want to add a new apartment MLO or create more rooms? Follow these guides:

| Guide | What It Does |
|-------|--------------|
| [**Adding New Complex**](for-developers/adding-new-complex.md) | Set up a new apartment MLO (complexes) |
| [**Creating Rooms**](for-developers/creating-rooms.md) | Use the in-game creator to add rooms to your complex |

These guides show you how to configure any MLO and add unlimited rooms using the built-in creator tool.

***

## Language/Translations (Optional)

**English is included by default.** Only configure this if you need other languages.

### How to add translations:

1. Go to `meteo-apartments/shared/config.lua`
2. Find the `lib.locale('')` line
3. Change to your language code: `lib.locale('es')` for Spanish, `lib.locale('fr')` for French
4. Make sure your language file exists in `meteo-apartments/locales/`
5. If it doesn't exist, copy `en.json` and translate it

```lua
-- In shared/config.lua
lib.locale('en')  -- English (default)
lib.locale('es')  -- Spanish
lib.locale('fr')  -- French
```

{% hint style="info" %}
**Need help with translations?** Join our Discord: [http://discord.meteofivem.net/](http://discord.meteofivem.net/)
{% endhint %}

***

## Furniture Limits & Upgrades

### Default Furniture Limit

How many furniture items players can place in their apartments.

```lua
Config.defaultFurnitureLimit = 150  -- 150 items per apartment
```

Change this number to allow more or fewer furniture items.

### Member Limit Upgrades

Players can upgrade how many roommates they can add. Configured in tiers.

```lua
Config.upgrades = {
    memberLimit = {
        tiers = {
            [1] = {
                price = 5000,
                limits = {
                    roommate = 3,  -- Can have 3 roommates
                    guest = 5      -- Can have 5 guests
                }
            },
            [2] = {
                price = 10000,
                limits = {
                    roommate = 5,
                    guest = 10
                }
            },
            -- Add more tiers...
        }
    }
}
```

**What each tier includes:**

<table><thead><tr><th width="100">Tier</th><th width="120">Price</th><th>Roommates</th><th>Guests</th></tr></thead><tbody><tr><td>Default (0)</td><td>Free</td><td>2</td><td>3</td></tr><tr><td>Tier 1</td><td>$5,000</td><td>3</td><td>5</td></tr><tr><td>Tier 2</td><td>$10,000</td><td>5</td><td>10</td></tr><tr><td>Tier 3</td><td>$25,000</td><td>10</td><td>15</td></tr><tr><td>Tier 4</td><td>$50,000</td><td>20</td><td>30</td></tr></tbody></table>

Players purchase upgrades in-game through the apartment management menu.

***

## Security Levels & Doorlock

### Security Level System

Each door has a security level (1-6). Higher levels are harder to lockpick and have better features.

```lua
Config.doorlock = {
    enabled = true,
    defaultSecurityLevel = 1,  -- Default for new doors

    securityLevels = {
        [1] = {
            label = 'Basic Lock',
            difficulty = { 'easy', 'easy' },  -- Lockpick difficulty
            autoLockTime = 60,  -- Auto-lock after 60 seconds
            antiBurglary = false,  -- Can be lockpicked
            antiRaid = false,  -- Can be raided by police
            alertPolice = false  -- No police alert on lockpick
        },
        [2] = {
            label = 'Standard Lock',
            difficulty = { 'easy', 'medium' },
            autoLockTime = 45,
            antiBurglary = false,
            antiRaid = false,
            alertPolice = false
        },
        [3] = {
            label = 'Advanced Lock',
            difficulty = { 'medium', 'medium' },
            autoLockTime = 30,
            antiBurglary = false,
            antiRaid = false,
            alertPolice = true  -- Alerts police on lockpick
        },
        [4] = {
            label = 'High Security Lock',
            difficulty = { 'medium', 'hard' },
            autoLockTime = 20,
            antiBurglary = false,
            antiRaid = false,
            alertPolice = true
        },
        [5] = {
            label = 'Maximum Security Lock',
            difficulty = { 'hard', 'hard' },
            autoLockTime = 15,
            antiBurglary = true,  -- Cannot be lockpicked
            antiRaid = false,
            alertPolice = true
        },
        [6] = {
            label = 'Military Grade Lock',
            difficulty = { 'hard', 'hard' },
            autoLockTime = 10,
            antiBurglary = true,  -- Cannot be lockpicked
            antiRaid = true,  -- Cannot be raided
            alertPolice = true
        }
    }
}
```

### Security Level Features Explained:

| Feature | What It Does |
|---------|--------------|
| **difficulty** | Lockpick minigame difficulty (easy, medium, hard) |
| **autoLockTime** | Seconds before door auto-locks (lower = faster) |
| **antiBurglary** | If true, cannot be lockpicked at all |
| **antiRaid** | If true, police cannot raid with stormram |
| **alertPolice** | If true, police get alert when lockpicked |

### Door Security Upgrades

Players can upgrade their door security in-game. Configured in tiers.

```lua
Config.upgrades = {
    doorSecurity = {
        levels = {
            [2] = { price = 2500, label = 'Standard Lock' },
            [3] = { price = 5000, label = 'Advanced Lock' },
            [4] = { price = 10000, label = 'High Security Lock' },
            [5] = { price = 25000, label = 'Maximum Security Lock' },
            [6] = { price = 50000, label = 'Military Grade Lock' }
        }
    }
}
```

{% hint style="warning" %}
**Upgrades are permanent.** Players cannot downgrade security levels. They can only upgrade to higher levels.
{% endhint %}

### Lockpicking Settings

Configure lockpick behavior:

```lua
Config.doorlock.lockpick = {
    enabled = true,
    requireOwned = true,  -- Only owned apartments can be lockpicked
    requireOwnerOnline = true,  -- Owner must be online
    cooldown = 30000,  -- 30 second cooldown after failed attempt
    alertOwner = true,  -- Notify owner when lockpicked

    items = {
        lockpick = {
            breakChance = 15,  -- 15% chance to break on fail
            breakChanceSuccess = 5  -- 5% chance to break on success
        },
        advancedlockpick = {
            breakChance = 5,
            breakChanceSuccess = 0
        }
    }
}
```

### Police Raid (Stormram) Settings

Configure police raid mechanics:

```lua
Config.doorlock.stormram = {
    enabled = true,
    item = 'police_stormram',
    removeOnUse = true,  -- Remove item after use
    requireOwned = true,  -- Can only raid owned apartments
    requireOwnerOnline = true,  -- Owner must be online
    alertOwner = true,  -- Notify owner when raided
    cooldown = 60000,  -- 60 second cooldown

    jobs = {
        ['police'] = 3,  -- Police rank 3+ can use
        ['sheriff'] = 3
    }
}
```

***

## Apartment Prices

Configure prices for different room types:

```lua
Config.roomTypes = {
    modern = {
        label = 'Modern Apartment',
        price = 25000
    },
    classic = {
        label = 'Classic Apartment',
        price = 15000
    },
    luxury = {
        label = 'Luxury Apartment',
        price = 50000
    },
    penthouse = {
        label = 'Penthouse Suite',
        price = 100000
    }
}
```

When players sell, they get 80% of the purchase price back.

***

## Quick Configuration Checklist

* Language set to your server's language
* Furniture limit configured
* Security levels configured for your server's difficulty
* Lockpick settings match your server's crime balance
* Police raid settings configured (jobs, ranks, cooldowns)
* Apartment prices set for your economy

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
