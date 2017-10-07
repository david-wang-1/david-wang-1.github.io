---
layout: post
title: 'Maximum Inertia'
---

This project was a Top 3 Hardware Prize winner at YaleHack 2016.

Maximum Inertia is a distance measuring tool - utilizing a newly released Maxim Cortex development board and an Android device, it monitored the absolute distance between them, emulating a virtual measuring tape. Both devices' Inertial Measurement Units were leveraged to collect raw acceleration and rotation data. I implemented and integrated numerous real time signal processing algorithms such as low pass filters, Kalman filtering, and quaternion vector rotation in C to process the raw data into usable formats. I also worked on the communication protocols between the Android application and the Maxim microcontroller.

{% include image.html url="http://www.gratisography.com" image="projects/proj-5/thumb.jpg" %}
