---
description: >-
  Every meteo-medicaljob export with a simple example and what it gives back -
  death and knockout state, injuries, bleeding, item buffs and hospital beds.
icon: code
---

# Exports

Check whether a player is down, read their injuries, and show who is in which hospital bed from your own scripts.

Client exports read the calling player. Server exports cover the hospital beds. To revive or down a player from the server, use the [compatibility events](#compatibility) at the bottom.

***

## Client: Death and Knockout

A player goes down in two stages. First **knocked out** (KO), where anyone can help them up. Then **BW** (black and white), where only EMS can revive them. Some damage, like explosions, fire, drowning or dying in water, skips KO and goes straight to BW.

### IsPlayerDead()

True while the player is down, KO or BW.

```lua
if exports['meteo-medicaljob']:IsPlayerDead() then
    return -- can't do this while down
end
```

### IsPlayerKnockedOut()

True only in the KO stage.

```lua
print(exports['meteo-medicaljob']:IsPlayerKnockedOut()) --> true
```

### IsPlayerBW()

True only in the BW stage, when the player needs EMS.

```lua
print(exports['meteo-medicaljob']:IsPlayerBW()) --> false
```

### GetKOTimeRemaining()

Seconds left on the KO timer. `0` when it is not running.

```lua
print(exports['meteo-medicaljob']:GetKOTimeRemaining()) --> 87
```

### GetPlayerState()

The raw state number.

```lua
local state = exports['meteo-medicaljob']:GetPlayerState()
print(state) --> 2
```

| Value | State |
| ----- | ----- |
| `0` | Alive |
| `1` | Injured |
| `2` | Knocked out |
| `3` | BW, needs EMS |

***

## Client: Injuries

### IsPlayerInjured()

True if the player is down or has any injured body part.

```lua
if exports['meteo-medicaljob']:IsPlayerInjured() then
    -- slow them down in your minigame
end
```

### GetPlayerBleeding()

The overall bleeding level, `0` (not bleeding) to `4`.

```lua
print(exports['meteo-medicaljob']:GetPlayerBleeding()) --> 1
```

### GetInjuriesCount()

A quick summary. A body part counts as `critical` at 80% damage or more.

```lua
local count = exports['meteo-medicaljob']:GetInjuriesCount()
print(json.encode(count))
--> { "total": 3, "bleeding": 1, "critical": 1, "hasInjuries": true }
```

### GetInjuriesForInventory()

All 13 body parts, ready for a wound panel. Body parts: `HEAD`, `NECK`, `SPINE`, `CHEST`, `STOMACH`, `LEFT_ARM`, `LEFT_HAND`, `RIGHT_ARM`, `RIGHT_HAND`, `LEFT_LEG`, `LEFT_FOOT`, `RIGHT_LEG`, `RIGHT_FOOT`.

```lua
local parts = exports['meteo-medicaljob']:GetInjuriesForInventory()
for part, data in pairs(parts) do
    if data.health < 100 then
        print(data.label, data.health, data.severityLabel)
    end
end
--> Left Arm   35   Gunshot
```

```lua
-- each body part:
{
    health        = 35,         -- 0-100, 100 = untouched
    severity      = 2,          -- 0-3
    severityLabel = 'Gunshot',  -- wound name, nil on an untouched part
    bleeding      = true,
    broken        = false,      -- true at 80% damage or more
    label         = 'Left Arm', -- from the locale
}
```

### GetPlayerInjuries()

The full injury table, if you need more than the exports above.

```lua
local injuries = exports['meteo-medicaljob']:GetPlayerInjuries()
print(injuries.state, injuries.bleeding)
for part, limb in pairs(injuries.limbs) do
    print(part, limb.damage, limb.bleeding)
end
--> LEFT_ARM   65   true
```

Treat it as read-only. Changing it does not sync to the server.

***

## Client: Item Buffs

### GetActiveDamageReduction()

Total damage reduction from active painkillers and adrenaline, in percent. Caps at `50`.

```lua
print(exports['meteo-medicaljob']:GetActiveDamageReduction()) --> 25
```

### IsPainSuppressed()

True while an item that blocks pain is active. Limping is off while it is.

```lua
print(exports['meteo-medicaljob']:IsPainSuppressed()) --> true
```

### GetPainkillersBuff() / GetAdrenalineBuff()

For a HUD timer. `remaining` and `duration` are in seconds.

```lua
local buff = exports['meteo-medicaljob']:GetPainkillersBuff()
print(json.encode(buff))
--> { "active": true, "remaining": 142, "duration": 300 }
--> { "active": false, "remaining": 0, "duration": 0 }   when not active
```

***

## Client: Hospital Bed

### IsInBed()

```lua
print(exports['meteo-medicaljob']:IsInBed()) --> true
```

### GetCurrentBedId()

The bed id, or `nil` when not in a bed.

```lua
print(exports['meteo-medicaljob']:GetCurrentBedId()) --> medical_bed_1_4
```

***

## Server: Hospital Beds

Read-only. Good for a bed board or a records system.

Bed ids look like `medical_bed_<hospital>_<bed>`, both numbers starting at 1 in the order of your hospitals and beds. `label` is the short code shown to players, like `LSMC-03`, built from the hospital name's initials.

### GetBeds()

Every hospital with its beds. A hospital with no beds is still listed with an empty `beds`.

```lua
local wards = exports['meteo-medicaljob']:GetBeds()
print(wards[1].name, wards[1].occupied .. '/' .. wards[1].total)
--> Los Santos Medical Center   2/8
```

```lua
-- each hospital:
{
    index    = 1,
    name     = 'Los Santos Medical Center',
    code     = 'LSMC',
    total    = 8,
    occupied = 2,
    beds     = { ... }, -- see GetBed
}
```

### GetHospitalBeds(hospitalIndex)

The beds of one hospital, or `nil` if that hospital does not exist.

```lua
local beds = exports['meteo-medicaljob']:GetHospitalBeds(1)
print(#beds) --> 8
```

### GetBed(bedId)

One bed, or `nil` for an unknown id.

```lua
local bed = exports['meteo-medicaljob']:GetBed('medical_bed_1_4')
print(bed.label, bed.occupied) --> LSMC-04   true
```

```lua
-- each bed:
{
    id            = 'medical_bed_1_4',
    index         = 4,
    label         = 'LSMC-04',
    hospital      = 'Los Santos Medical Center',
    hospitalIndex = 1,
    coords        = { x = 106.43, y = -391.03, z = 40.21, w = 340.07 },
    occupied      = true,
    patient       = { ... }, -- see GetBedPatient, nil when free
}
```

### GetBedPatient(bedId)

Who is in the bed, or `nil` when it is free.

```lua
local patient = exports['meteo-medicaljob']:GetBedPatient('medical_bed_1_4')
print(patient.name, patient.condition) --> John Doe   RECOVERING
```

```lua
{
    source    = 12,
    citizenid = 'ABC12345',  -- nil if they left before the bed was freed
    name      = 'John Doe',  -- nil if they left before the bed was freed
    condition = 'RECOVERING', -- CRITICAL | RECOVERING | STABLE
    injuries  = 2,           -- injured body parts
    bleeding  = 1,
    since     = 1782360000,  -- unix seconds they were admitted
}
```

`CRITICAL` means KO, BW, a severe injury or heavy bleeding. `RECOVERING` means injured but stable. `STABLE` means no injuries.

### IsBedOccupied(bedId)

```lua
print(exports['meteo-medicaljob']:IsBedOccupied('medical_bed_1_4')) --> true
```

### GetBedStats()

```lua
local stats = exports['meteo-medicaljob']:GetBedStats()
print(json.encode(stats))
--> { "total": 17, "occupied": 3, "available": 14 }
```

### Bed changes

A local server event fires whenever a bed is taken or freed, so you can refresh instead of polling.

```lua
AddEventHandler('meteo-medicaljob:server:bedsChanged', function()
    local wards = exports['meteo-medicaljob']:GetBeds()
end)
```

***

## Compatibility

meteo-medicaljob listens to the same events as qb-ambulancejob, so scripts written for it keep working.

### Revive a player

Fully heals and revives. If they are lying in a hospital bed, they stay in it and can get up when ready.

```lua
-- server
TriggerClientEvent('hospital:client:Revive', targetSrc)
```

`meteo-medicaljob:client:Revive` does the same thing.

### Down a player

Drops an alive player to KO, or a KO player to BW. Does nothing if they are already BW.

```lua
-- server
TriggerClientEvent('hospital:client:KillPlayer', targetSrc)
```

### Reading death state on the server

The client exports above only work on the player's own client. On the server, read the player metadata or state bags instead.

```lua
local player = exports.qbx_core:GetPlayer(src)
print(player.PlayerData.metadata.inlaststand) --> true while KO
print(player.PlayerData.metadata.isdead)      --> true while BW

print(Player(src).state.isDead)        --> true while KO or BW
print(Player(src).state.isKnockedDown) --> true while KO
```
