---
layout: post
title:  "#19 Computer Vision and AI with Accessible Hardware for Makers, Intel RealSense"
date:   2020-06-17 12:42:05 -0700
categories: IoT
tags: [Intel RealSense, Stereo Depth Camera, IMU, Arduino]
---
![Temp Calibrator](/assets/img/19Intelrealsense.jpg)

# Quick Note
There is no argue that vision is the key player when it comes to having computer intelligence taking over tasks. Vision not only enables the AI to understand the surrounding environment, but also can gives algorithms such as **[SLAM](https://en.wikipedia.org/wiki/Simultaneous_localization_and_mapping)** the required inputs to feed the machine its own location and position within that world.


To achieve the goal there are couple of key components such as RGB camera, IMU and in absence of a LiDAR sensor a second camera to enable the **[Stereophotogrammetry](https://www.sciencedirect.com/topics/medicine-and-dentistry/stereophotogrammetry)**.

I am currently experimenting with the [Intel RealSense](https://www.intelrealsense.com/stereo-depth/). The out of the box SDK is powerful and provides raw output of all sensors as well as a processed 3D map of generated point cloud.


