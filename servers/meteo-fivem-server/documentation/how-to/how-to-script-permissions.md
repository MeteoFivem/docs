---
description: >-
  How to change which permissions can use a meteo script's admin features using
  the sv_permissions.lua file.
icon: user-lock
---

# How to Change Script Permissions

Every meteo script that has admin features comes with a `server/sv_permissions.lua` file. This is where you choose which permissions can use that script. By default it allows `admin` (owners) and `mod` (staff admins).

***

## How it works

Open any meteo script and look in its `server` folder for `sv_permissions.lua`. The top of the file holds one or two permission lists:

```lua
-- permissions allowed to use admin features. add your own if needed
-- admin = owners, mod = staff admins
local AdminGroups = {
    'admin',
    'mod',
}

-- owner only stuff
local GodGroups = {
    'admin',
}
```

* **AdminGroups** - permissions that can use the script's admin features.
* **GodGroups** - only some scripts have this. It is for sensitive actions (like banning a player or granting admin in the admin menu).

These are **ace permissions**, not the group names. In your `permissions.cfg`, `group.admin` is granted the `admin` permission and `group.mod` is granted the `mod` permission:

```
add_ace group.admin admin allow
add_ace group.mod mod allow
```

A player passes the check if they have **any** of the listed permissions.

{% hint style="info" %}
After editing `sv_permissions.lua`, restart the script (or the server) for the change to take effect.
{% endhint %}

***

## Example: give a custom group access

Say you want a "vehicle team" to be able to use the admin menu, without making them full admins.

{% stepper %}
{% step %}
**Create the group and its permission in permissions.cfg**

Make a new group, grant it a permission name, and assign players to it:

```
add_ace group.vehicleteam vehicleteam allow
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.vehicleteam
```
{% endstep %}

{% step %}
**Add the permission to the script**

Open the script's `server/sv_permissions.lua` and add your permission to `AdminGroups`:

```lua
local AdminGroups = {
    'admin',
    'mod',
    'vehicleteam',
}
```
{% endstep %}

{% step %}
**Restart**

Restart the script. Anyone in `group.vehicleteam` can now use it.
{% endstep %}
{% endstepper %}

***

## Example: lock a script to one group only

If you want a script to be used **only** by owners, remove the other permissions so just `admin` is left:

```lua
local AdminGroups = {
    'admin',
}
```

Or give a script to one specific team and no one else (using a custom permission you set up in `permissions.cfg`):

```lua
local AdminGroups = {
    'devteam',
}
```

***

## Example: keep sensitive actions owner-only

On scripts that have a `GodGroups` list (like the admin menu), the normal features use `AdminGroups`, but the sensitive ones use `GodGroups`. You can let staff use the menu while keeping bans and admin-granting for owners only:

```lua
-- staff and owners can use the menu
local AdminGroups = {
    'admin',
    'mod',
}

-- but only owners can ban / grant admin
local GodGroups = {
    'admin',
}
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
