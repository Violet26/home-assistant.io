---
title: "Setting up presence detection"
description: "Instructions on how to setup presence detection within Home Assistant."
---

Presence detection detects if people are home, which is the most valuable input for automation. Knowing who is home or where they are, will open a whole range of other automation options:

- Send me a notification when my child arrives at school
- Turn on the AC when I leave work

<p class='img'>
<img src='/images/screenshots/map.png' />
Screenshot of Home Assistant showing a school, work and home zone and two people.
</p>

### Adding presence detection

There are different ways of setting up presence detection. Usually the easiest way to detect presence is by checking which devices are connected to the network. You can do that if you have one of our [supported routers][routers]. By leveraging what your router already knows, you can easily detect if people are at home.

It's also possible to run an app on your phone to provide detailed location information to your Home Assistant instance. If you're on iOS we suggest to use the [Home Assistant iOS app](/ios/). For Android, we suggest [OwnTracks][ha-owntracks].

<div class='videoWrapper'>
<iframe width="560" height="315" src="https://www.youtube.com/embed/UieAQ8sC6GY" frameborder="0" allowfullscreen></iframe>
</div>

### Zones

<img src='/images/screenshots/badges-zone.png' style='float: right; margin-left: 8px; height: 100px;'>

Zones allow you to name areas on a map. These areas can then be used to name the location a tracked user is, or use entering/leaving a zone as an automation [trigger] or [condition]. Zones can be set up from the integration page in the configurations screen.

<div class='note'>
The map view will hide all devices that are home.
</div>

[routers]: /integrations/#presence-detection
[nmap]: /integrations/nmap_tracker
[ha-bluetooth]: /integrations/bluetooth_tracker
[ha-bluetooth-le]: /integrations/bluetooth_le_tracker
[ha-owntracks]: /integrations/owntracks/
[ha-locative]: /integrations/locative
[ha-gpslogger]: /integrations/gpslogger
[ha-presence]: /integrations/#presence-detection
[mqtt-self]: /integrations/mqtt/#run-your-own
[mqtt-cloud]: /integrations/mqtt/#cloudmqtt
[zone]: /integrations/zone/
[trigger]: /getting-started/automation-trigger/#zone-trigger
[condition]: /getting-started/automation-condition/#zone-condition
[ha-map]: /integrations/map/

### [Next step: Join the Community &raquo;](/getting-started/join-the-community/)
