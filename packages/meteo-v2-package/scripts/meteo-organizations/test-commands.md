---
description: >-
  Showcase server commands for meteo organizations script. Only available on the
  meteo showcase server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-organizations/test-commands.md
---

# Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server. Use them to quickly test organization features without grinding.
{% endhint %}

***

## Available Commands

### /setorglevel \[action] \[amount]

Manage your organization's progression. You must be in an organization to use this command.

#### Add XP to your org

```
/setorglevel xp 500
/setorglevel xp 2000
```

Defaults to 500 XP if no amount specified.

#### Force upkeep due

```
/setorglevel upkeep
```

Sets your org's upkeep to unpaid and due immediately. Test the upkeep payment flow.

#### Delete your organization

```
/setorglevel reset
```

Removes the org, all members, and all upgrades.

| Action     | Parameter           | Description                        |
| ---------- | ------------------- | ---------------------------------- |
| **xp**     | amount (default 500) | Add XP to your org                |
| **upkeep** | -                   | Force upkeep to be due now         |
| **reset**  | -                   | Delete your entire organization    |

***

{% hint style="info" %}
Need help? Contact Meteo support if you have any questions. Get access to our exclusive test guide videos on our Discord.
{% endhint %}
