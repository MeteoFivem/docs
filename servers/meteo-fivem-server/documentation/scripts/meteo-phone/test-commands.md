---
description: >-
  showcase server commands for meteo phone script. only available on the meteo
  showcase server.
---

# Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server. use them to quickly test phone features without setup.
{% endhint %}

***

## Available Commands

### /testnotification \[priority] \[message]

Send a test notification to your phone.

```
/testnotification normal Hello world
/testnotification high Important message
/testnotification critical Server alert
```

| Priority     | Description            |
| ------------ | ---------------------- |
| **normal**   | Standard notification  |
| **high**     | Highlighted notification |
| **critical** | Urgent notification    |

If no message is provided, a default test message is used.

### /sendemail \[phoneSerial]

Send a test email to a phone by its serial number.

```
/sendemail Ifruit_123456
```

Sends a test email from `test@example.com` with a sample subject and body. Test the email app without needing server-side triggers.

***

{% hint style="info" %}
Need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
