---
title: "Embedded Development"
date: 2020-05-24T13:48:47-04:00
description: All things related to embedded development. Microcontrollers, firmware, libraries, etc.
draft: false
---

# Wifi

## ESP8266 / ESP32

ESP8266 is a microcontroller with embedded wifi. It first became popular as a
cheap wifi solution for arduino devices but it is a very capable μC on its
own. It's now supported directly in Arduino.

### esp8266/Arduino

[github](https://github.com/esp8266/Arduino)

This is the Arduino core implementation for the esp8266 chip.

### Tasmota

[github](https://tasmota.github.io/docs/)

From the project page:

  > Tasmota is an open source firmware for ESP8266 based devices created and maintained by Theo Arendst.

### Tasmota Device Templates Repository

[github](https://templates.blakadder.com/)

Tasmota firmware can be configured using templates to define which
peripheral devices GPIO and ADC are connected to. Templates are
defined by JSON strings as described [here](https://tasmota.github.io/docs/Templates/).
This repository contains a large selection of user-submitted templates
for various devices. Each device has an entry which makes it easy to find
a device for your region, and has links to where you can conveniently buy
the modules.

### Tuya-convert

[github](https://github.com/ct-Open-Source/tuya-convert)

This project provides a way to flash a custom firmware onto a wide array of
devices which use a turn-key smarthome solution provided by a company called
Tuya. Their README is pretty thorough.

Hi, folks!
