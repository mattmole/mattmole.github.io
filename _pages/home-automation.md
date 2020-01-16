---
permalink: /home-automation/
title: "Home Automation"
#excerpt: "This post should [...]"
---

# Home Assistant

During the last few years, I have really enjoyed using the [Home Assistant](https://www.home-assistant.io/) automation software to tie together various brands of home automation equipment I regularly use.

I have equipment of the following brand:

* [Raspberry Pi 3B](https://www.raspberrypi.org/) running [Hass.io]
* [Ikea Tradfri](https://www.ikea.com/gb/en/product-guides/ikea-home-smart-system/) lighting, motion sensor and socket
* [TP-Link Kasa](https://www.tp-link.com/us/kasa-smart/kasa.html) Wi-Fi plug
* Various [Raspberry Pi](https://www.raspberrypi.org/) SBCs with temperature sensors and cameras
* [Google Nest](https://store.google.com/product/nest_learning_thermostat_3rd_gen) Thermostat
* [Google home mini](https://store.google.com/product/google_home_mini)
* [Google chromecast](https://store.google.com/product/chromecast)
* ESP8266 microcontroller boards, linked to Home Assistant with [ESPHome](https://esphome.io/)

# Some of my Projects
## Temperature sensor and video monitor for certain rooms in the house

This was completed using [DS18B20](https://datasheets.maximintegrated.com/en/ds/DS18B20.pdf) sensors, raspberry pi camera, raspberry pi zero w SBC and the [motion]() software to use the camera as a live video source. The sensor data was sent to the Home Assistant instance using [MQTT](mqtt.org)

## External temperature sensor and temperature sensor for other rooms in the house

This project was completed using the amazxing [ESPHome](https://esphome.io/) software, which provides an easy way to upload firmware to the ESP8266 (and other) microcontroller boards. I have used a mixture of NodeMCU and Wemos D1 mini boards. Data from these devices can then be communicated to and from the Home Assistant instance. [DS18B20](https://datasheets.maximintegrated.com/en/ds/DS18B20.pdf) sensors were used (as above) due to them being callibrated.

## Switch unit to control all smart lights in the house

A switch was added to one of the microcontroller boards and this is used with an automation to be able to switch off any smart lights that are left on and then switch on a particular light on the next switch press. This is really useful when going to bed to switch off lights and then switch on a light downstairs if needing to in the middle of the night!

## Unifi security camera

I have a unifi security camera outside the house and the live feed from this is added to the Home Assistant lovelace interface. I have a useful automation setup where a button can be pressed and this live feed is then shown on the TV in the living room

# Future projects

Some future projects are noted down below:

* Integrate the google nest with the temperature in the coldest room of the house. This will allow for the temperature of the heating to be moderated in the night for the coldest room, while keeping the thermostat in a different location
* Add automations to the system to allow notifications of events to be sent to the google home mini / echo dot units around the house
* Add monitoring of current usage of home appliances, to notify when devices finish their cycles

# Blog posts

Home Automation related blog posts will be linked to below...

{% assign tags_max = 0 %}
{% for tag in site.tags %}
  {% if tag[1].size > tags_max %}
    {% assign tags_max = tag[1].size %}
  {% endif %}
{% endfor %}

{% for i in (1..tags_max) reversed %}
  {% for tag in site.tags %}
#    {% if tag == 'homeautomation' %}
    {% if tag[1].size == i %}
      <section id="{{ tag[0] | slugify | downcase }}" class="taxonomy__section">
        <h2 class="archive__subtitle">{{ tag[0] }}</h2>
        <div class="entries-{{ page.entries_layout | default: 'list' }}">
          {% for post in tag.last %}
            {% include archive-single.html type=page.entries_layout %}
          {% endfor %}
        </div>
        <a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>
      </section>
    {% endif %}
#    {% endif %}
  {% endfor %}
{% endfor %}