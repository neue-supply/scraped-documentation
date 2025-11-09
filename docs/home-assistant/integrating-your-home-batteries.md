---
title: Integrating your home batteries - Home Assistant
description: Learn how to add information about your home batteries to Home Assistant home energy management.
source_url: https://www.home-assistant.io/docs/energy/battery
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:05:55.441Z
---

A home battery allows homes to store energy when you are either producing more solar power than you’re using, or store energy from the grid if the current price is low.

Home Assistant allows you to track how much energy flows from/to your battery.

## Hardware

Home Assistant will need to know the amount of energy flowing from/to your batteries. This data can be tracked in various ways.

### Provided by the battery

Some battery vendors have an API to integrate the data into your Home Assistant instance. An example is [Tesla Powerwall](https://www.home-assistant.io/integrations/powerwall/).

### Using a CT clamp sensor

Current transformer (CT) clamp sensors measure your energy usage by looking at the current passing through an electrical wire. This makes it possible to calculate the energy usage. In Home Assistant we have support for off-the-shelf CT clamp sensors or you can build your own.

- The off-the-shelf solution that we advise is the [Shelly EM](https://www.shelly.com/products/shelly-em-50a-clamp-1?tracking=A7FsiPIfUWsFpnfKHa8SRyUYLXjr2hPq). The device has a local API, updates are pushed to Home Assistant and it has a high quality [integration](https://www.home-assistant.io/integrations/shelly/).
- You can build your own using ESPHome’s [CT Clamp Current sensor](https://esphome.io/components/sensor/ct_clamp.html) or energy meter sensors like the [ATM90E32](https://esphome.io/components/sensor/atm90e32.html). For the DIY route, check out [this video by digiblur](https://www.youtube.com/watch?v=n2XZzciz0s4) to get started.
- Using a Raspberry Pi, you can use a CT clamp HAT from LeChacal called [RPICT hats](https://lechacal.com/docs/RPICT/Raspberrypi_Current_and_Temperature_Sensor_Adaptor/). They can be stacked to expand the number of lines to monitor. They also provide Active, Apparent, and Reactive power and power factor for single-phase and three-phase installations. They integrate with Home Assistant using MQTT.

_Attention! Installing CT clamp sensor devices requires opening your electrical cabinet. This work should be done by someone familiar with electrical wiring and may require a licensed professional in some regions. Your qualified installer will know how to do this._

_Disclaimer: Some links in this section are affiliate links._

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/energy/battery.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fenergy%2Fbattery%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fenergy%2Fbattery%2F%22&in=body "View given feedback for this page")
