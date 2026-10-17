---
description: >-
  Every meteo-jail export with a simple example and what it gives back -
  sentences, solitary, inmates, reputation, the alarm, the tunnel and meals.
icon: code
---

# Exports

Jail and release players, read sentences and drive prison events from your own scripts. Almost everything is server side.

Sentences are counted in **months**. One month lasts `Config.timePerMonth` milliseconds (default 60000, so one real minute). The sentence itself lives in the player's core metadata (`injail` and `insolitary`).

{% hint style="info" %}
These exports do no permission checks of their own. If a player can trigger your code, check their job or permission before you call them.
{% endhint %}

***

## Server: Sentences

### JailPlayer(source, months, jailerName?)

Jails an online player. Their belongings are confiscated and they are teleported inside, exactly like a sentence from the jail menu.

```lua
local result = exports['meteo-jail']:JailPlayer(targetId, 30, 'Officer Vargas')
print(result.success, result.targetName) --> true  John Doe
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `source` | number | The player's server id |
| `months` | number | 1 to 1200 |
| `jailerName` | string | Optional, defaults to `System` |

Returns `{ success, online?, targetName?, message? }`. `message` is a locale string when `success` is false - the player was not found, the time is out of range, or they are already jailed.

### UnjailPlayer(source)

Releases an online player early and hands their belongings back.

```lua
local result = exports['meteo-jail']:UnjailPlayer(targetId)
print(result.success) --> true
```

Returns the same table as `JailPlayer`. Fails if the player is not jailed.

### SolitaryPlayer(source, months) / UnsolitaryPlayer(source)

Moves a jailed player into solitary, or pulls them out. `months` is 1 to 1200.

```lua
exports['meteo-jail']:SolitaryPlayer(targetId, 5)
exports['meteo-jail']:UnsolitaryPlayer(targetId)
```

Returns the same table as `JailPlayer`. `SolitaryPlayer` fails if the player is not jailed or already in solitary.

### GetSentence(source)

Months left on an online player's sentence. `0` means not jailed.

```lua
if exports['meteo-jail']:GetSentence(source) > 0 then
    -- they are serving time
end
```

### GetSolitaryTime(source)

Months left in solitary, or `0`.

```lua
print(exports['meteo-jail']:GetSolitaryTime(source)) --> 3
```

### GetJailedPlayers()

Every **online** player serving time.

```lua
for _, p in ipairs(exports['meteo-jail']:GetJailedPlayers()) do
    print(p.source, p.name, p.jailTime, p.solitaryTime)
end
--> 12   John Doe   24   0
```

```lua
-- each entry:
{ source = 12, citizenid = 'ABC12345', name = 'John Doe', jailTime = 24, solitaryTime = 0 }
```

### GetInmates()

Everyone serving, online or not. Online players use their live clock.

```lua
local inmates = exports['meteo-jail']:GetInmates()
print(#inmates) --> 7
```

```lua
-- each entry:
{
    citizenid      = 'ABC12345',
    name           = 'John Doe',
    online         = true,
    source         = 12,      -- online only
    inside         = true,    -- online only, inside the prison zone
    months         = 24,      -- months left
    solitaryMonths = 0,
    sentenced      = 30,
    served         = 4,
    commuted       = 2,
    startedAt      = 1782300000, -- unix seconds, nil if unknown
}
```

### GetSentenceProgress(citizenid)

Where every month of a sentence went. `nil` when the citizen has no open sentence. Works for offline players.

```lua
local p = exports['meteo-jail']:GetSentenceProgress('ABC12345')
print(p.sentenced, p.served, p.commuted, p.remaining)
--> 30  4  2  24
```

`sentenced = served + commuted + remaining`. Commuted months were taken off by prison jobs or staff, not sat through.

### GetPrisonSpawn(source)

A random spawn point inside the prison for this player, or the solitary spawn if they are in solitary. `nil` when none are configured.

```lua
local spawn = exports['meteo-jail']:GetPrisonSpawn(source)
--> { x = 1765.2, y = 2565.8, z = 45.5, w = 180.0 }
```

***

## Server: Sentences by citizenid

The same actions keyed by citizenid, for admin panels and record screens. The player still has to be online, since jailing needs the live player for the teleport and confiscation. An offline citizen comes back as `{ success = false, online = false, message }`.

### GetJailStatus(citizenid)

```lua
local status = exports['meteo-jail']:GetJailStatus('ABC12345')
print(json.encode(status))
--> { "online": true, "jailed": true, "months": 24, "solitary": false, "solitaryMonths": 0 }
--> { "online": false, "jailed": false, "solitary": false }   when offline
```

### ManageJail(citizenid, months, solitaryMonths?)

Jails them, optionally starting in solitary. Jailer name is `Admin`.

```lua
local result = exports['meteo-jail']:ManageJail('ABC12345', 30, 5)
```

### ManageUnjail(citizenid)

```lua
exports['meteo-jail']:ManageUnjail('ABC12345')
```

### ManageSetJailTime(citizenid, months)

Sets the months left outright. Raising it lengthens the sentence, lowering it counts as commuted.

```lua
exports['meteo-jail']:ManageSetJailTime('ABC12345', 10)
```

### ManageSetSolitary(citizenid, enable, months?)

```lua
exports['meteo-jail']:ManageSetSolitary('ABC12345', true, 5) -- into solitary for 5 months
exports['meteo-jail']:ManageSetSolitary('ABC12345', false)   -- back to the yard
```

### ManageSetSolitaryTime(citizenid, months)

```lua
exports['meteo-jail']:ManageSetSolitaryTime('ABC12345', 2)
```

All of these return `{ success, online?, targetName?, message? }`.

***

## Server: Belongings

### HasPendingJailData(citizenid)

Is the jail holding confiscated belongings for this citizen.

```lua
print(exports['meteo-jail']:HasPendingJailData('ABC12345')) --> true
```

### GetBelongings(citizenid)

What is being held. `items` is `nil` (not empty) when the stash cannot be read.

```lua
local b = exports['meteo-jail']:GetBelongings('ABC12345')
print(b.held, b.cash, b.bank) --> true  450  0
for _, item in ipairs(b.items or {}) do print(item.name, item.count) end
--> phone   1
```

***

## Server: Prison Job Reputation

### GetReputationInfo(citizenid)

```lua
local rep = exports['meteo-jail']:GetReputationInfo('ABC12345')
print(rep.reputation, rep.jobs, rep.level) --> 140  23  Trusted
```

`level` is the name from `Config.jobSystem.repLevels`. Returns `nil` for an empty citizenid.

### GetPlayerReputation(citizenid)

Returns two values: reputation and total jobs completed.

```lua
local rep, jobs = exports['meteo-jail']:GetPlayerReputation('ABC12345')
```

### UpdatePlayerReputation(citizenid, delta)

Adds (or removes, with a negative number) reputation and returns the new total. Never goes below 0. A positive `delta` also counts as one completed job.

```lua
local newRep = exports['meteo-jail']:UpdatePlayerReputation('ABC12345', 10)
```

### ResetPlayerReputation(citizenid)

```lua
exports['meteo-jail']:ResetPlayerReputation('ABC12345')
```

***

## Server: Prison State

### IsPlayerInPrison(source)

Is the player inside the prison zone right now, jailed or not.

```lua
if exports['meteo-jail']:IsPlayerInPrison(source) then end
```

### GetAlarmState() / SetAlarmState(on)

```lua
print(exports['meteo-jail']:GetAlarmState()) --> false
exports['meteo-jail']:SetAlarmState(true)     -- sirens on for everyone
```

### IsTunnelOpen() / CloseTunnel()

The escape tunnel. `CloseTunnel` returns `true` if a tunnel was open and is now closed.

```lua
if exports['meteo-jail']:IsTunnelOpen() then
    exports['meteo-jail']:CloseTunnel()
end
```

### StartMealRun() / GetMealState()

`StartMealRun` serves a meal now. Returns `nil` when meals are off or no canteen is set.

```lua
exports['meteo-jail']:StartMealRun()

local meal = exports['meteo-jail']:GetMealState()
--> { enabled = true, canteen = true, active = true, endsIn = 120, nextIn = nil }
--> { enabled = false } when meals are off
```

`endsIn` and `nextIn` are seconds.

***

## Client

### IsInPrisonZone()

Is the local player inside the prison zone.

```lua
if exports['meteo-jail']:IsInPrisonZone() then end
```

### IsAlarmPlaying()

```lua
print(exports['meteo-jail']:IsAlarmPlaying()) --> false
```

***

## Events

```lua
-- server, any sentence change. reason: started, tick, added, reduced, set,
-- cleared, solitary_start, solitary_tick, solitary_set, solitary_complete, solitary_pulled
AddEventHandler('meteo-jail:server:sentenceChanged', function(citizenid, reason) end)

-- server, a player left prison (finished, released or escaped)
-- tally = { sentenced, served, commuted, remaining, startedAt, reason } or nil
AddEventHandler('meteo-jail:server:playerReleased', function(citizenid, source, tally) end)

-- server, the alarm, tunnel or meal changed. what: 'alarm' | 'tunnel' | 'meal'
AddEventHandler('meteo-jail:server:prisonChanged', function(what) end)
```

`tally.reason` is `completed`, `released`, `escaped` or `admin`.
