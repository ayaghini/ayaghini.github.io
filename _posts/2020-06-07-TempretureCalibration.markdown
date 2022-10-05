---
layout: post
title:  "#18 Accurate Temperature Measurement; Calibration, Calibration, and Calibration"
date:   2020-06-07 12:42:05 -0700
categories: IoT
tags: [DIY, Temperature Calibration, Dallas DS18B20, Arduino]
---
![Temp Calibrator](/assets/img/18Calibrator.JPEG)

# Intro
This is a well-known fact that even the most precise sensor cannot deliver an accurate reading unless it has been well calibrated. 

In normal environment even one- or two-degree difference in reading can make a difference. I have come to the realization that now well monitored home cannot be managed properly (temperature wise) until I calibrate my network of sensors. 

Had someone had access to a lab with pre-calibrated sensors would make the process for them extremely easy (and no pain, no fun they say!), in my case I decided to build a dedicated device for any future needed calibration.

# The Setup
As simple as it can be, an Arduino pro mini, a Dallas DS18B20 and a 7-segment LED to show the temperature! 

I picked the Dallas DS18B20 because it covers a good temperature range from -45-degree c up to 125-degree c, it already came with IP68 casing and a good length cable. 

# The Method
Two-point calibration seems to be the easiest and most accessible one. Triple-point bath for the close to 0-degree c and boiling water for the 100-degree c. Of course, you need to check those points properly considering your altitude.  


