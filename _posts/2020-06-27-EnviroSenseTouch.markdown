---
layout: post
title:  "#20 EnviroSense Touch, TVOC, eCO2 and More"
date:   2020-06-17 12:42:05 -0700
categories: IoT
tags: [EnviroSense, SGP30, SHT30, 2.4" Touch Screen]
---
![Temp Calibrator](/assets/img/20Enviro1.JPEG)

# Intro
Latest addition to my EnviroSense family is here. I was experimenting how quickly one can put a complete set of sensors, microcontroller and display together leveraging the concept introduced by [WEMOS](https://www.wemos.cc/en/latest/index.html). The result is very promising.


# SGP30

This is a I2C Interface TVOC and eCO2 sensor shield based SGP30 from WEMOS. Main specs are: 

- I2C Interface
- TVOC: 0-60000 ppb
- eCO2: 400-60000 ppm


# SHT30

This one is I2C Interface digital temperature and humidity sensor shield based SHT30. Main specs:

- I2C Interface
- Typical accuracy ±3%RH and ±0.3°C


# WEMOS 2.4" Touch Screen Display
The display is versatile 2.4-inch color display with integrated touch capability. 


# Weather Data
The display is nice and big enough that can accommodate the weather forecast data. It is nice to have that feature and thanks to the [WeatherMap API](https://openweathermap.org/api) it is straight forward to add the feature to the project.
![Temp Calibrator](/assets/img/20Enviro.JPEG)

# Clock from NTP
Thanks to the **NTPClient** it is also possible to add accurate clock to the project.
