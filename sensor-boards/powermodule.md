---
title: Power module
parent: Sensor Boards
has_toc: true
nav_order: 5
layout: default
---

The power module is designed to make the system last longer by adding a battery combined with a solar panel to the system. The system can therefore be powered off the grid and without a power bank. The power module can also measure the incident light by means of a light dependent resistor to get an idea of how well the solar panel is performing. If ever the battery gets drained, there is still a possibility to charge the battery by the micro USB port.

The three main components on the printed circuit board of the power module are: the BQ25570, the BQ24040 and the PIC16F18446. The latter chip is a microcontroller that is responsible to control the the whole module. It connects and disconnects different parts of the circuit and measures the occurring voltages. By means of I2C, the chip communicates with the motherboard for further processing.

The BQ25570 chip is designed to harvest energy from incident light. It is a nano power boost charger and buck converter that is able to efficiently extract microwatts to milliwatts of power generated from photovoltaic cells. The connected solar panel provides energy to the chip which charges the battery subsequently. The BQ25570 has an integrated buck converter which provides energy to the whole system. This converter is disabled when the battery voltage reaches approximately 2.4 V to protect the battery from degrading in those undervoltage conditions. When the battery gets charged up to 2.8 V, the buck converter becomes active again and the system can restart performing measurements.

The BQ24040 is a USB charger IC that converts the supplied 5V to the proper battery voltage. The LED’s indicate whether the battery is charging or has finished charging. 
To make the power module energy efficient, some parts of the circuit can be disable. For instance the circuit to measure the battery voltage is enabled only during measurement. The analog to digital converter of the PIC16F18446 samples the occurring voltage, performs some calculations and communicates the result to the motherboard. 

Besides the battery voltage, the amount of light is measured by means of a light dependent resistor. This value can be used as an indication of the incident light.

