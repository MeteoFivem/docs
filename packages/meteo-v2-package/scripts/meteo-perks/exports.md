---
description: >-
  Every meteo-perks export with a simple example and what it gives back -
  register your own perk line, award XP and check perks and levels.
icon: code
---

# Exports

Add your own script to the Perks tab, award XP to it and read what the player has unlocked. Everything is server side, except `GetProgress` and `GetLine`, which also have a client version.

Perks are grouped into **lines**. A line is one activity (Pickpocket, House Robbery, Fishing) with its own level from 1 to 10. Each perk on a line unlocks when the line reaches the perk's level - there is nothing to spend and nothing to pick.

* **Your script owns the line** - you register it, and it disappears when your resource stops
* **The owner owns the numbers** - the reward each perk pays out can be changed in the admin menu, so your `default` is only the starting value
* **Daily cap** - XP per line per day is capped by `Config.dailyXpLimit` (1500 by default, `0` removes the cap)

***

## Registering a Line

### RegisterPerks(line)

Adds a line (or replaces it, if your script registers it again) with the perks that unlock as it levels. Returns `true`, or `false` if the table is invalid.

```lua
exports['meteo-perks']:RegisterPerks({
    line = 'smuggling',       -- optional, defaults to your resource name
    label = 'Smuggling',
    icon = 'sailing',         -- Material Icons name
    group = 'outlaw',         -- outlaw, hustler, worker, lifestyle or other
    perks = {
        { id = 'smg_fastload', level = 3, name = 'Quick Loader', icon = 'speed',
          type = 'percent', default = 15, desc = 'Load crates %s% faster' },
        { id = 'smg_bonus', level = 6, name = 'Good Contacts', icon = 'payments',
          type = 'flat', default = 250, desc = '+$%s per delivery' },
        { id = 'smg_nightrun', level = 10, name = 'Night Runs', icon = 'dark_mode',
          type = 'unlock', default = 1, desc = 'Unlocks night deliveries' },
    },
})
```

**Line fields**

| Field | Type | Notes |
| ----- | ---- | ----- |
| `line` | string | Line id. Defaults to your resource name. Lowercased, anything not a letter, number or `_` becomes `_`. Max 48 |
| `label` | string | Name shown in the Perks tab. Defaults to the id |
| `icon` | string | Material Icons name. Defaults to `star` |
| `group` | string | Heading it sits under: `outlaw`, `hustler`, `worker`, `lifestyle` or `other`. Unknown groups fall back to `other` |
| `perks` | table | The perks on the line. A line with no perks is allowed - it still levels and shows in the tab |

**Perk fields**

| Field | Type | Notes |
| ----- | ---- | ----- |
| `id` | string | Required. Must be unique across the whole server. Max 64 |
| `level` | number | Line level that unlocks it, 1 to 10 |
| `name` | string | Defaults to the id |
| `icon` | string | Material Icons name. Defaults to `star` |
| `type` | string | `percent`, `flat` or `unlock`. Anything else is treated as `percent` |
| `default` | number | Reward before an owner edits it in the admin menu |
| `desc` | string | Shown under the perk. `%s` is replaced with the reward, `%s%` adds a percent sign. Max 160 |

A perk id another line already owns is skipped with a warning in the console.

**Register it every time meteo-perks starts**, since the registry lives in memory. This is the pattern every Meteo script uses:

```lua
local LINE = { line = 'smuggling', label = 'Smuggling', icon = 'sailing', group = 'outlaw', perks = { ... } }

local function register()
    if GetResourceState('meteo-perks') ~= 'started' then return end
    exports['meteo-perks']:RegisterPerks(LINE)
end

CreateThread(function()
    while GetResourceState('meteo-perks') ~= 'started' do Wait(500) end
    Wait(250)
    register()
end)

AddEventHandler('onResourceStart', function(res)
    if res == 'meteo-perks' then CreateThread(function() Wait(500); register() end) end
end)
```

When your resource stops, its line and perks are removed for you.

***

## Awarding XP

### AddXp(source, amount)

Awards XP to the line your resource registered, so you never need to know your own line id. Shows the XP toast and levels the line up when it crosses a threshold.

```lua
local awarded = exports['meteo-perks']:AddXp(source, 50)
print(awarded) --> 50    (less once the daily cap is reached, 0 if capped)
```

Returns the XP actually awarded. `0` if your resource has no registered line, the player is not loaded or `amount` is not above 0.

### AddXpTo(source, line, amount)

Same as `AddXp`, but into a line you name. Use it when your script pays into another script's line.

```lua
exports['meteo-perks']:AddXpTo(source, 'pickpocket', 25)
```

Returns the XP actually awarded, or `0` if the line is not registered.

***

## Checking Perks

### GetPerkValue(source, perkId)

The reward a perk pays out, or `0` if the player has not unlocked it. This is the one to use for number perks, since a `0` means "no bonus" and needs no extra check.

```lua
local faster = exports['meteo-perks']:GetPerkValue(source, 'smg_fastload')
print(faster) --> 15    (0 if not unlocked)

local duration = baseDuration * (1 - faster / 100)
```

```lua
local bonus = exports['meteo-perks']:GetPerkValue(source, 'smg_bonus')
Player.Functions.AddMoney('cash', basePay + bonus, 'smuggling-delivery')
```

### HasPerk(source, perkId)

`true` once the player has unlocked the perk. Use it for `unlock` perks.

```lua
if not exports['meteo-perks']:HasPerk(source, 'smg_nightrun') then
    return QBCore.Functions.Notify(source, 'You need more Smuggling experience', 'error')
end
```

Returns `false` if the perk id is not registered.

### GetLevel(source, line)

The player's level on a line, from 1 up.

```lua
local level = exports['meteo-perks']:GetLevel(source, 'smuggling')
print(level) --> 4
```

Returns `1` for a player with no XP on that line, or a line that does not exist.

***

## Reading Progress

### GetProgress(source) - server

Every group, line and perk for one player, already marked unlocked or not. This is what the Perks tab draws.

```lua
local progress = exports['meteo-perks']:GetProgress(source)
for _, group in ipairs(progress.groups) do
    for _, line in ipairs(group.lines) do
        print(group.label, line.label, line.level, line.xp)
    end
end
--> Outlaw   Smuggling   4   960
```

```lua
-- shape:
{
    groups = {
        {
            id = 'outlaw', label = 'Outlaw', icon = 'local_police', color = '#ff5d52',
            lines = {
                {
                    id = 'smuggling', label = 'Smuggling', icon = 'sailing',
                    level = 4, maxLevel = 10,
                    xp = 960,       -- total XP on the line
                    into = 160,     -- XP into the current level
                    needed = 600,   -- XP the current level needs in total
                    perks = {
                        { id, level, name, icon, desc, type, reward, unlocked },
                    },
                },
            },
        },
    },
}
```

### GetProgress() - client

Same shape, for the local player. Kept up to date as they earn XP.

```lua
local progress = exports['meteo-perks']:GetProgress()
```

The client event `meteo-perks:client:progressChanged` fires with the new table whenever the server sends fresh progress (a level up, a new line registering).

### GetLine(lineId) - client

One line from the local player's progress, or `nil` if nothing registered it.

```lua
local line = exports['meteo-perks']:GetLine('smuggling')
if line then
    print(line.level, line.into, line.needed) --> 4   160   600
end
```

***

## Registry

### GetRegistry()

Every registered perk on the server, from every line.

```lua
for _, perk in ipairs(exports['meteo-perks']:GetRegistry()) do
    print(perk.line, perk.id, perk.level, perk.type)
end
--> smuggling   smg_fastload   3   percent
```

```lua
-- each perk:
{ id, line, level, name, icon, desc, type, default }
```

### GetRegisteredPerk(perkId)

One perk, or `nil` if no line registered it.

```lua
local perk = exports['meteo-perks']:GetRegisteredPerk('smg_fastload')
print(perk.line, perk.level) --> smuggling   3
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
