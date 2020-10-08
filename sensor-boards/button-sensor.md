---
title: Button Sensor
parent: Sensor Boards
has_toc: true
nav_order: 3
layout: default
---

The button sensor hosts four buttons. When a button is pressed, all buttons will briefly light up 
(0.5 s) and the pressed button will keep glowing for about 1.2 seconds.

When either button is pressed, all other buttons become unresponsive until the current press has
been handled.

The button-sensor works completely interrupt-based and is always in sleep. Sleep current is below
1 µA and typically around 350 nA. On a button press, the device becomes active for 1.7 seconds with
an average current consumption of 7.3 mA.

See description file [here](https://github.com/dramco-iwast/sensor-description-files/blob/master/button-sensor.yaml).