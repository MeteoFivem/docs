---
description: >-
  Meteo Image Studio - captures clean, transparent vehicle, clothing and
  furnishing images in game designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - packages/meteo-v2-package/how-to/how-to-fivemanage-vehicle-images.md
    - packages/meteo-v2-package/how-to/how-to-fivemanage-clothing-images.md
    - servers/meteo-fivem-server/documentation/how-to/how-to-fivemanage-vehicle-images.md
    - servers/meteo-fivem-server/documentation/how-to/how-to-fivemanage-clothing-images.md
---

# Meteo Image Studio

This is a guide about testing the Meteo V2 image studio script designed exclusively for the Meteo V2 package.

The image studio captures the images your other scripts show - vehicles in dealerships, clothing in the clothing menu and props in furnishing. Everything is done in game, so you do not need any 3rd party capture scripts. It replaces the old meteo-clothingcapture and meteo-vehiclecapture tools.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* The **Image studio** permission. It is god only out of the box, and you can give it to a role under **Staff > Roles** in [meteo-manage](../meteo-manage/)
* Open the studio from **Image Studio** in the admin menu sidebar, or with `/imagestudio [model]`

{% hint style="warning" %}
Capturing is turned off on the showcase server. You can open the studio, browse every tab and look at the existing images, but nothing is captured or saved. On your own server it all works.
{% endhint %}

***

## Testing Image Studio

### Opening the Studio

{% stepper %}
{% step %}
Open the admin menu with **F9** or `/admin` and click **Image Studio** in the sidebar. You can also open it from **Script Settings > Image Studio > Open image studio**
{% endstep %}

{% step %}
Or type `/imagestudio` in chat. Add a vehicle model, for example `/imagestudio adder`, to load that vehicle straight away
{% endstep %}

{% step %}
The list is on the left, the live studio in the middle, and the loaded item with its current image on the right
{% endstep %}
{% endstepper %}

### Vehicles

{% stepper %}
{% step %}
Open the **Vehicles** tab. Every vehicle on the server is listed, with search by model, name or brand and a category filter
{% endstep %}

{% step %}
Use the filters - **All**, **Missing**, **Captured**, **Flagged** and **Selected**
{% endstep %}

{% step %}
Click a row to load the vehicle in the studio. It spawns in an empty sky studio and the camera frames it on its own
{% endstep %}

{% step %}
Hit **Capture** (or **Recapture** if it already has an image). The new image shows on the right with its file name and size
{% endstep %}
{% endstepper %}

### Clothing

{% stepper %}
{% step %}
Open the **Clothing** tab. Every drawable is listed for both male and female, grouped like "Male · Top" and "Female · Shoes"
{% endstep %}

{% step %}
The categories are mask, top / jacket, legs, shoes and bag - the ones meteo-appearance shows images for
{% endstep %}

{% step %}
Capture an item. A separate studio ped is used, so your own character is never changed, and only the item itself ends up in the image
{% endstep %}

{% step %}
Empty drawables have nothing to draw. They are marked **Empty**, skipped and no longer count as missing. Recapture checks one again
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Custom clothing works too. Capture on a server that has all of your clothing streamed, so the images match what players see.
{% endhint %}

### Furnishing

{% stepper %}
{% step %}
Open the **Furnishing** tab. Every prop in the [meteo-furnishing](../meteo-furnishing/) catalog is listed, grouped by its furnishing category
{% endstep %}

{% step %}
Click a prop and capture it. A prop that is in more than one category is only captured once
{% endstep %}
{% endstepper %}

### Capturing Many at Once

{% stepper %}
{% step %}
Tick the box on any rows you want, or use **Select shown** to pick everything the current search and filter shows
{% endstep %}

{% step %}
At the bottom use **Capture selected**, **Capture missing** or **Recapture flagged**. Each button shows how many it will do
{% endstep %}

{% step %}
Pick a speed - **Quality**, **Balanced** or **Fast**
{% endstep %}

{% step %}
A progress screen shows what is being captured now, how many are saved and roughly how long is left. **Cancel** stops the run
{% endstep %}

{% step %}
Shots that come out wrong (cut off at the edge, frames not matching, nothing found) are re-shot automatically. Anything still off is saved and marked **Flagged**, so you can recapture it later
{% endstep %}
{% endstepper %}

### Where Images Are Saved

Images are saved as `.webp` with a transparent background inside the meteo-imagestudio resource:

| Tab | File |
| --- | ---- |
| Vehicles | `images/vehicles/<model>.webp` |
| Clothing | `images/clothing/<gender>_<category>_<drawable>.webp` (for example `male_top_15.webp`) |
| Furnishing | `images/furnishing/<model>.webp` |

### How Scripts Use the Images

[meteo-dealerships](../meteo-dealerships/), [meteo-appearance](../meteo-appearance/) and [meteo-furnishing](../meteo-furnishing/) ask the image studio where the images are, so nothing needs to be copied. Other scripts that show vehicle images, like garages, job garage, bennys and the admin menu, use the studio's vehicle images the same way.

{% hint style="warning" %}
Restart meteo-imagestudio after capturing so the new images are served to players.
{% endhint %}

### Optional CDN

You do not need a third party host. The studio serves the images itself, so it works out of the box.

{% hint style="info" %}
If you would rather keep the images off the server download, upload the `vehicles`, `clothing` and `furnishing` folders to any CDN and set `Config.imageCdn` in `meteo-imagestudio/shared/config.lua` to the root URL that holds them, ending with `/`.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
The command, the studio location and lighting, the camera shot, vehicle colour and plate, the clothing categories, image quality and size, the glass tint and the capture speeds are all configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

* The defaults are already tuned, nothing needs changing for normal use
* Access is checked against meteo-manage every time, so taking the permission away stops a player mid session
* Vehicle windows get a smoked tint instead of a see-through hole
* For the cleanest live clothing view run `allowEmptyHeadDrawable true` once in F8. The images never contain the head either way

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}

{% content-ref url="../meteo-dealerships/" %}
[meteo-dealerships](../meteo-dealerships/)
{% endcontent-ref %}

{% content-ref url="../meteo-appearance/" %}
[meteo-appearance](../meteo-appearance/)
{% endcontent-ref %}

{% content-ref url="../meteo-furnishing/" %}
[meteo-furnishing](../meteo-furnishing/)
{% endcontent-ref %}
