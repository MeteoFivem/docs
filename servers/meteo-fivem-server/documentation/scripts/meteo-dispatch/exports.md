---
description: >-
  Use meteo-dispatch exports to send dispatch alerts from your own scripts -
  robberies, shootings, medical calls and more.
icon: code
---

# Exports

Want your own script to send alerts to police or EMS? meteo-dispatch has a simple `AddCall` export for that. One function call and the alert shows up on the dispatch UI with sound, blip and all the details.

{% hint style="info" %}
Works from both server and client. The client version just triggers the server one internally, so the parameters are exactly the same.
{% endhint %}

***

## AddCall

```lua
exports['meteo-dispatch']:AddCall(data)
```

Returns the call ID as a `number` if the call was created, or `nil` if it failed.

### Parameters

The `data` table accepts:

| Field             | Type   | Required | Description                                                     |
| ----------------- | ------ | -------- | --------------------------------------------------------------- |
| `code`            | string | Yes      | Police code, e.g. `'10-35'`, `'10-71'`                          |
| `title`           | string | Yes      | Short title for the call                                        |
| `description`     | string | Yes      | Detailed description                                            |
| `location`        | string | Yes      | Street and zone name                                            |
| `street`          | string | Yes      | Street name (can be same as location)                           |
| `coords`          | table  | Yes      | Coordinates `{x, y, z}`                                         |
| `callType`        | string | No       | `'auto'` (default), `'911'`, `'panic'`                          |
| `priority`        | number | No       | 1 = high, 2 = medium, 3 = low (default: `3`)                    |
| `jobFilter`       | string | No       | `'leo'`, `'ems'` or `'all'` (default: `'all'`)                  |
| `callerCitizenid` | string | No       | Caller's citizenid, for tracking                                |
| `callerName`      | string | No       | Caller's name                                                   |
| `callerPhone`     | string | No       | Caller's phone number                                           |
| `metadata`        | table  | No       | Extra info shown on the call (weapon, vehicle, plate and so on) |

***

## Examples

### Vehicle Theft Alert

```lua
local coords = GetEntityCoords(vehicle)
local plate = QBCore.Functions.GetPlate(vehicle)
local vehicleModel = GetDisplayNameFromVehicleModel(GetEntityModel(vehicle))
local vehicleLabel = GetLabelText(vehicleModel)

exports['meteo-dispatch']:AddCall({
    code = '10-35',
    title = 'Vehicle Theft',
    description = 'Vehicle being stolen',
    location = GetStreetAndZone(coords),
    street = GetStreetAndZone(coords),
    coords = { x = coords.x, y = coords.y, z = coords.z },
    priority = 1,
    jobFilter = 'leo',
    metadata = {
        vehicle = vehicleLabel,
        plate = plate
    }
})
```

### Store Robbery Alert

```lua
local coords = GetEntityCoords(cache.ped)

exports['meteo-dispatch']:AddCall({
    code = '10-65',
    title = 'Armed Robbery',
    description = 'Store robbery in progress',
    location = GetStreetAndZone(coords),
    street = GetStreetAndZone(coords),
    coords = { x = coords.x, y = coords.y, z = coords.z },
    priority = 1,
    jobFilter = 'leo'
})
```

### Medical Emergency

```lua
local coords = GetEntityCoords(cache.ped)

exports['meteo-dispatch']:AddCall({
    code = '10-52',
    title = 'Medical Emergency',
    description = 'Person down, needs medical attention',
    location = GetStreetAndZone(coords),
    street = GetStreetAndZone(coords),
    coords = { x = coords.x, y = coords.y, z = coords.z },
    priority = 1,
    jobFilter = 'ems'
})
```

### Helper Function

The examples above use this little helper to get a readable street and zone from coordinates:

```lua
function GetStreetAndZone(coords)
    local zone = GetLabelText(GetNameOfZone(coords.x, coords.y, coords.z))
    local street = GetStreetNameFromHashKey(GetStreetNameAtCoord(coords.x, coords.y, coords.z))
    return street .. ", " .. zone
end
```

***

## Priorities and Job Filters

| Priority | Color  | When to use                       |
| -------- | ------ | --------------------------------- |
| 1        | Red    | High - immediate response needed  |
| 2        | Orange | Medium - respond when available   |
| 3        | Yellow | Low - non-urgent                  |

| Filter  | Who gets the alert          |
| ------- | --------------------------- |
| `'leo'` | Law enforcement only        |
| `'ems'` | EMS/Fire only               |
| `'all'` | Every dispatch-enabled job  |

***

## Police Codes Reference

<details>

<summary>Call types and codes used by the script</summary>

### Call Types

| Code | Description                   |
| ---- | ----------------------------- |
| 911  | Emergency call from civilian  |
| 911E | Medical emergency call        |
| 911A | Anonymous emergency tip       |
| 311  | Non-emergency call            |

### Emergency Codes

| Code   | Description               |
| ------ | ------------------------- |
| 10-35  | Vehicle theft             |
| 10-65  | Armed robbery             |
| 10-71  | Shooting                  |
| 10-71V | Vehicle shooting          |
| 10-78  | Officer needs assistance  |
| 10-80  | Explosion                 |
| 10-99  | Officer down              |

### Common Codes

| Code   | Description                  |
| ------ | ---------------------------- |
| 10-11  | Shots fired                  |
| 10-14  | Prowler / vehicle tampering  |
| 10-16  | Domestic disturbance         |
| 10-31  | Reckless driving             |
| 10-32  | Weapons violation            |
| 10-52  | Medical emergency            |
| 10-55  | Traffic hazard               |
| 10-57  | Missing person               |
| 10-59  | Theft report                 |
| 10-66  | Suspicious person/vehicle    |
| 10-85  | Drug activity                |
| 10-87  | Suspicious package           |
| 10-91  | Suspicious activity          |
| 10-96  | Abandoned vehicle            |
| 10-415 | Noise complaint              |

</details>

***

## Alert Sounds

Every alert plays a sound based on its priority, and you can override the sound for specific codes. It all lives in the config.

### Native GTA Sounds (Recommended)

```lua
Config.sounds = {
    enabled = true,
    priority = {
        [1] = { type = 'native', sound = 'Lose_1st', soundset = 'GTAO_FM_Events_Soundset' },
        [2] = { type = 'native', sound = 'Boss_Message', soundset = 'GTAO_Boss_Goons_FM_Soundset' },
        [3] = { type = 'native', sound = 'Text_Arrive_Tone', soundset = 'Phone_SoundSet_Default' }
    },
    custom = {
        ['10-99'] = { type = 'native', sound = 'Lose_1st', soundset = 'GTAO_FM_Events_Soundset' },
    }
}
```

### Custom Audio Files

Prefer your own sounds? Drop audio files into the `web/sounds/` folder and point the config at them:

```lua
Config.sounds.custom = {
    ['10-71'] = { type = 'custom', file = 'shots_fired.ogg' },
    ['911'] = { type = 'custom', file = 'emergency_call.ogg' },
}
```

<details>

<summary>Handy native sounds to try</summary>

| Sound                | Soundset                               | Description        |
| -------------------- | -------------------------------------- | ------------------ |
| `Lose_1st`           | `GTAO_FM_Events_Soundset`              | Dramatic alert     |
| `Boss_Message`       | `GTAO_Boss_Goons_FM_Soundset`          | Message tone       |
| `Text_Arrive_Tone`   | `Phone_SoundSet_Default`               | Phone notification |
| `CONFIRM_BEEP`       | `HUD_MINI_GAME_SOUNDSET`               | Confirmation beep  |
| `CHECKPOINT_NORMAL`  | `HUD_MINI_GAME_SOUNDSET`               | Checkpoint sound   |
| `Mission_Pass_Notify`| `DLC_HEISTS_GENERAL_FRONTEND_SOUNDS`   | Success sound      |
| `Hack_Failed`        | `DLC_HEIST_BIOLAB_PREP_HACKING_SOUNDS` | Failure sound      |

</details>

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
