---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/hPLkuIrL5TffIt3aasi9/paid-scripts/meteo-phone/useful-exports
---

# Useful Exports

## Quick Exports Reference Table

| Export                                            | Purpose                      | Side             |
| ------------------------------------------------- | ---------------------------- | ---------------- |
| `exports['meteo-phone']:RegisterCustomLaberJob`   | Register a Custom Job        | Server side Only |
| `exports['meteo-phone']:GetCustomLaberJobs`       | Get All Custom Jobs          | Server side Only |
| `exports['meteo-phone']:GetPlayerPhoneBySource`   | Get Player Phone Info        | Server side Only |
| `exports['meteo-phone']:SendEmailToPhone`         | Send Email to Phone          | Server side Only |
| `exports['meteo-phone']:SendNotificationToPhone`  | Send Priority Notification   | Server side Only |
| `exports['meteo-phone']:ClearPhoneNotifications`  | Clear Priority Notifications | Server side Only |
| `exports['meteo-phone']:GetActivePhoneNumber`     | Get Player Phone Number      | Server side Only |
| `exports['meteo-phone']:GetActivePhoneSerial`     | Get Player Phone Serial      | Server side Only |
| `exports['meteo-phone']:DispatchSMSToPlayer`      | Send SMS to Player           | Server side Only |
| `exports['meteo-phone']:DispatchLocationToPlayer` | Send Location via SMS        | Server side Only |
| `exports['meteo-phone']:IsPhoneUIOpen`            | Check if Phone is Open       | Client side Only |
| `exports['meteo-phone']:CanUsePhone`              | Check if Can Use Phone       | Client side Only |
| `exports['meteo-phone']:ClosePhone`               | Close Phone UI               | Client side Only |
| `exports['meteo-phone']:StopMusicPlayback`        | Stop Music Playback          | Client side Only |
| `exports['meteo-phone']:IsMusicPlaying`           | Check if Music is Playing    | Client side Only |

{% stepper %}
{% step %}
#### RegisterCustomLaberJob

Register a Custom Job

Example

```lua
-- server-side
exports['meteo-phone']:RegisterCustomLaberJob({
    id = 'mining',
    name = 'Miner',
    icon = 'hardware', -- Find icons at: https://fonts.google.com/icons
    location = vector3(2950.0, 2780.0, 40.0),
    blip = { sprite = 618, color = 1, scale = 0.7 }
})
```
{% endstep %}

{% step %}
#### GetCustomLaberJobs

Get All Custom Jobs

Example

```lua
-- server-side
local customJobs = exports['meteo-phone']:GetCustomLaberJobs()
```

**Job Data Structure**

<table><thead><tr><th width="107.5">Field</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Yes</td><td>Unique identifier</td></tr><tr><td>name</td><td>string</td><td>Yes</td><td>Display name in UI</td></tr><tr><td>icon</td><td>string</td><td>No</td><td>Material icon name (default: 'work')</td></tr><tr><td>location</td><td>vector3</td><td>No</td><td>Waypoint coordinates</td></tr><tr><td>blip</td><td>table</td><td>No</td><td>Blip settings { sprite, color, scale }</td></tr></tbody></table>
{% endstep %}

{% step %}
#### GetPlayerPhoneBySource

Get Player Phone Info

Example

```lua
-- server-side
local phoneItem, phoneSerial, slot = exports['meteo-phone']:GetPlayerPhoneBySource(serverId)

if phoneSerial then
    print('Player has phone with serial:', phoneSerial)
    -- Now you can send emails, etc.
else
    print('Player does not have a phone')
end
```

**Practical Use Case**

```lua
-- Send email/notification to a single player
local function SendPhoneAlert(serverId, message, emailData)
    local phoneItem, phoneSerial, slot = exports['meteo-phone']:GetPlayerPhoneBySource(serverId)

    if phoneSerial then
        exports['meteo-phone']:SendEmailToPhone(
            phoneSerial,
            emailData.sender or 'security@gruppesechs.com',
            emailData.subject or 'Security Alert',
            emailData.content or message
        )
        print('Email sent to player:', serverId)
        return true
    else
        print('Player has no phone:', serverId)
        return false
    end
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>serverId</td><td>number</td><td>Yes</td><td>Player server ID (source)</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="120">Return</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>phoneItem</td><td>table/nil</td><td>Phone item data or nil if no phone</td></tr><tr><td>phoneSerial</td><td>string/nil</td><td>Phone serial number or nil if no phone</td></tr><tr><td>slot</td><td>number/nil</td><td>Inventory slot number or nil if no phone</td></tr></tbody></table>
{% endstep %}

{% step %}
#### SendEmailToPhone

Send Email to Phone

Example

```lua
-- server-side
exports['meteo-phone']:SendEmailToPhone(phoneSerial, sender, subject, content)

-- Real example
exports['meteo-phone']:SendEmailToPhone(
    'PHONE-ABC123',
    'Los Santos Police',
    'Citation Notice',
    'You have an unpaid fine of $500.'
)
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>phoneSerial</td><td>string</td><td>Yes</td><td>Phone serial number</td></tr><tr><td>sender</td><td>string</td><td>Yes</td><td>Sender name</td></tr><tr><td>subject</td><td>string</td><td>Yes</td><td>Email subject</td></tr><tr><td>content</td><td>string</td><td>Yes</td><td>Email content/message</td></tr></tbody></table>
{% endstep %}

{% step %}
#### SendNotificationToPhone

Send Priority Notification to Phone

Example

```lua
-- server-side
exports['meteo-phone']:SendNotificationToPhone(phoneSerial, app, icon, message, priority, sound, label)

-- Real examples
exports['meteo-phone']:SendNotificationToPhone(
    'PHONE-ABC123',
    'Los Santos Police',
    'local_police',
    'You have a warrant for your arrest.',
    'urgent',
    'security-notify',
    'Warrant'
)

exports['meteo-phone']:SendNotificationToPhone(
    'PHONE-ABC123',
    'Mission',
    'flag',
    'New mission available: deliver the package.',
    'high',
    nil,
    'Mission'
)

exports['meteo-phone']:SendNotificationToPhone(
    'PHONE-ABC123',
    'Bank',
    'account_balance',
    'Your transfer of $5,000 was successful.',
    'normal'
    -- no sound, no custom label (defaults to 'Normal')
)
```

**Priority Levels**

<table><thead><tr><th width="100">Priority</th><th width="100">Duration</th><th>Description</th></tr></thead><tbody><tr><td>low</td><td>5 seconds</td><td>Low importance - brief display</td></tr><tr><td>normal</td><td>8 seconds</td><td>Standard notification</td></tr><tr><td>high</td><td>15 seconds</td><td>Important - longer display with orange accent</td></tr><tr><td>urgent</td><td>30 seconds</td><td>Critical - longest display with red accent and pulse animation</td></tr></tbody></table>

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>phoneSerial</td><td>string</td><td>Yes</td><td>Phone serial number</td></tr><tr><td>app</td><td>string</td><td>No</td><td>App name displayed (default: 'System')</td></tr><tr><td>icon</td><td>string</td><td>No</td><td>Material icon name (default: 'notifications'). Find icons at: https://fonts.google.com/icons</td></tr><tr><td>message</td><td>string</td><td>Yes</td><td>Notification message text</td></tr><tr><td>priority</td><td>string</td><td>No</td><td>'low', 'normal', 'high', or 'urgent' (default: 'normal')</td></tr><tr><td>sound</td><td>string</td><td>No</td><td>Sound name (e.g. 'security-notify', 'email', 'message')</td></tr><tr><td>label</td><td>string</td><td>No</td><td>Custom badge label (e.g. 'Mission', 'Bounty', 'Alert'). Overrides default priority text</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if notification was sent, false if player not online or invalid params</td></tr></tbody></table>

**Practical Use Case**

```lua
-- Send alert to a player by server ID
local function SendPriorityAlert(serverId, message, priority, appName, iconName, soundName)
    local phoneItem, phoneSerial, slot = exports['meteo-phone']:GetPlayerPhoneBySource(serverId)

    if phoneSerial then
        exports['meteo-phone']:SendNotificationToPhone(
            phoneSerial,
            appName or 'System',
            iconName or 'notifications',
            message,
            priority or 'normal',
            soundName
        )
        return true
    end
    return false
end
```
{% endstep %}

{% step %}
#### ClearPhoneNotifications

Clear Priority Notifications from Phone

Example

```lua
-- server-side
exports['meteo-phone']:ClearPhoneNotifications(phoneSerial)

-- Real example: clear after mission ends
local phoneItem, phoneSerial, slot = exports['meteo-phone']:GetPlayerPhoneBySource(serverId)
if phoneSerial then
    exports['meteo-phone']:ClearPhoneNotifications(phoneSerial)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>phoneSerial</td><td>string</td><td>Yes</td><td>Phone serial number</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if cleared, false if player not online or invalid params</td></tr></tbody></table>

**Notes**

Only clears priority notifications (sent via `SendNotificationToPhone`). Regular notifications, call notifications, and music notifications are not affected.
{% endstep %}

{% step %}
#### GetActivePhoneNumber

Get a player's active phone number from their equipped SIM card.

Example

```lua
-- server-side
local phoneNumber = exports['meteo-phone']:GetActivePhoneNumber(serverId)

if phoneNumber then
    print('Player phone number:', phoneNumber) -- e.g. "310-555-0199"
else
    print('Player has no phone or no valid SIM')
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>serverId</td><td>number</td><td>Yes</td><td>Player server ID (source)</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>string/nil</td><td>Phone number in 000-000-0000 format, or nil if no phone/SIM</td></tr></tbody></table>
{% endstep %}

{% step %}
#### GetActivePhoneSerial

Get a player's equipped phone serial number.

Example

```lua
-- server-side
local phoneSerial = exports['meteo-phone']:GetActivePhoneSerial(serverId)

if phoneSerial then
    print('Phone serial:', phoneSerial)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>serverId</td><td>number</td><td>Yes</td><td>Player server ID (source)</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>string/nil</td><td>Phone serial string, or nil if player has no phone</td></tr></tbody></table>
{% endstep %}

{% step %}
#### DispatchSMSToPlayer

Send a text message to a player's phone. The sender number does not need to be a real player - system/NPC numbers work fine (e.g. `555-000-0001`). The message is stored in the database and shows up in their SMS conversations.

Example

```lua
-- server-side
local success, messageId = exports['meteo-phone']:DispatchSMSToPlayer(serverId, senderNumber, text)

-- Real examples
exports['meteo-phone']:DispatchSMSToPlayer(
    serverId,
    '555-000-0001',
    'Your vehicle has been impounded. Visit the impound lot to retrieve it.'
)

-- Using a player's actual number as sender
local senderPhone = exports['meteo-phone']:GetActivePhoneNumber(senderServerId)
if senderPhone then
    exports['meteo-phone']:DispatchSMSToPlayer(targetServerId, senderPhone, 'Meet me at the warehouse.')
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>recipientId</td><td>number</td><td>Yes</td><td>Player server ID of the recipient</td></tr><tr><td>senderNumber</td><td>string</td><td>Yes</td><td>Phone number of the sender (any format works, e.g. '555-000-0001')</td></tr><tr><td>text</td><td>string</td><td>Yes</td><td>Message content (max 500 characters)</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if message was sent successfully</td></tr><tr><td>number/nil</td><td>Message ID in database, or nil on failure</td></tr></tbody></table>

**Notes**

* Respects the recipient's SMS notification settings (sound, enabled/disabled)
* If the recipient has the sender number saved as a contact, the notification shows the contact name
* Messages persist in the database and appear in the SMS app conversation list
{% endstep %}

{% step %}
#### DispatchLocationToPlayer

Send map coordinates via SMS to a player's phone. The location appears as a tappable pin in the SMS conversation.

Example

```lua
-- server-side
local success, messageId = exports['meteo-phone']:DispatchLocationToPlayer(serverId, senderNumber, position, label)

-- Send a location with a label
exports['meteo-phone']:DispatchLocationToPlayer(
    serverId,
    '555-000-0001',
    vector3(215.76, -810.12, 30.73),
    'Meet here for the job'
)

-- Send player's current position
local ped = GetPlayerPed(serverId)
local coords = GetEntityCoords(ped)
exports['meteo-phone']:DispatchLocationToPlayer(serverId, '555-000-0001', coords, 'Your last known location')
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>recipientId</td><td>number</td><td>Yes</td><td>Player server ID of the recipient</td></tr><tr><td>senderNumber</td><td>string</td><td>Yes</td><td>Phone number of the sender</td></tr><tr><td>position</td><td>vector3</td><td>Yes</td><td>World coordinates to share</td></tr><tr><td>label</td><td>string</td><td>No</td><td>Optional text message to accompany the location</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if location was sent successfully</td></tr><tr><td>number/nil</td><td>Message ID in database, or nil on failure</td></tr></tbody></table>
{% endstep %}

{% step %}
#### IsPhoneUIOpen

Check if Phone is Open

Example

```lua
-- client-side
local isOpen = exports['meteo-phone']:IsPhoneUIOpen()

if isOpen then
    print('Phone is currently open')
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if phone UI is open, false if closed</td></tr></tbody></table>
{% endstep %}

{% step %}
#### CanUsePhone

Check if Can Use Phone

Example

```lua
-- client-side
local canUse = exports['meteo-phone']:CanUsePhone()

if canUse then
    print('Player can use phone')
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if player can use phone, false if restricted</td></tr></tbody></table>
{% endstep %}

{% step %}
#### ClosePhone

Close Phone UI

Example

```lua
-- client-side
exports['meteo-phone']:ClosePhone()
```

**Notes**

Forces the phone UI to close. Useful for cutscenes or specific game events where phone should be closed.
{% endstep %}

{% step %}
#### StopMusicPlayback

Stop Music Playback

Example

```lua
-- client-side
exports['meteo-phone']:StopMusicPlayback()
```

**Notes**

Stops any currently playing music from the phone music app. Useful for external music systems or event scripts.
{% endstep %}

{% step %}
#### IsMusicPlaying

Check if Music is Playing

Example

```lua
-- client-side
local isPlaying = exports['meteo-phone']:IsMusicPlaying()

if isPlaying then
    print('Music is currently playing from phone')
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if music is playing, false if stopped</td></tr></tbody></table>
{% endstep %}
{% endstepper %}
