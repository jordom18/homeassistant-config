# My Home Assistant Configuration
This is my Home Assistant configuration at the current state. It is not nearly finished yet, but I am working constantly on it. Also I implemented just a few automation for now. However, one step after the other I plan to automate a lot of more scenes.

<p align="center">
  <img src="https://github.com/home-assistant/home-assistant-assets/blob/master/loading-screen.gif">
</p>

## Hardware
My Home Assistant configuration is running on a [Raspberry Pi 3 Model B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/). In the current state it delivers enough peformance to run my Home Automation. But I am sure this will not be enough for all time. Therefore I try to configurate my HA platform to be variable. It is my target to be able to easily switch from my Raspberry Pi to a more powerful machine in the future.
To reach this target I try to run all software integrations in docker containers.

## Software
As described above I am running Home Assistant on a Raspberry Pi 3. Therefore I use the standard Debian OS named [Raspbian](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/). For security reasons I also use a nginx instance as a reverse proxy with a SSL encryption. For that I used the [this tutorial](https://webcodr.io/2018/02/nginx-reverse-proxy-on-raspberry-pi-with-lets-encrypt/).
A deskription of the three main components of my home automation follow in the next lines.

### Docker
[Docker](https://www.docker.com) is a container virtualization software. To get it to work on my Raspberry Pi I used [this](https://blog.alexellis.io/5-things-docker-rpi/) and [this](https://blog.alexellis.io/getting-started-with-docker-on-raspberry-pi/) blog posts by [Alex Ellis](https://blog.alexellis.io).
Docker is easy to use and highly increases my flexibility. HA provides Docker containers for every new version. With that I am able to upadte to a new version within few minutes. I just download the new image, stop the old container and restart a new container with the new version.
But even if I want to move to new hardware is very easy. Of course there are some network preconditions. After that even to move on a x86 architecture machine is done within a very short time.
Docker is very helpful in my use case and I do not want to miss it anymore.

### Home Gear
Since I use several Homematic devices I also need a interface to them. I do not use the official Homematic hub, but I use a self build [nanoCUL](http://blog.steveundkristin.de/2016/02/04/fhem-selbstbau-cul-868-fuer-homematic/)(german, not https) sender in combination with the [Home Gear](https://homegear.eu) software. With that I can interact with my switches and heater devices as I would use the official hub.
Home Gear runs in my configuration in a Docker container.

### Home Assistant
The core of my home automation is [Home Assistant](https://www.home-assistant.io). It displays all information in a more or less clear way and helps me to write scripts and automations in YAML files. Currently I am using mostly the standard UI, but in the future I want to switch to Lovalace tabs. For now I realized some scripts and automations to help me controll my flat. For example I turn off every switch and all heaters when I leave my home. Also I automated some devices to live my morning rituals. 
However, that is not all by far. I have many more ideas to realize in the future and I am sure HA will be usefull partner for that.
Home Assistant runs in my configuration in a Docker container.

## HA Discoverys
Meanwhile HA is able to discover many integrations by its own. In my case these are currently the following integrations.

### HA iOS
I think this integrations discovered that I am using the iOS integration. With it I can see now the battery and loading state of my iOS devices in HA.

### Philips hue
Some minutes after I connected the [Philips Hue](https://www2.meethue.com/en-us) hub to my network, HA automatically discovered it.
Of course I use the Philips Hue integration to control some of my light bulbs. However, since the Philips Hue hub uses [Zigbee](https://www.zigbee.org) I am also able to use other Zigbee devices like [Osram plugs and lights](https://smartplus.ledvance.de/produkte/innenbeleuchtung/index.jsp)(german).
I am a huge fan of light decoration. Therefore I will integrate more light devices by Philips and Osram in the future.

## HA Integrations
Home Assistant provides a huge amount of additional [integrations](https://www.home-assistant.io/components/) to increase its functionality. Since my HA is running on a small Raspberry Pi I have to filter for the most needed integrations. However, even with this small selection I am able to create lot of automations.
Integrations are not official parts of HA, but provided by the community.

### Homekit
With [Homekit](https://www.home-assistant.io/components/homekit/) I am able to map a selection of my smart home devices to Apple Home. I decide by my own which devices will be mapped and which devices not.

### Homematic
After HA the [Homematic](https://www.home-assistant.io/components/homematic/) integration in combination with Home Gear is the second core of my smart home, since most of my devices are Homematic devices.
While Home Gear controls my Homematic devices, HA and the Homematic integration control Home Gear.
I have heater devices in all rooms and thermostates in some rooms. Additionally I use some switches to control automations and electricity consumers.
I am still satisfied with the devices. However, I am struggeling with replacing them with the follow up generation Homematic IP to be safe for the future.

### iOS
The [iOS](https://www.home-assistant.io/components/ios/) integration is required to use the companion app on iPhone and iPad.

### Philips TV
Sadly the [Philips TV](https://www.home-assistant.io/components/philips_js/) integration is not working for me. I still have not figured out why...
The TV is connected to my network and JOINTspace is activated. I will re-try this one later.

### Sonos
The [Sonos](https://www.home-assistant.io/components/sonos/) integration can control my Sonos speakers. I use it to start the radio with low volume as a alarm clock in the moring.
In the evening I use it for some calm down music before I go to sleep.
The Sonos integration would also work with HA discovery.

### Google TTS
Currently I am not using [Google text-to-speech](https://www.home-assistant.io/components/google_translate/) frequently. For my HA instance it is in experimental stage.
In the future I want to use it with my Sonos speakers to send warnings. Something like: "The window is still open."

### OpenWeatherMap
With the [OpenWeatherMap](https://www.home-assistant.io/components/openweathermap/) integration I track the local weather conditions. This is important for my automations to decide whether to turn on the heaters or not. Of cause with the build in temperature sensors the heaters could decide on their own. But I want to economize wireless signals.
In the future I plan to control my shutters with HA to close them on a high sun or open them on strong wind.

## Suggestions?
First of all I want to thank [Adam](https://github.com/SilvrrGIT) for sharing his awesome [HA configuration](https://github.com/SilvrrGIT/HomeAssistant) on gitHub. I am still beginning my home automation journey and you are a huge inspiration.
I can not invest as much time as I would like. But I am happy for every suggestion about my configuration. If there are any questions to my configuration I would like to try to answer them in the [HA Forum](https://community.home-assistant.io). My user name is [Xargon](https://community.home-assistant.io/u/Xargon/activity).
While I work on my Home Assistant configuration I will also update this README file from time to time.