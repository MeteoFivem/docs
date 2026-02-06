---
description: >-
  How to add vehicle images to your dealership shop UI. Supports local images or
  CDN hosting.
---

# Adding Vehicle Images

## How do vehicle images work?

Vehicle images appear on the shop UI cards. If an image is found, it shows the image. If not, it falls back to the default car icon.

**Image naming is important:** The filename must match the vehicle's `model` name from QBCore.

| Vehicle Model | Image Filename  |
| ------------- | --------------- |
| `adder`       | `adder.webp`    |
| `zentorno`    | `zentorno.webp` |
| `t20`         | `t20.webp`      |
| `speeder`     | `speeder.webp`  |

***

## Option 1: Local Images

Store images directly in your resource folder.

### Setup

1. Add images to `meteo-dealerships/web/build/images/`
2. Leave `Config.imagesCDN` empty in config

```lua
Config.imagesCDN = ''
```

### File Structure

```
meteo-dealerships/
└── web/
    └── build/
        └── images/
            ├── adder.webp
            ├── zentorno.webp
            ├── t20.webp
            └── speeder.webp
```

### Image Requirements

| Property   | Recommendation                  |
| ---------- | ------------------------------- |
| Format     | `.webp` (preferred) or `.png`   |
| Size       | 400x225px or similar 16:9 ratio |
| Background | Transparent recommended         |
| File size  | Under 100KB per image           |

***

## Option 2: CDN Hosting

Host images on an external server or CDN for better performance.

### Setup

Set your CDN URL in `shared/config.lua`:

```lua
Config.imagesCDN = 'https://assets.meteofivem.net/vehicles/'
```

### How URL is Built

The script builds the image URL automatically:

```
{CDN} + {model} + '.webp'
```

**Example:**

* CDN: `https://assets.meteofivem.net/vehicles/`
* Model: `adder`
* Result: `https://assets.meteofivem.net/vehicles/adder.webp`

### CDN File Structure

```
https://assets.meteofivem.net/vehicles/
├── adder.webp
├── zentorno.webp
├── t20.webp
└── speeder.webp
```

***

## Finding Vehicle Model Names

The model name comes from QBCore's `shared/vehicles.lua`:

```lua
{ model = 'adder', name = 'Adder', brand = 'Truffade', price = 900000, category = 'super', type = 'automobile', shop = 'pdm' },
```

Use the `model` value (e.g., `adder`) for your image filename.

***

## Quick Checklist

**For local images:**

* Images in `web/build/images/` folder
* `Config.imagesCDN = ''`
* Filename matches model name
* Using `.webp` or `.png` format

**For CDN images:**

* `Config.imagesCDN` set to your CDN URL
* URL ends with `/`
* Images uploaded to CDN
* Filename matches model name

***

## Troubleshooting

### Image not showing

1. Check filename matches model name exactly (case-sensitive)
2. Verify file extension is `.webp`
3. For CDN: check URL is accessible in browser
4. For local: ensure file is in `web/build/images/` folder

### Image shows but looks wrong

* Use transparent background for best results
* Recommended aspect ratio is 16:9
* Keep file size under 100KB for fast loading

***

## Capturing Your Own Images

Use our free [meteo-vehiclecapture](https://github.com/MeteoStudios/meteo-vehiclecapture) tool to automatically capture vehicle images with transparent backgrounds.

### Features

* Automatic green screen removal
* Transparent PNG/WebP output
* Batch capture from vehicle list
* Adjustable camera angles per vehicle

### Quick Start

1. Download from [GitHub](https://github.com/MeteoStudios/meteo-vehiclecapture)
2. Install the `screencapture` dependency
3. Add your vehicles to `in/vehicles.lua`
4. Run `/veh-c-all` to capture all vehicles

### Commands

| Command                 | Description                   |
| ----------------------- | ----------------------------- |
| `/veh-c [model]`        | Capture single vehicle        |
| `/veh-c-all`            | Capture all from vehicles.lua |
| `/veh-c-adjust [model]` | Adjust camera settings        |

Images are saved to `meteo-vehiclecapture/images/` - copy them to your dealership's `web/build/images/` folder.
