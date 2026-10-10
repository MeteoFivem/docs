---
description: >-
  Every meteo-garages export with a simple example and what it gives back -
  owned vehicles, saving vehicle state, garage labels, mileage and property
  garages.
icon: code
---

# Exports

Read and update owned vehicles, look up garages and open a garage from your own housing or job script. Exports are server side. Property garages are opened with client events.

***

## Server: Owned Vehicles

### GetPlayerVehicles(filters)

Owned vehicles from `player_vehicles` that match every filter you pass.

```lua
local vehicles = exports['meteo-garages']:GetPlayerVehicles({
    citizenid = 'ABC12345',
    states = { 1 },          -- garaged only
})

for _, v in ipairs(vehicles) do
    print(v.id, v.modelName, v.garage)
end
--> 14   sultan     pillboxgarage
--> 22   kuruma     legion
```

| Filter | Type | Notes |
| ------ | ---- | ----- |
| `citizenid` | string | Owner |
| `garage` | string | Garage id |
| `states` | number / number\[] | `0` out, `1` garaged, `2` impounded |
| `vehicleId` | number | One vehicle by its database id |

{% hint style="warning" %}
Always pass at least one filter. An empty table builds an invalid query.
{% endhint %}

```lua
-- each vehicle:
{
    id            = 14,
    citizenid     = 'ABC12345',
    modelName     = 'sultan',
    garage        = 'pillboxgarage',
    state         = 1,             -- 0 out | 1 garaged | 2 impounded
    depotPrice    = 0,
    impoundReason = nil,
    isFavorite    = false,
    mileage       = 1240.5,        -- km
    props         = { ... },       -- vehicle properties (mods, colours, plate)
}
```

### GetPlayerVehicle(vehicleId, filters?)

One vehicle by its database id, or `nil`. `filters` takes the same fields as above, so you can also check ownership in one call.

```lua
local v = exports['meteo-garages']:GetPlayerVehicle(14, { citizenid = 'ABC12345' })
print(v and v.modelName) --> sultan
--> nil when vehicle 14 is not owned by ABC12345
```

### GetVehicleIdByPlate(plate)

The database id for a plate, or `nil`. The plate is trimmed for you.

```lua
local id = exports['meteo-garages']:GetVehicleIdByPlate('ABC 123')
print(id) --> 14
```

### DoesPlayerVehiclePlateExist(plate)

`true` if any player owns a vehicle with this plate. Use it before handing out a custom plate.

```lua
if exports['meteo-garages']:DoesPlayerVehiclePlateExist('MYPLATE') then
    -- plate already taken
end
```

### SaveVehicle(vehicle, options)

Writes a spawned vehicle's state back to the database. The vehicle is matched by its garage id, or by plate.

```lua
local ok, err = exports['meteo-garages']:SaveVehicle(vehicle, {
    state = 1,
    garage = 'pillboxgarage',
    props = lib.getVehicleProperties(vehicle), -- from the client
})
print(ok) --> true
```

| Option | Type | Notes |
| ------ | ---- | ----- |
| `state` | number | `0` out, `1` garaged, `2` impounded |
| `garage` | string | Garage id |
| `depotPrice` | number | Price to get it out of the depot |
| `props` | table | Vehicle properties. Also saves `plate`, `fuelLevel`, `engineHealth` and `bodyHealth` from it |

Pass at least one option. Returns `true`, or `false` plus `{ code = 'not_owned', message }` when the vehicle is not a player vehicle.

### GetVehicleMileage(vehicleId)

The live mileage in km, or `nil` if the vehicle does not exist.

```lua
local km = exports['meteo-garages']:GetVehicleMileage(14)
print(km) --> 1240.5
```

***

## Server: Garages

### GetGarageLabel(garageId)

The label of a garage, impound or depot. Anything not in the config (a property garage) returns `'Private Garage'`.

```lua
print(exports['meteo-garages']:GetGarageLabel('pillboxgarage')) --> Pillbox Garage
```

### GetGarageInfo(garageId)

The label and map position of a garage, impound or depot, or `nil` if it is not in the config.

```lua
local info = exports['meteo-garages']:GetGarageInfo('pillboxgarage')
print(json.encode(info))
--> { "label": "Pillbox Garage", "x": 215.8, "y": -810.0, "impound": false }
```

`impound` is `true` for impounds and depots.

***

## Server: Towing

### IsTower(source)

`true` if the player has one of the tow jobs from the towing config (and is on duty, when on-duty only is enabled).

```lua
if exports['meteo-garages']:IsTower(source) then
    -- show your tow menu
end
```

***

## Client: Property Garages

A housing script can open a garage that is not in the config. Use any unique id per property, for example `'property_42'`. Vehicles parked there only show up in that garage.

### Open the garage menu

```lua
TriggerEvent('meteo-garages:client:openPropertyGarage', 'property_42', 'car', vector4(-12.4, -1439.2, 30.5, 180.0))
```

| Argument | Type | Notes |
| -------- | ---- | ----- |
| `garageId` | string | Required |
| `vehicleClass` | string | Optional, defaults to `'car'` |
| `spawnPoint` | vector4 | Optional. Where the vehicle spawns, if the spot is clear |

### Park the current vehicle

```lua
TriggerEvent('meteo-garages:client:parkPropertyVehicle', 'property_42', 'car')
```

The player has to be in a vehicle. `vehicleClass` defaults to `'all'`.
