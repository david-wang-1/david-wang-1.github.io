---
layout: post
title: 'Ghost Mouse'
---

Technical Review Presentation <a href="https://drive.google.com/a/seas.upenn.edu/uc?authuser=0&id=0B9FFDZDZvlAzb3lqbkVWR2tmQ0U&export=download">download</a>.

Ghost Mouse is a device that transforms any flat surface into an invisible mouse/touchpad. With Ghost Mouse, users could control their computer/cell phone over Bluetooth by swiping and tapping on a nearby desk or coffee table. It functions by projecting a plane of infrared light onto the surface and using an infrared camera to detect finger position. Firmware for the product was developed on a NXP microcontroller in C and C++, to filter, synthesize, and process raw camera data into mouse movements and clicks. 

{% include image.html url="https://github.com/david-wang-1/ghost-mouse" image="projects/proj-1/mouse1.jpg" %}


GhostMouse was inspired by <a href="http://www.amazon.com/AGS-Projection-Bluetooth-Keyboard-Smartphone/dp/B00RP59MC0/">these</a> poorly rated "laser keyboards", which claimed to allow users to type on their desk as if it were a keyboard. In practise, they suffer from poor error rejection and slow typing speed. Using these products as inspiration, we  worked by projecting a plane of infrared light onto the surface and uses a infrared camera sensor to detect user fingertip positions. As the user interacts with the surface, we collect data on the displacement in fingertip positions and process it into real-time cursor responses seen on the paired PC/Android device. A multitude of different filtering approaches are used to remove signal jitter, as well as signal artifacts caused by errant user behavior. The Bluetooth HID mouse protocols are handled by an Bluefruit EZ-Key HID controller.

Our biggest challenges while building Ghost Mouse can be separated into 2 main categories: data collection and data processing. Physically collecting data on the position of user fingertips was one of the largest obstacles we faced during the developmental process. Our product utilizes an infrared camera from Nintendo's Wiimote to track infrared hotspots; our initial attempts to use the camera to track fingertips illuminated with a line laser failed due to a lack of availability of appropriate 940nm line lasers (the sensor we used is primarily sensitive to 940nm wavelengths). Our testing with 980nm and 808nm lasers showed that our sensor was not sensitive enough to those wavelengths to reliably detect fingertips. We had to pivot towards the use of infrared LEDs, which, while significantly less collimated, were easy to acquire in 940nm format. With the use of LEDs to illuminate our fingertips, we found that the camera could accurately isolate user finger positions.

{% include image.html url="https://github.com/david-wang-1/ghost-mouse" image="projects/proj-1/mouse2.jpg" %}

Once we had this data, we faced another significant obstacle in the process of processing the raw sensor data into a desirable user response. A significant amount of filtering and processing was implemented to reduce the drift, jitter, and jumpiness of the raw camera data. The most challenging signal artifact we had to address were the "spikes" caused by Z-Axis gestures. Z-Axis gestures are cases where the user lifts/places their finger on the interactive surface; due to the angled orientation of our camera sensor, Z-Axis gestures cause significant and unintentional "spikes" in the position data read by our camera. Our signal processing algorithm attempts to recognize intentional user Z-Axis gestures and actively removes unintentional mouse gestures that they would otherwise cause.




