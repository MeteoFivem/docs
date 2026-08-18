---
description: >-
  Every meteo-evidence export with a simple example and what it gives back -
  prints, blood, statuses, GSR, alcohol and evidence lockers.
icon: code
---

# Exports

Leave prints and blood, apply statuses, and fill evidence lockers from your own scripts.

Client exports act on the calling player. Server exports take a server id. Identity is always worked out server side.

***

## Client: Prints and Blood

### CreateFingerprint(data)

Leaves a print. Does nothing if the player is wearing gloves or the chance roll misses.

```lua
local left = exports['meteo-evidence']:CreateFingerprint({
    coords  = vector3(100.0, 200.0, 30.0),  -- optional, defaults to the player
    surface = 'Kitchen counter',            -- optional, shown on the collected evidence
    chance  = 75,                           -- optional, 1-100. defaults to 100
})

print(left) --> true
--> false when gloved or the roll missed
```

The server still distance-checks and rate-limits before it records anything.

### CreateBloodDrop(data)

```lua
exports['meteo-evidence']:CreateBloodDrop({
    coords = vector3(100.0, 200.0, 30.0),  -- optional, defaults to the player
    isPool = false,                        -- optional, a pool skips the drip throttle
    force  = false,                        -- optional, bypasses rain/water/vehicle gating
})
--> always returns true
```

***

## Client: Player State

### ClearGSR()

Washes gunshot residue off the calling player. Rate-limited to once per 10 seconds.

```lua
exports['meteo-evidence']:ClearGSR()
```

### ApplyStatus(statusId, duration)

```lua
exports['meteo-evidence']:ApplyStatus('weedsmell', 600) -- 10 minutes
```

`statusId` is one of `gunpowder`, `widepupils`, `agitated`, `weedsmell`, `alcohol`, `heavyalcohol`. Unknown ids are rejected server side. `duration` is in seconds and caps at 7200.

### AddAlcohol(amount)

```lua
exports['meteo-evidence']:AddAlcohol(0.05)
```

The server only accepts values above 0 and up to 0.2 per call. Total BAC caps at 0.40 and decays about 0.00025 per minute.

### IsInvestigating()

Is the player in CSI Kit investigation mode.

```lua
print(exports['meteo-evidence']:IsInvestigating()) --> true
```

### IsWearingGloves()

Checks the appearance integration first, then falls back to `Config.bareHands`.

```lua
if exports['meteo-evidence']:IsWearingGloves() then
    -- no print will be left, they planned ahead
end
```

***

## Server: Prints and Blood

Use these when the acting player is not the one calling.

### CreateFingerprint(src, coords?, details?)

```lua
local ok = exports['meteo-evidence']:CreateFingerprint(src, coords, { surface = 'Safe handle' })
print(ok) --> true    (false if the player does not exist)
```

`coords` defaults to the player's position. `surface` is trimmed to 48 chars.

### CreateBloodDropForPlayer(src, coords?, opts?)

```lua
local ok = exports['meteo-evidence']:CreateBloodDropForPlayer(src, coords, { isPool = true })
print(ok) --> true
```

***

## Server: Statuses

### ApplyStatus(src, statusId, duration)

```lua
local ok = exports['meteo-evidence']:ApplyStatus(src, 'gunpowder', 300)
print(ok) --> true
--> false if the status id is unknown or duration is 0 or less
```

### ClearStatus(src, statusId)

```lua
local ok = exports['meteo-evidence']:ClearStatus(src, 'weedsmell')
print(ok) --> true    (false if they did not have it)
```

### GetStatuses(src)

```lua
for _, s in ipairs(exports['meteo-evidence']:GetStatuses(src)) do
    print(s.id, s.remaining)
end
--> gunpowder   240
--> weedsmell   85
```

### HasGSR(src)

Shorthand for the `gunpowder` status.

```lua
if exports['meteo-evidence']:HasGSR(src) then
    -- they fired a weapon recently
end
```

***

## Server: Alcohol

### AddAlcohol(src, amount)

```lua
exports['meteo-evidence']:AddAlcohol(source, 0.05)
```

Total caps at 0.40.

### GetBAC(src)

```lua
local bac = exports['meteo-evidence']:GetBAC(source)
print(bac) --> 0.12    (0.0 if none)

if bac > 0.08 then
    -- over the limit
end
```

***

## Server: Evidence Lockers

### CreateEvidenceLocker(name, createdBy)

`name` has to be unique.

```lua
local lockerId = exports['meteo-evidence']:CreateEvidenceLocker('Case-2026-001', 'ABC12345')
print(lockerId) --> 5
--> false if the name already exists or the write failed
```

### AddEvidenceToLocker(lockerId, evidenceData)

```lua
local ok = exports['meteo-evidence']:AddEvidenceToLocker(5, {
    itemName = 'filled_evidence_bag',  -- optional, defaults to the filled evidence bag
    count    = 1,                      -- optional, defaults to 1
    metadata = {
        type        = 'Blood Sample',
        label       = 'Evidence: Blood',
        description = 'DNA: A1B2C3D4\n\nBlood Type: O+\n\nLocation: Grove Street',
    },
})

print(ok) --> true
```

`metadata` is required. Uses ox_inventory.

### GetLockerEvidence(lockerId)

```lua
local evidence = exports['meteo-evidence']:GetLockerEvidence(5)

if evidence then
    for _, item in ipairs(evidence) do
        print(item.label, item.count)
    end
end
--> Evidence: Blood   1
```

Returns `false` if the locker does not exist or is empty.
