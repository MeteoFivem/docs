---
description: Build your own apps that live inside Meteo Phone, from any FiveM resource.
icon: grid-2-plus
---

# Custom Apps

Any FiveM resource can register its own app on Meteo Phone. An app can be a simple button that runs a Lua callback when tapped, or a full UI app rendered inside the phone with access to the phone's popups, pickers, notifications and player data.

Two reference resources live on our GitHub if you want to dive straight in:

- <a href="https://github.com/MeteoStudios/meteo-customapp-demo" target="_blank">meteo-customapp-demo</a> - exercises every part of the API (popups, pickers, fetchNui, server push, multi-screen navigation)
- <a href="https://github.com/MeteoStudios/meteo-customapp-prpgroups" target="_blank">meteo-customapp-prpgroups</a> - app for prp-bridge
- <a href="https://github.com/MeteoStudios/meteo-customapp-finance" target="_blank">meteo-customapp-finance</a> - app for meteo dealership finances manage

***

## Registering an App

Custom apps live in their own resource. Register on your own client start **and** on `meteo-phone:customAppsReady` (so the app re-registers when the phone restarts).

```lua
-- client.lua of YOUR resource
local function registerApp()
    exports['meteo-phone']:AddCustomApp({
        identifier   = 'weather',          -- unique id, no spaces
        name         = 'Weather',          -- shown on the home screen
        description  = 'Live city weather',
        developer    = 'YourName',
        ui           = 'ui/index.html',    -- path inside YOUR resource (omit for simple apps)
        icon         = 'ui/icon.png',      -- or use materialIcon below
        materialIcon = nil,                -- e.g. 'cloud' to use a Material Icon (matches native apps)
        defaultApp   = false,              -- false = listed in the App Store, true = pre-installed
        size         = 1.0,                -- size shown in the App Store (MB)
    })
end

AddEventHandler('onClientResourceStart', function(res)
    if res == GetCurrentResourceName() then registerApp() end
end)
AddEventHandler('meteo-phone:customAppsReady', registerApp)
```

### App Fields

| Field | Type | Required | Description |
|-------|------|:--------:|-------------|
| `identifier` | string | yes | Unique id. No spaces. |
| `name` | string | yes | Display name on the home screen. |
| `description` | string | no | Shown in the App Store. |
| `developer` | string | no | Your name / studio. |
| `ui` | string | no | Path to the UI html. Omit for a simple app. |
| `icon` | string | no | Path to the icon image (png/jpg/svg, square). |
| `materialIcon` | string | no | Material Icons Outlined name (e.g. `groups`, `cloud`). Matches the native phone look. Takes precedence over `icon`. |
| `iconBackground` | string | no | CSS background behind the icon (e.g. `#1e1e1e`, gradients). |
| `defaultApp` | bool | no | `true` = pre-installed, `false` = listed in the App Store. |
| `size` | number | no | Size shown in the App Store, in MB. |
| `onUse` | function | no | Simple apps only - client callback when tapped. |

To remove an app: `exports['meteo-phone']:RemoveCustomApp('weather')`.

***

## Simple Apps (No UI)

If you only need a button on the home screen that triggers something, omit `ui` and provide `onUse`:

```lua
exports['meteo-phone']:AddCustomApp({
    identifier = 'panic',
    name       = 'Panic Button',
    icon       = 'ui/icon.png',
    onUse      = function()
        TriggerServerEvent('my-panic:trigger')
    end,
})
```

A server-side `onServerUse` is also available - register the same `identifier` from `server.lua`.

***

## UI Apps

A UI app provides its own `index.html`. **You do not need to include any script from meteo-phone** - the phone injects everything for you when the iframe loads. Just wait for the `componentsLoaded` event:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="app.css">
</head>
<body>
    <div id="root">Loading...</div>
    <script src="app.js"></script>
</body>
</html>
```

```js
// app.js
window.addEventListener('componentsLoaded', function () {
    document.getElementById('root').textContent = 'Hello ' + PhoneInfo.name;
});
```

### Injected Globals

These are placed on `window` once `componentsLoaded` fires:

| Global | What it is |
|--------|-----------|
| `resourceName` | Your resource name. |
| `appName` | The app identifier you passed to `AddCustomApp`. |
| `PhoneInfo` | `{ name, source, citizenid, phoneNumber, phoneSerial }` for the local player. |
| `PhoneSettings` | `{ theme, language, volume, currency }` - current phone settings. |
| `fetchNui(event, data, target?)` | POST to a NUI callback. Default target is your own resource. Returns a Promise. |
| `onNuiEvent(name, handler)` | Receive `SendCustomAppMessage` events from your Lua. |
| `setPopUp(opts)` | Confirm or input popup. Returns a Promise. |
| `setContextMenu(opts)` | Actions sheet. Returns a Promise. |
| `setContactSelector(opts)` | Pick a contact from the phone. Returns a Promise. |
| `setGallery(opts)` | Pick a photo from the phone gallery. Returns a Promise. |
| `sendNotification(opts)` | Show a phone notification. |
| `onBack(handler)` | Register a back handler. Return `true` to stop the phone exiting your app. |
| `onSettingsChange(handler)` | Called when phone settings change. |
| `closeApp()` | Exit the app, return to the home screen. |

***

## Talking to Your Backend

`fetchNui` POSTs to a `RegisterNUICallback` in your own resource by default:

```js
// app.js
fetchNui('getWeather', { city: 'Los Santos' }).then(function (data) {
    document.getElementById('temp').textContent = data.temp + '°C';
});
```

```lua
-- client.lua of YOUR resource
RegisterNUICallback('getWeather', function(data, cb)
    local result = lib.callback.await('my-weather:server:get', false, data.city)
    cb(result)
end)
```

### Pushing Messages From Lua

Push live updates into your running app:

```lua
-- client side
exports['meteo-phone']:SendCustomAppMessage('weather', 'update', { temp = 21 })

-- server side (player source, table of sources, or -1 for all)
exports['meteo-phone']:SendCustomAppMessage(source, 'weather', 'update', { temp = 21 })
```

```js
onNuiEvent('update', function (payload) {
    console.log('New temp:', payload.temp);
});
```

***

## Native Components

Use the phone's own UI for popups and pickers. Browser dialogs like `alert()` / `confirm()` do not work inside FiveM.

### Confirm / Input Popup

```js
// Confirm
setPopUp({
    type: 'confirm',
    title: 'Delete photo?',
    description: 'This action cannot be undone.',
    icon: 'delete',
    danger: true,
    confirmText: 'Delete',
    denyText: 'Keep'
}).then(function (r) {
    if (r.confirmed) { /* ... */ }
});

// Input
setPopUp({
    type: 'input',
    title: 'Rename group',
    icon: 'edit',
    placeholder: 'New group name',
    defaultValue: 'Old name'
}).then(function (r) {
    if (r.confirmed) console.log(r.value);
});
```

| Option | Default | Notes |
|--------|---------|-------|
| `type` | `'confirm'` | `'confirm'` or `'input'`. |
| `title` | `'Confirm'` | Heading text. |
| `description` | `''` | Body text (confirm only). |
| `icon` | `'help_outline'` or `'edit'` | Material Icons Outlined name. |
| `danger` | `false` | Red confirm button. Auto-detected for icons like `delete`, `person_remove`, `block`. |
| `confirmText` / `denyText` | `'Accept'` / `'Deny'` | Button labels. |
| `placeholder` / `defaultValue` | `''` | Input only. |

### Context Menu

A bottom sheet with a list of actions.

```js
setContextMenu({
    title: 'Photo options',
    options: [
        { label: 'Set as profile', icon: 'account_circle', value: 'profile' },
        { label: 'Share',          icon: 'share',          value: 'share' },
        { label: 'Delete',         icon: 'delete',         value: 'delete', danger: true }
    ]
}).then(function (r) {
    if (r.selected === -1) return;       // dismissed
    if (r.value === 'delete') { /* ... */ }
});
```

### Contact Picker

```js
setContactSelector({
    title: 'Send invite to',
    excludeNumbers: [PhoneInfo.phoneNumber]   // hide yourself
}).then(function (r) {
    if (!r.selected) return;
    fetchNui('inviteByNumber', { number: r.number, name: r.name });
});
```

### Gallery Picker

```js
setGallery({ multiSelect: false }).then(function (r) {
    if (!r.selected) return;
    console.log(r.photo);   // single photo URL
    console.log(r.photos);  // array (always present)
});
```

***

## Notifications

`sendNotification(opts)` queues a notification in the same stack the native apps use.

```js
sendNotification({
    app: 'Weather',
    icon: 'cloud',
    message: 'Light rain expected this evening.',
    type: 'info'
});

// With sound and a long duration
sendNotification({
    app: 'Groups',
    icon: 'check_circle',
    message: 'Player added to your group.',
    type: 'success',
    sound: 'contact-accepted',
    duration: 5000
});

// Sticky alert with action buttons
sendNotification({
    app: 'Panic',
    icon: 'crisis_alert',
    message: 'Officer needs assistance at Vespucci.',
    type: 'warning',
    priority: 'urgent',
    sound: 'security-notify',
    duration: 0,
    actions: [
        { id: 'respond', label: 'Respond', primary: true },
        { id: 'dismiss', label: 'Dismiss' }
    ]
});
```

| Option | Default | Notes |
|--------|---------|-------|
| `app` | `'System'` | Shown as the source app name. |
| `icon` | `'notifications'` | Material Icons Outlined name. |
| `message` | `'Notification'` | Body text. |
| `type` | `'info'` | `'info'`, `'success'`, `'warning'`, `'error'` - changes the icon tint. |
| `duration` | `4000` | Auto-dismiss in ms. Use `0` to stay until clicked. |
| `priority` | `null` | `'low'`, `'normal'`, `'high'`, `'urgent'`. Adds a priority badge. |
| `actions` | `null` | `[{ id, label, primary? }]` - action buttons under the message. |
| `sound` | `null` | Built-in sound name (see below). |

### Built-in Sounds

Pass any of these names as `sound` (no extension, no path):

| Sound | Mood |
|-------|------|
| `bleeter-notify` | Generic friendly chime - good default. |
| `bleeter-rebleet` | Light pop. |
| `bleeter-reply` | Soft tap. |
| `calendar-notify` | Calendar / reminder ding. |
| `company-notify` | Business-like ping. |
| `contact-accepted` | Positive confirmation. |
| `contact-cancel` | Soft negative. |
| `contact-request` | Pending request. |
| `email` | Email arrival. |
| `garage` | Garage update. |
| `garage-accepted` | Garage accepted. |
| `garage-cancel` | Garage declined. |
| `garage-request` | Garage request. |
| `message` | SMS-style ding. |
| `security-notify` | Alert / alarm. |
| `yellowpages-notify` | Listing update. |

***

## Back Navigation

ESC and the phone's home indicator both call your `onBack` handler. Return `true` to stop the phone closing your app (you handled the back yourself), or return nothing to let the phone exit:

```js
var stack = ['home'];

onBack(function () {
    if (stack.length > 1) {
        stack.pop();
        render();
        return true;       // handled - stay in the app
    }
    return false;          // root screen - phone exits the app
});
```

When a phone popup is open, ESC closes that first - your `onBack` only fires once nothing else is in the way.

***

## Full Example

```
my-weather-app/
├── fxmanifest.lua
├── client.lua
├── server.lua
└── ui/
    ├── index.html
    ├── app.js
    └── icon.png
```

**fxmanifest.lua**
```lua
fx_version 'cerulean'
game 'gta5'
name 'my-weather-app'
client_script 'client.lua'
server_script 'server.lua'
files { 'ui/index.html', 'ui/app.js', 'ui/icon.png' }
lua54 'yes'
```

**client.lua**
```lua
local function registerApp()
    exports['meteo-phone']:AddCustomApp({
        identifier  = 'weather',
        name        = 'Weather',
        description = 'Live city weather',
        ui          = 'ui/index.html',
        icon        = 'ui/icon.png',
    })
end

AddEventHandler('onClientResourceStart', function(res)
    if res == GetCurrentResourceName() then registerApp() end
end)
AddEventHandler('meteo-phone:customAppsReady', registerApp)

RegisterNUICallback('getWeather', function(data, cb)
    cb({ temp = math.random(10, 30), condition = 'Sunny' })
end)
```

**ui/index.html**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="app.css">
</head>
<body>
    <h1 id="temp">...</h1>
    <button id="refresh">Refresh</button>
    <script src="app.js"></script>
</body>
</html>
```

**ui/app.js**
```js
window.addEventListener('componentsLoaded', function () {
    function load() {
        fetchNui('getWeather', {}).then(function (data) {
            document.getElementById('temp').textContent =
                data.temp + '°C - ' + data.condition;
        });
    }
    document.getElementById('refresh').addEventListener('click', load);
    load();
});
```

***

## Notes & Limitations

- App icons can be image files (png/jpg/svg) via `icon`, or a Material Icons Outlined name via `materialIcon` to match the native phone look.
- Each app's iframe stays mounted while the phone is open, so app state survives switching between apps. It is unmounted when the phone closes.
- `fetchNui` reaches your own resource directly - it does not route through `meteo-phone`.
- Custom apps render inside the phone safe area (below the status bar, above the home indicator). You never need to pad for the phone chrome.
- Game-render / camera capture inside custom apps is not yet supported.

***

{% hint style="success" %}
**Reference implementations**

- <a href="https://github.com/MeteoStudios/meteo-customapp-demo" target="_blank">meteo-customapp-demo</a> - a sandbox app that exercises every API surface
- <a href="https://github.com/MeteoStudios/meteo-customapp-prpgroups" target="_blank">meteo-customapp-prpgroups</a> - a real Groups app built on prp-bridge

Clone either one, drop it into your resources folder, and use it as a starting template.
{% endhint %}

***

{% hint style="success" %}
**Need help building a custom app?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
