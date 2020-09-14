---
layout: post
title:  "#8 LoRa SX1262 Long Range Portable Tracker"
date:   2020-04-4 12:42:05 -0700
categories: IoT
---
![Portable Tracker](/assets/img/8portable.png)
# Intro
In post #7 I briefly introduced LoRa. The first logical project for me was to try and see how long I can reach using these promising modules! So, I started working on this Project.

The end platform comprises of a **base-station** and as many **portable nodes**. The base station uses the **NRF24 mesh network** I talked about in post #4 to log received communications and its activity through a **Node-Red** follow into an **influxDB** timeseries data base.   

At first, I started with the **Arduino pro mini 3.3 8HZ, ATMEGA 168**.

As it does not have a usb port, it needs to press the reset button on the board before uploading a sketch. At the end by adding other necessary libraries, the board did not have enough memory and I had to switch to **ATMEGA 238** for both base station and portable device.

For the first trial, the system comprises of two devices: a base-station located at my house balcony listening for incoming messages and a portable device with GPS sending its location and listening for any message. 

# Base-Station
Based on *Stuart Robinson* library, [LoRa tracker](https://github.com/StuartsProjects/SX12XX-LoRa), I decided to create one device and use my home fixed lat and log and have the device transmit it every X second. I will use the second portable device as a receiver. The main reason was to not have two devices need GPS.

Later I added the receiving feature to the transmitter. I grabbed the receiver code from Stuart and added it to my code. [right now, it is receiving messages from LoRa GPS tracker transmitter, I need to generalize it so it will receive any message)

I added **MQTT** and **MySensors** capability to my station so basically it would be a LoRa base station, transmitting my location and receiving any messages it receives.

MySensors is added successfully, in order to do so [having two **SPI** devices] I needed to change the *reset and cs[nss]* pin of the LoRa library because NRF24 [the communication module] is using those.

The base station is connected through MQTT / MySensors via a NRF24 mesh network to my Node-Red backend that parses and logs all incoming traffic to my InfluxDB data centre and a Grafana web interface displays the information. It has a battery monitoring system which monitors and sends the battery level to the data base. It also sends all incoming traffic (i.e. GPS coordinates, RSSI and SNR) to the data base.

![Base Station](/assets/img/8base.png)

in order to install the station on my balcony, I am using a weather sealed enclosure.

![base station weather sealed enclosure](/assets/img/8baseEncolsure3.JPG)

Some corner cuts were necessary to fit everything into the box!

# Portable node
![Node](/assets/img/8node.png)


