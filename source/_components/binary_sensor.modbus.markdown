---
layout: page
title: "Modbus Binary Sensor"
description: "Instructions on how to set up Modbus binary sensors within Home Assistant."
date: 2016-09-13 12:02
sidebar: true
comments: false
sharing: true
footer: true
logo: modbus.png
ha_category: Binary Sensor
ha_release: 0.28
ha_iot_class: Local Push
---

The `modbus` binary sensor allows you to gather data from [Modbus](http://www.modbus.org/) coils.

## {% linkable_title Configuration %}

To use your Modbus binary sensors in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
binary_sensor:
  - platform: modbus
    coils:
      - name: Sensor1
        hub: hub1
        slave: 1
        coil: 100
      - name: Sensor2
        hub: hub1
        slave: 1
        coil: 110
```

{% configuration %}
coils:
  description: The array contains a list of coils to read from.
  required: true
  type: [map, list]
  keys:
    name:
      description: Name of the sensor.
      required: true
      type: string
    hub:
      description: The name of the hub.
      required: false
      default: default
      type: string
    slave:
      description: The number of the slave (Optional for TCP and UDP Modbus).
      required: true
      type: integer
    coil:
      description: Coil number.
      required: true
      type: integer
{% endconfiguration %}

It's possible to change the default 30 seconds scan interval for the sensor updates as shown in the [Platform options](/docs/configuration/platform_options/#scan-interval) documentation.

## {% linkable_title Full example %}

Example a sensor with a 10 seconds scan interval:

```yaml
binary_sensor:
  - platform: modbus
    scan_interval: 10
    coils:
      - name: Sensor1
        hub: hub1
        slave: 1
        coil: 100
      - name: Sensor2
        hub: hub1
        slave: 1
        coil: 110
```
