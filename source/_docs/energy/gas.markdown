---
title: "Integrating your gas usage"
description: "Learn how to add information about your gas usage to Home Assistant home energy management."
---

Some homes are connected to gas. Gas is being used to heat water, cook and heat up the home.

Home Assistant allows you to track your gas usage and easily compare it against your energy usage for the same period of time.

## Hardware

Home Assistant will need to know the amount of gas that is being consumed.

### Connect to your meter

The best way to get this data is directly from your gas meter that sits between your house and the grid. In certain countries these meters contain standardized ways of reading out the information locally or provide this information via the electricity meter.

#### Connect using a P1 port

The P1 port is a standardized port on electricity meters in the Netherlands, Belgium and Luxembourg which also provides gas consumption information. A P1 reader can connect to this port and receive real-time information.

We have worked with creator [Marcel Zuidwijk](https://www.zuidwijk.com) to develop [SlimmeLezer+](https://www.zuidwijk.com/product/slimmelezer-plus/). It's an affordable P1 reader powered by [ESPHome](https://esphome.io) that will seamlessly integrate this information in Home Assistant. It is being sold on [his website](https://www.zuidwijk.com/product/slimmelezer-plus/) and the firmware is open source [on GitHub](https://github.com/zuidwijk/dsmr).

![Photo of SlimmeLezer attached to a smart electricity meter](/images/docs/energy/slimmelezer.jpg)

#### Read the Gas Meter using an AI-on-the-edge-device

[AI-on-the-edge-device](https://github.com/jomjol/AI-on-the-edge-device) is a project running on an ESP32-CAM and can be fully integrated into Home Assistant using the Home Assistant Discovery Functionality of MQTT. It digitalizes your gas/water/electricity meter display and provides its data in various ways. 

![Photo of the AI-on-the-edge-device Workflow](/images/docs/energy/ai-on-the-edge-device.jpg)

#### Read the Gas Meter using a magnetometer

[Diaphragm Gas Meters](https://en.wikipedia.org/wiki/Gas_meter#Diaphragm/bellows_meters) are very common and their movement can typically be measured by a magnetometer. The [QMC5883L](https://esphome.io/components/sensor/qmc5883l.html) is inexpensive and has an integration for ESPHome. There are many posts on the forums of users collecting their gas consumption this way, such as [this one](https://community.home-assistant.io/t/water-gas-meter-monitoring-via-magnetometer-sine-wave-to-pulse-issue/245904). Because the diaphragm typically goes through multiple cycles for each 'count' on the meter, higher resolution than other methods is possible.

![Photo of a typical residential gas meter]((https://en.wikipedia.org/wiki/File:Gas_meter.JPG))
