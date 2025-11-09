---
title: Integrating your solar panels - Home Assistant
description: Learn how to add information about your solar panels to Home Assistant home energy management.
source_url: https://www.home-assistant.io/docs/energy/solar-panels
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:00:22.586Z
---

Gain insight into your energy production by integrating your solar panels into Home Assistant.

If you also set up [the Solar Forecast integration](https://www.home-assistant.io/integrations/forecast_solar), you will be able to see expected solar production and automate based on planned production.

![Graphic showing energy flowing from the solar panels to Home Assistant and back to the grid.](https://www.home-assistant.io/images/docs/energy/solar.png)

## Hardware

Home Assistant will need to know the amount of energy that is being produced. This can be done in various ways.

### Using a CT clamp sensor

Current transformer (CT) clamp sensors measure your energy usage by looking at the current passing through an electrical wire. This makes it possible to calculate the energy usage. In Home Assistant we have support for off-the-shelf CT clamp sensors or you can build your own.

- The off-the-shelf solution that we advise is the [Shelly EM](https://www.shelly.com/products/shelly-em-50a-clamp-1?tracking=A7FsiPIfUWsFpnfKHa8SRyUYLXjr2hPq). The device has a local API, updates are pushed to Home Assistant and it has a high quality [integration](https://www.home-assistant.io/integrations/shelly/).
- You can build your own using ESPHome’s [CT Clamp Current sensor](https://esphome.io/components/sensor/ct_clamp.html) or energy meter sensors like the [ATM90E32](https://esphome.io/components/sensor/atm90e32.html). For the DIY route, check out [this video by digiblur](https://www.youtube.com/watch?v=n2XZzciz0s4) to get started.
- Using a Raspberry Pi, you can use a CT clamp HAT from LeChacal called [RPICT hats](https://lechacal.com/docs/RPICT/Raspberrypi_Current_and_Temperature_Sensor_Adaptor/). They can be stacked to expand the number of lines to monitor. They also provide Active, Apparent, and Reactive power and power factor for single-phase and three-phase installations. They integrate with Home Assistant using MQTT.

_Attention! Installing CT clamp sensor devices requires opening your electrical cabinet. This work should be done by someone familiar with electrical wiring and may require a licensed professional in some regions. Your qualified installer will know how to do this._

_Disclaimer: Some links in this section are affiliate links._

### Connecting to your inverter

Some solar inverters have APIs that can be read by Home Assistant.

[Energy integrations](https://www.home-assistant.io/integrations/#energy)

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/energy/solar-panels.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fenergy%2Fsolar-panels%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fenergy%2Fsolar-panels%2F%22&in=body "View given feedback for this page")
