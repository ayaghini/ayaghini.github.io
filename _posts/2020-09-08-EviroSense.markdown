---
layout: post
title:  "#2 EnviroSense, Let's care about the air!"
date:   2020-09-08 12:42:05 -0700
categories: IoT
---

# EnviroSense, an STM 32 Base Environmental Monitoring System

I started working on this project back when I was in Edmonton. There was couple of attemts failed because of complexities involved. After COVID-19 I was able to save couple of hours every day not forcing to commute to work which helped me finish this project.

The system measures following parameters:
1. Temperature
2. Humidity
3. Barometer presure


## Sensors
### BME 280
BME 280 is a well-known sensor from Bosch. It measures **Temerature, Humidity, and Barometer presure**. 

Use this page to learn more: 
[BME280 Guide](http://cactus.io/hookups/sensors/barometric/bme280/hookup-arduino-to-bme280-barometric-pressure-sensor)

NOTE: the I2C address is: 0x76

SCK pin to the I2C clock SCL pin on your Arduino. On an UNO & '328 based Arduino, this is also known as A5
SDI pin to the I2C data SDA pin on your Arduino. On an UNO & '328 based Arduino, this is also known as A4
It’s both 3.3 and 5 but I am using 3.3

you can also have a look at this web site:
[MySensors BME 280](https://forum.mysensors.org/topic/3816/bme280-temp-humidity-pressure-sensor/31)

### MIC-NOISE
I started the project with one of those cheap microphones.

First soldering the mic:
[How to find the polarity of a microphone](http://www.learningaboutelectronics.com/Articles/How-to-determine-the-polarities-of-a-microphone)

Sparkfun has good tutorial on how to read from mic breakout borads: 
[Sample code to read from amp](https://learn.sparkfun.com/tutorials/electret-mic-breakout-board-hookup-guide?_ga=2.169232168.860848578.1582503910-1289872436.1523318089)

The next logical question I needed to answer was: **Update: how to translate from sound to noise?**

A useful post to answer the question:
[Sound level meter](https://blog.yavilevich.com/2016/08/arduino-sound-level-meter-and-spectrum-analyzer/)

Plotting the analogue pin output shows small variations in the pin output due sound, that could be related to the mic amplifier, so I chenged my amplifier!

### MIC-MAX9814

This is the module I am using: 
[MAX9814 with Auto Gain Control](https://www.adafruit.com/product/1713)

It works, now lets move to STM 32:

For STM I am using Analogue pin (PA1) and this is the code:
```

const int sampleWindow = 200; // Sample window width in mS (250 mS = 4Hz)
#define AmpMax (4096 / 2)

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  long soundLevelAvg = 0;
  for (int i = 0; i <= 10; i++)
  {
    unsigned long start = millis(); // Start of sample window
    int numberOfSamples = 0;

    long soundVolMax = 0;
    // collect data for 200 miliseconds
    while (millis() - start < sampleWindow)
    {
      int k = analogRead(PA1);
      int amp = abs(k - AmpMax);
      soundVolMax = max(soundVolMax, amp);
      numberOfSamples += 1;
    }

    // convert from 0 to 100

    soundVolMax = 100 * soundVolMax / AmpMax;
    soundLevelAvg = soundLevelAvg + soundVolMax;
  }
  soundLevelAvg /= 10;
   Serial.println(" Amp: Max: " + String(soundLevelAvg));
}

```
### MH-Z19B CO2 sensor
From the sensor manual: 

*MH-Z19B NDIR infrared gas module is a common type, small size sensor, using non-dispersive infrared (NDIR) principle to detect the existence of CO 2 in the air, with good selectivity, non-oxygen dependent and long life. Built-in temperature compensation; and it has UART output and PWM output.*

[MH-Z19B manual](https://www.winsen-sensor.com/d/files/MH-Z19B.pdf)

[Arduino Library](https://github.com/WifWaf/MH-Z19)

[An example code using the sensor](https://github.com/Sasul/Arduino-CO2-Meter)

**Please be noted that the sensor needs 5v to operate properly**

### PMS7003 pm2.5

The PMS7003 is a particle matter counter capable of detecting particulates in the range of 0.3 to 10 microns. It provides PM1.0 (0.3-1.0um), PM2.5 (1.0-2.5um), and PM10 (2.5-10.0um).

A very good point to start: 
[PMS7003 Arduino Library](https://github.com/jmstriegel/Plantower_PMS7003)

I ended up using the **PMS.h** library as it puts the sensor into sleep. The sensor has a limitted life.


A mysensor code [needs to be checked as it is for Arduino]: 
[MySensors PMS7003](https://github.com/mysensors/MySensorsArduinoExamples/blob/master/examples/PMS-7003%20dust%20sensor)

## The Brain: STM32F103C8T6 AKA BluePill

As the Arduino  nano and pro only have 1 UART and my air quality sensors both require UART, I am switching to the STM.

A good starting point: [STM32 starting guide](https://circuitdigest.com/microcontroller-projects/getting-started-with-stm32-development-board-stm32f103c8-using-arduino-ide
)
