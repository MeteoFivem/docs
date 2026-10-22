---
description: >-
  showcase server commands for meteo phone script. only available on the meteo
  showcase server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-phone/test-commands.md
---

# Test Commands

## Player Commands

These work for everyone.

| Command        | Description                                         |
| -------------- | --------------------------------------------------- |
| `/phone`       | Open or close the phone (default key `M`)           |
| `/reloadphone` | Reload the phone UI if it gets stuck, then reopen it |

***

## Available Commands

{% hint style="warning" %}
These commands are only available on our showcase server. use them to quickly test phone features without setup.
{% endhint %}


### /phonetest \[action] \[value]

Test phone features on yourself without needing a second player.

```
/phonetest call 555-0199
/phonetest video 555-0199
/phonetest busy 555-0142
/phonetest notify
/phonetest info
```

| Action     | Description                                                                 |
| ---------- | --------------------------------------------------------------------------- |
| **call**   | Ring yourself from a number, answer it to test the call screen              |
| **video**  | Same as call, as a video call                                               |
| **busy**   | While you are on a call, someone else calls you - check the busy banner and the missed call in recents |
| **notify** | Send a test notification to your phone                                      |
| **info**   | Shows your phone serial, SIM number, SIM status and if you have service     |

***

{% hint style="info" %}
Need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
