---
description: >-
  How to change which ace groups can use a meteo script's admin features using
  the sv_permissions.lua file.
icon: user-lock
---

# How to Change Script Permissions

Every meteo script that has admin features comes with a `server/sv_permissions.lua` file. This is where you choose which permission groups can use that script. By default it allows `group.admin` (owners) and `group.mod` (staff admins).

***

## How it works

Open any meteo script and look in its `server` folder for `sv_permissions.lua`. The top of the file holds one or two group lists:

```lua
-- groups allowed to use admin features. add your own if needed
-- group.admin = owner, group.mod = staff
local AdminGroups = {
    'group.admin',
    'group.mod',
}

-- owner only stuff
local GodGroups = {
    'group.admin',
}
```

* **AdminGroups** - groups that can use the script's admin features.
* **GodGroups** - only some scripts have this. It is for sensitive actions (like banning a player or granting admin in the admin menu).

A player passes the check if they are in **any** of the listed groups.

{% hint style="info" %}
After editing `sv_permissions.lua`, restart the script (or the server) for the change to take effect.
{% endhint %}

***

## Example: give a custom group access

Say you want a "vehicle team" to be able to use the admin menu, without making them full admins.

{% stepper %}
{% step %}
**Create the group in permissions.cfg**

Add your new group and assign players to it in `permissions.cfg`:

```
add_ace group.vehicleteam command allow
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.vehicleteam
```
{% endstep %}

{% step %}
**Add the group to the script**

Open the script's `server/sv_permissions.lua` and add your group to `AdminGroups`:

```lua
local AdminGroups = {
    'group.admin',
    'group.mod',
    'group.vehicleteam',
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

If you want a script to be used **only** by owners, remove the other groups so just `group.admin` is left:

```lua
local AdminGroups = {
    'group.admin',
}
```

Or give a script to one specific team and no one else:

```lua
local AdminGroups = {
    'group.devteam',
}
```

***

## Example: keep sensitive actions owner-only

On scripts that have a `GodGroups` list (like the admin menu), the normal features use `AdminGroups`, but the sensitive ones use `GodGroups`. You can let staff use the menu while keeping bans and admin-granting for owners only:

```lua
-- staff and owners can use the menu
local AdminGroups = {
    'group.admin',
    'group.mod',
}

-- but only owners can ban / grant admin
local GodGroups = {
    'group.admin',
}
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
