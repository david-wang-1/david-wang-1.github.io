---
layout: post
title: 'Sencity'
---

{% include image.html url="http://www.bresslergroup.com/blog/sencity-lora-smart-city-iot-solution/" image="projects/proj-2/sencity3.jpg" %}

I worked on Sencity as an intern with <a href="http://bresslergroup.com" target="_blank">BresslerGroup</a>. Sencity was a project to create a network of distributed IoT nodes and interpret their data into a user-friendly representation of crowd traffic at different tourist hotspots across Philadelphia. Each Sencity node was equipped with a wide of array of sensors, such as time of flight, ambient light, sound, GPS, and temperature, as well as a LoRaWAN (Long Range Wide Area Network) radio. LoRaWAN is a new technology and protocol utilizing sub-GHz frequencies to transmit data at long ranges while having a low power budget. The tradeoff made is a very poor network bandwidth, on the order of a couple of kilobits per second. This technology was perfect for Sencity, as it allowed us to deploy the devices across the entire city of Philadelphia with small battery packs, and receive periodic data updates from a single central access point. 

{% include image.html url="http://www.bresslergroup.com/blog/sencity-lora-smart-city-iot-solution/" image="projects/proj-2/sencity1.jpg" %}

I worked on the board debug and the firmware development processes for the device. On the board debug side, I utilized oscilloscopes, function generators, and logic analyzers to debug board signals on communication buses, and performed manual rework to fix bugs(e.g. reflow to replace components, adding solder bridges, cutting traces). For firmware development, I was responsible for developing drivers for the onboard sensors, and devising an algorithm to parse raw sensor data into a "crowd traffic" metric. Developing with the IAR IDE/compiler for an STM32 microcontroller, I wrote driver packages in C to abstract raw register read/writes into usable interfaces for initalizing, configuring, and reading data from the sensors. Following the completion of the drivers, I developed the algorithm to synthesize raw data (in this case, from the time of flight sensor and microphone) into a traffic metric. 

The algorithm focused on analyzing data received from the time-of-flight sensor - a powerful device that reported the absolute distance of the closest object up to 2 meters away. By maintaining a moving window of past data, I looked for patterns in the distance that matched the signature of a person walking past the device. Mounted next to the sidewalk on a wall - or on the side of the bicycle - the device was able to accurately keep a running tally of the number of people walking past it. The devices were deployed on the side of bicycles to sidewalks in busy neighborhoods of Philadelphia, and reported data to update a website displaying current traffic levels at each site.

{% include image.html url="http://www.bresslergroup.com/blog/sencity-lora-smart-city-iot-solution/" image="projects/proj-2/sencity2.jpg" %}

