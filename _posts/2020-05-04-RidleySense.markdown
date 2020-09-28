---
layout: post
title:  "#14 Real-time FEA Based Machine Structural Health Monitoring; RidleySense v1.0"
date:   2020-05-04 12:42:05 -0700
categories: IoT Mining
tags: [FEA, Health Monitoring, Structural Analysis, ESP32, IMU, MPU9255, Arduino, whole body vibration]
---
![RidleySense v1.0](/assets/img/14Graphs.PNG)

# Intro

This project was initiated from a friend of mine Dr. Charles Constancon asking for a device that can measure stress and strain in structural elements of a mining equipment. 

Critically spread across key structural elements of the machine and fed into a live FEA model, the project aims at prolonging giant mining equipment Lifetime by continues monitoring of their status and triggering ML based notification to prevent excessive use and load.

The device measures, records and publishes following parameters:
- acceleration in X, Y, and Z
- angular rate in X, Y, and Z 
- magnetic field measurement
- N-channel 24-bit input from any **Wheatstone** bridged strain gauge, and 
- temperature.

## Hardware

![RidleySense v1.0](/assets/img/14ridleySense.JPG)

### MPU9255

I had a great success using these cheap IMU devices. For the next version I have picked up couple of **Bosch** sensors and looking forward working with them. 

### HX711

When dealing with small measurements and changes in the input, an amplifier is a must. **HX711**, a 24-bit amplifier, has been a go for among *maker* community for dealing with strain gauges. I have found it a useful and an easy to work with solution.

![HX711 Arduino output](/assets/img/14strainGauge.PNG)

### Dallas DS18B20
What a small, precise and handy piece of sensor. I love these and could not resist the urge to add them to this project, after all there are tons of calibrations needed to be done and they are possible if only you know the temperature.

### ESP32 multi-core
This specific project needed a high frequency of measurements. After initial run, I was not quite happy with the result. Although I did implement a **State Machine**, still reading from each sensor prevented the loop to proceed fast. 

The solution was to use ESP32 second processor. It was not hard to implement using the **Arduino IDE**. 

You can start from here: [ESP32 Dual Core](https://github.com/SensorsIot/ESP32-Dual-Core/blob/master/ESP32_Two_LED_Asynchron/ESP32_Two_LED_Asynchron.ino)

## Software

### MQTT

In this project too, the **MQTT** is implemented as it is expected to have multiple devices across one project. Each node has their unique *Identifier* which later will be used by the backend to process and distinguish the data. 

**mosquito** is selected as the *Broker* and will sit on either the local network or a private network established for our devices only.

### Node-Red
**Node-Red** is acting here as the data parser. It parses and logs all received MQTT messages across the platform. Also, the first line of notification system can be implemented here so very critical events can be identified and necessary alerts be sent to the ops/maintainers.

### InfluxDB
All data are stored in InfluxDB. I found InfluxDB reliable, light and practical.

### Grafana
And, the final part for the first stage is the Grafana that takes care of visual presentation of the sensor data in real-time

# Next
In terms of the software, the FEA model still needs to be developed, for the visualization, based on my experience, Unity 3D will be the choice.

For the hardware, I will be using the Bosch sensor!

