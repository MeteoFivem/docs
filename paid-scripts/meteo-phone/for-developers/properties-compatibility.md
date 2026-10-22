---
description: How the Properties app integrates with housing scripts, and how to add support for a custom one.
icon: house
---

# Properties App Compatibility

The Properties app on Meteo Phone shows every property a player owns (or holds keys to) across the housing scripts running on your server. Each entry has a "Set Waypoint" action that drops a GPS marker at the property's entry point.

The app uses a small **provider registry** so each housing script gets its own self-contained file. Out of the box we ship providers for the most common housing scripts, and you can drop in your own provider for any other script in a few lines of Lua.

***

## Supported Out of the Box

| Provider | Resource Name | Owned | Keyholders |
|----------|---------------|:-----:|:----------:|
| Meteo Apartments | `meteo-apartments` | Yes | - |
| Meteo Properties | `meteo-properties` | Yes | - |
| Skeleton Networks Properties | `sn_properties` | Yes | Yes |
| Vames Store Housing | `vms_housing` | Yes | - |

Each provider lives in its own file under:

```
meteo-phone/server/source/properties/
├── meteo-apartments.lua
├── meteo-properties.lua
├── sn_properties.lua
└── vms_housing.lua
```

This folder is **escrow-open**, so you can edit, remove, or add files freely without breaking the rest of the resource.

{% hint style="info" %}
**Auto-detection**

A provider only runs when its target resource is `started`. If the resource is missing or stopped, the provider is silently skipped, and the Properties app simply hides anything it would have contributed.
{% endhint %}

***

## What Each Provider Reads

### meteo-apartments

Reads owned apartments via `exports['meteo-apartments']:getOwnedPropertiesForPhone(citizenid)`. Apartment entries get the apartment icon and show extra fields in the detail view: **Complex** and **Room number**.

### meteo-properties

Reads owned houses via `exports['meteo-properties']:getOwnedPropertiesForPhone(citizenid)`. Each entry's `propertyType` (`mlo` or `shell`) drives the icon.

### sn_properties (Skeleton Networks)

Reads from <a href="https://skeletonnetworks.gitbook.io/skeletonnetworks/properties/exports/server-exports" target="_blank">`exports.sn_properties:getPlayerProperties(citizenid)`</a>. Returns both **owned** and **keyholder** entries. When `isOwner = false`, a small "Keyholder" pill is shown next to the property name and the detail view shows an Access row indicating keys-only access.

### vms_housing (Vames Store)

Reads from <a href="https://docs.vames-store.com/assets/vms_housing/developer-api/server-exports" target="_blank">`exports.vms_housing:GetPlayerProperties(citizenid)`</a> using `metadata.enter` for the entry coordinates. vms_housing only exposes owned properties via this export, so keyholders are not included.

***

## Adding a Custom Provider

If your server uses a housing script that is not in the list above, you can register it in a single Lua file. The phone will pick it up automatically the next time the resource starts.

### Step 1 - Create the file

Add a new file under `meteo-phone/server/source/properties/`. Name it after the resource you are integrating with (for example `qb-houses.lua`).

### Step 2 - Register the provider

Call `RegisterPhonePropertyProvider` with three fields: a unique `id`, the `resource` name to gate on, and a `fetch` function that returns the player's properties.

```lua
-- meteo-phone/server/source/properties/qb-houses.lua

RegisterPhonePropertyProvider({
    id = 'qb-houses',
    resource = 'qb-houses',
    fetch = function(citizenid)
        local rows = MySQL.query.await(
            'SELECT house, coords FROM player_houses WHERE citizenid = ?',
            { citizenid }
        )
        if not rows then return nil end

        local list = {}
        for _, row in ipairs(rows) do
            local coords = json.decode(row.coords) or {}
            list[#list + 1] = {
                id    = row.house,
                label = row.house,
                coords = { x = coords.x, y = coords.y, z = coords.z },
                type  = 'mlo',
                isOwner = true,
            }
        end
        return list
    end,
})
```

### Step 3 - Restart the resource

`ensure meteo-phone`. The new provider is active.

***

## The Return Shape

Your `fetch(citizenid)` function should return an array of property tables. Only `id` and `coords` are strictly required, the rest are optional.

| Field | Type | Description |
|-------|------|-------------|
| `id` | any | Unique identifier for the property (used internally only). |
| `label` | string | Display name shown in the list and detail header. |
| `coords` | `vector3` or `{x,y,z}` table | Entry coordinates. Used for the waypoint button. |
| `type` | string | One of `apartment`, `mlo`, `shell`, `ipl`, `motorhome`. Drives the icon and subtitle. Defaults to a generic house if omitted. |
| `zone` | string | Optional zone/area name. When present, it shows in the detail view. |
| `isOwner` | boolean | `true` for owners, `false` for keyholders. Defaults to `true` when omitted. |

### Type to Icon Mapping

| `type` | Icon | Subtitle |
|--------|------|----------|
| `apartment` | apartment | Apartment |
| `mlo` | villa | House (MLO) |
| `shell` | house | House (Shell) |
| `ipl` | location_city | House (IPL) |
| `motorhome` | rv_hookup | Motorhome |
| _(omitted / other)_ | home | House |

{% hint style="success" %}
**Keyholder support**

If your housing script tracks people who hold keys but do not own the property, return them in the same list with `isOwner = false`. They appear with a small **Keyholder** pill in the list and an Access row in the detail view.
{% endhint %}

***

## How It Works Under the Hood

`server/apps/sv_properties.lua` exposes one global function:

```lua
RegisterPhonePropertyProvider({ id, resource, fetch })
```

When a player opens the Properties app, the server iterates every registered provider, skips any whose `resource` is not `started`, calls `fetch(citizenid)`, normalizes the coords to a JSON-safe table, and merges everything into a single list before sending it to the UI.

Because every provider lives in its own file, removing support for a script is as simple as deleting its `.lua` file. Adding support for a new one is a single `RegisterPhonePropertyProvider` call.

***

{% hint style="success" %}
**Need help integrating a specific housing script?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
