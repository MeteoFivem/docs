---
description: >-
  Use meteo-dailyrewards exports to hook your own job scripts into daily tasks
  and the economy boost system.
icon: code
---

# Exports

Want your own job script to count toward daily tasks and pay out economy boost bonuses? meteo-dailyrewards has a few server exports for that. Track progress when a player finishes something, show their daily progress in your UI, and hand out boost money without writing any of the logic yourself.

{% hint style="info" %}
All exports are server side. Always wrap them in a resource state check so your script keeps working even if daily rewards is disabled:

```lua
if GetResourceState('meteo-dailyrewards') == 'started' then
    -- use exports here
end
```
{% endhint %}

***

## TrackTaskCompletion

Call this whenever a player completes a trackable action (a route, a delivery, a cleaned spot and so on). The script checks if the player has a daily task of that type and adds the progress.

```lua
exports['meteo-dailyrewards']:TrackTaskCompletion(source, trackingType, amount)
```

* `source` - player server ID
* `trackingType` - the task type to track, e.g. `'bus_route'` (see the table below)
* `amount` - optional, how much to add (default: `1`)

Returns a table, or `nil` if the player wasn't found:

```lua
{
    hasDailyTask = boolean,      -- player has a daily task of this type
    progress = number,           -- current progress
    target = number,             -- amount needed to complete the task
    taskCompleted = boolean,     -- the task just got completed
    milestoneReached = boolean,  -- a milestone unlocked (2/5/7 tasks)
    totalCompleted = number      -- total tasks completed today
}
```

### Tracking Types

These are the types currently defined in the config. If you add your own task pool you can invent new ones - whatever you set as `trackingType` in the config is what you pass here.

| Tracking Type       | Counts                     | Job             |
| ------------------- | -------------------------- | --------------- |
| `bus_route`         | Bus routes completed       | Bus Job         |
| `cleaning_spot`     | Individual spots cleaned   | Cleaning Job    |
| `cleaning_route`    | Cleaning routes completed  | Cleaning Job    |
| `delivery_package`  | Packages delivered         | Delivery Job    |
| `delivery_route`    | Delivery routes completed  | Delivery Job    |
| `electrician_route` | Electrician routes done    | Electrician Job |
| `electrician_box`   | Electrical boxes repaired  | Electrician Job |
| `fishing_catch`     | Fish caught                | Fishing Job     |
| `gruppe6_route`     | Security routes completed  | Gruppe 6 Job    |
| `gruppe6_package`   | Security packages moved    | Gruppe 6 Job    |
| `repo_vehicle`      | Vehicles collected         | Repo Job        |
| `taxi_passenger`    | Passengers transported     | Taxi Job        |

### Example

```lua
-- player cleaned 10 spots in one go
local result = exports['meteo-dailyrewards']:TrackTaskCompletion(source, 'cleaning_spot', 10)

if result and result.taskCompleted then
    QBCore.Functions.Notify(source, 'Daily task completed!', 'success')
end

if result and result.milestoneReached then
    QBCore.Functions.Notify(source, 'Milestone reward available!', 'primary')
end
```

***

## GetDailyProgress

Gets how many daily tasks the player has done today. Handy for showing "Daily Tasks: 3/7" in your job UI.

```lua
exports['meteo-dailyrewards']:GetDailyProgress(source)
```

Returns a table, or `nil` if the player wasn't found:

```lua
{
    completed = number,  -- tasks completed today
    total = number,      -- total tasks for the day (7 by default)
    text = string        -- ready-made "3/7" string
}
```

### Example

```lua
local progress = exports['meteo-dailyrewards']:GetDailyProgress(source)

if progress then
    QBCore.Functions.Notify(source, 'Daily Tasks: ' .. progress.text, 'primary')
end
```

***

## Economy Boost Exports

The economy boost multiplies job payments (2x or 3x) until the player earns a random bonus target between $4000 and $8000. Once the target is reached the boost ends. These exports let your job script take part in that.

### GiveEconomyBoostReward

**This is the one you want for job integrations.** Give it the money the player just earned and it does everything - checks if a boost is active, calculates the bonus, pays it out and notifies the player.

```lua
exports['meteo-dailyrewards']:GiveEconomyBoostReward(source, totalMoneyEarned)
```

* `source` - player server ID
* `totalMoneyEarned` - the money the player just earned from your job

Returns nothing. The bonus is `(multiplier - 1) x totalMoneyEarned`, so a 2x boost pays 100% extra and a 3x boost pays 200% extra on top of what you already paid.

```lua
-- pay the job reward like normal, then let the boost add its bonus
Player.Functions.AddMoney('cash', finalReward, 'job-payment')

if GetResourceState('meteo-dailyrewards') == 'started' then
    exports['meteo-dailyrewards']:GiveEconomyBoostReward(source, finalReward)
end
```

### GetEconomyBoost

Check the player's current boost status. Useful if you want to show the boost in your own UI.

```lua
exports['meteo-dailyrewards']:GetEconomyBoost(source)
```

Returns a table, or `nil` if the boost system is disabled in config or the player wasn't found:

```lua
{
    active = boolean,           -- boost is running right now
    multiplier = number,        -- 2 or 3
    earned = number,            -- bonus money earned so far
    target = number,            -- bonus target to reach
    remaining = number,         -- bonus left until the boost ends
    canActivateToday = boolean  -- player can still activate a boost today
}
```

### ApplyEconomyBoost

Lower level option. Multiplies an amount by the active boost and tracks the bonus, but **does not give any money** - paying the player is on you. Only use this if `GiveEconomyBoostReward` doesn't fit your flow.

```lua
exports['meteo-dailyrewards']:ApplyEconomyBoost(source, amount)
```

Always returns a table (with `multiplier = 1` when no boost is active):

```lua
{
    originalAmount = number,  -- what you passed in
    boostedAmount = number,   -- amount after the multiplier
    multiplier = number,      -- 1 if no boost
    boostEnded = boolean,     -- the boost just hit its target
    earned = number,          -- total bonus tracked so far
    target = number           -- bonus target
}
```

```lua
local boost = exports['meteo-dailyrewards']:ApplyEconomyBoost(source, 1000)
Player.Functions.AddMoney('cash', boost.boostedAmount, 'job-payment')
```

***

## Full Job Integration Example

This is the usual shape - pay the reward, track the task, hand out the boost bonus:

```lua
lib.callback.register('my-job:server:completeTask', function(source)
    local Player = QBCore.Functions.GetPlayer(source)
    if not Player then return false end

    local finalReward = 2000
    Player.Functions.AddMoney('cash', finalReward, 'job-payment')

    if GetResourceState('meteo-dailyrewards') == 'started' then
        local daily = exports['meteo-dailyrewards']:TrackTaskCompletion(source, 'my_job_route', 1)
        if daily and daily.taskCompleted then
            QBCore.Functions.Notify(source, 'Daily task completed!', 'success')
        end

        exports['meteo-dailyrewards']:GiveEconomyBoostReward(source, finalReward)
    end

    return true
end)
```

To make `'my_job_route'` a real daily task, add a pool for it in `shared/config.lua`:

```lua
Config.taskPools = {
    my_job = {
        enabled = true,
        tasks = {
            {
                id = 'my_job_route_1',
                title = 'Complete 1 Route',
                icon = 'directions',
                trackingType = 'my_job_route', -- what you pass to TrackTaskCompletion
                target = 1,
                estimatedTime = '15 min',
            },
        },
    },
}
```

***

## Good to Know

* If a task isn't tracking, make sure the `trackingType` matches the config exactly and the player hasn't already completed that task today.
* `GetEconomyBoost` and `GiveEconomyBoostReward` return `nil` when `Config.economyBoost.enabled = false`.
* Want to test without grinding? Use the [test commands](test-commands.md) on the showcase server.

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
