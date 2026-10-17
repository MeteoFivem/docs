---
description: >-
  Every meteo-restaurants export with a simple example and what it gives back -
  restaurants, employees, clock-in state, permissions, the business account,
  doors and recipes.
icon: code
---

# Exports

Check who works where, read and change a restaurant's staff and money, and open restaurant menus from your own scripts.

Restaurants are keyed by their numeric database id (`restaurantId`). Server exports take a citizenid. Client exports act on the calling player.

***

## Client: Employment

### isEmployee(restaurantId)

```lua
print(exports['meteo-restaurants']:isEmployee(1)) --> true
```

### isClockedIn(restaurantId) / isClockedInAnywhere()

```lua
print(exports['meteo-restaurants']:isClockedIn(1))        --> true
print(exports['meteo-restaurants']:isClockedInAnywhere()) --> true
```

### getClockedInRestaurant()

The restaurant the player is clocked in at, plus their employment, or `nil`.

```lua
local restaurantId, employment = exports['meteo-restaurants']:getClockedInRestaurant()
print(restaurantId, employment.gradeLabel) --> 1  Manager
```

### isSuspended(restaurantId)

```lua
print(exports['meteo-restaurants']:isSuspended(1)) --> false
```

### isOwner(restaurantId)

```lua
print(exports['meteo-restaurants']:isOwner(1)) --> false
```

### getGrade(restaurantId)

The player's grade number, or `nil` if they do not work there.

```lua
print(exports['meteo-restaurants']:getGrade(1)) --> 2
```

### hasPermission(restaurantId, permission)

Checks the permission against the player's grade in `Config.grades`. The owner grade (`all = true`) passes every check.

```lua
if exports['meteo-restaurants']:hasPermission(1, 'cook') then
    -- allowed
end
```

Permissions that ship with the config: `cook`, `storage`, `orders`, `cancelOrder`, `clockOthers`, `forceClockOut`, `hire`, `fire`, `viewLogs`, `viewEarnings`, `deposit`, `withdraw`, `payCommission`, `payBonus`, `editPrices`, `editCommissionRate`, `manageApplications`, `announce`, `manageRestaurant`, `transferOwnership`, `toggleShop`.

### getEmployment(restaurantId) / getAllEmployments()

```lua
local job = exports['meteo-restaurants']:getEmployment(1)
print(job.restaurantName, job.gradeLabel, job.clockedIn) --> Burger Shot  Manager  true
```

```lua
-- each employment:
{
    restaurantId   = 1,
    restaurantName = 'Burger Shot',
    grade          = 2,
    gradeLabel     = 'Manager',
    clockedIn      = true,
    clockInTime    = 1782300000,
    suspendedUntil = nil,
}
```

`getAllEmployments` returns every employment keyed by `restaurantId`.

***

## Client: Restaurants and Zones

### getRestaurant(restaurantId) / getAllRestaurants()

```lua
local r = exports['meteo-restaurants']:getRestaurant(1)
print(r.name, r.ownerName) --> Burger Shot  John Doe
```

`getAllRestaurants` returns every restaurant keyed by id.

### getNearestRestaurant(maxDistance?)

The closest restaurant location within `maxDistance` (default 100.0), plus the distance.

```lua
local restaurantId, dist = exports['meteo-restaurants']:getNearestRestaurant(50.0)
print(restaurantId, dist) --> 1  12.4
```

### isInsideRestaurant(restaurantId) / isInsideAnyRestaurant() / getCurrentRestaurantZone()

```lua
print(exports['meteo-restaurants']:isInsideRestaurant(1))      --> true
print(exports['meteo-restaurants']:isInsideAnyRestaurant())    --> true
print(exports['meteo-restaurants']:getCurrentRestaurantZone()) --> 1   (nil when outside)
```

### isDoorLocked(doorId)

```lua
print(exports['meteo-restaurants']:isDoorLocked(4)) --> true
```

### isCooking() / isProcessing() / isUsingItem()

`true` while the player is busy at a station or eating, so your script can wait or refuse.

```lua
if exports['meteo-restaurants']:isCooking() then return end
```

***

## Client: Menus

Each one does its own checks (employee, clocked in, permission), so you can bind them to your own targets or commands.

### openRestaurantMenu(restaurantId, mode?)

`mode` is `'employee'` (default) or `'manage'`.

```lua
exports['meteo-restaurants']:openRestaurantMenu(1, 'manage')
```

### openKitchenStorage(restaurantId) / openShopStash(restaurantId) / openPersonalStash(restaurantId)

```lua
exports['meteo-restaurants']:openKitchenStorage(1)
```

***

## Server: Restaurants

### getRestaurant(restaurantId) / getAllRestaurants()

```lua
local r = exports['meteo-restaurants']:getRestaurant(1)
print(r.name, r.owner) --> Burger Shot  ABC12345
```

```lua
-- restaurant:
{
    id = 1, name = 'Burger Shot',
    owner = 'ABC12345', ownerName = 'John Doe',   -- nil when unowned
    bank = 15000, totalSales = 320, totalRevenue = 48000, ordersCount = 210,
    commissionRate = 15, shopEnabled = 1, shopRevenue = 0,
    enabledCategories = { ... }, locations = { ... },
}
```

`getAllRestaurants` returns every restaurant keyed by id.

### isOwner(restaurantId, citizenid)

```lua
print(exports['meteo-restaurants']:isOwner(1, 'ABC12345')) --> true
```

***

## Server: Employees

### isEmployee(restaurantId, citizenid) / isClockedIn(restaurantId, citizenid)

```lua
local cid = exports.qbx_core:GetPlayer(source).PlayerData.citizenid
if exports['meteo-restaurants']:isClockedIn(1, cid) then
    -- on shift
end
```

### hasPermission(restaurantId, citizenid, permission)

Same permission keys as the client version.

```lua
print(exports['meteo-restaurants']:hasPermission(1, 'ABC12345', 'withdraw')) --> false
```

### getEmployee(restaurantId, citizenid)

```lua
local emp = exports['meteo-restaurants']:getEmployee(1, 'ABC12345')
print(emp.grade, emp.clockedIn) --> 2  1
```

Returns `{ restaurantId, citizenid, grade, clockedIn, clockInTime, suspendedUntil }` or `nil`. `clockedIn` is `0` or `1` here.

### getRestaurantEmployees(restaurantId)

Every employee keyed by citizenid, in the same shape as `getEmployee`.

```lua
for cid, emp in pairs(exports['meteo-restaurants']:getRestaurantEmployees(1)) do
    print(cid, emp.grade)
end
```

### getPlayerEmployments(citizenid)

Every restaurant a character works at, keyed by `restaurantId`, in the same shape as the client `getEmployment`.

```lua
local jobs = exports['meteo-restaurants']:getPlayerEmployments('ABC12345')
```

### hireEmployee(restaurantId, citizenid, grade?)

`grade` defaults to 0 (Employee).

```lua
local ok, err = exports['meteo-restaurants']:hireEmployee(1, 'ABC12345', 0)
print(ok, err) --> true  nil
```

Fails when the citizenid is empty, the person is the owner, or they already work there. `err` is a readable message.

### changeRank(restaurantId, citizenid, grade)

```lua
local ok, err = exports['meteo-restaurants']:changeRank(1, 'ABC12345', 2)
```

Error: `not_employee`.

### fireEmployee(restaurantId, citizenid)

```lua
local ok, err = exports['meteo-restaurants']:fireEmployee(1, 'ABC12345')
```

Error: `not_employee`.

### notifyRestaurantEmployees(restaurantId, message, type?)

Sends a notification to every clocked-in employee of the restaurant who is online.

```lua
exports['meteo-restaurants']:notifyRestaurantEmployees(1, 'Health inspection in 10 minutes', 'primary')
```

***

## Server: Money

The restaurant's business account. With meteo-banking running, it is the same account players see in the bank.

### getCompanyEarnings(restaurantId)

```lua
local e = exports['meteo-restaurants']:getCompanyEarnings(1)
print(e.bank, e.totalRevenue) --> 15000  48000
```

Returns `{ bank, totalSales, totalRevenue, ordersCount, commissionRate }`, or `nil` for an unknown restaurant.

### depositMoney(restaurantId, amount)

Adds money to the account. The transaction is labelled with your resource name.

```lua
local ok, err = exports['meteo-restaurants']:depositMoney(1, 500)
```

### withdrawMoney(restaurantId, amount)

Takes money out. Never overdraws.

```lua
local ok, err = exports['meteo-restaurants']:withdrawMoney(1, 500)
print(ok, err) --> false  insufficient_funds
```

Errors for both: `account_not_found`, `invalid_amount`, `insufficient_funds`, `server_error`.

***

## Server: Doors and Recipes

### lockAllDoors(restaurantId) / unlockAllDoors(restaurantId)

```lua
exports['meteo-restaurants']:lockAllDoors(1)
```

### getDoorsByRestaurant(restaurantId)

Every door of the restaurant, keyed by door id.

```lua
local doors = exports['meteo-restaurants']:getDoorsByRestaurant(1)
```

### getRecipe(itemName) / getRecipesByCategory(category)

Recipes from `shared/items.lua`.

```lua
local r = exports['meteo-restaurants']:getRecipe('meteo_sprunk')
print(r.label, r.price, r.category) --> Sprunk  8  drinks

local drinks = exports['meteo-restaurants']:getRecipesByCategory('drinks') -- keyed by item name
```
