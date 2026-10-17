---
description: >-
  Every meteo-chat export with a simple example - system, staff and
  announcement messages, ID and license cards, suggestions and the default chat
  exports.
icon: code
---

# Exports

Post messages into the chat from your own scripts. Server exports send to one player or everyone. Client exports only touch the calling player's chat.

***

## Server: Messages

`target` is a server id, or `-1` for everyone.

### SendSystemMessage(target, message)

Red **SYSTEM** tag, no name.

```lua
exports['meteo-chat']:SendSystemMessage(source, 'You cannot do that right now')
```

### SendInfoMessage(target, message)

Blue **INFO** tag, no name.

```lua
exports['meteo-chat']:SendInfoMessage(source, 'Your shift has started')
```

### SendServerMessage(target, message)

Purple **SERVER** tag, no name.

```lua
exports['meteo-chat']:SendServerMessage(-1, 'Server restart in 10 minutes')
```

### SendAnnouncementMessage(target, message)

Orange **ANNOUNCEMENT** tag.

```lua
exports['meteo-chat']:SendAnnouncementMessage(-1, 'The casino is now open')
```

### SendStaffMessage(target, username, message)

Orange **STAFF** tag with a name in front.

```lua
exports['meteo-chat']:SendStaffMessage(-1, 'Admin Mike', 'Please stop ramming cars at Legion')
```

### SendAdminMessage(target, username, message)

Red **ADMIN** tag with a name in front.

```lua
exports['meteo-chat']:SendAdminMessage(source, 'Admin Mike', 'Check your phone')
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `target` | number | Server id, or `-1` for everyone |
| `username` | string | Only on `SendStaffMessage` and `SendAdminMessage` |
| `message` | string | GTA colour codes (`~r~`, `^1`) and `~n~` new lines work. HTML is escaped |

None of these return anything.

### SendChatMessage(target, message)

Sends a raw message table, for full control over the tag and name.

```lua
exports['meteo-chat']:SendChatMessage(source, {
    category = 'ooc',           -- picks the tag and colour
    username = 'John Doe',      -- optional, shown before the message
    message  = 'Anyone up for a race?',
})
```

Categories: `me`, `do`, `say`, `tweet`, `ooc`, `server`, `system`, `info`, `staff`, `admin`, `announcement`, `custom`. `job-<name>` (e.g. `job-police`) shows the job name as the tag. Anything else falls back to `custom` (**MESSAGE**).

The old cfx format still works too: `{ args = { 'Name', 'Text' } }` or `{ template = '<div>{0}</div>', args = { 'Text' } }`.

### BroadcastChatMessage(message)

Same as `SendChatMessage` but to everyone.

```lua
exports['meteo-chat']:BroadcastChatMessage({ category = 'server', message = 'Storm incoming' })
```

***

## Server: Cards

### SendCardMessage(target, cardType, cardData)

Shows a card in chat, like an ID or a badge. Use it for "show ID" style items.

```lua
exports['meteo-chat']:SendCardMessage(nearbyId, 'id_card', {
    firstname   = 'John',
    lastname    = 'Doe',
    citizenid   = 'ABC12345',
    birthdate   = '1994-03-12',
    gender      = 'Male',
    nationality = 'American',
})
```

| Card type | Fields |
| --------- | ------ |
| `id_card` | `firstname`, `lastname`, `citizenid`, `birthdate`, `gender`, `nationality` |
| `driver_license` | `firstname`, `lastname`, `birthdate`, `type` |
| `weapon_license` | `firstname`, `lastname`, `birthdate`, `type` |
| `laywer_pass` | `firstname`, `lastname`, `birthdate`, `type` (bar card - the key is spelled like this in code) |
| `police_badge` | `firstname`, `lastname`, `badgenumber`, `rank`, `department` |
| `judge_badge` | `firstname`, `lastname`, `rank`, `department` |
| `rental_papers` | `firstname`, `lastname`, `vehicle`, `plate`, `deposit` |
| `mdt_license` | `title`, `color` (hex like `#38BDF8`), `rows = { { label, value, accent? } }` |

Empty fields are left off the card. An unknown `cardType` falls back to a normal message.

`mdt_license` is the free-form one, so you can build your own card:

```lua
exports['meteo-chat']:SendCardMessage(source, 'mdt_license', {
    title = 'Hunting Permit',
    color = '#34D399',
    rows = {
        { label = 'Holder', value = 'John Doe' },
        { label = 'State ID', value = 'ABC12345' },
        { label = 'Valid Until', value = '2026-12-01', accent = true },
    },
})
```

***

## Client

### addMessage(message)

Adds a message to this player's chat only. Takes a string or the same table as `SendChatMessage`.

```lua
exports['meteo-chat']:addMessage({ category = 'info', message = 'You found 3 coins' })
exports['meteo-chat']:addMessage('Plain text works too')
```

### addSuggestion(name, help, params?) / removeSuggestion(name)

Command hints shown while typing.

```lua
exports['meteo-chat']:addSuggestion('/givecash', 'Give cash to a player', {
    { name = 'id', help = 'Player id' },
    { name = 'amount', help = 'Amount' },
})

exports['meteo-chat']:removeSuggestion('/givecash')
```

### clearChat()

Clears this player's chat.

```lua
exports['meteo-chat']:clearChat()
```

### getChatSettings()

The player's chat size settings, in percent (50 to 150).

```lua
local s = exports['meteo-chat']:getChatSettings()
print(s.fontSize, s.chatWidth, s.chatHeight) --> 100  100  100
```

### updateChatSetting(setting, value) / resetChatSettings()

`setting` is `fontSize`, `chatWidth` or `chatHeight`. Values are clamped to 50-150 and saved on the player's PC.

```lua
exports['meteo-chat']:updateChatSetting('fontSize', 120)
exports['meteo-chat']:resetChatSettings() -- back to Config.ChatDefaults
```

***

## Compatibility

meteo-chat replaces the default cfx `chat` resource, so scripts written for it keep working.

* **Exports** - the client exports `addMessage`, `addSuggestion`, `removeSuggestion` and `clearChat` also answer `exports.chat:...` and `exports['chat']:...`
* **Events** - `chat:addMessage`, `chat:addSuggestion`, `chat:addSuggestions`, `chat:removeSuggestion`, `chat:resetSuggestions`, `chat:addTemplate`, `chat:clear` and the old `chatMessage` are all handled

```lua
-- server, the classic way still works
TriggerClientEvent('chat:addMessage', source, { args = { 'Bank', 'Payment received' } })
```

Do not run the default `chat` resource next to meteo-chat.
