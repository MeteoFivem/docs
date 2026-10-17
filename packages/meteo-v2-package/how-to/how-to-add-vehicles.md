---
description: >-
  How to add new vehicles to your Meteo V2 server. Add them in game from the
  dealership admin panel, then export them to meteo-core with one copy and
  paste.
icon: car
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/how-to/how-to-add-vehicles.md
---

# How to Add Vehicles

You add new vehicles in game from the dealership admin panel. Then you copy one generated block into `meteo-core/shared/vehicles.lua` so garages and every other script know the vehicle too.

***

{% hint style="warning" %}
**Before you start:** the vehicle must already be streamed on your server. Add its resource to your server and make sure you can spawn it with `/car spawncode`.
{% endhint %}

***

## Step by Step

{% stepper %}
{% step %}
**Open the dealership admin panel**

Type `/dealeradmin` in game, or open it from **Script Settings** in the admin menu. Go to **Vehicles**
{% endstep %}

{% step %}
**Add the vehicle**

Click **Add vehicle** and fill in:

| Field | What it is |
| ----- | ---------- |
| Spawn code | The model name, lowercase letters, numbers and underscore only |
| Name | Display name in the shop |
| Brand | Manufacturer |
| Category | Vehicle category, like `sports` or `suvs` |
| Class | S, A, B, C, D or E |
| Base price | The price before dealership markup |
| Shops | Which dealership shop tags sell it |

A vehicle shows at a dealership only if it matches one of the dealership's categories and one of its shop tags.
{% endstep %}

{% step %}
**Export for core**

On the Vehicles page click **Export for core**. It shows how many catalog vehicles are missing from your core and gives you the exact code for them. Click **Copy**
{% endstep %}

{% step %}
**Paste into vehicles.lua**

Open `meteo-core/shared/vehicles.lua` and paste the copied code before the closing brace. It looks like this:

```lua
    meteoc17 = {
        name = 'Dominator GT CTX C3',
        brand = 'Vapid',
        model = 'meteoc17',
        price = 80000,
        category = 'muscle',
        type = 'automobile',
        customclass = 'C',
        hash = `meteoc17`,
    },
```
{% endstep %}

{% step %}
**Restart the server**

Restart the server. Your vehicle is now in the dealership, and garages and other scripts know its name too.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Until you paste the code and restart, the vehicle can already be sold at the dealership, but scripts like garages have no name for it.
{% endhint %}

***

## Vehicle Images

Capture a clean image of your new vehicle in game with [Meteo Image Studio](../scripts/meteo-imagestudio/). The dealership uses it automatically.

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
