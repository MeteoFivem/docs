---
description: >-
  showcase server commands for meteo crime tablet script. only available on the
  meteo showcase server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-crimetablet/test-commands.md
---

# Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server. use them to quickly test crime tablet features without grinding.
{% endhint %}

***

## Available Commands

### /addcrypto \[amount]

Add crypto to your crime tablet account. Defaults to 10,000 if no amount is given.

```
/addcrypto
/addcrypto 50000
```

{% hint style="info" %}
This one is an admin command, so it also works on your own server for admins.
{% endhint %}

### /setachievement \[action] \[id] \[amount]

Manage crime tablet achievements.

#### Reset all achievements

```
/setachievement reset
```

#### Complete a specific achievement

```
/setachievement complete crypto_starter
```

#### Set progress on an achievement

```
/setachievement progress crypto_starter 5
```

#### Complete all achievements

```
/setachievement all
```

Achievements are set to "completed but uncollected" so you can test the collection flow.

| Action       | Parameters          | Description                    |
| ------------ | ------------------- | ------------------------------ |
| **reset**    | -                   | Wipe all achievement progress  |
| **complete** | achievement ID      | Mark one achievement as done   |
| **progress** | achievement ID, amount | Set progress value          |
| **all**      | -                   | Complete every achievement     |

***

{% hint style="info" %}
Need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
