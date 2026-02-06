---
description: >-
  Server-side exports for integrating with meteo-dealerships. Check vehicle
  finance status from your own scripts.
---

# Useful Exports

## Quick Exports Reference Table

| Export                                              | Purpose                        | Side             |
| --------------------------------------------------- | ------------------------------ | ---------------- |
| `exports['meteo-dealerships']:isVehicleFinanced`    | Check if vehicle is financed   | Server side Only |
| `exports['meteo-dealerships']:getVehicleFinanceData`| Get full finance data          | Server side Only |
| `exports['meteo-dealerships']:isVehicleOverdue`     | Check if payments are overdue  | Server side Only |

***

{% stepper %}
{% step %}
### isVehicleFinanced

Check if a vehicle is currently financed.

Example

```lua
-- server-side
local plate = GetVehicleNumberPlateText(vehicle)
local result = exports['meteo-dealerships']:isVehicleFinanced(plate)

if result.financed then
    print('Vehicle is financed!')
    print('Remaining balance: $' .. result.data.balanceRemaining)
    -- Block sale or show warning
else
    print('Vehicle is not financed')
    -- Allow sale
end
```

#### Parameters

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>plate</td><td>string</td><td>Yes</td><td>Vehicle license plate</td></tr></tbody></table>

#### Returns

<table><thead><tr><th width="120">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>financed</td><td>boolean</td><td>Whether the vehicle is financed</td></tr><tr><td>data</td><td>table/nil</td><td>Finance data if financed, nil otherwise</td></tr></tbody></table>

#### Finance Data Structure

```lua
{
    dealership = "pdm",           -- Dealership where vehicle was financed
    totalPrice = 150000,          -- Total financed amount
    downPayment = 15000,          -- Initial down payment
    balanceRemaining = 100000,    -- Remaining balance
    monthlyPayment = 5000,        -- Payment amount per interval
    paymentsTotal = 24,           -- Total number of payments
    paymentsMade = 4,             -- Payments completed
    paymentsRemaining = 20,       -- Payments left
    interestRate = 10,            -- Interest rate percentage
    nextPaymentDue = 1738764800,  -- Unix timestamp of next payment
    lastPaymentAt = 1738678400,   -- Unix timestamp of last payment
    missedPayments = 0,           -- Number of missed payments
}
```

#### Practical Use Case

```lua
-- Block vehicle sale if financed
local function CanSellVehicle(source, plate)
    local result = exports['meteo-dealerships']:isVehicleFinanced(plate)

    if result.financed then
        QBCore.Functions.Notify(source, 'Cannot sell financed vehicle. Pay off $' .. result.data.balanceRemaining .. ' first.', 'error')
        return false
    end

    return true
end
```
{% endstep %}

{% step %}
### getVehicleFinanceData

Get full finance data for a vehicle. Returns nil if not financed.

Example

```lua
-- server-side
local financeData = exports['meteo-dealerships']:getVehicleFinanceData(plate)

if financeData then
    print('Balance remaining: $' .. financeData.balanceRemaining)
    print('Payments made: ' .. financeData.paymentsMade .. '/' .. financeData.paymentsTotal)
end
```

#### Parameters

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>plate</td><td>string</td><td>Yes</td><td>Vehicle license plate</td></tr></tbody></table>

#### Returns

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>table/nil</td><td>Finance data table or nil if not financed</td></tr></tbody></table>
{% endstep %}

{% step %}
### isVehicleOverdue

Check if a financed vehicle has overdue payments.

Example

```lua
-- server-side
local isOverdue = exports['meteo-dealerships']:isVehicleOverdue(plate)

if isOverdue then
    print('Vehicle has overdue payments!')
    -- Show warning, restrict usage, etc.
end
```

#### Parameters

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>plate</td><td>string</td><td>Yes</td><td>Vehicle license plate</td></tr></tbody></table>

#### Returns

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if overdue, false if not financed or payments current</td></tr></tbody></table>

#### Practical Use Case

```lua
-- Check if player's vehicle is overdue before allowing garage store
local function CanStoreVehicle(source, plate)
    local isOverdue = exports['meteo-dealerships']:isVehicleOverdue(plate)

    if isOverdue then
        QBCore.Functions.Notify(source, 'This vehicle has overdue payments! Visit the dealership.', 'error')
        return false
    end

    return true
end
```
{% endstep %}
{% endstepper %}
