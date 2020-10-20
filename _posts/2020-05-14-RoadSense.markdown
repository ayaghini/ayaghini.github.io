---
layout: post
title:  "#15 Real-time Road Condition Monitoring; RoadSense v1.0"
date:   2020-05-14 12:42:05 -0700
categories: IoT Mining
tags: [Road Condition Monitoring, LoRa SX1262, E22M900, ESP32, IMU, MPU9255, Arduino, whole body vibration]
---
![RoadSense v1.0](/assets/img/15roadSenseBoard.PNG)

# Intro
Roads play a critical role in any industry either involves goods and material handling or access to remote locations is necessary for their function. 

Hence, monitoring their condition becomes more important as not only the production relies on them, but also equipment health could be affected to a great extent by the condition of roads.

In mining, the heavy weight of trucks collectively with the weather condition causes roads condition to deteriorate very quickly, and early detection of those could help reduce the road and also equipment maintenance costs.

**RoadSense** is the newest member of my **IoT** based family of connected sensors' family. It comprises of a 9-degree of freedom IMU sensor from *Bosch* and a 55-Channel **GPS** from *u-Blox*. For remote locations with limited wi-fi coverage, I am adding the **LoRa SX1262** with 100k+ range. 


