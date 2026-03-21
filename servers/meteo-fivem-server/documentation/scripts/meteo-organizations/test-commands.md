---
description: >-
  test server commands for meteo organizations script. only available on the
  meteo test server.
---

# Test Commands

these commands are only available on our test server. use them to quickly test organization features without grinding.

***

## Available Commands

### /setorglevel \[action] \[amount]

manage your organization's progression. you must be in an organization to use this command.

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
need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
