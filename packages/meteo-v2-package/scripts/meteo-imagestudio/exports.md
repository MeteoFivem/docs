---
description: >-
  Every meteo-imagestudio export with a simple example - building image URLs
  for captured vehicles, clothing and furnishing, and opening the studio.
icon: code
---

# Exports

Show the images the studio captured in your own UIs, and open the studio from your own admin tools.

***

## Shared

### GetImageBase(folder)

Works on the client and the server. Returns the base URL of a captured image folder. Add the file name to get a full image URL.

```lua
local base = exports['meteo-imagestudio']:GetImageBase('vehicles')
local url = base .. 'adder.webp'

print(url) --> https://cfx-nui-meteo-imagestudio/images/vehicles/adder.webp
```

| Folder | File name |
| ------ | --------- |
| `vehicles` | `<model>.webp` |
| `clothing` | `<gender>_<name>_<drawable>.webp` |
| `furnishing` | `<model>.webp` |

When `Config.imageCdn` is set, the URL points at your CDN instead (`Config.imageCdn .. folder .. '/'`). Returns `nil` if `folder` is not a lowercase word.

{% hint style="info" %}
Without a CDN the images are served from the resource itself. Restart meteo-imagestudio after capturing so the new files are served.
{% endhint %}

***

## Server

### OpenStudio(source)

Opens the studio for a player. They still need the **Image Studio** (`use_imagestudio`) permission in meteo-manage, otherwise they get a "no permission" notification.

```lua
local opened = exports['meteo-imagestudio']:OpenStudio(source)
print(opened) --> true
--> false if the player lacks the permission or meteo-manage is not started
```
