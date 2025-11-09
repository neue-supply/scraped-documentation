---
title: Understanding automations - Home Assistant
description: A breakdown of what an automation consists of.
source_url: https://www.home-assistant.io/docs/automation/basics
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:09:42.869Z
---

All automationsAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home. [\[Learn more\]](https://www.home-assistant.io/docs/automation/) are made up of a triggerA trigger is a set of values or conditions of a platform that are defined to cause an automation to run. [\[Learn more\]](https://www.home-assistant.io/docs/automation/trigger/) and an actionActions are used in several places in Home Assistant. As part of a script or automation, actions define what is going to happen once a trigger is activated. In scripts, an action is called _sequence_. [\[Learn more\]](https://www.home-assistant.io/docs/automation/action/). Optionally combined with a conditionConditions are an optional part of an automation that will prevent an action from firing if they are not met. [\[Learn more\]](https://www.home-assistant.io/docs/scripts/conditions/). Take for example the automation:

> When Paulus arrives home and it is after sunset: Turn the lights on in the living room.

We can break up this automation into the following three parts:

```text
(trigger)    When Paulus arrives home
(condition)  and it is after sunset:
(action)     Turn the lights on in the living room
```

Text

Copy

The first part is the [trigger](https://www.home-assistant.io/docs/automation/trigger/) of the automation. Triggers describe eventsEvery time something happens in Home Assistant, an event is fired. There are different types of events, such as state change events, when an action was triggered, or the time changed. All entities produce state change events. Every time a state changes, a state change event is produced. Events can be used to trigger automations or scripts. For example, you can trigger an automation when a light is turned on, then a speaker turns on in that room. Events can also be used to trigger actions in the frontend. For example, you can trigger an action when a button is pressed. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/events/) that should trigger the automation. In this case, it is a person arriving home, which can be observed in Home Assistant using devicesA device is a model representing a physical or logical unit that contains entities./sensorsSensors return information about a thing, for instance the level of water in a tank. [\[Learn more\]](https://www.home-assistant.io/integrations/sensor/) by observing the state of Paulus changing from `not_home` to `home`.

The second part is the [condition](https://www.home-assistant.io/docs/automation/condition/). Conditions are optional tests that can limit an automation to only work in your specific use cases. A condition will test against the current state of the system. This includes the current time, devices, people and other things like the sun. In this case, we only want to act when the sun has set.

The third part is the [action](https://www.home-assistant.io/docs/automation/action/), which will be performed when an automation is triggered and all conditions are met. For example, it can turn a light on, set the temperature on your thermostat or activate a scene.

Note

The difference between a trigger and a condition can be confusing as they are very similar.

Triggers require an event to happen for the conditions to be evaluated using current state information.

Event: Arrive home

Condition: After Sunset?

Action: Turn lights on

## Exploring the internal state

Automations interact directly with the internal state of Home Assistant, so you’ll need to familiarize yourself with it. Home Assistant exposes its current state via the developer tools. These are available at the bottom of the sidebar in the frontend. **[Developer Tools > States](https://my.home-assistant.io/redirect/developer_states)** will show all currently available states. An entity can be anything. A light, a switch, a person and even the sun. A state consists of the following parts:

| Name | Description | Example |
| --- | --- | --- |
| Entity ID | Unique identifier for the entity. | `light.living_room` |
| State | The current state of the device. | `off` |
| Attributes | Extra data related to the device and/or current state. | `brightness` |

State changes can be used as the source of triggers and the current state can be used in conditions.

To explore the available _actions_ open the [**Developer tools** \> **Actions**](https://my.home-assistant.io/redirect/developer_services). _Actions_ allow changing anything. For example, turn on a light, run a script, or enable a scene. Each _action_ has a domain and a name. For example, the _action_ [`light.turn_on`](https://my.home-assistant.io/redirect/developer_call_service?service=light.turn_on) is capable of turning on any light in your system. Parameters can be passed to an _action_ to indicate, for example, which device to activate or which color to use.

## Creating automations

Now that you’ve got a sneak peek of what is possible, it’s time to get your feet wet and create your first automation.

### [Using the automation editor »](https://www.home-assistant.io/docs/automation/editor/)

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/automation/basics.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fautomation%2Fbasics%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fautomation%2Fbasics%2F%22&in=body "View given feedback for this page")
