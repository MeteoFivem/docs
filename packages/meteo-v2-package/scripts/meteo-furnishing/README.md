---
description: >-
  Meteo furnishing - furnish your properties and apartments with an in-game
  furniture catalog script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-furnishing/
---

# Meteo Furnishing

This is a guide about testing the Meteo V2 furnishing script designed exclusively for the Meteo V2 package.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Familiar with [getting started](../../getting-started.md) basics
* Own a property or an apartment room. Check the [meteo-properties](../meteo-properties/) guide to get one

***

## Testing Furnishing

{% stepper %}
{% step %}
**Opening Furnish Mode**

Go inside your property or apartment room and open Furnish from the F1 radial menu. Members need the furnish permission on their role to use it
{% endstep %}

{% step %}
**Placing Furniture**

Browse the catalog by category or search for furniture. Place it and move it with the gizmo (W to move, R to rotate), snap it to the ground, clone it, copy and paste positions, and undo or redo. You can also move the camera freely around the room
{% endstep %}

{% step %}
**Cart**

Placed items go into your cart first. Buy the cart to save them (bank or cash). If you leave with items still in the cart you can buy them, discard them or keep editing
{% endstep %}

{% step %}
**Editing and Selling**

Click any placed furniture to move it again or sell it. Selling gives back 50% of the price (configurable). Furniture bought with an item gives the item back instead
{% endstep %}

{% step %}
**Storage and Wardrobe**

Storage furniture works as a stash and wardrobe furniture opens your outfits. How many storage pieces you can place depends on the storage upgrade of the property
{% endstep %}

{% step %}
**Storage Lockpicking**

Other players can try to lockpick your storage with a `lockpick` or `advancedlockpick`. The owner needs to be online and gets an alert. A picked storage stays open for 5 minutes
{% endstep %}
{% endstepper %}

***

## In-Game Catalog Creator

* The furniture catalog lives in game now. Open the admin menu and go to Script Settings > Furnishing > Creator
* Add categories and the props in them with a name, model, price, a max per property and an optional required item. A category can make its props storage or wardrobes
* Addon props work too if your server streams them
* The furniture limit, payment method, sell-back refund and storage lockpicking are changed in the same menu
* Furniture pictures come from the in-game image studio, no third party script needed

***

## Good to Know

{% hint style="success" %}
The furniture limit, payment method, sell-back refund and storage lockpicking are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit furniture categories and props in-game with the Furnishing creator on the same page. Storage size and wardrobe settings stay on our config.
{% endhint %}

{% content-ref url="../meteo-properties/" %}
[meteo-properties](../meteo-properties/)
{% endcontent-ref %}
