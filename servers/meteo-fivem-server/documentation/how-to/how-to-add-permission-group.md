---
description: >-
  How to create a new permission group in permissions.cfg and grant it to
  players on your meteo fivem server.
icon: users
---

# How to Add a Permission Group

Groups let you give a set of players the same permissions. The server runs on **Qbox**, so groups are set up in `permissions.cfg` using ace permissions.

***

## How groups work

There are two pieces:

* **Group** (`group.something`) - what a player belongs to. You assign players with `add_principal`.
* **Permission** (an ace) - what that group is allowed to do. You grant it with `add_ace`.

Your server ships with three default groups, from highest to lowest:

```
# Ace Groups
add_ace group.admin admin allow
add_ace group.mod mod allow
add_ace group.support support allow

# Inheritance
add_principal group.admin group.mod
add_principal group.mod group.support
```

The inheritance lines mean `group.admin` also has `mod` and `support`, and `group.mod` also has `support`. So an admin passes every check a mod or support does.

***

## Adding a new group

Say you want a "builder" group for your mapping team.

{% stepper %}
{% step %}
**Grant the group its permission**

In `permissions.cfg`, give your new group an ace permission. The name on the right is what scripts and commands check for:

```
add_ace group.builder builder allow
```
{% endstep %}

{% step %}
**Set up inheritance (optional)**

If you want your admins to also have this permission, let `group.admin` inherit it:

```
add_principal group.admin group.builder
```

Skip this if the builder group should be completely separate.
{% endstep %}

{% step %}
**Assign players to the group**

Add players using their Discord ID or license (see [How to Add Admins](how-to-add-admins.md) for how to find these):

```
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.builder
add_principal identifier.discord:000000000000000000 group.builder
```
{% endstep %}

{% step %}
**Use the group**

Use the `builder` permission name where you want it - for example add it to a script's `sv_permissions.lua` so the builder team can use that script:

```lua
local AdminGroups = {
    'admin',
    'mod',
    'builder',
}
```

See [How to Change Script Permissions](how-to-script-permissions.md) for more.
{% endstep %}

{% step %}
**Restart**

Restart the server so the new group is loaded.
{% endstep %}
{% endstepper %}

***

## Full example

A complete new group added to `permissions.cfg`:

```
# Builder group
add_ace group.builder builder allow
add_principal group.admin group.builder

# Builder team members
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.builder
add_principal identifier.discord:000000000000000000 group.builder
```

{% hint style="info" %}
Always restart the server after editing `permissions.cfg`. Changes are not picked up live.
{% endhint %}

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
