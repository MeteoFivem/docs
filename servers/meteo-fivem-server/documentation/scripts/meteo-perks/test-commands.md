---
description: >-
  showcase server commands for meteo perks script. only available on the meteo
  showcase server.
---

# Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server. use them to quickly test perk tree features without grinding.
{% endhint %}

***

## Available Commands

### /perksetlevel \[playerID] \[category] \[level]

Set a player's perk spec level.

```
/perksetlevel 1 crime 5
/perksetlevel 1 civilian 3
```

### /perkaddxp \[playerID] \[category] \[amount]

Add XP to a player's perk category.

```
/perkaddxp 1 crime 1000
```

### /perkgrant \[playerID] \[perkId]

Unlock a specific perk for a player.

```
/perkgrant 1 lockpicking_expert
```

### /perkreset \[playerID] \[category]

Reset all perks and progress for a category. clears spec, level, XP, and unlocked perks.

```
/perkreset 1 crime
/perkreset 1 civilian
```

### /perkresetdaily \[playerID]

Reset daily XP limits for a player.

```
/perkresetdaily 1
```

### /perkgivepoints \[playerID] \[category] \[amount]

Give bonus perk points to spend on the perk tree.

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
Need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
