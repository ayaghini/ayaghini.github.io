---
layout: post
title:  "#8 LoRa Base Station and Portable Tracker"
date:   2020-04-3 12:42:05 -0700
categories: IoT
---

# Intro
In post #7 I briefly introduced LoRa. The first logical project for me was to try and see how long I can reach using these promising modules! So I started working on this Project.

The end platform comprises of a **base-station** and as many **portable nodes**. The base station uses the **NRF24 mesh network** I talked about in post #4 to log recived comminications and its activity through a **Node-Red** follow into an **influxDB** timeseries data base.   