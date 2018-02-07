---
layout: default
title:  Updating python component (i.e. bellows for zigbee) in HASS.io
categories: 
  - Home Assistant
  - HASS.io
  - ZigBee
  - Raspberry
  - Home Automation
---

I'm currently running Home Assistant on a Raspberry Pi and I am trying to connect some zigbee devices. All of them fail to join. There are lots of reports of errors like mine an lots of changes in bellows, the underlying library used in Home Assistant. But fortunately updating the version of python components or them is quite easy, even within HASS.io.

**Step 1:** Get ssh access to you installation  
Take out your SD-Card and create an `authorized_keys` file in the root folder of the first partition (yes: mmcblkp01, directly in '/') and put your ssh pubkey in it. Afterwards boot your system and ssh into it by using `ssh -i <priv_id_file> -p 22222 <ip>`.

**Step 2:** Find and enter docker container  
Run `docker ps` to show your running containers (hass.io is based on docker containers). Look out for `homeassistant/raspberrypi3-homeassistant`. Note the container id and enter the continer with `docker exec -ti <id> /bin/sh`

**Step 3:** Update bellows and exit the container  
Inside the container simply use pip to update the bellows version by running `pip3 install --upgrade bellows`. Afterwards leave the container with a simple `exit`.

**Step 4:** Save your changes for restart  
Outside the container run `docker commit <id>` to commit the changes. Otherwise they'll be lost after container restart as they will not persist.

**Step 5:** Restart Home Assistant and enjoy  
You can restart Home Assistant in whatever way you like. Afterwards your bellows version should be bumped.

REMEBER TO REPEAT THE STEPS AFTER UPDATING HASS.IO ;)
