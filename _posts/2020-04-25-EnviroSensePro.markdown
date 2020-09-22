---
layout: post
title:  "#12 EnviroSense Pro, SENSIRION SCD30 and SPS30"
date:   2020-04-25 12:42:05 -0700
categories: IoT
---
![Schematic 3D View](/assets/img/12schematic.PNG)

# Intro

The newest member of my EnviroSense family is here. For this version I decided to go with an advanced selection of sensors.

[SENSIRION](https://www.sensirion.com/en/) has a family of sensors targeted the environmental and air quality monitoring applications.

I picked **[SPS30 Dust Sensor](https://www.sensirion.com/en/environmental-sensors/particulate-matter-sensors-pm25/)** that can measure **PM2.5, PM1.0, PM4.0 and PM10** with more than 10 years of lifetime. 

![SENSIRION SPS30](/assets/img/12SPS30.PNG) *Image credit: [Sensirion](https://www.sensirion.com/en/)*

Collectively with the **[SCD30](https://www.sensirion.com/en/environmental-sensors/carbon-dioxide-sensors/carbon-dioxide-sensors-co2/)** an *NDIR* sensor that can measure:

- PM2.5, 
- PM1.0,
- PM4.0
- PM10
- CO2, 
- Relative Humidity, and
- Temperature. 

It is envisioned that the device could be a good candidate for any industry grade air quality monitoring project. 

The device core processor is an **ESP32** the board is designed in a way that either an addressable **WS2812B** or a **1.8" TFT monitor** can be used to provide the real-time feedback to the user.

Device general specifications are as below:
- Wireless enabled 2.4GHz
- Bluetooth BLE
- 1.8" TFT display

I have ordered the board from [JLCPCB](https://jlcpcb.com) and waiting for its delivery! I will update this post as soon as I commission the trial.

