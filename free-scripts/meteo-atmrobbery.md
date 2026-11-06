---
description: Free and open source ATM robbery script. Pry ATMs out of the wall with a crowbar and grab the cash before the cops show up.
icon: money-bill-wave
---

# Meteo ATM Robbery

An immersive, open source ATM robbery script. Pry the ATM out of the wall with a crowbar, watch the cash burst out, and grab the notes off the ground before the cops show up.

{% hint style="info" %}
Get this script for free from: <a href="https://meteofivem.net/fivem-scripts/meteo-atmrobbery" target="_blank">meteo-atmrobbery</a>
{% endhint %}

***

## Features

* Pry the ATM out of the wall - the frame stays, the body falls out
* Keymash minigame, one ring segment per key
* Cash bursts out of the ATM and notes land on the ground beside it
* Anyone can pick up the notes, first one there gets it
* Reward as cash or as an item (for example folded cash)
* Police dispatch alert with a configurable chance
* Minimum cops, per player cooldown and ATM reset timer
* All amounts and checks run on the server

## How Robbing Works

1. Hold a crowbar in your hand, target an ATM and pick **Pry open ATM**.
2. Finish the keymash minigame. Each key fills one segment of the ring, and it drains if you stop pressing.
3. The ATM falls out of the wall and cash bursts out. Target the notes on the ground and pick **Pick up cash**.
4. After a robbery you have to lay low for `Config.playerCooldown` seconds before robbing another ATM. The robbed ATM comes back after `Config.resetTime` seconds.

{% hint style="info" %}
A server restart resets every robbed ATM.
{% endhint %}

***

## Installation Guide

**Requirements:** qb-core or qbox, `ox_lib`, `ox_target`, `ox_inventory`

{% stepper %}
{% step %}
**Install meteo-atmrobbery**

* Download the script from the link above
* Drop the `meteo-atmrobbery` folder into your resources (for example `[meteostudios]/meteo-atmrobbery`)
* Add `ensure meteo-atmrobbery` to your `server.cfg`

{% hint style="warning" %}
Make sure your core, `ox_lib`, `ox_target` and `ox_inventory` are started **before** `meteo-atmrobbery` in your `server.cfg`.
{% endhint %}
{% endstep %}

{% step %}
**Set up dispatch (optional)**

Dispatch alerts go to `meteo-mdt` out of the box. If you use another dispatch, swap the export in `Bridge.Dispatch` inside `bridge/sv_bridge.lua`:

```lua
function Bridge.Dispatch(src, coords)
    if GetResourceState('meteo-mdt') ~= 'started' then return end
    exports['meteo-mdt']:SendAlert({
        code = Config.dispatch.code,
        title = locale('dispatch_title'),
        description = locale('dispatch_desc'),
        coords = coords,
        priority = Config.dispatch.priority,
        jobs = Config.dispatch.jobs,
        suspect = src,
    })
end
```
{% endstep %}

{% step %}
**Restart the server**

Grab a crowbar, find an ATM and try it out.
{% endstep %}
{% endstepper %}

***

## Configuration

All settings live in `shared/config.lua`.

### General

```lua
Config.framework = 'auto'         -- 'auto', 'qbox', 'qbcore'

Config.weapon = 'WEAPON_CROWBAR'  -- must be in hand
Config.requiredCops = 0

Config.resetTime = 1800           -- seconds until the ATM is back
Config.playerCooldown = 600       -- seconds between robberies
Config.renderDistance = 60.0
```

### ATM models

Each ATM model needs a frame and a body prop. The frame stays in the wall and the body falls out. The `prop_atm_03` pieces come streamed with the script.

```lua
Config.atmModels = { 'prop_atm_03' }

Config.atmPieces = {
    prop_atm_03 = { frame = 'meteo_prop_atm03_frame', body = 'meteo_prop_atm03_body' },
}
```

### Minigame

```lua
Config.minigame = {
    keys = { 'Q', 'SPACE', 'E', 'E' },  -- letters or 'SPACE'
    presses = 10,                       -- taps per key
    drain = 3.5,                        -- seconds to drain empty
    time = 6,                           -- seconds per key, 0 = no limit
    anim = { dict = 'missheistfbi3b_ig7', clip = 'lift_fibagent_loop' },
}
```

### Reward

The total is split over the notes that drop on the ground.

```lua
Config.reward = {
    type = 'cash',                       -- 'cash' or 'item'
    item = 'meteo_foldedcash',           -- when type is 'item'
    total = { min = 1500, max = 3000 },  -- $ or item count, split over the notes
    notes = { min = 6, max = 9 },
}

Config.noteModel = 'h4_prop_h4_cash_stack_02a'
Config.currencySymbol = '$'
Config.pickupTime = 1200                 -- ms per note

Config.cashBurst = {
    duration = 10,                       -- seconds
    notesPerSecond = 20,
    model = 'prop_anim_cash_note',
}
```

{% hint style="warning" %}
If you set `type = 'item'`, make sure the item in `Config.reward.item` exists in your `ox_inventory/data/items.lua`.
{% endhint %}

### Dispatch

```lua
Config.dispatch = {
    enabled = true,
    chance = 100,       -- % per attempt
    code = '10-90',
    priority = 'medium',
    jobs = { 'police' },
}
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>.
{% endhint %}
