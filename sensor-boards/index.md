---
title: Sensor Boards
has_toc: true
has_children: true
nav_order: 3
layout: default
---


The functionalities and possible configurations for each sensor is defined in the [description files](https://github.com/dramco-iwast/sensor-description-files).

It is structured as:

```yaml
name: "Sensor name"

# How to parse the raw byte payload coming from TTN
parse-payload: !!js/function >
            function f(value) {
            error("Not Implemented yet")
            }();

# Information regarding the sensor board (Dutch and English)
info:
  nl: |-
    Deze sensor bevat vier verschillende functionaliteiten.
    Het kan de temperatuur, druk, Luchtkwaliteit en vochtigheid opmeten.
  en: |-
    This sensor has four functionalities.
    It can measure the temperature, air quality, pressure en humidity.

# Each sensor has at least one metric which can be measured
# For each metric we define the following:

sensor-metric:
  - unit: "°C"
    quantity:
      nl: "Temperatuur"
      en: "Temperature"
    info:
      nl: "Meet de temperatuur in °C."
      en: "Measure the temperature in °C."
    size: 2  # in bytes
    # machine interpretation of the raw byte payload
    type: "uint16"
    # number of decimals after comma
    precision: 2  
    # two functions converting the data between machine and human readible values
    # For instance: 15.2°C (human) can be converted to 15.2*100=152 in order to have one digit after comma
    convert-to-machine: !!js/function >
            function f(value) {}
            return value + 273.15 ;
            }();
    convert-to-human: !!js/function >
            function f(value) {
            return value - 273.15;
            }();
    # metric specific configuration
    config:
      - threshold: true
        threshold-max: 58
        threshold-min: -40
        minumum-polling-interval: 10  # in seconds
  - unit: "-"
    quantity:
      en: "Air Quality Indication"
      nl: "Luchtkwaliteitsindicatie"
    info:
      nl: |-
          Meet hoe vervuild de lucht rondom de module is.
          Kijk of er een risico is voor de gezondheid.
      en: |-
          Measure how polluted the air is.
          Evaluate if there are any health risks possible.
    size: 2  # in bytes
    type: "uint16"
    precision: 0  # number of decimals after comma
    convert-to-machine: !!js/function > #  no convertion needed
          function f(value) {}
          return value;
          }();
    convert-to-human: !!js/function > #  no convertion needed
          function f(value) {
          return value;
          }();
    config:
      - threshold: true
        threshold-max: 500
        threshold-min: 0
        minumum-polling-interval: 10  # in seconds
```

