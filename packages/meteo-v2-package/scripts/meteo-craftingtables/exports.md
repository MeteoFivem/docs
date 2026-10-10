---
description: >-
  The meteo-craftingtables export a server owner would call - read a player's
  crafting level and XP.
icon: code
---

# Exports

Read a player's crafting level from your own scripts, for example to lock a job or a shop behind crafting experience. Server side.

The other exports in this script open benches for meteo-furnishing and feed the admin menu, so they are not listed here.

***

## GetCraftingProfile(citizenid)

The player's crafting level and XP. Read straight from the database, so it works for offline players too.

```lua
local profile = exports['meteo-craftingtables']:GetCraftingProfile(citizenid)
print(profile.level, profile.xp, profile.xpNeeded)
--> 4   260   350
```

```lua
-- record:
{
    citizenid = 'ABC12345',
    level = 4,
    xp = 260,        -- total crafting XP
    xpNeeded = 350,  -- total XP the next level needs
    maxLevel = 10,
}
```

Returns `nil` if `citizenid` is not a string. A player who never crafted comes back as level 1 with 0 XP.

The level thresholds are `Config.LevelSystem.xpPerLevel` in `shared/config.lua`.

```lua
local profile = exports['meteo-craftingtables']:GetCraftingProfile(citizenid)
if not profile or profile.level < 5 then
    return QBCore.Functions.Notify(source, 'You need crafting level 5', 'error')
end
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
