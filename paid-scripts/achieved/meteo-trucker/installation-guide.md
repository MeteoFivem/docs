---
description: Guide to installations of meteo trucker job
---

# Installation guide

## 1. Before starting

You must carefully follow all the steps that you will see in this installation guide.

{% hint style="warning" %}
Please, before opening a ticket in our community, check all the steps of this installation, since the vast majority of tickets are due to ignoring certain steps in the guide. Each step is important and must be respected.
{% endhint %}

## 2. Asset download

To get started, you'll need to download your new resource previously purchased from [meteo.tebex.io ](https://meteo.tebex.io/)For that we must log in with our account at [`keymaster`](https://keymaster.fivem.net/asset-grants/) and look for the Asset grants section, there we will find our complete package.

{% hint style="info" %}
Updates will be announced via in our [`Discord`](https://discord.gg/U2aWW54jnY)`but` remember to claim your roles by logging into our website to view your customer channel.
{% endhint %}

## 3. Unzip

Unzip meteo-trucker-escrow using WinRAR or any other supported software.

## 4. Add to your resources

Add `meteo-trucker` to your server's resources folder and ensure it is loaded. We highly recommend creating a separate folder for the meteo scripts and placing `meteo-trucker` in it.

```
ensure [meteo]
```

or

```
ensure meteo-trucker
```

## 5. Run the sql file

```sql
CREATE TABLE IF NOT EXISTS `meteo_trucker` (
  `id` INT(11) NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(255) DEFAULT NULL,
  `currentXP` int(11) DEFAULT 0,
  `completedRoutes` int(11) DEFAULT 0,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

## 5. Config `'config.lua'`

configer config.lua file as you want and make changes. **If you are using different fuel or notify, change from** `cl_open.lua`

## 6. Ready to test

{% hint style="success" %}
Now you are officially done `meteo-trucker`Installation. if you still have problems, please contact us form Discord
{% endhint %}
