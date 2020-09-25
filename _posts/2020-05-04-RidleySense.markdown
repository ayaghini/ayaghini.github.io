---
layout: post
title:  "#14 RidleySense v1.0; Multi-core ESP32, MPU9255 and HX711"
date:   2020-05-04 12:42:05 -0700
categories: IoT
tags: [ESP32, IMU, MPU9255, Arduino, whole body vibration]
---
![RidleySense v1.0](/assets/img/14Graphs.PNG)

# Intro

I have had a customer asking for a road condition monitoring device. The core for that project was to be able to measure accelerations in three dimensions. 

This project was initiated from a friend of mine asking for a device that can measure stress and strain in structural elements of a mining equipment. 

The device measures following parameters:
- acceleration in X, Y, and Z
- angular rate in X, Y, and Z 
- magnetic field measurement
- N-channel 24-bit input from any **Wheatstone** bridged strain gauge
- temperature

## Hardware

![RidleySense v1.0](/assets/img/14ridleySense.JPG)

### MPU9255

I had a great success using these cheap IMU devices. For the next version I have picked up couple of **Bosch** sensors and looking forward working with them. 

### HX711

When dealing with small measurements and changes in the input, an amplifier is a must. **HX711** has been a go for among *maker* community for dealing with strain gauges. I have found it a useful and easy to work with solution.

![HX711 Arduino output](/assets/img/14strainGauge.PNG)

### Dallas DS18B20
What a small, precise and handy piece of sensor. I love these and could not resist the urge to add them to this project, after all there are tons of calibrations needed to be done and they are possible if only you know the temperature.

### ESP32 multi-core
This specific project needed a high frequency of measurements. After initial run, I was not quite happy with the result. Although I did implement a **State Machine**, still reading from each sensor prevented the loop to proceed fast. 

The solution was to use ESP32 second processor. It was not hard to implement using the **Arduino IDE**. 

You can start from here: [ESP32 Dual Core](https://github.com/SensorsIot/ESP32-Dual-Core/blob/master/ESP32_Two_LED_Asynchron/ESP32_Two_LED_Asynchron.ino)


# Next
I will be using the Bosch sensor!