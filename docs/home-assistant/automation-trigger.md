---
title: Automation Trigger - Home Assistant
description: All the different ways how automations can be triggered.
source_url: https://www.home-assistant.io/docs/automation/trigger/
source_domain: www.home-assistant.io
scraped_at: 2025-11-10T00:11:18.709Z
---

[ ](https://www.home-assistant.io/) [ 2025.11.1 ](https://www.home-assistant.io/blog/2025/11/05/release-202511/ "Latest version 2025.11.1 released November  7, 2025")
  * [Getting started](https://www.home-assistant.io/installation/)
  * [Documentation ](https://www.home-assistant.io/docs/)
    * [](https://www.home-assistant.io/installation/)
    * [](https://www.home-assistant.io/docs/automation/)
    * [](https://www.home-assistant.io/dashboards/)
    * [](https://www.home-assistant.io/voice_control/)
    * [](https://www.home-assistant.io/docs/organizing/)
    * [](https://www.home-assistant.io/docs/energy/)
    * [](https://www.home-assistant.io/docs/configuration/)
  * [Integrations](https://www.home-assistant.io/integrations/)
  * [Blog](https://www.home-assistant.io/blog/)
  * [Need help?](https://www.home-assistant.io/help/)
  * Search`K`


  * [Trigger ID](https://www.home-assistant.io/docs/automation/trigger/#trigger-id)
    * [Video tutorial](https://www.home-assistant.io/docs/automation/trigger/#video-tutorial)
  * [Trigger variables](https://www.home-assistant.io/docs/automation/trigger/#trigger-variables)
  * [Event trigger](https://www.home-assistant.io/docs/automation/trigger/#event-trigger)
  * [Home Assistant trigger](https://www.home-assistant.io/docs/automation/trigger/#home-assistant-trigger)
  * [MQTT trigger](https://www.home-assistant.io/docs/automation/trigger/#mqtt-trigger)
  * [Numeric state trigger](https://www.home-assistant.io/docs/automation/trigger/#numeric-state-trigger)
  * [State trigger](https://www.home-assistant.io/docs/automation/trigger/#state-trigger)
    * [Examples](https://www.home-assistant.io/docs/automation/trigger/#examples)
    * [Triggering on attribute changes](https://www.home-assistant.io/docs/automation/trigger/#triggering-on-attribute-changes)
    * [Holding a state or attribute](https://www.home-assistant.io/docs/automation/trigger/#holding-a-state-or-attribute)
  * [Sun trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-trigger)
    * [Sunset / Sunrise trigger](https://www.home-assistant.io/docs/automation/trigger/#sunset--sunrise-trigger)
    * [Sun elevation trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-elevation-trigger)
  * [Tag trigger](https://www.home-assistant.io/docs/automation/trigger/#tag-trigger)
  * [Template trigger](https://www.home-assistant.io/docs/automation/trigger/#template-trigger)
  * [Time trigger](https://www.home-assistant.io/docs/automation/trigger/#time-trigger)
    * [Time string](https://www.home-assistant.io/docs/automation/trigger/#time-string)
    * [Input datetime](https://www.home-assistant.io/docs/automation/trigger/#input-datetime)
    * [Sensors of datetime device class](https://www.home-assistant.io/docs/automation/trigger/#sensors-of-datetime-device-class)
    * [Sensors of datetime device class with offsets](https://www.home-assistant.io/docs/automation/trigger/#sensors-of-datetime-device-class-with-offsets)
    * [Multiple times](https://www.home-assistant.io/docs/automation/trigger/#multiple-times)
    * [Limited templates](https://www.home-assistant.io/docs/automation/trigger/#limited-templates)
    * [Weekday filtering](https://www.home-assistant.io/docs/automation/trigger/#weekday-filtering)
  * [Time pattern trigger](https://www.home-assistant.io/docs/automation/trigger/#time-pattern-trigger)
  * [Persistent notification trigger](https://www.home-assistant.io/docs/automation/trigger/#persistent-notification-trigger)
  * [Webhook trigger](https://www.home-assistant.io/docs/automation/trigger/#webhook-trigger)
    * [Webhook data](https://www.home-assistant.io/docs/automation/trigger/#webhook-data)
    * [Webhook security](https://www.home-assistant.io/docs/automation/trigger/#webhook-security)
  * [Zone trigger](https://www.home-assistant.io/docs/automation/trigger/#zone-trigger)
  * [Geolocation trigger](https://www.home-assistant.io/docs/automation/trigger/#geolocation-trigger)
  * [Device triggers](https://www.home-assistant.io/docs/automation/trigger/#device-triggers)
  * [Calendar trigger](https://www.home-assistant.io/docs/automation/trigger/#calendar-trigger)
  * [Sentence trigger](https://www.home-assistant.io/docs/automation/trigger/#sentence-trigger)
    * [Related topic](https://www.home-assistant.io/docs/automation/trigger/#related-topic)
    * [Sentence wildcards](https://www.home-assistant.io/docs/automation/trigger/#sentence-wildcards)
  * [Multiple triggers](https://www.home-assistant.io/docs/automation/trigger/#multiple-triggers)
  * [Multiple entity IDs for the same trigger](https://www.home-assistant.io/docs/automation/trigger/#multiple-entity-ids-for-the-same-trigger)
  * [Disabling a trigger](https://www.home-assistant.io/docs/automation/trigger/#disabling-a-trigger)
  * [Merging lists of triggers](https://www.home-assistant.io/docs/automation/trigger/#merging-lists-of-triggers)
  * [Related topics](https://www.home-assistant.io/docs/automation/trigger/#related-topics)


[Home](https://www.home-assistant.io/) ▸ [Documentation](https://www.home-assistant.io/docs/) ▸ [Automation](https://www.home-assistant.io/docs/automation/) ▸ 
#  Automation Trigger 
Triggers are what starts the processing of an automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/) rule. When _any_ of the automation’s triggers becomes true (trigger _fires_), Home Assistant will validate the [conditions](https://www.home-assistant.io/docs/automation/condition/), if any, and call the [action](https://www.home-assistant.io/docs/automation/action/).
An automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/) can be triggered by an eventEvery time something happens in Home Assistant, an event is fired. There are different types of events, such as state change events, when an action was triggered, or the time changed. All entities produce state change events. Every time a state changes, a state change event is produced. Events can be used to trigger automations or scripts. For example, you can trigger an automation when a light is turned on, then a speaker turns on in that room. Events can also be used to trigger actions in the frontend. For example, you can trigger an action when a button is pressed.[ [Learn more]](https://www.home-assistant.io/docs/configuration/events/), a certain entityAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) stateThe state holds the information of interest of an entity, for example, if a light is on or off. Each entity has exactly one state and the state only holds one value at a time. However, entities can store attributes related to that state such as brightness, color, or a unit of measurement.[ [Learn more]](https://www.home-assistant.io/docs/configuration/state_object/), at a given time, and more. These can be specified directly or more flexible via templates. It is also possible to specify multiple triggers for one automation.
  * [Trigger ID](https://www.home-assistant.io/docs/automation/trigger/#trigger-id)
  * [Trigger variables](https://www.home-assistant.io/docs/automation/trigger/#trigger-variables)
  * [Event trigger](https://www.home-assistant.io/docs/automation/trigger/#event-trigger)
  * [Home Assistant trigger](https://www.home-assistant.io/docs/automation/trigger/#home-assistant-trigger)
  * [MQTT trigger](https://www.home-assistant.io/docs/automation/trigger/#mqtt-trigger)
  * [Numeric state trigger](https://www.home-assistant.io/docs/automation/trigger/#numeric-state-trigger)
  * [State trigger](https://www.home-assistant.io/docs/automation/trigger/#state-trigger)
  * [Sun trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-trigger)
  * [Tag trigger](https://www.home-assistant.io/docs/automation/trigger/#tag-trigger)
  * [Template trigger](https://www.home-assistant.io/docs/automation/trigger/#template-trigger)
  * [Time trigger](https://www.home-assistant.io/docs/automation/trigger/#time-trigger)
  * [Time pattern trigger](https://www.home-assistant.io/docs/automation/trigger/#time-pattern-trigger)
  * [Persistent notification trigger](https://www.home-assistant.io/docs/automation/trigger/#persistent-notification-trigger)
  * [Webhook trigger](https://www.home-assistant.io/docs/automation/trigger/#webhook-trigger)
  * [Zone trigger](https://www.home-assistant.io/docs/automation/trigger/#zone-trigger)
  * [Geolocation trigger](https://www.home-assistant.io/docs/automation/trigger/#geolocation-trigger)
  * [Device triggers](https://www.home-assistant.io/docs/automation/trigger/#device-triggers)
  * [Calendar trigger](https://www.home-assistant.io/docs/automation/trigger/#calendar-trigger)
  * [Sentence trigger](https://www.home-assistant.io/docs/automation/trigger/#sentence-trigger)
  * [Multiple triggers](https://www.home-assistant.io/docs/automation/trigger/#multiple-triggers)
  * [Multiple Entity IDs for the same Trigger](https://www.home-assistant.io/docs/automation/trigger/#multiple-entity-ids-for-the-same-trigger)
  * [Disabling a trigger](https://www.home-assistant.io/docs/automation/trigger/#disabling-a-trigger)
  * [Merging lists of triggers](https://www.home-assistant.io/docs/automation/trigger/#merging-lists-of-triggers)


## Trigger ID [](https://www.home-assistant.io/docs/automation/trigger/#trigger-id)
All triggers can be assigned an optional `id`. If the ID is omitted, it will instead be set to the index of the trigger. The `id` can be referenced from [trigger conditions and actions](https://www.home-assistant.io/docs/scripts/conditions/#trigger-condition). The `id` does not have to be unique for each trigger, and it can be used to group similar triggers for use later in the automation (i.e., several triggers of different types that should all turn some entity on).
### Video tutorial [](https://www.home-assistant.io/docs/automation/trigger/#video-tutorial)
This video tutorial explains how trigger IDs work.
```
automation:
  triggers:
    - trigger: event
      event_type: "MY_CUSTOM_EVENT"
      id: "custom_event"
    - trigger: mqtt
      topic: "living_room/switch/ac"
      id: "ac_on"
    - trigger: state  # This trigger will be assigned id="2"
      entity_id:
        - device_tracker.paulus
        - device_tracker.anne_therese
      to: "home"
```

YAML
Copy
## Trigger variables [](https://www.home-assistant.io/docs/automation/trigger/#trigger-variables)
There are two different types of variables available for triggers. Both work like [script level variables](https://www.home-assistant.io/integrations/script/#variables).
The first variant allows you to define variables that will be set when the trigger fires. The variables will be able to use templates and have access to [the `trigger` variable](https://www.home-assistant.io/docs/automation/templating#available-trigger-data).
The second variant is setting variables that are available when attaching a trigger when the trigger can contain templated values. These are defined using the `trigger_variables` key at an automation level. These variables can only contain [limited templates](https://www.home-assistant.io/docs/configuration/templating/#limited-templates). The triggers will not re-apply if the value of the template changes. Trigger variables are a feature meant to support using blueprint inputs in triggers.
```
automation:
  trigger_variables:
    my_event: example_event
  triggers:
    - trigger: event
      # Able to use `trigger_variables`
      event_type: "{{ my_event }}"
      # These variables are evaluated and set when this trigger is triggered
      variables:
        name: "{{ trigger.event.data.name }}"
```

YAML
Copy
## Event trigger [](https://www.home-assistant.io/docs/automation/trigger/#event-trigger)
An event trigger fires when an [event](https://www.home-assistant.io/docs/configuration/events/) is being received. Events are the raw building blocks of Home Assistant. You can match events on just the event name or also require specific event data or context to be present.
Events can be fired by integrations or via the API. There is no limitation to the types. A list of built-in events can be found [here](https://www.home-assistant.io/docs/configuration/events/).
```
automation:
  triggers:
    - trigger: event
      event_type: "MY_CUSTOM_EVENT"
      # optional
      event_data:
        mood: happy
      context:
        user_id:
        # any of these will match
          - "MY_USER_ID"
          - "ANOTHER_USER_ID"
```

YAML
Copy
It is also possible to listen for multiple events at once. This is useful for event that contain no, or similar, data and contexts.
```
automation:
  triggers:
    - trigger: event
      event_type:
        - automation_reloaded
        - scene_reloaded
```

YAML
Copy
It’s also possible to use [limited templates](https://www.home-assistant.io/docs/configuration/templating/#limited-templates) in the `event_type`, `event_data` and `context` options.
The `event_type`, `event_data` and `context` templates are only evaluated when setting up the trigger, they will not be reevaluated for every event.
```
automation:
  trigger_variables:
    sub_event: ABC
    node: ac
    value: on
  triggers:
    - trigger: event
      event_type: "{{ 'MY_CUSTOM_EVENT_' ~ sub_event }}"
```

YAML
Copy
## Home Assistant trigger [](https://www.home-assistant.io/docs/automation/trigger/#home-assistant-trigger)
Fires when Home Assistant starts up or shuts down.
```
automation:
  triggers:
    - trigger: homeassistant
      # Event can also be 'shutdown'
      event: start
```

YAML
Copy
Automations triggered by the `shutdown` event have 20 seconds to run, after which they are stopped to continue with the shutdown.
## MQTT trigger [](https://www.home-assistant.io/docs/automation/trigger/#mqtt-trigger)
Fires when a specific message is received on given MQTT topic. Optionally can match on the payload being sent over the topic. The default payload encoding is ‘utf-8’. For images and other byte payloads use `encoding: ''` to disable payload decoding completely.
```
automation:
  triggers:
    - trigger: mqtt
      topic: "living_room/switch/ac"
      # Optional
      payload: "on"
      encoding: "utf-8"
```

YAML
Copy
The `payload` option can be combined with a `value_template` to process the message received on the given MQTT topic before matching it with the payload. The trigger in the example below will trigger only when the message received on `living_room/switch/ac` is valid JSON, with a key `state` which has the value `"on"`.
```
automation:
  triggers:
    - trigger: mqtt
      topic: "living_room/switch/ac"
      payload: "on"
      value_template: "{{ value_json.state }}"
```

YAML
Copy
It’s also possible to use [limited templates](https://www.home-assistant.io/docs/configuration/templating/#limited-templates) in the `topic` and `payload` options.
The `topic` and `payload` templates are only evaluated when setting up the trigger, they will not be re-evaluated for every incoming MQTT message.
```
automation:
  trigger_variables:
    room: "living_room"
    node: "ac"
    value: "on"
  triggers:
    - trigger: mqtt
      topic: "{{ room ~ '/switch/' ~ node}}"
      # Optional
      payload: "{{ 'state:' ~ value }}"
      encoding: "utf-8"
```

YAML
Copy
## Numeric state trigger [](https://www.home-assistant.io/docs/automation/trigger/#numeric-state-trigger)
Fires when the numeric value of an entity’s state (or attribute’s value if using the `attribute` property, or the calculated value if using the `value_template` property) **crosses** a given threshold (equal excluded). On state change of a specified entity, attempts to parse the state as a number and fires if the value is changing from above to below or from below to above the given threshold (equal excluded).
Crossing the threshold means that the trigger only fires if the state wasn’t previously within the threshold. If the current state of your entity is `50` and you set the threshold to `below: 75`, the trigger would not fire if the state changed to e.g. `49` or `72` because the threshold was never crossed. The state would first have to change to e.g. `76` and then to e.g. `74` for the trigger to fire.
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id: sensor.temperature
      # If given, will trigger when the value of the given attribute for the given entity changes..
      attribute: attribute_name
      # ..or alternatively, will trigger when the value given by this evaluated template changes.
      value_template: "{{ state.attributes.value - 5 }}"
      # At least one of the following required
      above: 17
      below: 25
      # If given, will trigger when the condition has been true for X time; you can also use days and milliseconds.
      for:
        hours: 1
        minutes: 10
        seconds: 5
```

YAML
Copy
Listing above and below together means the numeric_state has to be between the two values. In the example above, the trigger would fire a single time if a numeric_state goes into the 17.1-24.9 range (above 17 and below 25). It will only fire again, once it has left the defined range and enters it again.
When the `attribute` option is specified the trigger is compared to the given `attribute` instead of the state of the entity.
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id: climate.kitchen
      attribute: current_temperature
      above: 23
```

YAML
Copy
More dynamic and complex calculations can be done with `value_template`. The variable ‘state’ is the [state object](https://www.home-assistant.io/docs/configuration/state_object) of the entity specified by `entity_id`.
The state of the entity can be referenced like this:
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id: sensor.temperature
      value_template: "{{ state.state | float * 9 / 5 + 32 }}"
      above: 70
```

YAML
Copy
Attributes of the entity can be referenced like this:
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id: climate.kitchen
      value_template: "{{ state.attributes.current_temperature - state.attributes.temperature_set_point }}"
      above: 3
```

YAML
Copy
Number helpers (`input_number` entities), `number`, `sensor`, and `zone` entities that contain a numeric value, can be used in the `above` and `below` thresholds. However, the comparison will only be made when the entity specified in the trigger is updated. This would look like:
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id: sensor.outside_temperature
      # Other entity ids can be specified for above and/or below thresholds
      above: sensor.inside_temperature
```

YAML
Copy
The `for:` can also be specified as `HH:MM:SS` like this:
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id: sensor.temperature
      # At least one of the following required
      above: 17
      below: 25

      # If given, will trigger when condition has been for X time.
      for: "01:10:05"
```

YAML
Copy
You can also use templates in the `for` option.
```
automation:
  triggers:
    - trigger: numeric_state
      entity_id:
        - sensor.temperature_1
        - sensor.temperature_2
      above: 80
      for:
        minutes: "{{ states('input_number.high_temp_min')|int }}"
        seconds: "{{ states('input_number.high_temp_sec')|int }}"
  actions:
    - action: persistent_notification.create
      data:
        message: >
          {{ trigger.to_state.name }} too high for {{ trigger.for }}!
```

YAML
Copy
The `for` template(s) will be evaluated when an entity changes as specified.
Use of the `for` option will not survive Home Assistant restart or the reload of automations. During restart or reload, automations that were awaiting `for` the trigger to pass, are reset.
If for your use case this is undesired, you could consider using the automation to set an [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime) to the desired time and then use that [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime) as an automation trigger to perform the desired actions at the set time.
## State trigger [](https://www.home-assistant.io/docs/automation/trigger/#state-trigger)
In general, the state trigger fires when the state of any of given entities **changes**. The behavior is as follows:
  * If only the `entity_id` is given, the trigger fires for **all** state changes, even if only a state attribute changed.
  * If at least one of `from`, `to`, `not_from`, or `not_to` are given, the trigger fires on any matching state change, but not if only an attribute changed. 
    * To trigger on all state changes, but not on changed attributes, set at least one of `from`, `to`, `not_from`, or `not_to` to `null`.
  * Use of the `for` option doesn’t survive a Home Assistant restart or the reload of automations. 
    * During restart or reload, automations that were awaiting `for` the trigger to pass, are reset.
    * If for your use case this is undesired, you could consider using the automation to set an [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime) to the desired time and then use that [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime) as an automation trigger to perform the desired actions at the set time.


The values you see in your overview will often not be the same as the actual state of the entity. For instance, the overview may show `Connected` when the underlying entity is actually `on`. You should check the state of the entity by checking the states in the developer tool, under [**Developer Tools** > **States**](https://my.home-assistant.io/redirect/developer_states).
### Examples [](https://www.home-assistant.io/docs/automation/trigger/#examples)
This automation triggers if either Paulus or Anne-Therese are home for one minute.
```
automation:
  triggers:
    - trigger: state
      entity_id:
        - device_tracker.paulus
        - device_tracker.anne_therese
      # Optional
      from: "not_home"
      # Optional
      to: "home"
      # If given, will trigger when the condition has been true for X time; you can also use days and milliseconds.
      for:
        hours: 0
        minutes: 1
        seconds: 0
```

YAML
Copy
It’s possible to give a list of `from` states or `to` states:
```
automation:
  triggers:
    - trigger: state
      entity_id: vacuum.test
      from:
        - "cleaning"
        - "returning"
      to: "error"
```

YAML
Copy
If you want to trigger on all state changes, but not on attribute changes, you can `to` to `null` (this would also work by setting `from`, `not_from`, or `not_to` to `null`):
```
automation:
  triggers:
    - trigger: state
      entity_id: vacuum.test
      to:
```

YAML
Copy
If you want to trigger on all state changes _except_ specific ones, use `not_from` or `not_to` The `not_from` and `not_to` options are the counter parts of `from` and `to`. They can be used to trigger on state changes that are **not** the specified state.
```
automation:
  triggers:
    - trigger: state
      entity_id: vacuum.test
      not_from:
        - "unknown"
        - "unavailable"
      to: "on"
```

YAML
Copy
You cannot use `from` and `not_from` at the same time. The same applies to `to` and `not_to`.
### Triggering on attribute changes [](https://www.home-assistant.io/docs/automation/trigger/#triggering-on-attribute-changes)
When the `attribute` option is specified, the trigger only fires when the specified attribute **changes**. Changes to other attributes or state changes are ignored.
For example, this trigger only fires when the boiler has been heating for 10 minutes:
```
automation:
  triggers:
    - trigger: state
      entity_id: climate.living_room
      attribute: hvac_action
      to: "heating"
      for: "00:10:00"
```

YAML
Copy
This trigger fires whenever the boiler’s `hvac_action` attribute changes:
```
automation:
  triggers:
    - trigger: state
      entity_id: climate.living_room
      attribute: hvac_action
```

YAML
Copy
### Holding a state or attribute [](https://www.home-assistant.io/docs/automation/trigger/#holding-a-state-or-attribute)
You can use `for` to have the state trigger only fire if the state holds for some time.
This example fires, when the entity state changed to `"on"` and holds that state for 30 seconds:
```
automation:
  triggers:
    - trigger: state
      entity_id: light.office
      # Must stay "on" for 30 seconds
      to: "on"
      for: "00:00:30"
```

YAML
Copy
When holding a state, changes to attributes are ignored. Changes to attributes don’t cancel the hold time.
You can also fire the trigger when the state value changed from a specific state, but hasn’t returned to that state value for the specified time.
This can be useful, e.g., checking if a media player hasn’t turned “off” for the time specified, but doesn’t care about “playing” or “paused”.
```
automation:
  triggers:
    - trigger: state
      entity_id: media_player.kitchen
      # Not "off" for 30 minutes
      from: "off"
      for: "00:30:00"
```

YAML
Copy
Please note, that when using `from`, `to` and `for`, only the value of the `to` option is considered for the time specified.
In this example, the trigger fires if the state value of the entity remains the same for `for` the time specified, regardless of the current state value.
```
automation:
  triggers:
    - trigger: state
      entity_id: media_player.kitchen
      # The media player remained in its current state for 1 hour
      for: "01:00:00"
```

YAML
Copy
You can also use templates in the `for` option.
```
automation:
  triggers:
    - trigger: state
      entity_id:
        - device_tracker.paulus
        - device_tracker.anne_therese
      to: "home"
      for:
        minutes: "{{ states('input_number.lock_min')|int }}"
        seconds: "{{ states('input_number.lock_sec')|int }}"
  actions:
    - action: lock.lock
      target:
        entity_id: lock.my_place
```

YAML
Copy
The `for` template(s) will be evaluated when an entity changes as specified.
Use quotes around your values for `from` and `to` to avoid the YAML parser from interpreting values as booleans.
## Sun trigger [](https://www.home-assistant.io/docs/automation/trigger/#sun-trigger)
### Sunset / Sunrise trigger [](https://www.home-assistant.io/docs/automation/trigger/#sunset--sunrise-trigger)
Fires when the sun is setting or rising, i.e., when the sun elevation reaches 0°.
An optional time offset can be given to have it fire a set time before or after the sun event (e.g., 45 minutes before sunset). A negative value makes it fire before sunrise or sunset, a positive value afterwards. The offset needs to be specified in number of seconds, or in a hh:mm:ss format.
Since the duration of twilight is different throughout the year, it is recommended to use [sun elevation triggers](https://www.home-assistant.io/docs/automation/trigger/#sun-elevation-trigger) instead of `sunset` or `sunrise` with a time offset to trigger automations during dusk or dawn.
```
automation:
  triggers:
    - trigger: sun
      # Possible values: sunset, sunrise
      event: sunset
      # Optional time offset. This example will trigger 45 minutes before sunset.
      offset: "-00:45:00"
```

YAML
Copy
### Sun elevation trigger [](https://www.home-assistant.io/docs/automation/trigger/#sun-elevation-trigger)
Sometimes you may want more granular control over an automation than simply sunset or sunrise and specify an exact elevation of the sun. This can be used to layer automations to occur as the sun lowers on the horizon or even after it is below the horizon. This is also useful when the “sunset” event is not dark enough outside and you would like the automation to run later at a precise solar angle instead of the time offset such as turning on exterior lighting. For most automations intended to run during dusk or dawn, a number between 0° and -6° is suitable; -4° is used in this example:
```
automation:
  - alias: "Exterior Lighting on when dark outside"
    triggers:
      - trigger: numeric_state
        entity_id: sun.sun
        attribute: elevation
        # Can be a positive or negative number
        below: -4.0
    actions:
      - action: switch.turn_on
        target:
          entity_id: switch.exterior_lighting
```

YAML
Copy
If you want to get more precise, you can use this [solar calculator](https://gml.noaa.gov/grad/solcalc/), which will help you estimate what the solar elevation will be at any specific time. Then from this, you can select from the defined twilight numbers.
Although the actual amount of light depends on weather, topography and land cover, they are defined as:
  * Civil twilight: 0° > Solar angle > -6°
This is what is meant by twilight for the average person: Under clear weather conditions, civil twilight approximates the limit at which solar illumination suffices for the human eye to clearly distinguish terrestrial objects. Enough illumination renders artificial sources unnecessary for most outdoor activities.
  * Nautical twilight: -6° > Solar angle > -12°
  * Astronomical twilight: -12° > Solar angle > -18°


A very thorough explanation of this is available in the Wikipedia article about the [Twilight](https://en.wikipedia.org/wiki/Twilight).
## Tag trigger [](https://www.home-assistant.io/docs/automation/trigger/#tag-trigger)
Fires when a [tag](https://www.home-assistant.io/integrations/tag) is scanned. For example, a NFC tag is scanned using the Home Assistant Companion mobile application.
```
automation:
  triggers:
    - trigger: tag
      tag_id: A7-6B-90-5F
```

YAML
Copy
Additionally, you can also only trigger if a card is scanned by a specific device/scanner by setting the `device_id`:
```
automation:
  triggers:
    - trigger: tag
      tag_id: A7-6B-90-5F
      device_id: 0e19cd3cf2b311ea88f469a7512c307d
```

YAML
Copy
Or trigger on multiple possible devices for multiple tags:
```
automation:
  triggers:
    - trigger: tag
      tag_id:
        - "A7-6B-90-5F"
        - "A7-6B-15-AC"
      device_id:
        - 0e19cd3cf2b311ea88f469a7512c307d
        - d0609cb25f4a13922bb27d8f86e4c821
```

YAML
Copy
## Template trigger [](https://www.home-assistant.io/docs/automation/trigger/#template-trigger)
Template triggers work by evaluating a [template](https://www.home-assistant.io/docs/configuration/templating/) when any of the recognized entities change state. The trigger will fire if the state change caused the template to render ‘true’ (a non-zero number or any of the strings `true`, `yes`, `on`, `enable`) when it was previously ‘false’ (anything else).
This is achieved by having the template result in a true boolean expression (for example `{{ is_state('device_tracker.paulus', 'home') }}`) or by having the template render `true` (example below).
With template triggers you can also evaluate attribute changes by using is_state_attr (like `{{ is_state_attr('climate.living_room', 'away_mode', 'off') }}`)
```
automation:
  triggers:
    - trigger: template
      value_template: "{% if is_state('device_tracker.paulus', 'home') %}true{% endif %}"

      # If given, will trigger when template remains true for X time.
      for: "00:01:00"
```

YAML
Copy
You can also use templates in the `for` option.
```
automation:
  triggers:
    - trigger: template
      value_template: "{{ is_state('device_tracker.paulus', 'home') }}"
      for:
        minutes: "{{ states('input_number.minutes')|int(0) }}"
```

YAML
Copy
The `for` template(s) will be evaluated when the `value_template` becomes ‘true’.
Templates that do not contain an entity will be rendered once per minute.
Use of the `for` option will not survive Home Assistant restart or the reload of automations. During restart or reload, automations that were awaiting `for` the trigger to pass, are reset.
If for your use case this is undesired, you could consider using the automation to set an [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime) to the desired time and then use that [`input_datetime`](https://www.home-assistant.io/integrations/input_datetime) as an automation trigger to perform the desired actions at the set time.
## Time trigger [](https://www.home-assistant.io/docs/automation/trigger/#time-trigger)
The time trigger is configured to fire once a day at a specific time, or at a specific time on a specific date. There are three allowed formats:
### Time string [](https://www.home-assistant.io/docs/automation/trigger/#time-string)
A string that represents a time to fire on each day. Can be specified as `HH:MM` or `HH:MM:SS`. If the seconds are not specified, `:00` will be used.
```
automation:
  - triggers:
    - trigger: time
      # 24-hour time format. This trigger will fire at 3:32 PM
      at: "15:32:00"
```

YAML
Copy
### Input datetime [](https://www.home-assistant.io/docs/automation/trigger/#input-datetime)
The entity ID of an [input datetime](https://www.home-assistant.io/integrations/input_datetime/).
has_date | has_time | Description  
---|---|---  
`true` | `true` | Will fire at specified date & time.  
`true` | `false` | Will fire at midnight on specified date.  
`false` | `true` | Will fire once a day at specified time.  
```
automation:
  - triggers:
      - trigger: state
        entity_id: binary_sensor.motion
        to: "on"
    actions:
      - action: climate.turn_on
        target:
          entity_id: climate.office
      - action: input_datetime.set_datetime
        target:
          entity_id: input_datetime.turn_off_ac
        data:
          datetime: >
            {{ (now().timestamp() + 2*60*60)
               | timestamp_custom('%Y-%m-%d %H:%M:%S') }}
  - triggers:
      - trigger: time
        at: input_datetime.turn_off_ac
    actions:
      - action: climate.turn_off
        target:
          entity_id: climate.office
```

YAML
Copy
### Sensors of datetime device class [](https://www.home-assistant.io/docs/automation/trigger/#sensors-of-datetime-device-class)
The Entity ID of a [sensor](https://www.home-assistant.io/integrations/sensor/) with the “timestamp” device class.
```
automation:
  - triggers:
      - trigger: time
        at: sensor.phone_next_alarm
    actions:
      - action: light.turn_on
        target:
          entity_id: light.bedroom
```

YAML
Copy
### Sensors of datetime device class with offsets [](https://www.home-assistant.io/docs/automation/trigger/#sensors-of-datetime-device-class-with-offsets)
When the time is provided using a sensor of the timestamp device class, an offset can be provided. This offset will be added to (or subtracted from when negative) the sensor value.
For example, this trigger fires 5 minutes before the phone alarm goes off.
```
automation:
  - triggers:
      - trigger: time
        at:
          entity_id: sensor.phone_next_alarm
          offset: -00:05:00
    actions:
      - action: light.turn_on
        target:
          entity_id: light.bedroom
```

YAML
Copy
When using a positive offset the trigger might never fire. This is due to the sensor changing before the offset is reached. For example, when using a phone alarm as a trigger, the sensor value will change to the new alarm time when the alarm goes off, which means this trigger will change to the new time as well.
### Multiple times [](https://www.home-assistant.io/docs/automation/trigger/#multiple-times)
Multiple times can be provided in a list. All formats can be intermixed.
```
automation:
  triggers:
    - trigger: time
      at:
        - input_datetime.leave_for_work
        - "18:30:00"
        - entity_id: sensor.bus_arrival
          offset: "-00:10:00"
```

YAML
Copy
### Limited templates [](https://www.home-assistant.io/docs/automation/trigger/#limited-templates)
It’s also possible to use [limited templates](https://www.home-assistant.io/docs/configuration/templating/#limited-templates) for times.
```
blueprint:
  input:
    alarm:
      name: Alarm
      selector:
        text:
    hour:
      name: Hour
      selector:
        number:
          min: 0
          max: 24

  trigger_variables:
    my_alarm: !input alarm
    my_hour: !input hour
  trigger:
    - platform: time
      at:
      - "sensor.{{ my_alarm | slugify }}_time"
      - "{{ my_hour }}:30:00"
```

YAML
Copy
### Weekday filtering [](https://www.home-assistant.io/docs/automation/trigger/#weekday-filtering)
Time triggers can be filtered to fire only on specific days of the week using the `weekday` option. This allows you to create automations that only run on certain days, such as weekdays or weekends.
The `weekday` option accepts:
  * A single weekday as a string: `"mon"`, `"tue"`, `"wed"`, `"thu"`, `"fri"`, `"sat"`, `"sun"`
  * A list of weekdays using the expanded format


#### Single weekday [](https://www.home-assistant.io/docs/automation/trigger/#single-weekday)
This example will turn on the lights only on Mondays at 8:00 AM:
```
automation:
  - triggers:
      - trigger: time
        at: "08:00:00"
        weekday: "mon"
    actions:
      - action: light.turn_on
        target:
          entity_id: light.bedroom
```

YAML
Copy
#### Multiple weekdays [](https://www.home-assistant.io/docs/automation/trigger/#multiple-weekdays)
This example will run a morning routine only on weekdays (Monday through Friday) at 6:30 AM:
```
automation:
  - triggers:
      - trigger: time
        at: "06:30:00"
        weekday:
          - "mon"
          - "tue"
          - "wed"
          - "thu"
          - "fri"
    actions:
      - action: script.morning_routine
```

YAML
Copy
#### Weekend example [](https://www.home-assistant.io/docs/automation/trigger/#weekend-example)
This example demonstrates a different wake-up time for weekends:
```
automation:
  - alias: "Weekday alarm"
    triggers:
      - trigger: time
        at: "06:30:00"
        weekday:
          - "mon"
          - "tue"
          - "wed"
          - "thu"
          - "fri"
    actions:
      - action: script.weekday_morning

  - alias: "Weekend alarm"
    triggers:
      - trigger: time
        at: "08:00:00"
        weekday:
          - "sat"
          - "sun"
    actions:
      - action: script.weekend_morning
```

YAML
Copy
#### Combined with input datetime [](https://www.home-assistant.io/docs/automation/trigger/#combined-with-input-datetime)
The `weekday` option works with all time formats, including input datetime entities:
```
automation:
  - triggers:
      - trigger: time
        at: input_datetime.work_start_time
        weekday:
          - "mon"
          - "tue"
          - "wed"
          - "thu"
          - "fri"
    actions:
      - action: notify.mobile_app
        data:
          title: "Work Day!"
          message: "Time to start working"
```

YAML
Copy
## Time pattern trigger [](https://www.home-assistant.io/docs/automation/trigger/#time-pattern-trigger)
With the time pattern trigger, you can match if the hour, minute or second of the current time matches a specific value. You can prefix the value with a `/` to match whenever the value is divisible by that number. You can specify `*` to match any value.
```
automation:
  triggers:
    - trigger: time_pattern
      # Matches every hour at 5 minutes past whole
      minutes: 5

automation 2:
  triggers:
    - trigger: time_pattern
      # Trigger once per minute during the hour of 3
      hours: "3"
      minutes: "*"

automation 3:
  triggers:
    - trigger: time_pattern
      # You can also match on interval. This will match every 5 minutes
      minutes: "/5"
```

YAML
Copy
Do not prefix numbers with a zero - using `'01'` instead of `'1'` for example will result in errors.
## Persistent notification trigger [](https://www.home-assistant.io/docs/automation/trigger/#persistent-notification-trigger)
Persistent notification triggers are fired when a `persistent_notification` is `added` or `removed` that matches the configuration options.
```
automation:
  triggers:
    - trigger: persistent_notification
      update_type:
        - added
        - removed
      notification_id: invalid_config
```

YAML
Copy
See the [Persistent Notification](https://www.home-assistant.io/integrations/persistent_notification/) integration for more details on event triggers and the additional event data available for use by an automation.
## Webhook trigger [](https://www.home-assistant.io/docs/automation/trigger/#webhook-trigger)
Webhook trigger fires when a web request is made to the webhook endpoint: `/api/webhook/<webhook_id>`. The webhook endpoint is created automatically when you set it as the `webhook_id` in an automation trigger. The `webhook_id` can either be a static value or computed using [limited templates](https://www.home-assistant.io/docs/configuration/templating/#limited-templates).
The `webhook_id` template is only evaluated when setting up the trigger, they will not be re-evaluated for incoming webhook triggers.
```
automation:
  trigger_variables:
    webhook_id_variable: "template_webhook_id"
  triggers:
    - trigger: webhook
      webhook_id: "some_hook_id"
      allowed_methods:
        - POST
        - PUT
      local_only: true
    - trigger: webhook
      webhook_id: ""
      allowed_methods:
        - POST
```

YAML
Copy
You can run this automation by sending an HTTP POST request to `http://your-home-assistant:8123/api/webhook/some_hook_id`. Here is an example using the **curl** command line program, with an example form data payload:
```
curl -X POST -d 'key=value&key2=value2' https://your-home-assistant:8123/api/webhook/some_hook_id[](https://your-home-assistant:8123/api/webhook/some_hook_id)
```

Bash
Copy
Webhooks support HTTP POST, PUT, HEAD, and GET requests; PUT requests are recommended. HTTP GET and HEAD requests are not enabled by default but can be enabled by adding them to the `allowed_methods` option. The request methods can also be configured in the UI by clicking the settings gear menu button beside the Webhook ID.
By default, webhook triggers can only be accessed from devices on the same network as Home Assistant or via [Nabu Casa Cloud webhooks](https://www.nabucasa.com/config/webhooks/). The `local_only` option should be set to `false` to allow webhooks to be triggered directly via the internet. This option can also be configured in the UI by clicking the settings gear menu button beside the Webhook ID.
Remember to use an HTTPS URL if you’ve secured your Home Assistant installation with SSL/TLS.
Note that a given webhook can only be used in one automation at a time. That is, only one automation trigger can use a specific webhook ID.
### Webhook data [](https://www.home-assistant.io/docs/automation/trigger/#webhook-data)
Payloads may either be encoded as form data or JSON. Depending on that, its data will be available in an automation template as either `trigger.data` or `trigger.json`. URL query parameters are also available in the template as `trigger.query`.
Note that to use JSON encoded payloads, the `Content-Type` header must be set to `application/json`, e.g.:
```
curl -X POST -H "Content-Type: application/json" -d '{ "key": "value" }' https://your-home-assistant:8123/api/webhook/some_hook_id[](https://your-home-assistant:8123/api/webhook/some_hook_id)
```

Bash
Copy
### Webhook security [](https://www.home-assistant.io/docs/automation/trigger/#webhook-security)
Webhook endpoints don’t require authentication, other than knowing a valid webhook ID. Security best practices for webhooks include:
  * Do not use webhooks to trigger automations that are destructive, or that can create safety issues. For example, do not use a webhook to unlock a lock, or open a garage door.
  * Treat a webhook ID like a password: use a unique, non-guessable value, and keep it secret.
  * Do not copy-and-paste webhook IDs from public sources, including blueprints. Always create your own.
  * Keep the `local_only` option enabled for webhooks if access from the internet is not required.


## Zone trigger [](https://www.home-assistant.io/docs/automation/trigger/#zone-trigger)
Zone trigger fires when an entity is entering or leaving the zone. The entity can be either a person, or a device_tracker. For zone automation to work, you need to have setup a device tracker platform that supports reporting GPS coordinates. This includes [GPS Logger](https://www.home-assistant.io/integrations/gpslogger/), the [OwnTracks platform](https://www.home-assistant.io/integrations/owntracks/) and the [iCloud platform](https://www.home-assistant.io/integrations/icloud/).
```
automation:
  triggers:
    - trigger: zone
      entity_id: person.paulus
      zone: zone.home
      # Event is either enter or leave
      event: enter # or "leave"
```

YAML
Copy
## Geolocation trigger [](https://www.home-assistant.io/docs/automation/trigger/#geolocation-trigger)
Geolocation trigger fires when an entity is appearing in or disappearing from a zone. Entities that are created by a [Geolocation](https://www.home-assistant.io/integrations/geo_location/) platform support reporting GPS coordinates. Because entities are generated and removed by these platforms automatically, the entity ID normally cannot be predicted. Instead, this trigger requires the definition of a `source`, which is directly linked to one of the Geolocation platforms.
This isn’t for use with `device_tracker` entities. For those look above at the `zone` trigger.
```
automation:
  triggers:
    - trigger: geo_location
      source: nsw_rural_fire_service_feed
      zone: zone.bushfire_alert_zone
      # Event is either enter or leave
      event: enter # or "leave"
```

YAML
Copy
## Device triggers [](https://www.home-assistant.io/docs/automation/trigger/#device-triggers)
Device triggers encompass a set of events that are defined by an integration. This includes, for example, state changes of sensors as well as button events from remotes. [MQTT device triggers](https://www.home-assistant.io/integrations/device_trigger.mqtt/) are set up through autodiscovery.
In contrast to state triggers, device triggers are tied to a device and not necessarily an entity. To use a device trigger, set up an automation through the browser frontend. If you would like to use a device trigger for an automation that is not managed through the browser frontend, you can copy the YAML from the trigger widget in the frontend and paste it into your automation’s trigger list.
## Calendar trigger [](https://www.home-assistant.io/docs/automation/trigger/#calendar-trigger)
Calendar trigger fires when a [Calendar](https://www.home-assistant.io/integrations/calendar/) event starts or ends, allowing for much more flexible automations than using the Calendar entity state which only supports a single event start at a time.
An optional time offset can be given to have it fire a set time before or after the calendar event (e.g., 5 minutes before event start).
```
automation:
  triggers:
    - trigger: calendar
      # Possible values: start, end
      event: start
      # The calendar entity_id
      entity_id: calendar.light_schedule
      # Optional time offset
      offset: "-00:05:00"
```

YAML
Copy
See the [Calendar](https://www.home-assistant.io/integrations/calendar/) integration for more details on event triggers and the additional event data available for use by an automation.
## Sentence trigger [](https://www.home-assistant.io/docs/automation/trigger/#sentence-trigger)
A sentence trigger fires when [Assist](https://www.home-assistant.io/voice_control/) matches a sentence from a voice assistant using the default [conversation agent](https://www.home-assistant.io/integrations/conversation/). Sentence triggers work with Home Assistant Assist. They will not work with external conversation agents such as OpenAI or Google Generative AI unless “Prefer handling commands locally” is enabled in the conversation agent settings.
Sentences are allowed to use some basic [template syntax](https://developers.home-assistant.io/docs/voice/intent-recognition/template-sentence-syntax/#sentence-templates-syntax) like optional and alternative words. For example, `[it's ]party time` will match both “party time” and “it’s party time”.
```
automation:
  triggers:
    - trigger: conversation
      command:
        - "[it's ]party time"
        - "happy (new year|birthday)"
```

YAML
Copy
The sentences matched by this trigger will be:
  * party time
  * it’s party time
  * happy new year
  * happy birthday


Punctuation and casing are ignored, so “It’s PARTY TIME!!!” will also match.
### Related topic [](https://www.home-assistant.io/docs/automation/trigger/#related-topic)
  * [Adding a custom sentence to trigger an automation](https://www.home-assistant.io/voice_control/custom_sentences/#adding-a-custom-sentence-to-trigger-an-automation)


### Sentence wildcards [](https://www.home-assistant.io/docs/automation/trigger/#sentence-wildcards)
Adding one or more `{lists}` to your trigger sentences will capture any text at that point in the sentence. A `slots` object will be [available in the trigger data](https://www.home-assistant.io/docs/automation/templating#sentence). This allows you to match sentences with variable parts, such as album/artist names or a description of a picture.
For example, the sentence `play {album} by {artist}` will match “play the white album by the beatles” and have the following variables available in the action templates:
  * `{{ trigger.slots.album }}` - “the white album”
  * `{{ trigger.slots.artist }}` - “the beatles”


Wildcards will match as much text as possible, which may lead to surprises: “play day by day by taken by trees” will match `album` as “day” and `artist` as “day by taken by trees”. Including extra words in your template can help: `play {album} by artist {artist}` can now correctly match “play day by day by artist taken by trees”.
## Multiple triggers [](https://www.home-assistant.io/docs/automation/trigger/#multiple-triggers)
It is possible to specify multiple triggers for the same rule. To do so just prefix the first line of each trigger with a dash (-) and indent the next lines accordingly. Whenever one of the triggers fires, processing of your automation rule begins.
```
automation:
  triggers:
    # first trigger
    - trigger: time_pattern
      minutes: 5
      # our second trigger is the sunset
    - trigger: sun
      event: sunset
```

YAML
Copy
## Multiple entity IDs for the same trigger [](https://www.home-assistant.io/docs/automation/trigger/#multiple-entity-ids-for-the-same-trigger)
It is possible to specify multiple entities for the same trigger. To do so add multiple entities using a nested list. The trigger will fire and start, processing your automation each time the trigger is true for any entity listed.
```
automation:
  triggers:
    - trigger: state
      entity_id:
        - sensor.one
        - sensor.two
        - sensor.three
```

YAML
Copy
## Disabling a trigger [](https://www.home-assistant.io/docs/automation/trigger/#disabling-a-trigger)
Every individual trigger in an automation can be disabled, without removing it. To do so, add `enabled: false` to the trigger. For example:
```
# Example script with a disabled trigger
automation:
  triggers:
    # This trigger will not trigger, as it is disabled.
    # This automation does not run when the sun is set.
    - enabled: false
      trigger: sun
      event: sunset

    # This trigger will fire, as it is not disabled.
    - trigger: time
      at: "15:32:00"
```

YAML
Copy
Triggers can also be disabled based on limited templates or blueprint inputs. These are only evaluated once when the automation is loaded.
```
blueprint:
  input:
    input_boolean:
      name: Boolean
      selector:
        boolean:
    input_number:
      name: Number
      selector:
        number:
          min: 0
          max: 100

  trigger_variables:
    _enable_number: !input input_number

  triggers:
    - trigger: sun
      event_type: sunrise
      enabled: !input input_boolean
    - trigger: sun
      event_type: sunset
      enabled: "{{ _enable_number < 50 }}"
```

YAML
Copy
## Merging lists of triggers [](https://www.home-assistant.io/docs/automation/trigger/#merging-lists-of-triggers)
This feature requires Home Assistant version 2024.10 or later. If using this in a blueprint, set the `min_version` for the blueprint to at least this version. See the [blueprint schema documentation](https://www.home-assistant.io/docs/blueprint/schema/#min_version) for more details.
In some advanced cases (like for blueprints with trigger selectors), it may be necessary to insert a second list of triggers into the main trigger list. This can be done by adding a dictionary in the main trigger list with the sole key `triggers`, and the value for that key contains a second list of triggers. These will then be flattened into a single list of triggers. For example:
```
blueprint:
  name: Nested Trigger Blueprint
  domain: automation
  input:
    usertrigger:
      selector:
        trigger:

triggers:
  - trigger: event
    event_type: manual_event
  - triggers: !input usertrigger
```

YAML
Copy
This blueprint automation can then be triggered either by the fixed manual_event trigger, or additionally by any triggers selected in the trigger selector. This is also applicable for `wait_for_trigger` action.
## Related topics[](https://www.home-assistant.io/docs/automation/trigger/#related-topics)
  * [ Adding a custom sentence to trigger an automation ](https://www.home-assistant.io/voice_control/custom_sentences/#adding-a-custom-sentence-to-trigger-an-automation)


####  **Help us improve our documentation**[](https://www.home-assistant.io/docs/automation/trigger/#feedback_section)
Suggest an edit to this page, or provide/view feedback for this page. 
  * [](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/automation/trigger.markdown "Edit this page")
  * [](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fautomation%2Ftrigger%2F&version=2025.11.1&labels=current "Provide feedback on this page")
  * [](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fautomation%2Ftrigger%2F%22&in=body "View given feedback for this page")


  * [Overview ](https://www.home-assistant.io/docs/) | [FAQ ](https://www.home-assistant.io/faq/) | [Glossary ](https://www.home-assistant.io/docs/glossary/)
  * [Automations ](https://www.home-assistant.io/docs/automation/)
    * [Basic automations ](https://www.home-assistant.io/docs/automation/basics/)
      * [Using automation blueprints ](https://www.home-assistant.io/docs/automation/using_blueprints/)
      * [Editor ](https://www.home-assistant.io/docs/automation/editor/)
      * [Triggers ](https://www.home-assistant.io/docs/automation/trigger/)
      * [Conditions ](https://www.home-assistant.io/docs/automation/condition/)
      * [Actions ](https://www.home-assistant.io/docs/automation/action/)
      * [Run modes ](https://www.home-assistant.io/docs/automation/modes/)
      * [Automation actions ](https://www.home-assistant.io/docs/automation/services/)
      * [Templates ](https://www.home-assistant.io/docs/automation/templating/)
      * [YAML ](https://www.home-assistant.io/docs/automation/yaml/)
      * [Troubleshooting automation ](https://www.home-assistant.io/docs/automation/troubleshooting/)
    * [Scenes ](https://www.home-assistant.io/docs/scene/)
    * [Blueprints ](https://www.home-assistant.io/docs/blueprint/)
    * [Scripts ](https://www.home-assistant.io/docs/scripts/)
  * [Dashboards ](https://www.home-assistant.io/dashboards)
  * [Voice assistants ](https://www.home-assistant.io/voice_control/)
  * [Organization ](https://www.home-assistant.io/docs/organizing/)
  * [Home energy management ](https://www.home-assistant.io/docs/energy/)
  * [Common tasks ](https://www.home-assistant.io/common-tasks/general/)
  * [Advanced configuration ](https://www.home-assistant.io/docs/configuration/)
  * [Authentication ](https://www.home-assistant.io/docs/authentication/)
  * [Backend ](https://www.home-assistant.io/docs/backend/)
  * [Tools and helpers ](https://www.home-assistant.io/docs/tools/)
  * [iOS and Android apps ](https://companion.home-assistant.io/docs)
  * [MQTT ](https://www.home-assistant.io/integrations/mqtt)
  *     * [Home Assistant Green ](https://support.nabucasa.com/hc/en-us/categories/24638797677853-Home-Assistant-Green)
    * [Home Assistant Connect ZBT-1 ](https://support.nabucasa.com/hc/en-us/categories/24734620813469)
    * [Home Assistant Connect ZWA-2 ](https://support.nabucasa.com/hc/en-us/categories/28669861145885)
    * [Home Assistant Yellow ](https://support.nabucasa.com/hc/en-us/categories/24734575925149-Home-Assistant-Yellow)
    * [Home Assistant Voice Preview Edition ](https://support.nabucasa.com/hc/en-us/categories/24451727188125-Home-Assistant-Voice-Preview-Edition)


  * [Trigger ID](https://www.home-assistant.io/docs/automation/trigger/#trigger-id)
    * [Video tutorial](https://www.home-assistant.io/docs/automation/trigger/#video-tutorial)
  * [Trigger variables](https://www.home-assistant.io/docs/automation/trigger/#trigger-variables)
  * [Event trigger](https://www.home-assistant.io/docs/automation/trigger/#event-trigger)
  * [Home Assistant trigger](https://www.home-assistant.io/docs/automation/trigger/#home-assistant-trigger)
  * [MQTT trigger](https://www.home-assistant.io/docs/automation/trigger/#mqtt-trigger)
  * [Numeric state trigger](https://www.home-assistant.io/docs/automation/trigger/#numeric-state-trigger)
  * [State trigger](https://www.home-assistant.io/docs/automation/trigger/#state-trigger)
    * [Examples](https://www.home-assistant.io/docs/automation/trigger/#examples)
    * [Triggering on attribute changes](https://www.home-assistant.io/docs/automation/trigger/#triggering-on-attribute-changes)
    * [Holding a state or attribute](https://www.home-assistant.io/docs/automation/trigger/#holding-a-state-or-attribute)
  * [Sun trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-trigger)
    * [Sunset / Sunrise trigger](https://www.home-assistant.io/docs/automation/trigger/#sunset--sunrise-trigger)
    * [Sun elevation trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-elevation-trigger)
  * [Tag trigger](https://www.home-assistant.io/docs/automation/trigger/#tag-trigger)
  * [Template trigger](https://www.home-assistant.io/docs/automation/trigger/#template-trigger)
  * [Time trigger](https://www.home-assistant.io/docs/automation/trigger/#time-trigger)
    * [Time string](https://www.home-assistant.io/docs/automation/trigger/#time-string)
    * [Input datetime](https://www.home-assistant.io/docs/automation/trigger/#input-datetime)
    * [Sensors of datetime device class](https://www.home-assistant.io/docs/automation/trigger/#sensors-of-datetime-device-class)
    * [Sensors of datetime device class with offsets](https://www.home-assistant.io/docs/automation/trigger/#sensors-of-datetime-device-class-with-offsets)
    * [Multiple times](https://www.home-assistant.io/docs/automation/trigger/#multiple-times)
    * [Limited templates](https://www.home-assistant.io/docs/automation/trigger/#limited-templates)
    * [Weekday filtering](https://www.home-assistant.io/docs/automation/trigger/#weekday-filtering)
  * [Time pattern trigger](https://www.home-assistant.io/docs/automation/trigger/#time-pattern-trigger)
  * [Persistent notification trigger](https://www.home-assistant.io/docs/automation/trigger/#persistent-notification-trigger)
  * [Webhook trigger](https://www.home-assistant.io/docs/automation/trigger/#webhook-trigger)
    * [Webhook data](https://www.home-assistant.io/docs/automation/trigger/#webhook-data)
    * [Webhook security](https://www.home-assistant.io/docs/automation/trigger/#webhook-security)
  * [Zone trigger](https://www.home-assistant.io/docs/automation/trigger/#zone-trigger)
  * [Geolocation trigger](https://www.home-assistant.io/docs/automation/trigger/#geolocation-trigger)
  * [Device triggers](https://www.home-assistant.io/docs/automation/trigger/#device-triggers)
  * [Calendar trigger](https://www.home-assistant.io/docs/automation/trigger/#calendar-trigger)
  * [Sentence trigger](https://www.home-assistant.io/docs/automation/trigger/#sentence-trigger)
    * [Related topic](https://www.home-assistant.io/docs/automation/trigger/#related-topic)
    * [Sentence wildcards](https://www.home-assistant.io/docs/automation/trigger/#sentence-wildcards)
  * [Multiple triggers](https://www.home-assistant.io/docs/automation/trigger/#multiple-triggers)
  * [Multiple entity IDs for the same trigger](https://www.home-assistant.io/docs/automation/trigger/#multiple-entity-ids-for-the-same-trigger)
  * [Disabling a trigger](https://www.home-assistant.io/docs/automation/trigger/#disabling-a-trigger)
  * [Merging lists of triggers](https://www.home-assistant.io/docs/automation/trigger/#merging-lists-of-triggers)
  * [Related topics](https://www.home-assistant.io/docs/automation/trigger/#related-topics)


![Home Assistant](https://www.home-assistant.io/images/footer-logo-text.svg)
Home Assistant is a project from the [Open Home Foundation](https://www.openhomefoundation.org/), sponsored by [Nabu Casa](https://www.nabucasa.com/). 
### Join us and contribute!
  * [GitHub repo ](https://github.com/home-assistant/)
  * [Developers Portal ](https://developers.home-assistant.io)
  * [Design Portal ](https://design.home-assistant.io)
  * [Data Science Portal ](https://data.home-assistant.io)
  * [Community Forum ](https://community.home-assistant.io)
  * [Creator Network ](https://creators.home-assistant.io/)
  * [Works With Home Assistant ](https://works-with.home-assistant.io/)
  * [Our community](https://www.home-assistant.io/community)
[ ](https://www.home-assistant.io/community)
  * [](https://www.home-assistant.io/community)[Reporting issues](https://www.home-assistant.io/help/reporting_issues/)


### System status
  * [Integration Alerts ](https://alerts.home-assistant.io)
  * [Security Alerts](https://www.home-assistant.io/security/)
  * [System Status ](https://status.home-assistant.io)


### Companion apps
  * [iOS and Apple devices](https://apps.apple.com/us/app/home-assistant/id1099568401)
  * [Android and Wear OS](https://play.google.com/store/apps/details?id=io.homeassistant.companion.android)
  * [...and more!](https://companion.home-assistant.io/)


### Governance
  * [Privacy Notices](https://www.home-assistant.io/privacy/)
  * [Contributor License Agreement](https://www.home-assistant.io/developers/cla/)
  * [Terms of Service](https://www.home-assistant.io/tos/)
  * [Code of Conduct](https://www.home-assistant.io/code_of_conduct/)
  * [Credits](https://www.home-assistant.io/developers/credits/)
  * [License](https://www.home-assistant.io/developers/license/)


### Follow us
[Sign up for our newsletter ](https://newsletter.openhomefoundation.org/#/portal)
[](https://youtube.com/@home_assistant "YouTube") [](https://reddit.com/r/homeassistant "Reddit") [](https://github.com/home-assistant "GitHub")   
[](https://fosstodon.org/@homeassistant "Mastodon") [](https://bsky.app/profile/home-assistant.io "Bluesky") [](https://x.com/home_assistant "X")   
[](https://www.facebook.com/homeassistantio "Facebook") [](https://www.instagram.com/homeassistant/ "Instagram") [](https://www.linkedin.com/company/home-assistant "LinkedIn")
For partnership inquiries please check out [Works With Home Assistant](https://works-with.home-assistant.io/). For media, get in touch here. For other questions, you can contact us here (No technical support!) 
Website powered by [Jekyll](https://jekyllrb.com/)  
Originally based on the [Oscailte theme](https://github.com/coogie/oscailte)
[ ![Deploys by Netlify Badge](https://www.home-assistant.io/images/frontpage/netlify.svg) ](https://www.netlify.com)

