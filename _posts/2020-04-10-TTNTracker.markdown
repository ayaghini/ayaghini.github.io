---
layout: post
title:  "#10 TTN and Arduino MKR WAN 1310"
date:   2020-04-10 12:42:05 -0700
categories: IoT
---

# Intro
**[The Things Network (TTN)](https://www.thethingsnetwork.org)** is a global open **LoRaWAN®** network relying on the maker community members and their contribution to provide a wide coverage for LoRa enabled IoT devices. 

It's sad to see the TTN community is not very active in Canada (There are less than 5 Gateways in Greater Vancouver today!). I am planning to build my own GW and provide North vancouver with the service, as always money is the issue!

The **[Arduino MKR WAN 1310](https://store.arduino.cc/usa/mkr-wan-1310)** is a *SAMD21* based board that has the *Murata CMWX1ZZABZ LoRa®* module. It has **2BM** of SPI flash  which gives the board ***OTA Update*** compatibility and includes a battery charger.

# My Take
This project aims at using the **TTN** capabilities and built the prototype for a **LoRa** based **GPS tracker** that logs the coordinates into the TTN network and those could be used to track assets virtually any where around the world. 