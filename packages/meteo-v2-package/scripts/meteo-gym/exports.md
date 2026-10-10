---
description: >-
  Every meteo-gym export with a simple example and what it gives back - the
  player's physical form, stats and energy.
icon: code
---

# Exports

Read how fit the local player is from your own client scripts, for example to make a climb or a fight harder for an unfit character. Both exports are client side and read the local player.

Both return `nil` until the player's gym data has loaded.

***

## GetPhysicalForm()

One number for overall fitness: the average of strength, dexterity and endurance, rounded, 0 to 100. Stats fade over time, so this is the live value with fading applied.

```lua
local form = exports['meteo-gym']:GetPhysicalForm()
print(form) --> 62

if form and form < 40 then
    QBCore.Functions.Notify('You are too out of shape for this', 'error')
    return
end
```

***

## GetGymStatus()

Every stat with its effect, plus energy. This is what the Gym tab in the inventory shows, already worded for the player.

```lua
local status = exports['meteo-gym']:GetGymStatus()
for _, stat in ipairs(status.stats) do
    print(stat.id, stat.value, stat.effect)
end
--> strength    71.5   +36% melee damage
--> dexterity   48     +5% sprint speed
--> endurance   66.2   Stamina 71 / 100

print(status.energy.value, status.energy.max) --> 80   100
```

```lua
-- record:
{
    stats = {
        {
            id = 'strength',      -- 'strength', 'dexterity' or 'endurance'
            label = 'Strength',
            value = 71.5,         -- 0 to 100, one decimal
            effect = '...',       -- the effect line, worded
            fadesIn = 51200,      -- seconds until it starts fading, 0 if already fading
        },
    },
    energy = {
        value = 80,
        max = 100,
        fullIn = 400,             -- seconds until full, -1 when not regenerating
        paused = nil,             -- 'hunger', 'thirst' or 'both' when regen is paused
    },
}
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
