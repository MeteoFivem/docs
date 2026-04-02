---
description: >-
  Translate the meteo fivem server in seconds with one config change. Supports
  any language thanks to ox_lib based locales.
icon: language
---

# How to Translate the Server

Translate the entire meteo server in seconds. No UI edits, no code changes - just one config line and you are done.

{% hint style="success" %}
**One config translations** - change your language in ox.cfg and every script updates automatically.
{% endhint %}

***

## Languages Included

The server comes with these languages out of the box:

| Code | Language   |
| ---- | ---------- |
| ar   | Arabic     |
| bg   | Bulgarian  |
| de   | German     |
| en   | English    |
| es   | Spanish    |
| et   | Estonian   |
| fr   | French     |
| he   | Hebrew     |
| nl   | Dutch      |
| pl   | Polish     |
| pt   | Portuguese |
| sv   | Swedish    |
| vi   | Vietnamese |

***

## How to Set Your Language

{% stepper %}
{% step %}
**Open ox.cfg**

Find the `ox.cfg` file in your server config folder and open it
{% endstep %}

{% step %}
**Find the locale line**

Look for this line (it's commented out by default):

```
# setr ox:locale "fr"
```
{% endstep %}

{% step %}
**Uncomment and set your language**

Remove the `#` and replace `fr` with your language code:

```
setr ox:locale "de"
```

Use any of the language codes from the table above
{% endstep %}

{% step %}
**Restart the server**

That's it. Every script will now use your chosen language.
{% endstep %}
{% endstepper %}

***

## Adding a Custom Language

Don't see your language? No problem. You don't need to touch any UI or codebase.

{% stepper %}
{% step %}
**Create your locale file**

Create a new `.json` file named with your language code (e.g. `tr.json` for Turkish). Use any existing locale file like `en.json` as a base and translate all the values.
{% endstep %}

{% step %}
**Add it to every script**

Place your `.json` file into the `locales/` folder of each script. All scripts follow the same structure so it's a simple copy and translate.
{% endstep %}

{% step %}
**Set the locale in ox.cfg**

Set your new language code in ox.cfg:

```
setr ox:locale "tr"
```
{% endstep %}

{% step %}
**Done**

Your custom language works everywhere with zero code changes. No UI edits needed, no config per script - just the locale files.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
All scripts use ox_lib locale system so adding a new language once covers every script on the server.
{% endhint %}
