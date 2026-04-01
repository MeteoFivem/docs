---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/hPLkuIrL5TffIt3aasi9/paid-scripts/meteo-phone/changelogs
---

# Changelogs

## Changelog

### \[1.6.0]

- Added prp-bridge support with new SMS, location, and notification exports
- Added DispatchSMSToPlayer, DispatchLocationToPlayer, GetActivePhoneNumber, GetActivePhoneSerial exports
- Added unread message indicators with count badges for Email and SMS apps
- Added slide transitions for all app screen navigation
- Updated Laber app for new meteo jobs (transit, gopostal, fishing) with GetJobLocation export
- Updated Laber app detail view with perks, stats, and job descriptions
- Updated all fonts to Plus Jakarta Sans
- Fixed security camera placement allowing inventory to open
- Fixed settings not saving correctly
- Fixed contacts sharing minor issue
- Fixed item quality (durability) for ox_inventory
- Added ox_lib logger support for all logs
- Removed old job references (busjob, deliveryjob, gruppe6job)

### \[1.5.0]

- Added App Store for downloading and managing apps
- Added home screen app repositioning with drag support and multiple screen pages
- Added Properties app with meteo-apartments and meteo-properties support
- Added meteo-dealerships support as a company in the Companies app
- Added GetPlayerPhone export
- Updated Banking, Companies, and Laber app UI

### \[1.4.0]

* Added points based optimization for security cameras and motion sensors
* Added keybind support for ending/declining calls
* Added GetPlayerPhoneBySource export
* Fixed blocked contacts not preventing calls
* Fixed call cooldown security issue

### \[1.3.0]

* Added Music app with artist system, playlists, and song uploads
* Added Calendar Events app with admin posting and reminder notifications
* Added phone UI zoom level adjustment (50% to 150%)
* Added Meteo Companies support for company announcements

### \[1.2.0]

* Added multiple blips support for Laber custom jobs
* Added per-blip custom names for Laber custom jobs

### \[1.1.0]

* Added custom job support for Laber app (config + server exports)
