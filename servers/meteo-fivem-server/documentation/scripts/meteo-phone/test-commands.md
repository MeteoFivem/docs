---
description: >-
  test server commands for meteo phone script. only available on the meteo
  test server.
---

# Test Commands

these commands are only available on our test server. use them to quickly test phone features without setup.

***

## Available Commands

### /testnotification \[priority] \[message]

send a test notification to your phone.

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

send a test email to a phone by its serial number.

```
/sendemail Ifruit_123456
```

Sends a test email from `test@example.com` with a sample subject and body. Test the email app without needing server-side triggers.

***

{% hint style="info" %}
need help? contact Meteo support if you have any questions. get access to our exclusive test guide videos on our Discord.
{% endhint %}
