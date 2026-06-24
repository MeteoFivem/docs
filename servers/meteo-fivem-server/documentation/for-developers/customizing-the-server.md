---
description: >-
  What you can change on the meteo fivem server, what it takes, the framework and
  exports we support, and how to add or remove your own content.
icon: wrench
---

# Customizing the Server

Yes, the meteo server can be customized. But read this page first so you know exactly what you can change and what it takes.

***

## What Is Open and What Is Not

Our own scripts are protected with <a href="https://docs.fivem.net/docs/server-manual/asset-escrow/" target="_blank">FiveM asset escrow</a>. All meteo scripts core is encrypted, so the internal logic of each script is not something you edit directly. The QBox core and all open source scripts that ship with the server stay open and fully editable, exactly as they are.

Escrow does not lock you in. We deliberately left open everything you would actually want to customize:

* **Every config file is fully open.** Prices, rewards, locations, cooldowns, items, languages and more - all editable, no coding needed.
* **The parts meant to be extended are left open too**, outside the escrow, so you can edit them directly.
* **You can add your own content** like custom phone apps, custom crime tablet services and custom job tablet jobs, without touching the protected core at all.

So you get protected, secure scripts and the freedom to customize the parts that matter.

***

## You Need Real Development Experience

Simple changes need no coding at all. Editing config files - prices, rewards, locations, language - is something anyone can do by following the docs.

But once you go past configs and start editing the open files or wiring in your own scripts, you need genuine FiveM development experience. Configuring a few scripts and following setup guides does not make you a developer. This takes real, hands-on experience actually writing and building FiveM resources.

We mean someone who genuinely geeks out over FiveM. Someone who has built resources end to end from scratch, not just edited what others made. Someone who can open a script, understand exactly how it works, and change it without breaking three other things in the process. That is the kind of experience deeper customization actually takes.

If that is not you, stick to the config files. Do not start editing the open code or adding new third party scripts from other developers, or you will break things and not know why.

{% hint style="danger" %}
**We do not provide support for a customized server.**

Once you modify the server, we cannot help debug it. We learned this the hard way. Too many people with no development knowledge changed core things, broke their server, and then opened tickets saying "this and that is not working" - when the cause was their own untested edits.

If you customize, you are on your own for that part. Please test your own changes.
{% endhint %}

{% hint style="success" %}
**Are you a professional developer with a genuine limitation?**

If you actually know what you are doing and you hit a real limitation in how the server is built, contact us. Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a> and explain it. We will try our best to support you.
{% endhint %}

***

## The Core - Built on QBox

The server is built on the modern **QBox** framework, using **ox\_inventory** and **ox\_lib**. These are the most widely used resources in the FiveM ecosystem right now.

Because of that, you can install most scripts from the top FiveM creators without any issues. If a script supports QBox and ox\_inventory (and almost all modern ones do), it will work alongside our scripts.

***

## How We Built for Customization

The problem with using custom scripts is exports. Our meteo scripts have their own exports, and those exports are not what other developers build against. So a random script you buy will not know how to talk to our banking, our appearance, our phone, and so on.

We solved this. Where it matters, our scripts **also** support the exports of the widely used script everyone already builds for. That means a third party script can talk to our scripts without the other developer ever having to add "meteo" support.

| Our script | Also supports the exports of | What that means |
| --- | --- | --- |
| Appearance | <a href="https://github.com/iLLeniumStudios/illenium-appearance" target="_blank">illenium-appearance</a> | Almost every clothing related FiveM script supports illenium-appearance. Any script that needs clothing support will work with our appearance. |
| Banking | <a href="https://github.com/Renewed-Scripts/Renewed-Banking" target="_blank">Renewed-Banking</a> | Your custom scripts can use Renewed-Banking exports directly. No need to contact the script author and ask them to add meteo banking support. |
| Boss Menu | <a href="https://github.com/Qbox-project/qbx_management" target="_blank">qbx\_management</a> | Use qbx\_management exports for your custom boss / management features. |
| Phone | npwd and QBox default phone exports | Scripts built for npwd or the default QBox phone work with our phone. |
| Fuel | LegacyFuel | LegacyFuel exports are supported, so fuel dependent scripts just work. |
| Garages | jg-advancedgarages events | We added the widely used `jg-advancedgarages:client:store-vehicle` and `jg-advancedgarages:client:open-garage` events, so other developer scripts built for jg-advancedgarages work with our garages. |
| Medical Job | QBox health events | Our medical job supports the standard QBox based health events. |

For the minigames, every minigame is a standalone resource with a single export you can call from any script. See [Meteo Minigames](../scripts/meteo-minigames/README.md) for how to call them.

{% hint style="info" %}
**Need support for another export?** Contact us. If the request is reasonable and worth it, we will add support for it.
{% endhint %}

***

## Adding Custom Content to Meteo

You do not have to fight the server to add your own content. We built parts of it specifically so you can extend them.

### Custom Phone Apps

Our phone supports custom apps. You can build your own app as a standalone resource and add it to the meteo phone. See the [Meteo Phone](../scripts/meteo-phone/README.md) docs.

### Custom Crime Tablet Services

Our crime tablet supports custom services. You can connect any heist or criminal service to the crime tablet system.

* Demo: <a href="https://github.com/MeteoStudios/meteo-crimesservice-demo" target="_blank">meteo-crimesservice-demo</a>

### Custom Job Tablet Jobs

Our job tablet supports custom jobs. You can create your own job and connect it to the job tablet system.

* Demo: <a href="https://github.com/MeteoStudios/meteo-tablet-customjobs-demo" target="_blank">meteo-tablet-customjobs-demo</a>

***

## Removing Content

You can also remove things you do not want. The job tablet jobs, the crime tablet services - if you do not like them, take them out. We designed our core to handle all of this, so removing a job or a service will not break the rest of the server.

***

{% hint style="success" %}
**Genuine question about customizing?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Remember we only support customization questions from developers with the right experience.
{% endhint %}
