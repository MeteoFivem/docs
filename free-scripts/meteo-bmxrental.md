---
description: Free and open source immersive BMX rental script with animated docks that bring the bike up and take it back down.
icon: bicycle
---

# Meteo Bmx Rental

An immersive, open source bike rental script. Players rent a BMX from a dock, a pod rises out of the dock with the bike, and takes it back down when it is returned.

{% hint style="info" %}
Get this script for free from: <a href="https://meteofivem.net/fivem-scripts/meteo-bmxrental" target="_blank">meteo-bmxrental</a>
{% endhint %}

***

## Features

* Animated rental docks - the pod brings the bike up and takes it back down on return
* Rent with cash first, or from the bank if there is not enough cash
* Deposit system - get it back when you return the bike to any dock
* Rental papers item that shows the bike, plate and deposit in its tooltip
* Place and remove docks in game with `/bmxdock`, no config editing
* Add any bicycle that fits the pod, with its own price, deposit, image and colours

## How Renting Works

1. Target a dock and pick **Rent a bike**, then pick a model. You pay the price plus the deposit.
2. The pod brings the bike up. It stays frozen upright until someone gets on.
3. If nobody gets on within `Config.claimTime` seconds, the pod takes it back and you get the price and the deposit back.
4. To return the bike, park it on any dock, get off, then target the dock and pick **Return bike**. The deposit is refunded.

{% hint style="warning" %}
The deposit is lost if the bike is destroyed or deleted, or if the player logs out or disconnects. The bike is removed and leftover papers are cleaned up the next time the player logs in.
{% endhint %}

***

## Installation Guide

**Requirements:** qb-core or qbox, `ox_lib`, `ox_target`, `ox_inventory`, `oxmysql`

{% stepper %}
{% step %}
**Install meteo-bmxrental**

* Download the script from the link above
* Drop the `meteo-bmxrental` folder into your resources (for example `[meteostudios]/meteo-bmxrental`)
* Add `ensure meteo-bmxrental` to your `server.cfg`

{% hint style="warning" %}
Make sure your core, `ox_lib`, `ox_target`, `ox_inventory` and `oxmysql` are started **before** `meteo-bmxrental` in your `server.cfg`.
{% endhint %}
{% endstep %}

{% step %}
**Add the rental papers item**

Copy `install/meteo_bmxpapers.png` to `ox_inventory/web/images/`.

Add this to `ox_inventory/data/items.lua`:

```lua
['meteo_bmxpapers'] = {
    label = 'BMX Rental Papers',
    weight = 10,
    close = true,
    description = 'Proof you rented this bike.',
},
```

To use another item name, change `Config.papersItem`.
{% endstep %}

{% step %}
**Restart the server**

The database table `meteo_bmxrental_docks` is created automatically on first start.
{% endstep %}

{% step %}
**Place your docks**

Run `/bmxdock` in game and pick **Place new dock**. See [Managing Docks](#managing-docks) below for the controls.
{% endstep %}
{% endstepper %}

***

## Managing Docks

Admins (`Config.adminPermission`, default `admin`) run `/bmxdock` to open the dock menu. It lists every dock, nearest first, with teleport, waypoint and remove options. Pick **Place new dock** to add one:

| Key             | Action                |
| --------------- | --------------------- |
| LMB             | Place where you aim   |
| E               | Place where you stand |
| Scroll          | Rotate 5 degrees      |
| Ctrl + Scroll   | Rotate 1 degree       |
| Shift + Scroll  | Raise or lower        |
| RMB / Backspace | Cancel                |

You can also remove a dock by targeting it and picking **Remove dock**.

***

## Configuration

All settings live in `shared/config.lua`.

```lua
Config.framework = 'auto'         -- 'auto', 'qbox', 'qbcore'

Config.adminPermission = 'admin'  -- can place and remove docks
Config.placeCommand = 'bmxdock'

Config.papersItem = 'meteo_bmxpapers'
Config.currencySymbol = '$'

Config.renderDistance = 20.0      -- dock prop spawns within this
Config.claimTime = 60             -- seconds to get on before it goes back

Config.blip = {
    enabled = true,
    sprite = 226,
    color = 5,
    scale = 0.6,
}
```

### Adding bikes

`price` is kept, `deposit` comes back when the bike is returned.

```lua
Config.bikes = {
    { model = 'bmx', label = 'BMX', price = 25, deposit = 150 },
    { model = 'scorcher', label = 'Scorcher', price = 40, deposit = 250 },
}
```

Any bicycle that fits the pod works. Optional per bike:

* `image = 'https://...'` changes the picture shown in the menu
* `colors = { primary, secondary, pearl, wheel }` sets fixed GTA colour ids. Without it, each rental gets a random colour.

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>.
{% endhint %}
