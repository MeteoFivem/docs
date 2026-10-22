---
description: >-
  showcase server commands for meteo perks script. only available on the meteo
  showcase server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-perks/test-commands.md
---

# Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server. use them to quickly test perk lines without grinding. They always act on yourself.
{% endhint %}

***

## Available Commands

### /perks lines

Prints every registered perk line with your level and XP on it to the server console.

```
/perks lines
```

### /perks show \[line]

Prints the perks on one line, the level each unlocks at, what it pays and whether you have it.

```
/perks show pawn
```

### /perks xp \[line] \[amount]

Gives XP the normal way, so the daily cap and the XP toast both apply. Amount defaults to 100.

```
/perks xp pickpocket 200
```

### /perks level \[line] \[level]

Jumps a line straight to a level, ignoring the daily cap.

```
/perks level pawn 7
```

### /perks max

Puts every line at the max level so you can check every unlock at once.

```
/perks max
```

### /perks reset

Puts all your perk progress back to level 1 on every line.

```
/perks reset
```

### /perks toast \[line] \[amount] \[up]

Shows the XP toast without changing your XP. Add `up` to see the level up toast.

```
/perks toast fishing 25
/perks toast fishing 25 up
```

### /perks reward \[perkId]

Shows what a perk pays you right now. Find perk ids with `/perks show`.

```
/perks reward hu_afterhours
```

| Parameter  | Description                                                                 |
| ---------- | --------------------------------------------------------------------------- |
| **line**   | Line id, like `pickpocket`, `pawn`, `crafting`. A unique start of the name works too |
| **amount** | XP amount                                                                   |
| **level**  | Level to set (1 to 10 by default)                                           |
| **perkId** | ID of the perk                                                              |

***

{% hint style="info" %}
Need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
