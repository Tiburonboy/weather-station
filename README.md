# weather-station
I started working on the weather station again.  The old weather station is described [here](https://af6ea.blogspot.com/2016/02/arduino-pressure-humidity-temperature.html).  It had a number of problems.  Primarily, the SparkFun WiFi library code for the Ardunio would not maintain a connection to the server.  This was back in 2018 when I was working on version 1 of my weather station.  Not knowing much about WiFi and not being particularity interested in doing a deep dive into the code, I did however do some research and found that someone had re-written the SparkFun WiFi code, documenting the deficiencies and fixed a number of issues.  I found it discouraging that Sparkfun would release code in such a poor state.  They should have at least included a warning that the code was incomplete.  

In the summer of 2020, I was motivated to get my weather station working and powered up the Ardunio stack.  I forgot that I had bypassed the voltage regulator on the Sparkfun Red board, so when I applied 9V to the power jack, I smoked the board.  Luckily, only the Ardunio Red board was damaged.  Version 2 of the weather station now uses a PIC16F18857 microcontroller installed on my break out board.  The boards are no longer stacked on the Ardunio headers, but are wired together by discrete wires.  

![Test Image 1](P1200320_croped.png)  
The LCD, WiFi shield, PIC16F18857 and TEPT4400 light sensor are mounted inside on the lid of the enclosure.   

![Test Image 1](P1200331_croped.png)  
The LCD, WiFi shield, PIC16F18857 and TEPT4400 light sensor are mounted inside on the lid of the enclosure.   

## Schematic of the weather station wiring
![Test Image 2](Schematic_Weather_v2_2020-10-22_07-31-23.png)  
The schematic was drawn using easyEDA, the link is [here](https://easyeda.com/editor#id=|017257c0cde345f2abf3dac7ea6eeea2|1e0ec5df3e4c47318fbd02b9b1d24101).


## Digital Relative Humidity sensor with Temperature output, HTU21D
The HTU21D digital humidity sensors is a dedicated humidity and temperature sensor.  It has a typical accuracy of ±2% with an operating range that's optimized from 5% to 95% RH. Operation outside this range is still possible - just the accuracy might drop a bit. The temperature output has an accuracy of ±1°C from -30~90°C. 

## Ambient Light Sensor ALS-PT19
The ALS-PT19-315C/L177/TR8 is a low cost ambient light sensor, consisting of phototransistor in miniature SMD.  The collector is connected to 3.3 volts and the emitter is pulled down to ground with a 10K resistor.  The data sheet is a little confusing, but the emitter current varies from 5 to 200 uA over a LUX of 0 to 1000.  ADC read back from the sensor varies from 10 to 400.  For a dark room the ADC value is 1.    

TEMT4400 ambient light sensor
TEPT4400 ambient light sensor is a silicon NPN epitaxial planar phototransistor in a T-1 package. It is sensitive to visible light much like the human eye and has peak sensitivity at 570 nm.

## Precision Altimeter, MPL3115A2
The MPL3115A2 employs a MEMS pressure sensor with an I2C interface to provide accurate Pressure/Altitude and Temperature data. The sensor outputs are digitized by a high resolution 24-bit ADC.  The sensor die is sensitive to light exposure. Direct light exposure through the port hole can lead to varied accuracy of pressure measurement. Avoid such exposure to the port
during normal operation.

## 8 character by 2 line LCD display, LCD0821
The LCD0821 is designed as the display unit for an associated controller.  The LCD0821 provides a simple command structure to allow text and bar graphs to be displayed on the screen. Text fonts are built in, and use standard ASCII mapping. Provision is made for up to 8 user-defined characters.  The screen is back lite for low-light situations. Back lighting may be turned on or off under program control. Contrast is adjustable to compensate for differing lighting conditions and viewing angles.

## Testing

![Test Image 1](P1200254.png)
Testing of the weather station.  Components are temporarily mounted in a cardboard box.  On the left side is the 8 by 2 LCD and below is the weather shield. The real time clock is mounted under the weather shield.  In the center is the PIC16F18857 microcontroller break out board and to the right of it is the WiFi shield.  

