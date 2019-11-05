---
layout: default
title: General
nav_order: 1
---

These pages contain the technical documentation of the Dramco IoT with a Soft Touch (IWAST) project.


An application, running locally on a computer, is used to configure the mother board. More specifically, the mother board notifies the client application of the connected sensors. Based on the configuration file of each sensor --hosted online-- the client application allows to configure the update frequency of each sensor and corresponding parameters. 


```
Client App <--> Motherboard  <--> sensor
                             <--> sensor
                             <--> sensor
```


## Terminology


| Sensor | The sensor denotes the whole sensor board. |
| Metric | Each sensor can measure different metrics, e.g. temperature and humidity. |
| Motherboard | All sensors are connected to the motherboard. More info [here](motherboard/). |
| Client App  | Configures the motherboard and sensors connected to it. |
| Web App  | . |
