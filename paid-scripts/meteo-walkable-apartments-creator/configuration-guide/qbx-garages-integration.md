# QBX Garages Integration

Make apartment garages work with qbx_garages. Players can store and retrieve vehicles from their apartments.

***

## How it works

Meteo Apartments uses exports to communicate with qbx_garages. When a player uses an apartment garage, we:

1. Check if they have access to the apartment
2. Call qbx_garages exports to open garage menu or park vehicle
3. Garage name is based on apartment ID (e.g., `apartment_wiwang_hotel_6`)

{% hint style="info" %}
**Auto-creation.** If a garage doesn't exist, it's created automatically when first accessed. No manual garage configuration needed.
{% endhint %}

***

## Setup Instructions

{% stepper %}
{% step %}
### Add Client Export

Open `qbx_garages/client/main.lua` and add this at the end:

```lua
-- Property garage exports for meteo-apartments integration
local function openPropertyGarage(garageName, vehicleType)
    local garages = lib.callback.await('qbx_garages:server:getGarages')
    local garage = garages[garageName]

    if not garage then
        -- Auto-create property garage config
        garage = {
            label = garageName,
            type = 'property',
            vehicleType = vehicleType or VehicleType.CAR,
            shared = false,
        }
    end

    openGarageMenu(garageName, garage, 1)
end

exports('OpenPropertyGarage', openPropertyGarage)

local function parkPropertyVehicle(garageName)
    if not cache.vehicle then return false end
    parkVehicle(cache.vehicle, garageName)
    return true
end

exports('ParkPropertyVehicle', parkPropertyVehicle)
```


{% endstep %}

{% step %}
### Add Server Export

Open `qbx_garages/server/main.lua` and add this at the end:

```lua
-- Register property garage if it doesn't exist
local function ensurePropertyGarage(garageName, vehicleType)
    if not Garages[garageName] then
        local garage = {
            label = garageName,
            type = 'property',
            vehicleType = vehicleType or 'car',
            shared = false,
            skipGarageCheck = true,
            accessPoints = {},
        }
        registerGarage(garageName, garage)
    end
end

exports('EnsurePropertyGarage', ensurePropertyGarage)
```


{% endstep %}

{% step %}
### Restart qbx_garages

Restart the resource:

```
restart qbx_garages
```

That's it. Apartment garages will now work automatically.
{% endstep %}
{% endstepper %}

***

## How Meteo Apartments Uses It

When a player interacts with an apartment garage target:

```lua
-- Open garage (retrieve vehicles)
exports['qbx_garages']:OpenPropertyGarage(garageId, vehicleClass)

-- Park vehicle (store vehicle)
exports['qbx_garages']:ParkPropertyVehicle(garageId)

-- Ensure garage exists (called automatically)
exports['qbx_garages']:EnsurePropertyGarage(garageId, vehicleClass)
```

**Garage naming:**
- Garage ID format: `apartment_[apartmentId]`
- Example: `apartment_wiwang_hotel_6`

***

## Features

### Auto-Creation

Garages are created automatically when first accessed. No need to pre-configure garages for every apartment.

### Per-Apartment Storage

Each apartment has its own garage. Vehicles are stored separately per apartment.

### Vehicle Class Support

Configure different vehicle classes per apartment (car, boat, air, etc.) in the apartment creator.

***

## Troubleshooting

### Garage not opening?

Make sure you added both exports (client and server) and restarted qbx_garages.

### Vehicles not showing?

Check that the garage name matches the apartment ID. Enable debug mode in config.lua to see garage names.

{% hint style="warning" %}
**Important:** You must restart qbx_garages after adding the exports. A simple `/ensure` will not work.
{% endhint %}

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
