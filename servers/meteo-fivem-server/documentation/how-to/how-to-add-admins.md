---
description: >-
  How to add admins to your meteo fivem server. Give owner or admin permissions
  using Discord ID or license identifier via permissions.cfg.
icon: shield-halved
---

# How to Add Admins

Admin permissions are set in `permissions.cfg`. You can use a player's Discord ID or their license identifier.

***

## Permission Levels

| Permission | Who it's for |
| ---------- | ------------ |
| `group.admin` | Server owner - full access to everything including all commands |
| `qbcore.admin` | Staff admins - access to admin commands without full owner permissions |

***

## Getting a Player's Identifier

You need either their **Discord ID** or **license identifier** to add them.

{% stepper %}
{% step %}
**Discord ID**

Right click the player in Discord → **Copy User ID** (make sure Developer Mode is on in Discord settings)
{% endstep %}

{% step %}
**License identifier via txAdmin**

Open **txAdmin** → go to **Players** → search and select the player → scroll to **Player Identifiers** → copy the `license:` value from there
{% endstep %}
{% endstepper %}

***

## Adding an Owner

Use `group.admin` for the server owner. Owners have access to all commands.

**Using Discord ID:**

```
add_principal identifier.discord:YOUR_DISCORD_ID group.admin
```

**Using license:**

```
add_principal identifier.license:YOUR_LICENSE_HERE group.admin
```

***

## Adding an Admin

Use `qbcore.admin` for staff admins.

**Using Discord ID:**

```
add_principal identifier.discord:YOUR_DISCORD_ID qbcore.admin
```

**Using license:**

```
add_principal identifier.license:YOUR_LICENSE_HERE qbcore.admin
```

***

## Example

```
# Owner
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.admin

# Staff admins
add_principal identifier.discord:000000000000000000 qbcore.admin
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx qbcore.admin
```

{% hint style="info" %}
After editing `permissions.cfg` you need to restart the server for changes to take effect.
{% endhint %}
