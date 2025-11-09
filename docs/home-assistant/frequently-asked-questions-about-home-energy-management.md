---
title: Frequently Asked Questions about home energy management - Home Assistant
description: Home Energy Management is a vast topic and not everything might be clear. This page tries to clarify a couple of things.
source_url: https://www.home-assistant.io/docs/energy/faq
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:07:02.598Z
---

## Energy vs Power

It’s a common mistake to take Power as an Energy value, but the two are not alike.

[Energy](https://en.wikipedia.org/wiki/Energy) is a quantitative measurement of what it takes to produce work (e.g. heat water) while [Power](https://en.wikipedia.org/wiki/Electric_power) measures the speed at which energy is transferred.

Electrical Power is measured in Watts (W) and Electrical Energy is measured in kiloWatt-hour (kWh).

Think of this in a parallel to speed and distance: Power is the speed you are going and Energy is the distance driven.

Therefore Energy (kiloWatt-hour) is not an average of the Power you are consuming over a given period of time (the unit of the average power would be Watt or kiloWatt again). Energy is the integral (mathematical operation) of the Power function.

This difference is very important as you need to use the proper entities in our Energy dashboard.

## Creating an Energy Sensor out of a Power Sensor

Since in Home Assistant, we don’t deal with Power functions but with samples of the power being used, we can’t do the integral (mathematical operation) directly and get the true amount of energy consumed/produced.

That said, if you can sample Power values fast enough (every few seconds) you can reliably measure energy transferred through mathematic approximations called [Riemann Sum](https://en.wikipedia.org/wiki/Riemann_sum). Home Assistant provides this mathematical operation through the [integration](https://www.home-assistant.io/integrations/integration/#energy).

## Split consumption by tariffs

If you are using a 3rd party device (e.g. not reading directly from your utility meter device or from the utility provider cloud service) you need HA to split your energy measurements into 2 (or more) tariffs, in order to track these energy consumptions separately.

To accomplish such, you can use the [utility\_meter integration](https://www.home-assistant.io/integrations/utility_meter/). With this integration, you define as many tariffs as required (in accordance with your utility provider contract) and HA will be able to differentiate energy consumptions in each of the tariffs. Please note that each utility provider has its own time schedules for peak and off-peak and you are required to create an automation that switches the utility\_meter entity from one tariff to the other.

## The energy dashboard is not visible

If you do not see the Energy dashboard in the sidebar, make sure you have not removed [`default_config:`](https://www.home-assistant.io/integrations/default_config/) from your `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/). If you have, you will need to add the `energy:` integration manually.

## Troubleshooting missing entities

### Condition

You are trying to add a sensor to the energy dashboard, but it does not appear in the selection list.

### Resolution

To find out why the sensor is not showing, check the following points:

- The sensor must have the appropriate attributes. Check your entity attributes in [**Developer Tools** \> **States**](https://my.home-assistant.io/redirect/developer_states) to confirm the following:


  - `device_class` must be `energy` for electricity grid, solar, or battery categories. It must be `gas` for gas, or `water` for water.
  - `state_class` must be `total` or `total_increasing`.
  - The sensor must have an appropriate `unit_of_measurement`. See the help text for each category to see which units are accepted. Units containing an exponent must match superscript characters exactly as defined, e.g. `m³` is accepted, `m3` is not.

If any of the attributes are not correct, please open an issue against the integration that provides your sensor, or if you are developing custom template sensors, make sure the templates have the correct settings.

- The entity must be a `sensor`. If you are trying to add something from another domain (for example an `input_number`), then you must first create a template sensor from it.

- The entity must not have any statistics errors. Go to [**Developer Tools** \> **Statistics**](https://my.home-assistant.io/redirect/developer_statistics) to check your specific entity. If your unit has a listed issue here, you must fix the issue before it can be added to the dashboard.


#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/energy/faq.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fenergy%2Ffaq%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fenergy%2Ffaq%2F%22&in=body "View given feedback for this page")
