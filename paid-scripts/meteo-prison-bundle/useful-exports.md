---
description: Server side exports for the meteo-jail script. Use these from your MDT, admin menu or any other resource that needs to interact with the prison system.
---

# Useful Exports

## Quick Exports Reference Table

| Export                                       | Purpose                                  | Side             |
| -------------------------------------------- | ---------------------------------------- | ---------------- |
| `exports['meteo-jail']:JailPlayer`           | Jail a player by server ID               | Server side Only |
| `exports['meteo-jail']:UnjailPlayer`         | Release a jailed player                  | Server side Only |
| `exports['meteo-jail']:SolitaryPlayer`       | Send a jailed player to solitary         | Server side Only |
| `exports['meteo-jail']:UnsolitaryPlayer`     | Remove a player from solitary            | Server side Only |
| `exports['meteo-jail']:GetJailedPlayers`     | Get every currently jailed player        | Server side Only |
| `exports['meteo-jail']:GetSentence`          | Get a player's remaining jail time       | Server side Only |
| `exports['meteo-jail']:GetSolitaryTime`      | Get a player's remaining solitary time   | Server side Only |
| `exports['meteo-jail']:IsPlayerInPrison`     | Check if a player is in the prison zone  | Server side Only |
| `exports['meteo-jail']:SetAlarmState`        | Toggle the prison alarm globally         | Server side Only |
| `exports['meteo-jail']:GetAlarmState`        | Get the current prison alarm state       | Server side Only |
| `exports['meteo-jail']:IsTunnelOpen`         | Check if the escape tunnel is open       | Server side Only |

{% hint style="warning" %}
The mutating exports (`JailPlayer`, `UnjailPlayer`, `SolitaryPlayer`, `UnsolitaryPlayer`) require an invoking resource context (they are called via `exports[...]`, not from inside meteo-jail itself). The caller is responsible for any permission checks.
{% endhint %}

{% stepper %}
{% step %}
#### JailPlayer

Jail a player by their server ID. Confiscates their items, cash, bank and clothing, applies the prison outfit, runs the mugshot, and starts their sentence.

Example

```lua
-- server-side
local result = exports['meteo-jail']:JailPlayer(targetSource, jailTime, jailerName)

-- Real example: jail player from MDT for 30 months
local result = exports['meteo-jail']:JailPlayer(15, 30, 'Officer Smith')

if result.success then
    print('Jailed:', result.targetName)
else
    print('Failed:', result.message)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>targetSource</td><td>number</td><td>Yes</td><td>Player server ID to jail</td></tr><tr><td>jailTime</td><td>number</td><td>Yes</td><td>Sentence in months (must be > 0)</td></tr><tr><td>jailerName</td><td>string</td><td>No</td><td>Name shown to the inmate (default: 'System')</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="120">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>true if jailed</td></tr><tr><td>message</td><td>string</td><td>Error message when success is false</td></tr><tr><td>targetName</td><td>string</td><td>Player full name on success</td></tr></tbody></table>
{% endstep %}

{% step %}
#### UnjailPlayer

Release a jailed player. Restores their cash, bank and clothing and clears any solitary time. Confiscated items remain in their belongings stash for them to pick up at the belongings ped.

Example

```lua
-- server-side
local result = exports['meteo-jail']:UnjailPlayer(targetSource)

if result.success then
    print('Released:', result.targetName)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>targetSource</td><td>number</td><td>Yes</td><td>Player server ID to release</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="120">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>true if released</td></tr><tr><td>message</td><td>string</td><td>Error message when success is false</td></tr><tr><td>targetName</td><td>string</td><td>Player full name on success</td></tr></tbody></table>
{% endstep %}

{% step %}
#### SolitaryPlayer

Send a jailed player to solitary. The player must already be jailed and not currently in solitary.

Example

```lua
-- server-side
local result = exports['meteo-jail']:SolitaryPlayer(15, 5) -- 5 months in solitary

if result.success then
    print('Sent to solitary:', result.targetName)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>targetSource</td><td>number</td><td>Yes</td><td>Player server ID</td></tr><tr><td>solitaryTime</td><td>number</td><td>Yes</td><td>Solitary time in months (must be > 0)</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="120">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>true if sent to solitary</td></tr><tr><td>message</td><td>string</td><td>Error message when success is false</td></tr><tr><td>targetName</td><td>string</td><td>Player full name on success</td></tr></tbody></table>
{% endstep %}

{% step %}
#### UnsolitaryPlayer

Remove a player from solitary early. Their main jail sentence is not affected.

Example

```lua
-- server-side
local result = exports['meteo-jail']:UnsolitaryPlayer(15)
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>targetSource</td><td>number</td><td>Yes</td><td>Player server ID</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="120">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>true if removed from solitary</td></tr><tr><td>message</td><td>string</td><td>Error message when success is false</td></tr><tr><td>targetName</td><td>string</td><td>Player full name on success</td></tr></tbody></table>
{% endstep %}

{% step %}
#### GetJailedPlayers

Get every player who is currently jailed. Useful for MDT inmate lists, dashboards or admin tools.

Example

```lua
-- server-side
local jailed = exports['meteo-jail']:GetJailedPlayers()

for _, inmate in ipairs(jailed) do
    print(inmate.name, '-', inmate.jailTime, 'months left, solitary:', inmate.solitaryTime)
end
```

**Returns**

A table of inmate entries, each with these fields:

<table><thead><tr><th width="140">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>source</td><td>number</td><td>Player server ID</td></tr><tr><td>citizenid</td><td>string</td><td>Player citizen ID</td></tr><tr><td>name</td><td>string</td><td>Player full name</td></tr><tr><td>jailTime</td><td>number</td><td>Remaining sentence in months</td></tr><tr><td>solitaryTime</td><td>number</td><td>Remaining solitary time in months</td></tr></tbody></table>
{% endstep %}

{% step %}
#### GetSentence

Get a player's remaining jail time in months.

Example

```lua
-- server-side
local months = exports['meteo-jail']:GetSentence(15)

if months > 0 then
    print('Player is jailed with', months, 'months left')
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>targetSource</td><td>number</td><td>Yes</td><td>Player server ID</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>number</td><td>Remaining jail time in months (0 if not jailed)</td></tr></tbody></table>
{% endstep %}

{% step %}
#### GetSolitaryTime

Get a player's remaining solitary time in months.

Example

```lua
-- server-side
local months = exports['meteo-jail']:GetSolitaryTime(15)
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>targetSource</td><td>number</td><td>Yes</td><td>Player server ID</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>number</td><td>Remaining solitary time in months (0 if not in solitary)</td></tr></tbody></table>
{% endstep %}

{% step %}
#### IsPlayerInPrison

Check if a player is currently inside the prison zone.

Example

```lua
-- server-side
if exports['meteo-jail']:IsPlayerInPrison(source) then
    -- block contraband drops, gun usage, etc.
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>source</td><td>number</td><td>Yes</td><td>Player server ID</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if inside the prison zone, false otherwise</td></tr></tbody></table>
{% endstep %}

{% step %}
#### SetAlarmState

Turn the prison alarm on or off for every player. Used internally when a tunnel breaks; you can also trigger it from your own scripts (e.g. a manual riot event).

Example

```lua
-- server-side
exports['meteo-jail']:SetAlarmState(true)  -- start alarm
exports['meteo-jail']:SetAlarmState(false) -- stop alarm
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>shouldPlay</td><td>boolean</td><td>Yes</td><td>true to start the alarm, false to stop it</td></tr></tbody></table>
{% endstep %}

{% step %}
#### GetAlarmState

Read the current prison alarm state.

Example

```lua
-- server-side
local active = exports['meteo-jail']:GetAlarmState()
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if the alarm is currently on</td></tr></tbody></table>
{% endstep %}

{% step %}
#### IsTunnelOpen

Check if the escape tunnel is currently dug open.

Example

```lua
-- server-side
if exports['meteo-jail']:IsTunnelOpen() then
    print('Tunnel is open - inmates can escape')
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if the tunnel is open</td></tr></tbody></table>
{% endstep %}
{% endstepper %}

***

## Practical Use Case - MDT Integration

```lua
-- In your MDT server-side code, after the officer hits "send to jail":
RegisterNetEvent('my-mdt:server:jailFromMDT', function(targetId, months, charges)
    local src = source
    local Player = exports['qb-core']:GetCoreObject().Functions.GetPlayer(src)
    if not Player or Player.PlayerData.job.type ~= 'leo' then return end

    local jailerName = Player.PlayerData.charinfo.firstname .. ' ' .. Player.PlayerData.charinfo.lastname
    local result = exports['meteo-jail']:JailPlayer(targetId, months, jailerName)

    if result.success then
        TriggerClientEvent('QBCore:Notify', src, ('Jailed %s for %d months'):format(result.targetName, months), 'success')
    else
        TriggerClientEvent('QBCore:Notify', src, result.message, 'error')
    end
end)
```

***

## Need Help?

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
