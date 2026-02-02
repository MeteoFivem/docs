# Useful Exports

## Quick Exports Reference Table

| Export                                          | Purpose                  | Side             |
| ----------------------------------------------- | ------------------------ | ---------------- |
| `exports['meteo-phone']:RegisterCustomLaberJob` | Register a Custom Job    | Server side Only |
| `exports['meteo-phone']:GetCustomLaberJobs`     | Get All Custom Jobs      | Server side Only |
| `exports['meteo-phone']:GetPlayerPhoneBySource` | Get Player Phone Info    | Server side Only |
| `exports['meteo-phone']:SendEmailToPhone`       | Send Email to Phone      | Server side Only |
| `exports['meteo-phone']:IsPhoneUIOpen`          | Check if Phone is Open   | Client side Only |
| `exports['meteo-phone']:CanUsePhone`            | Check if Can Use Phone   | Client side Only |
| `exports['meteo-phone']:ClosePhone`             | Close Phone UI           | Client side Only |
| `exports['meteo-phone']:StopMusicPlayback`      | Stop Music Playback      | Client side Only |
| `exports['meteo-phone']:IsMusicPlaying`         | Check if Music is Playing| Client side Only |



{% stepper %}
{% step %}
### RegisterCustomLaberJob

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
### GetCustomLaberJobs

Get All Custom Jobs

Example

```lua
-- server-side
local customJobs = exports['meteo-phone']:GetCustomLaberJobs()
```

#### Job Data Structure

<table><thead><tr><th width="107.5">Field</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Yes</td><td>Unique identifier</td></tr><tr><td>name</td><td>string</td><td>Yes</td><td>Display name in UI</td></tr><tr><td>icon</td><td>string</td><td>No</td><td>Material icon name (default: 'work')</td></tr><tr><td>location</td><td>vector3</td><td>No</td><td>Waypoint coordinates</td></tr><tr><td>blip</td><td>table</td><td>No</td><td>Blip settings { sprite, color, scale }</td></tr></tbody></table>
{% endstep %}

{% step %}
### GetPlayerPhoneBySource

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

#### Practical Use Case

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

#### Parameters

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>serverId</td><td>number</td><td>Yes</td><td>Player server ID (source)</td></tr></tbody></table>

#### Returns

<table><thead><tr><th width="120">Return</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>phoneItem</td><td>table/nil</td><td>Phone item data or nil if no phone</td></tr><tr><td>phoneSerial</td><td>string/nil</td><td>Phone serial number or nil if no phone</td></tr><tr><td>slot</td><td>number/nil</td><td>Inventory slot number or nil if no phone</td></tr></tbody></table>
{% endstep %}

{% step %}
### SendEmailToPhone

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

#### Parameters

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>phoneSerial</td><td>string</td><td>Yes</td><td>Phone serial number</td></tr><tr><td>sender</td><td>string</td><td>Yes</td><td>Sender name</td></tr><tr><td>subject</td><td>string</td><td>Yes</td><td>Email subject</td></tr><tr><td>content</td><td>string</td><td>Yes</td><td>Email content/message</td></tr></tbody></table>
{% endstep %}

{% step %}
### IsPhoneUIOpen

Check if Phone is Open

Example

```lua
-- client-side
local isOpen = exports['meteo-phone']:IsPhoneUIOpen()

if isOpen then
    print('Phone is currently open')
end
```

#### Returns

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if phone UI is open, false if closed</td></tr></tbody></table>
{% endstep %}

{% step %}
### CanUsePhone

Check if Can Use Phone

Example

```lua
-- client-side
local canUse = exports['meteo-phone']:CanUsePhone()

if canUse then
    print('Player can use phone')
end
```

#### Returns

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if player can use phone, false if restricted</td></tr></tbody></table>
{% endstep %}

{% step %}
### ClosePhone

Close Phone UI

Example

```lua
-- client-side
exports['meteo-phone']:ClosePhone()
```

#### Notes

Forces the phone UI to close. Useful for cutscenes or specific game events where phone should be closed.
{% endstep %}

{% step %}
### StopMusicPlayback

Stop Music Playback

Example

```lua
-- client-side
exports['meteo-phone']:StopMusicPlayback()
```

#### Notes

Stops any currently playing music from the phone music app. Useful for external music systems or event scripts.
{% endstep %}

{% step %}
### IsMusicPlaying

Check if Music is Playing

Example

```lua
-- client-side
local isPlaying = exports['meteo-phone']:IsMusicPlaying()

if isPlaying then
    print('Music is currently playing from phone')
end
```

#### Returns

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if music is playing, false if stopped</td></tr></tbody></table>
{% endstep %}
{% endstepper %}
