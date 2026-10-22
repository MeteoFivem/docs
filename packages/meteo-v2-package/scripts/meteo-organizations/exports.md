---
description: >-
  Every meteo-organizations export a server owner would call - read a player's
  organization, award org XP, scale bonuses by org level and check HQs.
icon: code
---

# Exports

Read which organization a player is in, award org XP from your own crime scripts and scale your payouts by the org's level. All exports are server side and read straight from the database, so they work for offline players too.

Creating, inviting, promoting and the treasury are handled through the crime tablet, which calls its own set of exports on this script. Those are not listed here.

***

## Reading Organizations

### GetPlayerOrg(citizenid)

The full organization a player belongs to, or `nil` if they are not in one. A player who only has an org waiting for admin approval is not a member yet.

```lua
local org = exports['meteo-organizations']:GetPlayerOrg(citizenid)
if org then
    print(org.name, org.tag, org.level, org.myRank.id)
end
--> Southside Kings   SSK   4   veteran
```

```lua
-- record:
{
    id = 12, name = 'Southside Kings', tag = 'SSK', color = '#ff5d52', image = nil,
    level = 4,
    xp = 1200,           -- XP into the current level
    xpForNext = 3500,    -- nil at max level
    isMaxLevel = false,
    treasury = 8500,
    memberCapacity = 8,
    members = {
        { citizenid, name, profileImage, rankId, rankLabel, rankLevel, online, joinedAt },
    },
    myRank = { id = 'veteran', label = 'Veteran', level = 2, permissions = { ... }, isOwner = false },
    upkeep = { cost = 400, paid = false, dueAt = '2026-10-20 18:00:00' },
    upgrades = { members = { currentTier, maxTier, currentCapacity, nextTier, allTiers } },
    createdAt = ..., ownerCitizenid = 'ABC12345', hqPropertyId = nil,
}
```

This builds the whole member list, so call it when you need the details. To only check membership, the `id` from it is all you need for the other exports.

### GetOrgPublicProfile(orgId)

The public view of any organization, or `nil` if the id does not exist.

```lua
local p = exports['meteo-organizations']:GetOrgPublicProfile(12)
print(p.name, p.members, p.memberCapacity, p.leaderName)
--> Southside Kings   5   8   John Doe
```

```lua
-- record:
{ id, name, tag, color, image, level, members, memberCapacity, leaderName, createdAt }
```

### GetAllOrgs()

Every active organization, highest level first.

```lua
for _, org in ipairs(exports['meteo-organizations']:GetAllOrgs()) do
    print(org.tag, org.name, org.level, org.members)
end
--> SSK   Southside Kings   4   5
```

```lua
-- each org:
{ id, name, tag, color, level, image, members, leaderName, hqPropertyId }
```

### GetOrgRanks()

The ranks from `Config.ranks`, with their permissions.

```lua
for _, rank in ipairs(exports['meteo-organizations']:GetOrgRanks()) do
    print(rank.id, rank.level, #rank.permissions)
end
--> leader    3   11
--> veteran   2   7
--> member    1   1
```

***

## Org XP and Level Perks

### AddOrgXP(orgId, amount)

Awards XP to an organization and levels it up when it crosses a threshold. `amount` must be above 0.

```lua
local org = exports['meteo-organizations']:GetPlayerOrg(citizenid)
if org then
    local result = exports['meteo-organizations']:AddOrgXP(org.id, 150)
    print(result.success, result.newLevel, result.leveled)
end
--> true   5   true
```

```lua
-- result:
{ success = true, newXp = 350, newLevel = 5, leveled = true }
-- or
{ success = false }
```

If you only have a player's citizenid, `exports['meteo-crimetablet']:AddServiceOrgXP(citizenid, amount)` finds their org for you.

### GetOrgPerkValue(orgId, key)

The best value for a level perk that the org's level has unlocked, or `0` if none. Use it to scale your own bonuses by org level.

```lua
local bonus = exports['meteo-organizations']:GetOrgPerkValue(org.id, 'drug_sale_bonus')
print(bonus) --> 0.10    (level 3 or higher)

local price = basePrice * (1 + bonus)
```

The perks come from `Config.levelPerks`. You can add your own keys there and read them the same way:

```lua
Config.levelPerks = {
    { level = 1, key = 'drug_sale_bonus', value = 0.05, icon = 'payments', name = '...', desc = '...' },
    { level = 5, key = 'my_heist_bonus', value = 0.10, icon = 'payments', name = '...', desc = '...' },
}
```

### GetLevelPerks()

Every entry from `Config.levelPerks`, for showing a roadmap in your own UI.

```lua
for _, perk in ipairs(exports['meteo-organizations']:GetLevelPerks()) do
    print(perk.level, perk.key, perk.value)
end
--> 1   drug_sale_bonus   0.05
```

***

## Headquarters

### GetOrgHQ(orgId)

The property id the organization uses as its HQ, or `nil`.

```lua
local propertyId = exports['meteo-organizations']:GetOrgHQ(org.id)
print(propertyId) --> 37
```

### IsPropertyOrgHQ(propertyId)

The id of the active organization that uses the property as its HQ, or `false`.

```lua
local orgId = exports['meteo-organizations']:IsPropertyOrgHQ(37)
print(orgId) --> 12    (false if no org uses it)
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
