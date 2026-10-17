---
description: >-
  Server-side and client-side exports for using meteo-restaurants in your own
  scripts.
---

# Useful Exports

## Quick Reference - Server Side

| Export                                                    | Purpose                    |
| --------------------------------------------------------- | -------------------------- |
| `exports['meteo-restaurants']:getRestaurant(id)`           | Get restaurant data        |
| `exports['meteo-restaurants']:getAllRestaurants()`          | Get all restaurants        |
| `exports['meteo-restaurants']:isEmployee(restId, cid)`     | Check if player is employee |
| `exports['meteo-restaurants']:isClockedIn(restId, cid)`    | Check if clocked in        |
| `exports['meteo-restaurants']:isOwner(restId, cid)`        | Check if player is owner   |
| `exports['meteo-restaurants']:hasPermission(restId, cid, perm)` | Check permission      |
| `exports['meteo-restaurants']:getPlayerEmployments(cid)`   | Get all player jobs        |
| `exports['meteo-restaurants']:hireEmployee(restId, cid, grade)` | Hire an employee      |
| `exports['meteo-restaurants']:fireEmployee(restId, cid)`   | Fire an employee           |
| `exports['meteo-restaurants']:getCompanyEarnings(restId)`  | Get restaurant balance     |
| `exports['meteo-restaurants']:depositMoney(restId, amount)` | Deposit to bank           |
| `exports['meteo-restaurants']:withdrawMoney(restId, amount)` | Withdraw from bank       |

## Quick Reference - Client Side

| Export                                                       | Purpose                          |
| ------------------------------------------------------------ | -------------------------------- |
| `exports['meteo-restaurants']:isEmployee(restId)`             | Check if local player is employee |
| `exports['meteo-restaurants']:isClockedIn(restId)`            | Check if clocked in              |
| `exports['meteo-restaurants']:isClockedInAnywhere()`          | Check if clocked in anywhere     |
| `exports['meteo-restaurants']:isOwner(restId)`                | Check if owner                   |
| `exports['meteo-restaurants']:hasPermission(restId, perm)`    | Check permission                 |
| `exports['meteo-restaurants']:isInsideRestaurantZone(restId)` | Check if inside restaurant zone  |
| `exports['meteo-restaurants']:getNearestRestaurant(maxDist)`  | Get nearest restaurant           |

***

{% stepper %}
{% step %}
**isEmployee**

Check if a player is an employee of a restaurant.

```lua
-- server-side
local isEmp = exports['meteo-restaurants']:isEmployee(restaurantId, citizenid)

if isEmp then
    print('Player is an employee')
end
```

```lua
-- client-side
local isEmp = exports['meteo-restaurants']:isEmployee(restaurantId)

if isEmp then
    print('You are an employee here')
end
```
{% endstep %}

{% step %}
**hasPermission**

Check if an employee has a specific permission.

```lua
-- server-side
local canCook = exports['meteo-restaurants']:hasPermission(restaurantId, citizenid, 'cook')

if canCook then
    -- allow cooking action
end
```

**Available permissions:** `cook`, `storage`, `orders`, `cancelOrder`, `clockOthers`, `hire`, `fire`, `forceClockOut`, `viewLogs`, `viewEarnings`, `deposit`, `withdraw`, `payCommission`, `payBonus`, `editCommissionRate`, `manageRestaurant`, `transferOwnership`, `editPrices`, `toggleShop`, `announce`, `manageApplications`
{% endstep %}

{% step %}
**getPlayerEmployments**

Get all restaurants a player works at.

```lua
-- server-side
local employments = exports['meteo-restaurants']:getPlayerEmployments(citizenid)

for restaurantId, emp in pairs(employments) do
    print(emp.restaurantName, emp.gradeLabel, emp.clockedIn)
end
```

**Returns:**

```lua
{
    restaurantId = 1,
    restaurantName = "Burger Shot",
    grade = 2,
    gradeLabel = "Manager",
    clockedIn = true,
    clockInTime = "2024-01-01 12:00:00",
    suspendedUntil = nil,
}
```
{% endstep %}

{% step %}
**hireEmployee / fireEmployee**

Manage employees from other scripts.

```lua
-- server-side - hire at grade 0
local success = exports['meteo-restaurants']:hireEmployee(restaurantId, citizenid, 0)

-- server-side - fire employee
local success = exports['meteo-restaurants']:fireEmployee(restaurantId, citizenid)
```
{% endstep %}

{% step %}
**getCompanyEarnings / depositMoney / withdrawMoney**

Manage restaurant bank from other scripts.

```lua
-- server-side
local balance = exports['meteo-restaurants']:getCompanyEarnings(restaurantId)
print('Restaurant Balance: $' .. balance)

-- deposit
local success = exports['meteo-restaurants']:depositMoney(restaurantId, 5000)

-- withdraw
local success = exports['meteo-restaurants']:withdrawMoney(restaurantId, 1000)
```
{% endstep %}

{% step %}
**Bank Exports**

For phone/banking integration:

```lua
-- get all restaurant bank accounts player has access to
local accounts = exports['meteo-restaurants']:getRestaurantBankAccounts(citizenid)

-- transfer from restaurant bank
local success, message, newBalance = exports['meteo-restaurants']:transferFromRestaurantBank(
    source, restaurantId, amount, recipientAccountNumber, note
)

-- check if player has any restaurant bank access
local hasAccess = exports['meteo-restaurants']:hasRestaurantBankAccess(citizenid)
```

{% hint style="info" %}
Bank exports need the player to have `viewEarnings` permission (usually Manager/Owner).
{% endhint %}
{% endstep %}
{% endstepper %}
