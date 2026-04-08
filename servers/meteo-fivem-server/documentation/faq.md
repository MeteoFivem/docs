---
description: >-
  Frequently asked questions about the meteo fivem server. Common questions
  about testing, purchasing, setup and customization.
icon: circle-question
---

# FAQ

***

## Why Meteo Server?

<details>

<summary>What makes meteo server different from other premade servers?</summary>

Every script is built from scratch exclusively for meteo server. We dont use random free scripts stitched together. Everything is custom, works together out of the box, and is secured from the code level following official FiveM security guidelines.

</details>

<details>

<summary>Is it secured against cheaters?</summary>

Yes. Most anti-cheats are useless if your server code has exploits. We follow every official FiveM security guideline - all server events are validated, server-side authority on all critical actions, input validation on all client-to-server communication, no exposed exports that can be abused, and rate limiting on sensitive actions. The code itself is secured, not just a layer on top. See the full breakdown at [Security and Optimization](security-and-optimization.md).

</details>

<details>

<summary>What framework does it use?</summary>

Built on a mix of QBCore and QBox framework - best of both worlds. Works with ox_inventory, ox_target, ox_lib and other popular resources.

</details>

<details>

<summary>Can I translate it to my language?</summary>

Yes. One config change and every script updates automatically. 13+ languages included out of the box. You can add any language by creating a single JSON file per script using ox_lib locales. No code or UI changes needed. See [How to Translate the Server](how-to/how-to-translate.md) for full steps.

</details>

***

## Testing

<details>

<summary>How do I get access to the test server?</summary>

Join our Discord at [discord.meteofivem.net](https://discord.meteofivem.net), open a ticket and say you want to test the meteo server. We will grant you access. See [How to Access the Testing Server](how-to/how-to-access-testing-server.md) for full steps.

</details>

<details>

<summary>Do I need to pay anything to test?</summary>

No. Testing is completely free. You can try every script on the test server before buying.

</details>

<details>

<summary>Where are the video testing guides?</summary>

Once you get test server access on Discord, you will see the exclusive testing guide channel with all video guides.

</details>

<details>

<summary>My FiveM account is not connecting to the test server</summary>

Make sure your Discord account is linked to your FiveM account. Go to FiveM Settings and connect your Discord, or go to Discord Settings → Connections → add FiveM.

</details>

***

## Purchasing

<details>

<summary>Where do I buy the server?</summary>

Purchase at [meteofivem.net/meteo-fivem-server](https://meteofivem.net/meteo-fivem-server).

</details>

<details>

<summary>What do I get when I purchase?</summary>

You get the full server package with all scripts, all future updates, and full support from our team.

</details>

<details>

<summary>Do I get updates after purchasing?</summary>

Yes. All updates are included with your purchase. We push updates regularly.

</details>

***

## Setup & Installation

<details>

<summary>How do I install the server?</summary>

Follow the [Installation Guide](installation-guide.md). We also have an exclusive installation video in the customer section on Discord.

</details>

<details>

<summary>What do I need to run the server?</summary>

A Windows VPS, MariaDB, HeidiSQL, VS Code, WinRAR and FiveM artifacts. Everything is covered in the [Installation Guide](installation-guide.md).

</details>

<details>

<summary>Do I need a CFX subscription?</summary>

Only if you need more than 8 player slots or want custom clothing streaming. For 8 slots with custom clothing it's free. For more you need Argentum or higher from [portal.cfx.re/subscriptions](https://portal.cfx.re/subscriptions).

</details>

<details>

<summary>How do I add admins to my server?</summary>

Edit `permissions.cfg` with player identifiers. See [How to Add Admins](how-to/how-to-add-admins.md).

</details>

***

## Customization

<details>

<summary>Can I change the server language?</summary>

Yes. One config change in `ox.cfg` and every script updates automatically. 13 languages included out of the box. You can also add your own. See [How to Translate the Server](how-to/how-to-translate.md).

</details>

<details>

<summary>Can I change prices, rewards, locations and other settings?</summary>

Yes. Almost everything is configurable. Each script has its own config file where you can change prices, rewards, locations, cooldowns, difficulty and more.

</details>

<details>

<summary>Can I change the currency symbol?</summary>

Yes. Set `meteo:currency` in `meteo.cfg` to any symbol you want (`$`, `€`, `£`, etc). See [Configuration Guide](configuration-guide.md).

</details>

<details>

<summary>Can I add my own Discord rich presence?</summary>

Yes. Set up your own Discord app and configure it in `meteo.cfg`. See [How to Change Discord RPC](how-to/how-to-discord-rpc.md).

</details>

<details>

<summary>Do I need to edit any code to customize the server?</summary>

No. Everything is config-based. You dont need to touch any code, UI or codebase to customize.

</details>

***

## Support

<details>

<summary>Where do I get support?</summary>

Join our Discord at [discord.meteofivem.net](https://discord.meteofivem.net) and open a ticket. We are happy to help with any questions.

</details>

<details>

<summary>Is there documentation for each script?</summary>

Yes. Every script has its own testing guide with step-by-step instructions. Check the [Scripts](scripts/) page.

</details>
