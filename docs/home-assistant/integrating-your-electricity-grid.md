---
title: Integrating your electricity grid - Home Assistant
description: Learn how to add information about your electricity grid to Home Assistant home energy management.
source_url: https://www.home-assistant.io/docs/energy/electricity-grid
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:07:42.012Z
---

Energy management is all about knowing how much energy you’re consuming, where it’s coming from and where it’s going.

Almost all houses are connected to the electricity grid which provides the energy your home will need. The energy usage is being tracked by your energy meter and is billed to you by your energy provider. Energy prices can differ based on a schedule or change according to market price.

![Graphic showing energy flowing from the grid to Home Assistant.](https://www.home-assistant.io/images/docs/energy/grid.png)

## Tariffs

It has become popular for energy utilities to split the price of energy based on time of the day; this is done in order to incentivise consumers to shift their power needs towards times where the grid has lower loads. These periods of time are commonly referred to as Peak and Off Peak, exactly because they match periods of time where everyone is consuming energy (Peak) and periods of time where the energy is abundant but no one is using it (Off Peak). Therefore Peak energy is more expensive then Off Peak energy.

If you want to split energy usage into multiple tariffs, [read this](https://www.home-assistant.io/docs/energy/faq/#split-consumption-by-tariffs).

## Hardware

Home Assistant will need to know the amount of energy flowing through your meter. This data can be tracked in various ways.

### Connect to your meter

The best way to get this data is directly from your electricity meter that sits between your house and the grid. In certain countries these meters contain standardized ways of reading out the information locally.

#### Connect using a P1 port

The P1 port is a standardized port in the Netherlands, Belgium and Luxembourg. A P1 reader can connect to this port and receive real-time information.

We have worked with creator [Marcel Zuidwijk](https://www.zuidwijk.com/) to develop [SlimmeLezer+](https://www.zuidwijk.com/product/slimmelezer-plus/). It’s an affordable P1 reader powered by [ESPHome](https://esphome.io/) that will seamlessly integrate this information in Home Assistant. It is being sold on [his website](https://www.zuidwijk.com/product/slimmelezer-plus/) and the firmware is open source [on GitHub](https://github.com/zuidwijk/dsmr).

![Photo of SlimmeLezer attached to a smart electricity meter](https://www.home-assistant.io/images/docs/energy/slimmelezer.jpg)

#### Connect via Zigbee Energy Profile

The Zigbee Energy Profile is a wireless energy standard to provide real-time information about electricity usage. This standard is available in some meters in the US, UK and Australia. This is not “normal” Zigbee as implemented by Home Assistant but requires special certified hardware.

We are not currently aware of a device that implements this which supports a local API and is compatible with Home Assistant.

#### Reading the meter via a pulse counter

Many meters, including older ones, have an LED that will flash whenever energy passes through it. For example, each flash is a 1/1000th kWh. By monitoring the time between flashes it’s possible to determine the energy consumption.

We have developed [Home Assistant Glow](https://github.com/klaasnicolaas/home-assistant-glow), an open source solution powered by ESPHome’s [pulse meter sensor](https://esphome.io/components/sensor/pulse_meter.html). You put it on top of the activity LED of your electricity meter and it will bring your consumption into Home Assistant.

![Photo of Home Assistant Glow attached to an electricity meter](https://www.home-assistant.io/images/docs/energy/home-assistant-glow.jpg)

#### Reading the meter via a IEC62056-21

The IEC62056-21 is a common protocol not only for electric meters. It uses an infrared port to read data.
[Aquaticus](https://github.com/aquaticus) has created an [ESPHome component](https://community.home-assistant.io/t/new-iec62056-21-component/555236) for reading this data. [PiggyMeter](https://aquaticus.info/meter.html) is a complete project that allows easy installation.
![Photo of PiggyMeter attached to an electricity meter](https://aquaticus.info/_images/meter_and_probe.png)

#### Using (Smart Message Language) interface

In countries like Germany, SML (Smart Message Language) is used typically. ESPHome’s [SML (Smart Message Language)](https://esphome.io/components/sml.html) is one way to integrate it. If you prefer to integrate it via MQTT, [sml2mqtt](https://github.com/spacemanspiff2007/sml2mqtt) is another open source option.

#### Read the meter using an AI-on-the-edge-device

[AI-on-the-edge-device](https://github.com/jomjol/AI-on-the-edge-device) is a project running on an ESP32-CAM and can be fully integrated into Home Assistant using the Home Assistant discovery functionality of MQTT. It digitalizes your gas/water/electricity meter display and provides its data in various ways.

![Photo of the AI-on-the-edge-device Workflow](https://www.home-assistant.io/images/docs/energy/ai-on-the-edge-device.jpg)

### Using a CT clamp sensor

Current transformer (CT) clamp sensors measure your energy usage by looking at the current passing through an electrical wire. This makes it possible to calculate the energy usage. In Home Assistant we have support for off-the-shelf CT clamp sensors or you can build your own.

- The off-the-shelf solution that we advise is the [Shelly EM](https://www.shelly.com/products/shelly-em-50a-clamp-1?tracking=A7FsiPIfUWsFpnfKHa8SRyUYLXjr2hPq). The device has a local API, updates are pushed to Home Assistant and it has a high quality [integration](https://www.home-assistant.io/integrations/shelly/).
- You can build your own using ESPHome’s [CT Clamp Current sensor](https://esphome.io/components/sensor/ct_clamp.html) or energy meter sensors like the [ATM90E32](https://esphome.io/components/sensor/atm90e32.html). For the DIY route, check out [this video by digiblur](https://www.youtube.com/watch?v=n2XZzciz0s4) to get started.
- Using a Raspberry Pi, you can use a CT clamp HAT from LeChacal called [RPICT hats](https://lechacal.com/docs/RPICT/Raspberrypi_Current_and_Temperature_Sensor_Adaptor/). They can be stacked to expand the number of lines to monitor. They also provide Active, Apparent, and Reactive power and power factor for single-phase and three-phase installations. They integrate with Home Assistant using MQTT.

_Attention! Installing CT clamp sensor devices requires opening your electrical cabinet. This work should be done by someone familiar with electrical wiring and may require a licensed professional in some regions. Your qualified installer will know how to do this._

_Disclaimer: Some links in this section are affiliate links._

### Data provided by your energy provider

Some energy providers will provide you real-time information about your usage and have this data integrated into Home Assistant.

### Manual integration

If you manually integrate your sensors, for example, using the [MQTT](https://www.home-assistant.io/integrations/mqtt) or [Template](https://www.home-assistant.io/integrations/template) integrations: Make sure you set and provide the `device_class`, `state_class`, and `unit_of_measurement` for those sensors.

### Troubleshooting

If you are unable to select your energy sensor in the grid consumption drop-down, make sure that its value is being recorded in the Recorder settings.

[Energy integrations](https://www.home-assistant.io/integrations/#energy)

_Disclaimer: Some links on this page are affiliate links helping support the Home Assistant project._

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/energy/electricity-grid.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fenergy%2Felectricity-grid%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fenergy%2Felectricity-grid%2F%22&in=body "View given feedback for this page")
