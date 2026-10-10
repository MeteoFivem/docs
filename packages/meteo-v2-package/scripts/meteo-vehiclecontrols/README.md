---
description: >-
  Meteo vehicle controls - a control panel for doors, windows, seats and the
  engine designed exclusively for the Meteo V2 package.
---

# Meteo Vehicle Controls

This is a guide about testing the Meteo V2 vehicle controls script designed exclusively for the Meteo V2 package.

One small panel for everything you do inside a vehicle - open doors, roll windows, swap seats and switch the engine, all with the mouse while you keep driving.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* A vehicle to sit in. Spawn one with `/car adder` or take one out of your [garage](../meteo-garages/)

***

## Testing Vehicle Controls

### Opening the Panel

{% stepper %}
{% step %}
Get in any vehicle and type `/vehcontrol` in chat
{% endstep %}

{% step %}
The panel opens on the **Seats** tab. It only opens while you are sitting in a vehicle
{% endstep %}

{% step %}
The panel only takes your mouse. You can keep driving, type in chat and use your keybinds while it is open
{% endstep %}

{% step %}
Press **ESC** or click anywhere outside the panel to close it
{% endstep %}
{% endstepper %}

{% hint style="info" %}
There is no default key, but you can bind one yourself under **Settings > Key Bindings > FiveM**. The keybind only works while you are in a vehicle.
{% endhint %}

### Doors

{% stepper %}
{% step %}
Open the **Doors** tab. A 4 door car shows the driver, front right, rear left and rear right doors plus the hood and trunk
{% endstep %}

{% step %}
Only the doors the vehicle really has are listed - a coupe has no rear doors, and a van or bus also shows its back doors
{% endstep %}

{% step %}
Click a door to open it and click it again to shut it. **Open all** opens everything and then turns into **Close all**
{% endstep %}

{% step %}
Rip a door off in a crash and it shows as **Broken** and can no longer be clicked
{% endstep %}
{% endstepper %}

### Windows

{% stepper %}
{% step %}
Open the **Windows** tab and click a window to roll it down, click again to roll it up
{% endstep %}

{% step %}
**Roll down** does every window at once and then turns into **Roll up**
{% endstep %}

{% step %}
Shoot a window out and it shows as **Smashed** and can no longer be clicked
{% endstep %}
{% endstepper %}

### Seats

{% stepper %}
{% step %}
Open the **Seats** tab. Your own seat is marked **You**, seats with someone in them are marked **Taken**
{% endstep %}

{% step %}
Click a free seat to move into it straight away. Bigger vehicles like a bus list their extra seats as Seat 5, Seat 6 and so on
{% endstep %}

{% step %}
Try to move into or out of the driver seat above 50 km/h and it tells you to slow down first
{% endstep %}
{% endstepper %}

### Engine

{% stepper %}
{% step %}
The power button turns the engine on and off
{% endstep %}

{% step %}
Only the driver can use it, a passenger gets told so
{% endstep %}

{% step %}
Without keys to the vehicle the engine and the doors refuse to work. Keys come from [meteo-vehiclekeys](../meteo-vehiclekeys/)
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Other players see your doors, windows and engine change too. Bicycles do not have a panel.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
The command, a default keybind, the key checks for the engine and doors, driver only engine, hiding broken doors, the seat swap speed limit and blocked vehicle classes are all configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

{% content-ref url="../meteo-vehiclekeys/" %}
[meteo-vehiclekeys](../meteo-vehiclekeys/)
{% endcontent-ref %}
