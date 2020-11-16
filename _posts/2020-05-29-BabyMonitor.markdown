---
layout: post
title:  "#17 ESP32 CAM; DIY Baby Monitor with Night Vision, Motion Detection, and Live Stream"
date:   2020-05-29 12:42:05 -0700
categories: IoT
tags: [DIY, ESP32 CAM, Web Stream, IR-Camera, PIR Sensor]
---
![ESP32_cam_Baby_Monitor](/assets/img/17BabyMonitorESP32CAM.jpeg)

# Intro
It was the first time that our baby slept on their own and we were free next room that we realized we needed a "baby monitor". 

*"Challenge Accepted!"*

As a ***"maker"*** I had to finish building a working baby monitor before my wife could go to a store and buy one!

Quick search and I figured following functions are must:
- Night vision
- Live stream to a screen or mobile phone

I had couple of **ESP32-Cam** modules lying around so pretty confident I head to my lab.

## ESP32-Cam

Except lack of a native USB on-board, the module is easy to work with. Please read my post #11 on it. 

The only catch here is that in order to device to work at night and have a night vision, the camera **IR filter** needs to be removed. A quick internet search shows that it is possible. The camera I have is different and I end up improving it myself. In nutshell you need to unscrew the lens cap, push the lens out from its holder and remove the filter. The filter is the most front element.

## IR-LEDs and PIR Motion Detector

Cameras need some source of light in dark. ***Infra-Red (IR)*** while is invisible to our light can be a good source of light for cameras at night. I had couple of **5mm IR LEDs** in my LED assortment box. I am planning to use a 3.3v source and hence needed to use a 39-ohm resistor to limit the current.

The next was to figure out the way to only turn them on when needed (i.e. when the little one started to move, wake up etc.). A natural choice is **"PIR Motion Detector"** sensor and have it turn LEDs on when it detects a movement. I picked a 2N 222 transistor and have the detection pin of the PIR sensor connected to it.

