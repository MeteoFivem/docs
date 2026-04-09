---
description: >-
  showcase server commands for meteo buffs script. only available on the meteo
  showcase server.
---

# Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server. use them to quickly test buff and status effect features without grinding.
{% endhint %}

***

## Available Commands

### /buffs \[action] \[type] \[value]

All-in-one command for managing player buffs and status effects.

#### Set food addiction

```
/buffs food fastFood 80
/buffs food healthyFood 50
```

Categories: `fastFood`, `junkFood`, `healthyFood`, `balancedMeals`

#### Set drug addiction

```
/buffs drug cocaine 60
/buffs drug alcohol 40
```

Types: `alcohol`, `weed`, `cocaine`, `meth`, `oxy`

#### Set basic needs

```
/buffs hunger 100
/buffs thirst 100
/buffs stress 0
/buffs drunk 50
/buffs streak 5
```

#### Reset everything

```
/buffs reset all
/buffs reset food
/buffs reset drug
```

#### View current state

```
/buffs info
```

Prints all buff data to F8 console.

| Action             | Parameters            | Description                    |
| ------------------ | --------------------- | ------------------------------ |
| **food**           | category, value (0-100) | Set food addiction level     |
| **drug**           | type, value (0-100)   | Set drug addiction level       |
| **hunger**         | value (0-100)         | Set hunger level               |
| **thirst**         | value (0-100)         | Set thirst level               |
| **stress**         | value (0-100)         | Set stress level               |
| **drunk**          | value (0-100)         | Set drunk level                |
| **streak**         | value (0-10)          | Set healthy eating streak      |
| **clearimmunity**  | -                     | Clear food addiction immunity  |
| **reset**          | food/drug/all         | Reset buff data                |
| **info**           | -                     | Print debug info to F8         |

***

{% hint style="info" %}
Need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
