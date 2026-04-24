---
description: How we build and ship updates to the meteo fivem server.
icon: code-branch
---

# Development and Updates

How we ship updates, and how your server tells you when one is out.

***

## How updates ship

Every release goes through our own automation tool. It bundles the changes, tags the version, and produces the same package every single time. No manual copy-paste, no "it worked on my machine" releases.

***

## Discord and GitBook get updated automatically

When a release goes out, the same tool does three things:

1. Sends the build to customers
2. Posts the full changelog to our Discord
3. Updates the [Changelogs](changelogs.md) page here on GitBook

You only need to check one place. They all show the same thing.

***

## Changelogs list every changed file

Each changelog includes the exact files we touched. So when an update drops, you can:

* Replace only the files that actually changed instead of swapping out your whole server
* See exactly what's different before applying it
* Confidently update without worrying about overwriting the wrong thing

***

## Your server tells you when an update is out

The server checks our version file the moment it starts up, then again every 30 minutes. If you are behind:

* The console banner turns red on startup
* A line shows your current version next to the latest version
* The same warning prints every time a player joins or leaves the server

So even if you missed the Discord ping that week, the console will keep reminding you.

You also always know exactly what version you are running. It prints on every server start, alongside your loaded settings (currency, speed unit, language, etc.) and a link to support.

***

{% hint style="success" %}
All updates are free for life. Nothing extra to buy.
{% endhint %}

{% hint style="info" %}
Want to see what we have shipped? Check the [Changelogs](changelogs.md) for the full history.
{% endhint %}
