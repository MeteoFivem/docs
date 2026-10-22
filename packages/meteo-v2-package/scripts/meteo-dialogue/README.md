---
description: >-
  Meteo Dialogue - the NPC conversation system used across the Meteo V2
  package, with a camera that focuses the NPC, voice lines, chained steps and
  item previews.
---

# Meteo Dialogue

This is a guide about testing the Meteo V2 dialogue script designed exclusively for the Meteo V2 package.

Meteo Dialogue is the conversation window you see whenever you talk to an NPC. Civilian job bosses, the vehicle rental clerk, the crime tablet contacts, prison NPCs, properties and more all use it, so every conversation in the city looks and works the same way.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Nothing else - any NPC you can talk to opens a dialogue

***

## Testing Dialogue

### Talking to an NPC

{% stepper %}
{% step %}
Go to an NPC you can talk to, for example a civilian job boss or the vehicle rental clerk, and use your target on them
{% endstep %}

{% step %}
The camera moves in front of the NPC's face and the NPC greets you with a voice line
{% endstep %}

{% step %}
The NPC name, role and what they say show at the bottom. The text types out letter by letter
{% endstep %}

{% step %}
Other players are hidden while you talk, so nothing gets in the way of the camera
{% endstep %}
{% endstepper %}

### Picking an Option

{% stepper %}
{% step %}
Click an option, or press `1` to `9` to pick it with your keyboard
{% endstep %}

{% step %}
Options can show a price tag, a small item picture, or a big preview image when you hover them
{% endstep %}

{% step %}
Options that are not available right now are greyed out and cannot be picked
{% endstep %}

{% step %}
When an NPC has a long list of options, a search box shows at the top so you can find one fast
{% endstep %}
{% endstepper %}

### Going Through Steps

{% stepper %}
{% step %}
Some options open a new step of the conversation. The new step slides in and the camera stays on the NPC
{% endstep %}

{% step %}
The trail of what you picked shows next to the NPC name, for example `Fix my car › Pay cash`
{% endstep %}

{% step %}
Press `Backspace` or pick a back option to go to the previous step
{% endstep %}

{% step %}
Press `ESC` or pick **Leave** to end the conversation
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
The typing animation, hiding other players, when the search box shows, the NPC greeting voice line and the camera distance, height, field of view and transition speed are all configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

* Every conversation in the package uses this one script, so they all look the same
* Developers can use it in their own scripts with a few exports - see [Exports](exports.md)
* It supports 20 languages like the rest of the package

{% content-ref url="exports.md" %}
[exports.md](exports.md)
{% endcontent-ref %}
