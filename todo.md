# TODO list for the developers
List of things that need to be looked into, organized on topic.

## Motherboard
* Measure current consumption
* Redesign power supply (work-in-progress)
* Silkscreen (needs to be more comprehensive)
* Update documentation

## BME680
* Improve results concerning the air quality
* Hardware redesign (work-in-progress)

## Sound Level
* There is a ripple visible in the acoustic measurements originating from the wake up and sleep functionality of the motherboard. A small fluctuation of the supply voltage causes a visible spike in the measurement. The fluctuation is already smaller by removing Diodes 4 and 5, but then there is no possibility to use multiple supply voltages. If the wake up and sleep of the motherboard is more coordinated to not occur during a sound measurement, the problem can also be solved without altering the hardware.
* Silkscreen (needs to be more comprehensive)

## Buttons
* Check naming of the repo's

## Future addon boards
* battery module
* luminosity sensor
* actuator board e.g., LEDs, buzzer, etc.

## Configurator
* todo's for the configurator tool
* Make it possible to program the motherboard for a second time without the need of restarting the tool
* check .exe release
* Add extra functionality concerning the battery module
* Disable polling for buttons
* Incorporate "enable/disable data accumulation"

## Web application
* Support new message formats
* Add extra functionality concerning the battery module
* if more than x-time, no data is received in the databank, make the graph 0 for that time to make sure that when the measurements start again, no intersection line is drawn between the 2 points.
