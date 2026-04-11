---
description: >-
  How the meteo fivem server is secured and optimized at the code level.
  lib.points, job-gated targets, server-side authority, event validation and
  real resmon tested performance.
icon: shield-check
---

# Security and Optimization

Most premade FiveM servers are built by stitching random scripts together. They have no consistent security, no optimization standards, and rely on anti-cheats that dont actually protect against code-level exploits.

We build every single script from scratch. That means we control the security and performance of the entire server - not just a layer on top.

***

## Why Anti-Cheats Alone Dont Work

There are no shortcuts in securing a FiveM server. You cant just install an anti-cheat and call it secure.

Cheat menus find exploits, bugs and loopholes in bad code and abuse them. If your server events are not validated, if your server trusts the client for critical actions, if your exports are exposed - no anti-cheat will save you. Secure code is the backbone of all server security.

That is what we focused on. Every script follows official FiveM security guidelines:

* [FiveM Server Security Docs](https://docs.fivem.net/docs/developers/server-security/)
* [Securing Your Server - CFX Forum Guide](https://forum.cfx.re/t/tut-securing-your-server/345465)
* [How to Protect Your Server from Cheaters - CFX Forum](https://forum.cfx.re/t/how-to-protect-your-server-from-most-cheaters-easily-101/5160816)

***

## What We Did - Security

### Server-Side Authority

All critical actions are handled server-side. The client never decides how much money to add, what items to give, or what job to set. The server validates everything.

* Money, items, jobs, vehicles - all server-side authority
* Client sends requests, server validates and executes
* No trusting the client for any critical game state

### Event Validation

Every server event validates the source player. No event can be triggered from client without proper checks.

* All net events check the source player exists and has permission
* No exposed server events that can be triggered by injectors
* Rate limiting on sensitive actions to prevent spam exploits

### No Exposed Exports

Server exports are only used for inter-resource communication where needed. No exports that can be called externally to bypass security.

### NUI Callback Strict Mode

A recent FiveM addition that prevents other resources from triggering NUI callbacks in your resource. Without this, another resource on the server could call your NUI callbacks and potentially exploit them. All our scripts with NUI have `nui_callback_strict_mode 'true'` enabled in their fxmanifest. We tested every script with this enabled and no issues or errors were found. See [CFX Forum - NUI Callback Strict Mode](https://forum.cfx.re/t/how-to-nui-callback-strict-mode-what-is-it/) for more details.

***

## What We Did - Optimization

### lib.points for Zone Targets

This is a big one that most servers completely ignore. When you have target zones (like job locations, shop locations, interaction points), most scripts load ALL targets at once when the resource starts. That means hundreds of targets running in memory even when the player is nowhere near them.

We use `lib.points` from ox_lib to only load targets when the player is actually nearby. Target zones load within 15m and unload when the player leaves. This massively reduces idle resource usage.

### Job-Gated Target Loading

For job scripts like police, mechanic, EMS - the targets at stations (duty points, armory, lockers, garages) only load if the player actually has that job. If you are not a police officer, zero police station targets are running. Switch to police job and they load. Switch away and they unload.

This means a player who is not a cop has zero overhead from the police script. Same for mechanic, EMS and every other job. Most premade servers load all job targets for all players at all times regardless of their job.

### No Polling Loops

We dont use `while true` loops to check player state. Instead we use `lib.points`, `lib.onCache` and event-driven patterns. The server only does work when something actually changes, not every frame.

### Entity Cleanup

All spawned entities (peds, props, vehicles) are properly cleaned up when:
* Player leaves the area
* Player changes job
* Resource stops
* Player disconnects

No leftover entities eating server performance.

***

## See It Yourself - Resmon Tests

Dont just take our word for it. When you are on the showcase server, enable developer mode in FiveM and use resmon to see real-time resource usage for every script. Follow the [FiveM Developer Commands guide](https://docs.fivem.net/docs/client-manual/console-commands/#developer-commands) to enable it.

We recorded resmon performance tests showing real idle and active usage:

* [Resmon Performance Test 1](https://youtu.be/cUFGliuV0mc?si=YVQYWsaJ1kd_2w-Y)
* [Resmon Performance Test 2](https://youtu.be/lSWvbfkhsE4?si=C4tunOhg-Q0jncMW)

{% hint style="success" %}
When testing the meteo server, open FiveM with developer mode enabled and use resmon to check the performance yourself. Compare it with any other premade server. The difference is clear.
{% endhint %}

***

## Server Configuration

Beyond code-level security, we also configure FiveM server convars for additional protection:

* `sv_pureLevel` - blocks modified client files to prevent texture/script injection
* `sv_entityLockdown` - prevents clients from creating unauthorized entities
* `sv_filterRequestControl` - blocks unauthorized entity control requests
* `sv_authMaxVariance` and `sv_authMinTrust` - reduces identity spoofing
* `sv_disableClientReplays` - reduces cheating vectors by disabling replay features

These are server-level protections that work alongside our code-level security. They are not a replacement for secure code - they are an additional layer.

***

## The Difference

Most premade servers:
* Use random free scripts with no security standards
* Load all targets for all players at all times
* Use polling loops that waste CPU every frame
* Rely on anti-cheats instead of secure code
* Never clean up spawned entities properly
* Have no consistent optimization across scripts
* Trust the client for prices, item data and action validation
* Broadcast sensitive data to all connected players
* No distance checks - actions can be triggered from anywhere on the map

Meteo server:
* Every script built from scratch with security and optimization as priority
* lib.points based target loading - only loads what is nearby
* Job-gated targets - zero overhead for jobs you dont have
* Event-driven patterns instead of polling loops
* Proper entity cleanup on all state changes
* Server-side authority and event validation on everything
* Distance validation on all location-dependent actions
* Input validation and bounds checking on all client-sent data
* Forensic and sensitive data protected from unnecessary exposure
* Server-side price resolution - client cannot manipulate transaction amounts
* Rate limiting on inventory and economy actions
* Secure callbacks (lib.callback) instead of raw events for data fetching
* Server convars configured for additional protection layers
* Real resmon tested and proven performance

Since we build all scripts ourselves, we can guarantee every single one follows the same security and optimization standards. That is something no other premade server can offer when they are mixing scripts from different authors with different coding practices.