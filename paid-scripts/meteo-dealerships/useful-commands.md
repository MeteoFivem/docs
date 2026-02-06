---
description: >-
  These Meteo Dealerships commands help you manage dealerships, finance
  blacklists, and overdue payments on your server. All commands require admin
  permissions.
---

# Useful Commands

## Quick Reference Table

| Command                            | Purpose                         | Example                           |
| ---------------------------------- | ------------------------------- | --------------------------------- |
| `/dealeradmin`                     | Open admin panel                | `/dealeradmin`                    |
| `/clearfinanceblacklist [citizen]` | Clear finance blacklist         | `/clearfinanceblacklist ABC12345` |
| `/checkfinances`                   | Manually check overdue payments | `/checkfinances`                  |

***

## Admin Panel

{% stepper %}
{% step %}
#### `/dealeradmin`

**Open the Dealerships Admin Panel**

* **Usage:** `/dealeradmin`
* **Parameters:** None
* **What it does:** Opens the admin panel UI where you can:
  * Manage all dealerships
  * Import/export vehicles
  * Set dealership owners

**Example:**

```
/dealeradmin
```
{% endstep %}
{% endstepper %}

***

## Finance Commands

{% stepper %}
{% step %}
#### `/clearfinanceblacklist [citizenid]`

**Clear finance blacklist for a player**

* **Usage:** `/clearfinanceblacklist ABC12345`
* **Parameter:**
  * `citizenid` - The player's Citizen ID (required)
* **What it does:** Removes a player from the finance blacklist, allowing them to finance vehicles again. Players get blacklisted when they have too many repossessed vehicles.

**Example:**

```
/clearfinanceblacklist ABC12345
```

**When to use:**

* Player was wrongly blacklisted
* Player has resolved their debt issues
* Admin discretion for special cases
{% endstep %}

{% step %}
#### `/checkfinances`

**Manually trigger overdue payment check**

* **Usage:** `/checkfinances`
* **Parameters:** None
* **What it does:** Manually runs the overdue finance payment check. This is normally done automatically by the server on a schedule, but you can trigger it manually if needed.

**Example:**

```
/checkfinances
```

**What happens during check:**

* Finds all vehicles with overdue payments
* Applies late fees if configured
* Repossesses vehicles that exceed the grace period
* Notifies affected players if online
{% endstep %}
{% endstepper %}

***
