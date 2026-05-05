---
description: >-
  These Meteo Admin Menu commands open the menu and provide quick access to the
  most-used dev tools. All commands require admin permissions.
---

# Useful Commands

## Quick Reference Table

| Command     | Purpose                                       | Example     |
| ----------- | --------------------------------------------- | ----------- |
| `/admin`    | Open the admin menu                           | `/admin`    |
| `/noclip`   | Toggle noclip mode                            | `/noclip`   |
| `/admincar` | Save the current vehicle to your garage       | `/admincar` |
| `/maxmods`  | Apply max performance mods to current vehicle | `/maxmods`  |
| `/blips`    | Toggle player blips on the map                | `/blips`    |
| `/coords`   | Copy current coords as `vector3`              | `/coords`   |
| `/vec2`     | Copy current coords as `vector2`              | `/vec2`     |
| `/vec3`     | Copy current coords as `vector3`              | `/vec3`     |
| `/vec4`     | Copy current coords as `vector4` (with heading)| `/vec4`    |

***

## Default Keybinds

| Keybind | Command          | Purpose                |
| ------- | ---------------- | ---------------------- |
| `F9`    | `cmd_admin_menu` | Open admin menu        |
| `F10`   | `cmd_admin_noclip` | Toggle noclip        |
| `F11`   | `cmd_admin_coords` | Copy coords          |

{% hint style="info" %}
After changing keybinds in `shared/config.lua`, existing players need to manually update them in-game under **Settings > Key Bindings > FiveM > Admin Menu**. New players will automatically get the new keybinds.
{% endhint %}

***

## Menu

{% stepper %}
{% step %}
**`/admin`**

**Open the Admin Menu**

* **Usage:** `/admin`
* **Parameters:** None
* **What it does:** Opens the admin menu UI. Same as pressing `F9`.

**Example:**

```
/admin
```
{% endstep %}
{% endstepper %}

***

## Vehicle Commands

{% stepper %}
{% step %}
**`/admincar`**

**Save the current vehicle**

* **Usage:** `/admincar`
* **Parameters:** None
* **What it does:** Saves the vehicle you are currently in to your owned vehicles.

**Example:**

```
/admincar
```
{% endstep %}

{% step %}
**`/maxmods`**

**Max out vehicle performance mods**

* **Usage:** `/maxmods`
* **Parameters:** None
* **What it does:** Applies the highest tier of engine, brakes, transmission, suspension, armor, and turbo to the current vehicle.

**Example:**

```
/maxmods
```
{% endstep %}

***

## Dev Tools

{% stepper %}
{% step %}
**`/noclip`**

**Toggle noclip mode**

* **Usage:** `/noclip` or `/noclip true` / `/noclip false`
* **Parameters:**
  * `enabled` - Optional. `true` or `false` to force a state.
* **What it does:** Toggles freecam noclip movement. Default keybind is `F10`.

**Example:**

```
/noclip
```
{% endstep %}

{% step %}
**`/blips`**

**Toggle player blips**

* **Usage:** `/blips`
* **Parameters:** None
* **What it does:** Toggles map blips for all online players. Useful for finding players quickly.

**Example:**

```
/blips
```
{% endstep %}

{% step %}
**`/coords`, `/vec2`, `/vec3`, `/vec4`**

**Copy your current position to clipboard**

* **Usage:** `/coords`, `/vec2`, `/vec3`, `/vec4`
* **Parameters:** None
* **What it does:**
  * `/coords` and `/vec3` - copy as `vector3(x, y, z)`
  * `/vec2` - copy as `vector2(x, y)`
  * `/vec4` - copy as `vector4(x, y, z, heading)`

Default keybind for `/coords` is `F11`.

**Example:**

```
/vec4
```
{% endstep %}
{% endstepper %}

***

## Spectate

While spectating a player, press **Backspace** to exit. The on-screen keybind hint is shown via meteo-keybinddisplay.

{% hint style="success" %}
**Need help with a command or have a question?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
