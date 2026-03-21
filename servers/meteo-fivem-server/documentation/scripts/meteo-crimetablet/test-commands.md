---
description: >-
  test server commands for meteo crime tablet script. only available on the
  meteo test server.
---

# Test Commands

these commands are only available on our test server. use them to quickly test crime tablet features without grinding.

***

## Available Commands

### /addcrypto \[amount]

add crypto to your crime tablet account. defaults to 10,000 if no amount specified.

```
/addcrypto
/addcrypto 50000
```

### /setachievement \[action] \[id] \[amount]

manage crime tablet achievements.

#### Reset all achievements

```
/setachievement reset
```

#### Complete a specific achievement

```
/setachievement complete first_hack
```

#### Set progress on an achievement

```
/setachievement progress first_hack 5
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
need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
