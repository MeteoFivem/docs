---
description: >-
  test server commands for meteo perks script. only available on the meteo
  test server.
---

# Test Commands

these commands are only available on our test server. use them to quickly test perk tree features without grinding.

***

## Available Commands

### /perksetlevel \[playerID] \[category] \[level]

set a player's perk spec level.

```
/perksetlevel 1 crime 5
/perksetlevel 1 civilian 3
```

### /perkaddxp \[playerID] \[category] \[amount]

add XP to a player's perk category.

```
/perkaddxp 1 crime 1000
```

### /perkgrant \[playerID] \[perkId]

unlock a specific perk for a player.

```
/perkgrant 1 lockpicking_expert
```

### /perkreset \[playerID] \[category]

reset all perks and progress for a category. clears spec, level, XP, and unlocked perks.

```
/perkreset 1 crime
/perkreset 1 civilian
```

### /perkresetdaily \[playerID]

reset daily XP limits for a player.

```
/perkresetdaily 1
```

### /perkgivepoints \[playerID] \[category] \[amount]

give bonus perk points to spend on the perk tree.

```
/perkgivepoints 1 crime 10
```

| Parameter    | Description                              |
| ------------ | ---------------------------------------- |
| **playerID** | Server ID of the target player           |
| **category** | `crime` or `civilian`                    |
| **level**    | Level number to set                      |
| **amount**   | XP or points amount                      |
| **perkId**   | ID of the perk to unlock                 |

***

{% hint style="info" %}
need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
