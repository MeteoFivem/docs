---
description: >-
  Every meteo-phone export with a simple example and what it gives back -
  phone and SIM lookups, calls, notifications, mail, texts, timed requests,
  groups, services, Bleeter and custom apps.
icon: code
---

# Exports

Send notifications, texts and mail, read who holds which phone, and plug your own scripts into the phone. Every export is called on `exports['meteo-phone']`. If you renamed the resource, use your own name instead.

{% hint style="info" %}
**What is a target?** Many server exports take a `target`. That can be a player server id (`source`), a phone serial (`'PHN-AB12CD34'`) or a phone number (`'555-1234'`). A serial always has a letter in it and a number never does, which is how the phone tells them apart. A server id or number only works while that player is holding the phone. A serial also works when the owner is offline.
{% endhint %}

***

## Server: Phone and SIM

### GetPhone(target)

The phone a player is holding, in one call. Returns `nil` if nobody is holding it.

```lua
local phone = exports['meteo-phone']:GetPhone(source)
print(json.encode(phone))
--> { "source": 12, "serial": "PHN-AB12CD34", "number": "555-1234", "sim": "active", "slot": 4 }
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `source` | number | Server id of the player holding it |
| `serial` | string | Phone serial |
| `number` | string / nil | SIM number, `nil` with no SIM |
| `sim` | string | `active`, `locked`, `disabled` or `none` |
| `slot` | number | Inventory slot of the phone |

### HasPhone(src)

```lua
print(exports['meteo-phone']:HasPhone(source)) --> true
```

### HasService(src)

True when the phone can call and text: a SIM is in, unlocked, enabled, and airplane mode is off.

```lua
if not exports['meteo-phone']:HasService(source) then
    return -- no signal, no SIM or airplane mode
end
```

### GetSerial(src) / GetNumber(src)

```lua
local serial = exports['meteo-phone']:GetSerial(source) --> 'PHN-AB12CD34'
local number = exports['meteo-phone']:GetNumber(source) --> '555-1234'
```

Both return `nil` when the player has no phone. `GetNumber` also returns `nil` with no SIM in it.

### GetSourceByNumber(number) / GetSourceBySerial(serial)

The player holding that number or phone right now, or `nil`.

```lua
local src = exports['meteo-phone']:GetSourceByNumber('555-1234')
local src2 = exports['meteo-phone']:GetSourceBySerial('PHN-AB12CD34')
```

### IsSimNumber(number)

Does a SIM with this number exist, online or not.

```lua
if not exports['meteo-phone']:IsSimNumber('555-1234') then
    return -- that number does not exist
end
```

### GetSerialOwner(serial) / GetNumberOwner(number)

The citizenid that owns a phone or a SIM. Works offline, so it costs one database query.

```lua
local cid = exports['meteo-phone']:GetNumberOwner('555-1234')
print(cid) --> 'ABC12345'
```

***

## Server: Calls

### IsInCall(src)

On a call, ringing included.

```lua
print(exports['meteo-phone']:IsInCall(source)) --> false
```

### GetCall(src)

The call a player is on, or `nil`.

```lua
local call = exports['meteo-phone']:GetCall(source)
if call and call.state == 'active' then
    print('Talking to', call.number)
end
```

```lua
-- call:
{
    id        = 1004,
    state     = 'active',     -- ringing | active
    video     = false,
    direction = 'outgoing',   -- incoming | outgoing
    number    = '555-9876',   -- the other side
    source    = 18,           -- the other side's server id, nil while nobody answered
    service   = nil,          -- true for a call to a service line (911, a business)
    startedAt = 1782300000,   -- unix seconds the call was answered
}
```

### EndCall(src)

Hangs up and tells both sides. Useful when a player is cuffed, downed or jailed.

```lua
local ended = exports['meteo-phone']:EndCall(source)
print(ended) --> true    (false if there was no call)
```

***

## Server: Notifications and Mail

### Notify(target, data)

A notification on one phone, a list of them, or every phone in play (`-1`). Returns how many phones it reached.

```lua
exports['meteo-phone']:Notify(source, {
    app      = 'bank',
    name     = 'Fleeca Bank',
    icon     = 'landmark',
    color    = '#2E7D32',
    title    = 'Transfer complete',
    body     = 'Your transfer of $5,000 was successful.',
    priority = 'normal',
})

-- a whole crew at once
exports['meteo-phone']:Notify({ leader, member1, member2 }, {
    app = 'heist', name = 'Mission', title = 'Vault open', body = 'Grab the cash and get out.', priority = 'high',
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `title` | string | Max 96. `title` or `body` is required |
| `body` | string | Max 255 |
| `app` | string | App id. A phone app id (`mail`, `messages`) uses that app's icon. Any other id shows up in Settings so the player can mute it. Default `system` |
| `name` | string | App name on the banner and in Settings |
| `icon` | string | A <a href="https://lucide.dev/icons" target="_blank">Lucide</a> icon name. Default a bell |
| `color` | string | Icon colour as a hex code |
| `channel` | string | Sub-type the player can switch off on its own |
| `priority` | string | `low` (tray only, no banner or sound), `normal`, `high` (longer banner, keeps peeking a closed phone). `urgent` is the same as `high` |

### ClearNotifications(target, app?)

Without `app` it only clears what **your** resource sent, so you never wipe the player's texts or mail. Returns true if at least one phone was reached.

```lua
exports['meteo-phone']:ClearNotifications(source)          -- everything this resource sent
exports['meteo-phone']:ClearNotifications(source, 'heist') -- one app's notifications
```

### SendMail(target, data)

With a serial the email is saved even if the owner is offline. Returns the email id, or `nil` if the phone was not found.

```lua
local id = exports['meteo-phone']:SendMail(source, {
    sender  = 'Los Santos Police',
    address = 'noreply@lspd.gov',
    subject = 'Citation Notice',
    body    = 'You have an unpaid fine of $500.',
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `sender` | string | Max 64. `sender` or `address` is required |
| `address` | string | Max 96. Defaults to the sender |
| `subject` | string | Max 160. `subject` or `body` is required |
| `body` | string | Max 8000 |

### AddPhoto(target, data)

Puts a photo or clip in a player's gallery. Returns the gallery id, or `nil` (phone not found, link not allowed, or the gallery is full). Adding the same link twice keeps one.

```lua
exports['meteo-phone']:AddPhoto(source, {
    url      = 'https://r2.fivemanage.com/.../evidence.png',
    location = 'Vinewood Hills',
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `url` | string | Required. Image or video link, checked against the image allowlist |
| `kind` | string | `image` or `video`. Default `image` |
| `thumb` | string | Required for a video, the still shown in the grid |
| `duration` | number | Clip length in seconds |
| `location` | string | Place name shown in the photo info |
| `x`, `y` | number | Map spot shown in the photo info |

***

## Server: Messages

### SendText(to, text, from?)

Returns how many phones it reached. Who it comes from depends on `from`:

* **A number with a real SIM** (a business line) - lands in a normal chat, so the player can reply
* **Any other number** (a fixer) - its own thread with no verified badge, and nobody can reply
* **A sender key** from `Config.messages.services` (`dispatch`, `city`, `system`) or one you registered - a verified sender with a badge
* **Nothing** - the `system` sender

```lua
exports['meteo-phone']:SendText(source, 'Meet me at the warehouse.', '555-0199')

-- every phone that is online, from the city
exports['meteo-phone']:SendText('online', 'Storm warning tonight.', 'city')
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `to` | number / string / table | A target, a list of targets, `'online'`, or `'all'` |
| `text` | string | Required |
| `from` | string / table | A number, a sender key, or a sender table (see `SendServiceMessage`) |

{% hint style="warning" %}
Only use `'all'` for real city-wide alerts. It writes a thread for every SIM that exists, online or not. `'online'` is the cheap one.
{% endhint %}

### SendLocation(to, coords, label?, from?)

A location in a text. The player can open it on the map or set a waypoint. `to` and `from` work like `SendText`. Returns how many phones it reached.

```lua
exports['meteo-phone']:SendLocation(source, vector3(215.76, -810.12, 30.73), 'Meet here for the job', '555-0199')
```

`coords` is a vector3 or `{ x, y }`.

### RegisterMessageService(id, data)

Adds your own verified sender. It shows with a badge, and nobody can reply to it. Returns `true`, or `false` on bad input.

```lua
exports['meteo-phone']:RegisterMessageService('tow', {
    name   = 'Tow Dispatch',
    kind   = 'mission',      -- gov | system | mission. Default system
    number = '555-0123',     -- shown on the thread
    avatar = nil,            -- optional picture link
    color  = '#F5A623',
})

exports['meteo-phone']:SendText(source, 'New tow job on Route 68.', 'tow')
```

### SendServiceMessage(data)

The full version of `SendText` for verified senders, for when you want to send a picture, a location, a contact or a document. Returns how many phones it reached.

```lua
exports['meteo-phone']:SendServiceMessage({
    sender   = 'dispatch',
    to       = source,
    message  = 'Break-in detected\nSomeone broke into 12 Grove Street',
    type     = 'location',
    location = { x = 85.4, y = -1959.2, label = '12 Grove Street' },
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `sender` | string / table | A sender key, or a table shaped like `RegisterMessageService` data with an `id` |
| `to` | number / string / table | Server id, phone number, a list of either, `'online'` or `'all'` |
| `message` | string | Required for a text message |
| `type` | string | `text`, `image`, `video`, `location`, `contact`, `document`, `event` and more. Default `text` |
| `media` / `location` / `card` | table | The attachment for that type |

With more than one line, the first line shows in bold and is the chat list preview.

### SendMessageFromNumber(from, to, data)

Text a number from another number that has a SIM (a business line or a bot). Both numbers must exist. Lands in a normal chat. Returns `true` when it was written.

```lua
exports['meteo-phone']:SendMessageFromNumber('555-0199', '555-1234', { message = 'Your order is ready.' })
```

`data` can also be a plain string.

***

## Server: Timed Requests

An accept or decline card on someone's phone (take this car, join this deal) that declines itself when the clock runs out. One at a time per player.

### SendRequest(src, data, onAnswer)

Returns the request id, or `nil` plus an error: `invalid`, `no_phone`, `busy`.

```lua
local id, err = exports['meteo-phone']:SendRequest(target, {
    title        = 'Vehicle transfer',
    from         = 'John Doe',
    body         = 'John wants to give you his Sultan RS',
    seconds      = 60,
    price        = 0,
    acceptLabel  = 'Take it',
    declineLabel = 'No thanks',
    vehicle      = { model = 'sultanrs', kind = 'car' },
}, function(answer, payment, src)
    if answer ~= 'accept' then return end
    -- do the transfer here
    return true
end)
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `title` | string | Required. Max 48 |
| `from` | string | Who is asking. Max 48 |
| `body` | string | Max 120 |
| `seconds` | number | Default 60, clamped to `Config.requests` min and max (10 - 300) |
| `price` | number | Shows a price and makes the player pick cash or bank |
| `acceptLabel` / `declineLabel` | string | Button text. Max 24 |
| `appId` | string | Which app icon the card shows. Default `system` |
| `vehicle` | table | `{ model, kind }` to draw a vehicle. `kind` is `car`, `bike`, `boat`, `heli`, `plane`, `truck` or `van` |

`onAnswer(answer, payment, src)` runs once with `answer` set to `accept`, `decline`, `expired`, `cancelled` or `dropped`.

* On `accept`, return `true` to close the card, or `false, 'reason'` to keep it up with that message (for example "not enough money"), so the player can pay the other way or decline
* `payment` is `'cash'` or `'bank'` when you set a `price`. The phone does not take the money - charge it yourself in `onAnswer`

### CancelRequest(id)

Pull a request back (the other side left, the deal went away). `onAnswer` gets `cancelled`.

```lua
exports['meteo-phone']:CancelRequest(id)
```

***

## Server: Groups

Read a player's crew from the Groups app, and lock it while your job is running.

### GetPlayerGroup(src) / GetGroupById(id)

The group, or `nil`.

```lua
local group = exports['meteo-phone']:GetPlayerGroup(source)
```

```lua
-- group:
{
    id              = 'grp12345',
    name            = 'Night Shift',
    leader          = 12,          -- leader's server id, nil when offline
    leaderCitizenId = 'ABC12345',
    busy            = false,       -- true while an activity locks the roster
    task            = nil,         -- the activity name
    maxMembers      = 4,
    members = {
        { source = 12, citizenid = 'ABC12345', name = 'John Doe', display = 'Johnny', role = 'leader', online = true, ready = true },
    },
}
```

### GetPlayerGroupId(src)

```lua
local groupId = exports['meteo-phone']:GetPlayerGroupId(source) --> 'grp12345'
```

### IsPlayerInGroup(src) / IsPlayerGroupLeader(src) / IsPlayerBusy(src)

`IsPlayerBusy` is true while the player's group has a locking activity.

```lua
if exports['meteo-phone']:IsPlayerInGroup(source) and not exports['meteo-phone']:IsPlayerGroupLeader(source) then
    return -- only the leader can start this
end
```

### GetGroupMembers(id)

The `members` list from above, or an empty table.

```lua
for _, m in ipairs(exports['meteo-phone']:GetGroupMembers(groupId)) do
    if m.online then print(m.source, m.name) end
end
```

### SetGroupActivity(id, data) / ClearGroupActivity(id)

Shows what the crew is doing in the Groups app. A locking activity freezes the roster and drops open invites. It is cleared for you when your resource stops.

```lua
exports['meteo-phone']:SetGroupActivity(groupId, {
    name   = 'Bank Heist',    -- required, max 48
    id     = 'heist',         -- optional, defaults to the name
    icon   = 'landmark',      -- optional Lucide icon
    detail = 'Stage 2 of 3',  -- optional, max 96
    lock   = true,            -- optional, default true
})

exports['meteo-phone']:ClearGroupActivity(groupId)
```

Both return `true`, or `false` if the group was not found (or had no activity to clear).

### NotifyGroup(id, message, type?)

A framework notification to every online member. `type` defaults to `primary`.

```lua
exports['meteo-phone']:NotifyGroup(groupId, 'The van is ready at the docks', 'success')
```

### DisbandGroup(id)

```lua
exports['meteo-phone']:DisbandGroup(groupId)
```

### Group events

```lua
AddEventHandler('meteo-phone:server:groupChanged', function(groupId, what, citizenid)
    -- what: 'created', 'join', 'online', 'offline', 'leader', 'renamed', 'activity', 'disbanded', ...
end)
```

***

## Server: Services

Add your own businesses to the Services app (dealerships, restaurants and so on). The phone shows them, rings their staff on shift when someone calls, and gives bosses the roster screens. Your script stays the owner of who works where.

### RegisterServices(data)

Returns `true`, or `false` plus an error: `invalid_caller`, `invalid_data`, `invalid_id`, `id_taken`, `missing_<fn>`, `invalid_<fn>`.

```lua
exports['meteo-phone']:RegisterServices({
    id    = 'restaurants',                -- lowercase, max 16
    glyph = 'utensils',                   -- default logo for the entries
    brand = { '#FFB36B', '#C2410C' },     -- two hex colours

    -- every business this script runs
    list = function()
        return {
            { id = 'burgershot', name = 'Burger Shot', tagline = 'Fast food', location = { x = -1183.0, y = -884.0, label = 'Vespucci' } },
        }
    end,
    -- where a character works: [entryId] = { grade, boss }
    employments = function(citizenid)
        return { burgershot = { grade = 2, boss = true } }
    end,
    -- who takes calls right now: { source, ... }
    online = function(entryId)
        return { 12, 18 }
    end,

    -- optional, for the boss screens
    grades   = function(entryId) return { { level = 0, label = 'Cook' }, { level = 2, label = 'Owner', boss = true } } end,
    roster   = function(entryId) return { { cid = 'ABC12345', name = 'John Doe', grade = 2 } } end,
    hire     = function(entryId, actorCid, targetCid) return true end,
    fire     = function(entryId, actorCid, targetCid) return true end,
    setGrade = function(entryId, actorCid, targetCid, grade) return true end,
})
```

`hire`, `fire` and `setGrade` return `ok, error`. Check your own permissions in them, the phone only passes the request on.

### UnregisterServices(id)

Only works for the resource that registered it. Providers are also removed when their resource stops.

```lua
exports['meteo-phone']:UnregisterServices('restaurants')
```

***

## Server: Bleeter

For staff or moderation scripts. The handle can be given with or without the `@`. Each returns `true` if an account was changed.

### SetBleeterStatus(handle, status)

`status` is `active`, `suspended` or `banned`.

```lua
exports['meteo-phone']:SetBleeterStatus('@johndoe', 'suspended')
```

### SetBleeterVerified(handle, on) / SetBleeterModerator(handle, on)

```lua
exports['meteo-phone']:SetBleeterVerified('lspd', true)
exports['meteo-phone']:SetBleeterModerator('johndoe', false)
```

***

## Server: Labor

### GetJobs()

Every job in the Labor app whose resource is running.

```lua
for _, job in ipairs(exports['meteo-phone']:GetJobs()) do
    print(job.id, job.name, job.resource)
end
```

Each job is `{ id, name, icon, resource, clockIn, groupSupported }`.

***

## Client: Phone

### IsPhoneOpen() / OpenPhone() / ClosePhone()

`OpenPhone` does nothing if the player cannot use the phone right now.

```lua
if exports['meteo-phone']:IsPhoneOpen() then
    exports['meteo-phone']:ClosePhone()
end
```

### CanUsePhone()

Has a phone and nothing is stopping them: dead, downed, cuffed, pause menu, or disabled by `SetPhoneDisabled`.

```lua
print(exports['meteo-phone']:CanUsePhone()) --> true
```

### HasPhone() / GetSerial() / GetNumber()

```lua
local hasPhone = exports['meteo-phone']:HasPhone()
local serial = exports['meteo-phone']:GetSerial()
local number = exports['meteo-phone']:GetNumber()
```

`GetNumber` only returns a number while the SIM is active (unlocked and enabled), otherwise `nil`.

### SetPhoneDisabled(disabled)

Stops the player from using the phone, for jail, a minigame or a cutscene. Disabling closes the phone if it is open. Each resource has its own switch, so two scripts never undo each other, and yours is cleared when your resource stops.

```lua
exports['meteo-phone']:SetPhoneDisabled(true)
-- ...
exports['meteo-phone']:SetPhoneDisabled(false)
```

***

## Client: Music

### IsMusicPlaying() / GetMusic()

`GetMusic` returns `{ playing, title, artist, cast }` or `nil` when nothing is loaded. `cast` is set while the music plays on a car or a speaker.

```lua
if exports['meteo-phone']:IsMusicPlaying() then
    local song = exports['meteo-phone']:GetMusic()
    print(song.title, song.artist)
end
```

### StopMusic() / PauseMusic()

`StopMusic` stops the music and ends a cast to a car or speaker. `PauseMusic` only pauses, so the player can press play again.

```lua
exports['meteo-phone']:PauseMusic()
exports['meteo-phone']:StopMusic()
```

***

## Custom Apps

Your own resource with its own HTML page, shown like a built-in app: a home screen icon, an App Store listing, notifications with their own switches in Settings, a badge and home screen widgets. `Config.customApps = false` in the phone config turns them off.

### AddCustomApp(data) - client

Register from a **client** script, and again on `meteo-phone:customAppsReady` so the app comes back after a phone restart. Returns `true`, or `false` if the data was rejected. Apps are removed on their own when your resource stops.

```lua
local function register()
    if GetResourceState('meteo-phone') ~= 'started' then return end
    exports['meteo-phone']:AddCustomApp({
        identifier  = 'myapp',
        name        = 'My App',
        developer   = 'My Studio',
        tagline     = 'One line for the App Store list',
        description = 'The full description on the App Store page.',
        ui          = 'ui/index.html',
        icon        = 'ui/icon.png',
        defaultApp  = true,
        notifications = {
            badges = true,
            channels = { { id = 'orders', name = 'Orders', description = 'When an order comes in' } },
        },
        widgets = {
            { id = 'summary', name = 'Summary', sizes = { 'small', 'medium' }, ui = 'ui/widget.html' },
        },
    })
end

AddEventHandler('onClientResourceStart', function(res)
    if res == GetCurrentResourceName() then register() end
end)
AddEventHandler('meteo-phone:customAppsReady', register)
```

Every file the app uses (`ui`, `icon`, widget pages, `images`) must be in your `fxmanifest.lua` `files { }`.

| Field | Type | Notes |
| ----- | ---- | ----- |
| `identifier` | string | Required. Unique, letters, numbers, `-` and `_`, max 32 |
| `name` | string | Name under the icon. Max 32 |
| `ui` | string | Your page, like `ui/index.html`. A full link works too. `ui` or `onUse` is required |
| `onUse` | function | An app with no page: tapping the icon runs this instead (a flashlight, a quick toggle) |
| `icon` | string | Icon image |
| `iconBackground` | string | CSS background behind the icon, like a gradient |
| `glyph` | string | A <a href="https://lucide.dev/icons" target="_blank">Lucide</a> icon name, when there is no image |
| `color` | string | Tile colour (hex) behind a glyph or a transparent logo |
| `developer` / `tagline` / `description` | string | App Store text |
| `images` | table | Up to 6 App Store screenshots |
| `store` | boolean | `false` keeps it out of the App Store |
| `defaultApp` | boolean | On every home screen without installing it |
| `stayOpen` | boolean | ESC puts the phone away on this app instead of leaving it |
| `notifications` | table | `{ badges, sound, channels = { { id, name, description } } }` |
| `widgets` | table | Up to 6: `{ id, name, description, sizes = { 'small', 'medium', 'large' }, ui, frameless }` |

Send a notification from your app with the server `Notify` export, using your `identifier` as `app`:

```lua
exports['meteo-phone']:Notify(source, { app = 'myapp', channel = 'orders', title = 'New order', body = 'Table 4' })
```

### RemoveCustomApp(identifier) / IsCustomAppRegistered(identifier) / GetCustomApp(identifier) - client

```lua
exports['meteo-phone']:RemoveCustomApp('myapp')                  --> true
print(exports['meteo-phone']:IsCustomAppRegistered('myapp'))     --> false
local app = exports['meteo-phone']:GetCustomApp('myapp')         -- the cleaned app, or nil
```

### SendCustomAppMessage(identifier, event, payload) - client

Sends to your app page and its widgets, received in the page with `MeteoPhone.onNuiEvent(event, fn)`. Returns `false` if the app is not registered.

```lua
exports['meteo-phone']:SendCustomAppMessage('myapp', 'orderAdded', { id = 12 })
```

### SetCustomAppBadge(identifier, count) - client

The red count on the icon. `0` clears it.

```lua
exports['meteo-phone']:SetCustomAppBadge('myapp', 3)
```

### SendCustomAppMessage(src, identifier, event, payload) / SetCustomAppBadge(src, identifier, count) - server

The same two, for one player from the server.

```lua
exports['meteo-phone']:SendCustomAppMessage(source, 'myapp', 'orderAdded', { id = 12 })
exports['meteo-phone']:SetCustomAppBadge(source, 'myapp', 3)
```

### Your page

The phone connects your page after it loads. Wait for `meteo:ready`, then use `window.MeteoPhone`.

```js
window.addEventListener('meteo:ready', () => {
    const phone = window.MeteoPhone;
    console.log(phone.player.name, phone.player.phoneNumber);

    phone.onNuiEvent('orderAdded', (order) => { /* redraw */ });
    phone.fetchNui('getOrders', {}).then((orders) => { /* your RegisterNUICallback */ });
});
```

| MeteoPhone | What it does |
| ---------- | ------------ |
| `player` | `{ name, source, citizenid, phoneNumber, phoneSerial, simName }` |
| `settings` | `{ theme, currency, volume, silent }`, plus `onSettingsChange(fn)` |
| `fetchNui(event, data)` | Calls your resource's `RegisterNUICallback`, returns a promise |
| `onNuiEvent(event, fn)` | Receives `SendCustomAppMessage` |
| `notify({ title, body, channel, priority })` | A phone notification from your app |
| `setBadge(count)` | The red count on your icon |
| `confirm({ title, description, danger, confirmText })` | Resolves `true` or `false` |
| `prompt({ title, placeholder, value })` | Resolves the text, or `null` |
| `menu({ title, options })` | Up to 12 `{ label, icon, value, danger }`. Resolves the picked `value`, or `null` |
| `pickContact({ title })` / `pickImage({ title })` / `pickEmoji()` | Resolve the pick, or `null` |
| `call(number, video)` | Starts a call |
| `openApp(id, intent)` | Opens another app (`maps`, `messages`, or a custom app) |
| `onBack(fn)` | ESC and the back request. Return `true` if you went back a screen yourself |
| `close()` | Leaves the app |

Your page gets the phone's CSS variables and fonts (`var(--ink-900)`, `var(--text-hi)`, `var(--app-accent)`, `var(--font-ui)` and more), so it can look like the phone. Leave about 40px at the bottom for the home bar.

***

## Old Export Names

Scripts made for the old phone keep working. These names still exist with the same arguments, but new scripts should use the exports above.

| Old export | Use instead | Side |
| ---------- | ----------- | ---- |
| `GetPlayerPhoneBySource(source)` - returns item, serial, slot | `GetPhone(source)` | Server |
| `GetActivePhoneSerial(source)` / `GetPhoneSerial(source)` | `GetSerial(source)` | Server |
| `GetActivePhoneNumber(source)` / `GetPhoneNumber(source)` | `GetNumber(source)` | Server |
| `SendNotificationToPhone(serial, app, icon, message, priority, sound, label)` | `Notify(target, data)` | Server |
| `ClearPhoneNotifications(serial)` | `ClearNotifications(target)` | Server |
| `SendEmailToPhone(serial, sender, subject, content)` | `SendMail(target, data)` | Server |
| `SendEmail(target, data)` / `SendEmailToNumber(target, data)` | `SendMail(target, data)` | Server |
| `AddGalleryItem(target, data)` | `AddPhoto(target, data)` | Server |
| `DispatchSMSToPlayer(source, senderNumber, text)` | `SendText(source, text, senderNumber)` | Server |
| `DispatchLocationToPlayer(source, senderNumber, coords, label)` | `SendLocation(source, coords, label, senderNumber)` | Server |
| `GetCustomLaberJobs()` | `GetJobs()` | Server |
| `SetGroupBusy(id, busy, taskName)` / `ClearGroupTask(id)` | `SetGroupActivity` / `ClearGroupActivity` | Server |
| `IsPhoneUIOpen()` | `IsPhoneOpen()` | Client |
| `StopMusicPlayback()` | `StopMusic()` | Client |

{% hint style="warning" %}
**Icons from old scripts are not shown.** The old phone used Material icon names, the new one uses Lucide icons. `SendNotificationToPhone` ignores the icon and uses the app's own icon or a bell.

**Custom apps register on the client now.** The old server side `AddCustomApp`, `RemoveCustomApp` and `IsCustomAppRegistered` still exist so old scripts do not error, but they do nothing and return `false`.
{% endhint %}
