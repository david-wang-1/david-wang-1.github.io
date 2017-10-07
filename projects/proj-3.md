---
layout: post
title: 'Rugged Data Collection Device'
---

<i>Note: I am currently under NDA with <a href="http://bresslergroup.com" target="_blank">BresslerGroup</a> about the exact nature of this project, so many specifics/details have been omitted.</i>

The parameters for this project were to create a mechanically durable device to collect positional data. I served as one of the primary developers for this project for both the hardware and software, though the majority of my time was dedicated to software development. On the hardware side, I worked on the schematic design and PCB layout in Altium Designer for the board. 

Some interesting design constraints that I faced:

1. The device would be subjected to very strong impacts in an outdoor environment regularly, necessitating a completely sealed design and a complete potting of the board within the assembly. This meant that the device would have to communicate and charge entirely wirelessly. To address this, we selected a microcontroller module with a Bluetooth Low Energy chip antenna onboard, and added a wireless charging management IC alongside a charging coil.

2. The client was very interested in accurate measurements of the rotation of the device. As a result, a gyroscope had to be placed in the exact center of the PCB, which was made to be round and designed to fit into a spherical mechanical assembly. Furthermore, a cylindrical lithium ion cell was sourced to be stacked on top of the board to maintain a consistent center of gravity in the device.

3. The client had multiple desired use cases for the device, necessitating consistent data capture across several magnitudes of acceleration and rotation values. To address this, complementing a gyroscope and magnetometer, we incorporated two different accelerometers that had configurable sensitivity ranges, to cover acceleration values between 1 and 4000g's, that could be configured based on the use case.

On the software side, I worked on the firmware in C to read sensor data and export it from the device via Bluetooth Low Energy over a GATT server. A primitive 'round-robin' type scheduler was implemented, where data from each sensor was read and buffered for writing to external memory as it became available. Commands were received by the device over BLE to either begin data collection, stop data collection, or write data out over BLE. 

I was solely responsible for the development of an Android application to interface with this device. It was responsible for taking user commands (e.g. start taking impact data) and catalyzing the appropriate action on the device, and also receiving/saving data collected by the device to an external file on the Android device. The data transfer protocol we used, similar to primitive TCP packet sending, essentially consisted of the following steps on repeat:

1. Device writes a packet of data, notifies the phone that data is available.

2. Phone receives notification that data is available, reads data and sends back an acknowledge.

In case the transmission was ever lost or corrupted, the device would catch the lack of acknowledge and resend the dropped packets in question. 


{% include image.html image="projects/proj-3/thumb.jpg" %}
