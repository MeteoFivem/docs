---
description: >-
  Every meteo-scenes export with a simple example and what it gives back -
  graffiti counts and locations per organization.
icon: code
---

# Exports

Read how much graffiti each organization has on the map, for a territory board, a turf war or your own org perks. Both exports are server side.

A scene counts as an organization's graffiti when the player who placed it was in a meteo-organizations org at the time. The crime tablet uses these for its territory map.

***

## GetOrgGraffitiCounts()

How many live scenes each organization has placed, keyed by org id. Orgs with none are not in the table.

```lua
local counts = exports['meteo-scenes']:GetOrgGraffitiCounts()
for orgId, count in pairs(counts) do
    print(orgId, count)
end
--> 12   9
--> 4    3
```

The keys are org ids, not a list, so loop with `pairs`. To read one org:

```lua
local mine = exports['meteo-scenes']:GetOrgGraffitiCounts()[org.id] or 0
```

***

## GetOrgGraffitiLocations(orgId)

Where an organization's scenes are, as map coordinates. Empty table if the org has none.

```lua
for _, pin in ipairs(exports['meteo-scenes']:GetOrgGraffitiLocations(12)) do
    print(pin.id, pin.x, pin.y)
end
--> 318   -54.2   -1801.7
```

```lua
-- each location:
{ id = 318, x = -54.2, y = -1801.7 }   -- scene id and 2D position
```

Combine it with meteo-organizations to find the org first:

```lua
local org = exports['meteo-organizations']:GetPlayerOrg(citizenid)
if org then
    local pins = exports['meteo-scenes']:GetOrgGraffitiLocations(org.id)
    print(#pins) --> 9
end
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
