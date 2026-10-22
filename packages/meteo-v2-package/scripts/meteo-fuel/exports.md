---
description: >-
  Every meteo-fuel export with a simple example and what it gives back - read
  and set fuel, check for electric vehicles, and swap the payment method.
icon: code
---

# Exports

Read and set a vehicle's fuel from your own scripts, and plug in your own payment logic. Fuel exports are client side. The payment override is server side.

***

## Client: Fuel

### GetFuel(vehicle)

The vehicle's fuel level, `0.0` to `100.0`. Returns `0.0` if the vehicle does not exist.

```lua
local vehicle = GetVehiclePedIsIn(PlayerPedId(), false)
local fuel = exports['meteo-fuel']:GetFuel(vehicle)
print(fuel) --> 63.4
```

### SetFuel(vehicle, fuel)

Sets the fuel level. Values are clamped to `0` - `100`. Nothing happens if the vehicle does not exist or `fuel` is not a number.

```lua
exports['meteo-fuel']:SetFuel(vehicle, 100.0)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `vehicle` | number | Vehicle entity handle |
| `fuel` | number | `0` - `100` |

The level is also written to the vehicle's `fuel` statebag so other players and the server see it.

### IsElectricVehicle(vehicle)

`true` if the vehicle charges instead of fuelling. Uses the game's own electric flag plus `Config.electricVehicles`. Helicopters, planes and boats always return `false`, bicycles always return `true`.

```lua
if exports['meteo-fuel']:IsElectricVehicle(vehicle) then
    -- send them to a charger instead of a pump
end
```

***

## Client: Money Check

### setMoneyCheck(fn)

Replaces the "can the player afford this" check at the pump. `fn` takes no arguments and returns the amount of money the player has. Pass `nil` to go back to the default, which asks the server for the player's cash.

```lua
exports['meteo-fuel']:setMoneyCheck(function()
    return exports['my-wallet']:GetBalance()
end)
```

Use it together with `setPaymentMethod` on the server so the check and the charge come from the same place.

***

## Server: Payment

### setPaymentMethod(fn)

Replaces how fuel, jerrycans and jerrycan refills are paid for. By default the player pays in cash. Pass `nil` to go back to the default.

```lua
exports['meteo-fuel']:setPaymentMethod(function(playerId, amount, reason)
    local player = exports.qbx_core:GetPlayer(playerId)
    if not player then return false end
    return player.Functions.RemoveMoney('bank', amount, reason)
end)
```

| Argument | Type | Notes |
| -------- | ---- | ----- |
| `playerId` | number | Server id of the player paying |
| `amount` | number | Price, rounded to a whole number |
| `reason` | string | `fuel-purchase`, `jerrycan-purchase` or `jerrycan-refuel` |

Your function must return `true` when the payment went through. Returning anything else cancels the purchase.

{% hint style="info" %}
With a custom payment method set, the server's own cash check is skipped and your function owns the balance check.
{% endhint %}

***

## Server: Reading Fuel

There is no server `GetFuel` export. Read the vehicle's statebag instead:

```lua
local fuel = Entity(vehicle).state.fuel
print(fuel) --> 63.4   (nil if nobody has driven it yet)
```

Writing `Entity(vehicle).state.fuel` from the server also works - meteo-fuel picks the new value up on every client.

***

## Compatibility

meteo-fuel answers calls made to other fuel resources, so scripts written for them keep working without changes.

| Resource name | Exports |
| ------------- | ------- |
| `LegacyFuel` | `GetFuel`, `SetFuel` (client) |
| `ox_fuel` | `setMoneyCheck` (client), `setPaymentMethod` (server), plus the `fuel` statebag |
| `meteo-fuelv2` | `GetFuel`, `SetFuel`, `IsElectricVehicle` (client) |

```lua
-- an older script still calling LegacyFuel
exports['LegacyFuel']:SetFuel(vehicle, 100.0)
```

Do not run LegacyFuel or ox_fuel next to meteo-fuel.
