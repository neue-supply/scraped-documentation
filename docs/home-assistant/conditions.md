---
title: Conditions - Home Assistant
description: Documentation about all available conditions.
source_url: https://www.home-assistant.io/docs/scripts/conditions
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:08:30.712Z
---

Conditions can be used within a scriptScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on. [\[Learn more\]](https://www.home-assistant.io/docs/scripts/) or automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home. [\[Learn more\]](https://www.home-assistant.io/docs/automation/) to prevent further execution. When a condition evaluates true, the script or automation will be executed. If any other value is returned, the script or automation stops executing. A condition will look at the system at that moment. For example, a condition can test if a switch is currently turned on or off.

Unlike a triggerA trigger is a set of values or conditions of a platform that are defined to cause an automation to run. [\[Learn more\]](https://www.home-assistant.io/docs/automation/trigger/), which is always `or`, conditions are `and` by default - all conditions have to be true.

All conditions support an optional `alias`.

- [Logical conditions](https://www.home-assistant.io/docs/scripts/conditions/#logical-conditions)  - [AND condition](https://www.home-assistant.io/docs/scripts/conditions/#and-condition)
  - [OR condition](https://www.home-assistant.io/docs/scripts/conditions/#or-condition)
  - [Mixed AND and OR conditions](https://www.home-assistant.io/docs/scripts/conditions/#mixed-and-and-or-conditions)
  - [NOT condition](https://www.home-assistant.io/docs/scripts/conditions/#not-condition)
- [Numeric state condition](https://www.home-assistant.io/docs/scripts/conditions/#numeric-state-condition)
- [State condition](https://www.home-assistant.io/docs/scripts/conditions/#state-condition)  - [Sun condition](https://www.home-assistant.io/docs/scripts/conditions/#sun-condition)
  - [Sun elevation condition](https://www.home-assistant.io/docs/scripts/conditions/#sun-elevation-condition)
  - [Sunset/sunrise condition](https://www.home-assistant.io/docs/scripts/conditions/#sunsetsunrise-condition)
- [Template condition](https://www.home-assistant.io/docs/scripts/conditions/#template-condition)  - [Template condition shorthand notation](https://www.home-assistant.io/docs/scripts/conditions/#template-condition-shorthand-notation)
- [Time condition](https://www.home-assistant.io/docs/scripts/conditions/#time-condition)
- [Trigger condition](https://www.home-assistant.io/docs/scripts/conditions/#trigger-condition)
- [Zone condition](https://www.home-assistant.io/docs/scripts/conditions/#zone-condition)
- [Examples](https://www.home-assistant.io/docs/scripts/conditions/#examples)
- [Disabling a condition](https://www.home-assistant.io/docs/scripts/conditions/#disabling-a-condition)

## Logical conditions

### AND condition

Test multiple conditions in one condition statement. Passes if all embedded conditions are true.

```yaml
conditions:
  - alias: "Paulus home AND temperature below 20"
    condition: and
    conditions:
      - condition: state
        entity_id: "device_tracker.paulus"
        state: "home"
      - condition: numeric_state
        entity_id: "sensor.temperature"
        below: 20
```

YAML

Copy

If you do not want to combine AND and OR conditions, you can list them sequentially.

The following configuration works the same as the one listed above:

```yaml
conditions:
  - condition: state
    entity_id: "device_tracker.paulus"
    state: "home"
  - condition: numeric_state
    entity_id: "sensor.temperature"
    below: 20
```

YAML

Copy

Currently you need to format your conditions like this to be able to edit them using the [automations editor](https://www.home-assistant.io/docs/automation/editor/).

The AND condition also has a shorthand form. The following configuration works the same as the ones listed above:

```yaml
conditions:
  alias: "Paulus home AND temperature below 20"
  - and:
    - condition: state
      entity_id: "device_tracker.paulus"
      state: "home"
    - condition: numeric_state
      entity_id: "sensor.temperature"
      below: 20
```

YAML

Copy

### OR condition

Test multiple conditions in one condition statement. Passes if any embedded condition is true.

```yaml
conditions:
  - alias: "Paulus home OR temperature below 20"
    condition: or
    conditions:
      - condition: state
        entity_id: "device_tracker.paulus"
        state: "home"
      - condition: numeric_state
        entity_id: "sensor.temperature"
        below: 20
```

YAML

Copy

The OR condition also has a shorthand form. The following configuration works the same as the one listed above:

```yaml
conditions:
  - alias: "Paulus home OR temperature below 20"
    or:
      - condition: state
        entity_id: "device_tracker.paulus"
        state: "home"
      - condition: numeric_state
        entity_id: "sensor.temperature"
        below: 20
```

YAML

Copy

### Mixed AND and OR conditions

Test multiple AND and OR conditions in one condition statement. Passes if any embedded condition is true.
This allows you to mix several AND and OR conditions together.

```yaml
conditions:
  - condition: and
    conditions:
      - condition: state
        entity_id: "device_tracker.paulus"
        state: "home"
      - condition: or
        conditions:
          - condition: state
            entity_id: sensor.weather_precip
            state: "rain"
          - condition: numeric_state
            entity_id: "sensor.temperature"
            below: 20
```

YAML

Copy

Or in shorthand form:

```yaml
conditions:
  - and:
    - condition: state
      entity_id: "device_tracker.paulus"
      state: "home"
    - or:
      - condition: state
        entity_id: sensor.weather_precip
        state: "rain"
      - condition: numeric_state
        entity_id: "sensor.temperature"
        below: 20
```

YAML

Copy

### NOT condition

Test multiple conditions in one condition statement. Passes if all embedded conditions are **not** true.

```yaml
conditions:
  - alias: "Paulus not home AND alarm not disarmed"
    condition: not
    conditions:
      - condition: state
        entity_id: device_tracker.paulus
        state: "home"
      - condition: state
        entity_id: alarm_control_panel.home_alarm
        state: "disarmed"
```

YAML

Copy

The NOT condition also has a shorthand form. The following configuration works the same as the one listed above:

```yaml
conditions:
  alias: "Paulus not home AND alarm not disarmed"
  not:
    - condition: state
      entity_id: device_tracker.paulus
      state: "home"
    - condition: state
      entity_id: alarm_control_panel.home_alarm
      state: disarmed
```

YAML

Copy

## Numeric state condition

This type of condition attempts to parse the state of the specified entity or the attribute of an entity as a number, and triggers if the value matches the thresholds (strictly below/above, so equal excluded).

If both `below` and `above` are specified, both tests have to pass.

```yaml
conditions:
  - alias: "Temperature between 17 and 25 degrees"
    condition: numeric_state
    entity_id: sensor.temperature
    above: 17
    below: 25
```

YAML

Copy

You can optionally use a `value_template` to process the value of the state before testing it.

```yaml
conditions:
  - condition: numeric_state
    entity_id: sensor.temperature
    above: 17
    below: 25
    # If your sensor value needs to be adjusted
    value_template: "{{ float(state.state) + 2 }}"
```

YAML

Copy

It is also possible to test the condition against multiple entities at once.
The condition will pass if **all** entities match the thresholds.

```yaml
conditions:
  - condition: numeric_state
    entity_id:
      - sensor.kitchen_temperature
      - sensor.living_room_temperature
    below: 18
```

YAML

Copy

Alternatively, the condition can test against a state attribute.
The condition will pass if the attribute value of the entity matches the thresholds.

```yaml
conditions:
  - condition: numeric_state
    entity_id: climate.living_room_thermostat
    attribute: temperature
    above: 17
    below: 25
```

YAML

Copy

Number helpers (`input_number` entities), `number`, `sensor`, and `zone` entities
that contain a numeric value, can be used in the `above` and `below`
options to make the condition more dynamic.

```yaml
conditions:
  - condition: numeric_state
    entity_id: climate.living_room_thermostat
    attribute: temperature
    above: input_number.temperature_threshold_low
    below: input_number.temperature_threshold_high
```

YAML

Copy

## State condition

Tests if an entity has a specified state.

```yaml
conditions:
  - alias: "Paulus not home for an hour and a bit"
    condition: state
    entity_id: device_tracker.paulus
    state: "not_home"
    # optional: Evaluates to true only if state was this for last X time.
    for:
      hours: 1
      minutes: 10
      seconds: 5
```

YAML

Copy

It is also possible to test the condition against multiple entities at once.
The condition will pass if **all** entities match the state.

```yaml
conditions:
  - condition: state
    entity_id:
      - light.kitchen
      - light.living_room
    state: "on"
```

YAML

Copy

Instead of matching all, it is also possible if one of the entities matches.
In the following example the condition will pass if **any** entity matches the state.

```yaml
conditions:
  - condition: state
    entity_id:
      - binary_sensor.motion_sensor_left
      - binary_sensor.motion_sensor_right
    match: any
    state: "on"
```

YAML

Copy

Testing if an entity is matching a set of possible conditions;
The condition will pass if the entity matches one of the states given.

```yaml
conditions:
  - condition: state
    entity_id: alarm_control_panel.home
    state:
      - "armed_away"
      - "armed_home"
```

YAML

Copy

Or, combine multiple entities with multiple states. In the following example,
both media players need to be either paused or playing for the condition to pass.

```yaml
conditions:
  - condition: state
    entity_id:
      - media_player.living_room
      - media_player.kitchen
    state:
      - "playing"
      - "paused"
```

YAML

Copy

Alternatively, the condition can test against a state attribute.
The condition will pass if the attribute matches the given state.

```yaml
conditions:
  - condition: state
    entity_id: climate.living_room_thermostat
    attribute: fan_mode
    state: "auto"
```

YAML

Copy

Finally, the `state` option accepts helper entities (also known as `input_*`
entities). The condition will pass if the state of the entity matches the state
of the given helper entity.

```yaml
conditions:
  - condition: state
    entity_id: alarm_control_panel.home
    state: input_select.guest_mode
```

YAML

Copy

You can also use templates in the `for` option.

```yaml
conditions:
  - condition: state
    entity_id: device_tracker.paulus
    state: "home"
    for:
      minutes: "{{ states('input_number.lock_min')|int }}"
      seconds: "{{ states('input_number.lock_sec')|int }}"
```

YAML

Copy

The `for` template(s) will be evaluated when the condition is tested.

### Sun condition

#### Sun state condition

The sun state can be used to test if the sun has set or risen.

```yaml
conditions:
  - alias: "Sun up"
    condition: state  # 'day' condition: from sunrise until sunset
    entity_id: sun.sun
    state: "above_horizon"
```

YAML

Copy

```yaml
conditions:
  - alias: "Sun down"
    condition: state  # from sunset until sunrise
    entity_id: sun.sun
    state: "below_horizon"
```

YAML

Copy

### Sun elevation condition

The sun elevation can be used to test if the sun has set or risen, it is dusk, it is night, etc. when a trigger occurs.
For an in-depth explanation of sun elevation, see [sun elevation trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-elevation-trigger).

```yaml
conditions:
  - condition: and  # 'twilight' condition: dusk and dawn, in typical locations
    conditions:
      - condition: template
        value_template: "{{ state_attr('sun.sun', 'elevation') < 0 }}"
      - condition: template
        value_template: "{{ state_attr('sun.sun', 'elevation') > -6 }}"
```

YAML

Copy

```yaml
conditions:
  condition: template  # 'night' condition: from dusk to dawn, in typical locations
  value_template: "{{ state_attr('sun.sun', 'elevation') < -6 }}"
```

YAML

Copy

### Sunset/sunrise condition

The sun condition can also test if the sun has already set or risen when a trigger occurs. The `before` and `after` keys can only be set to `sunset` or `sunrise`. They have a corresponding optional offset value (`before_offset`, `after_offset`) that can be added, similar to the [sun trigger](https://www.home-assistant.io/docs/automation/trigger/#sun-trigger).

Note that if only `before` key is used, the condition will be true _from midnight_ until sunrise/sunset. If only `after` key is used, the condition will be true from sunset/sunrise _until midnight_. If both `before: sunrise` and `after: sunset` keys are used, the condition will be true _from midnight_ until sunrise **and** from sunset _until midnight_. If both `after: sunrise` and `before: sunset` keys are used, the condition will be true from sunrise until sunset.

Tip

The sunset/sunrise conditions do not work in locations inside the polar circles, and also not in locations with a highly skewed local time zone. In those cases it is advised to use conditions evaluating the solar elevation instead of the before/after sunset/sunrise conditions.

This is an example of 1 hour offset before sunset:

```yaml
conditions:
  - condition: sun
    after: sunset
    after_offset: "-01:00:00"
```

YAML

Copy

This is ‘when dark’ - equivalent to a state condition on `sun.sun` of `below_horizon`:

```yaml
conditions:
  - condition: sun
    after: sunset
    before: sunrise
```

YAML

Copy

This is ‘when light’ - equivalent to a state condition on `sun.sun` of `above_horizon`:

```yaml
conditions:
  - condition: sun
    after: sunrise
    before: sunset
```

YAML

Copy

A visual timeline is provided below, showing an example of when these conditions are true. In this chart, sunrise is at 6:00, and sunset is at 18:00 (6:00 PM). The green areas of the chart indicate when the specified conditions are true.

![Graphic showing an example of sun conditions](https://www.home-assistant.io/images/docs/scripts/sun-conditions.svg)

## Template condition

The template condition tests if the [given template](https://www.home-assistant.io/docs/configuration/templating/) renders a value equal to true. This is achieved by having the template result in a true boolean expression or by having the template render `True`.

```yaml
conditions:
  - alias: "Iphone battery above 50%"
    condition: template
    value_template: "{{ (state_attr('device_tracker.iphone', 'battery_level')|int) > 50 }}"
```

YAML

Copy

Within an automation, template conditions also have access to the `trigger` variable as [described here](https://www.home-assistant.io/getting-started/automation-templating/).

### Template condition shorthand notation

The template condition has a shorthand notation that can be used to make your scripts and automations shorter.

For example:

```yaml
conditions: "{{ (state_attr('device_tracker.iphone', 'battery_level')|int) > 50 }}"
```

YAML

Copy

Or in a list of conditions, allowing to use existing conditions as described in this
chapter and one or more shorthand template conditions

```yaml
conditions:
  - "{{ (state_attr('device_tracker.iphone', 'battery_level')|int) > 50 }}"
  - condition: state
    entity_id: alarm_control_panel.home
    state: armed_away
  - "{{ is_state('device_tracker.iphone', 'away') }}"
```

YAML

Copy

This shorthand notation can be used everywhere in Home Assistant where
conditions are accepted. For example, in [`and`](https://www.home-assistant.io/docs/scripts/conditions/#and-condition), [`or`](https://www.home-assistant.io/docs/scripts/conditions/#or-condition)
and [`not`](https://www.home-assistant.io/docs/scripts/conditions/#not-condition) conditions:

```yaml
conditions:
  - condition: or
    conditions:
      - "{{ is_state('device_tracker.iphone', 'away') }}"
      - condition: numeric_state
        entity_id: "sensor.temperature"
        below: 20
```

YAML

Copy

It’s also supported in the `repeat` action’s `while` or `until` option, or in a `choose` action’s `conditions` option:

```yaml
- while: "{{ is_state('sensor.mode', 'Home') and repeat.index < 10 }}"
  sequence:
    - ...
```

YAML

Copy

```yaml
- choose:
    - conditions: "{{ is_state('sensor.mode', 'Home') and repeat.index < 10 }}"
      sequence:
       - ...
```

YAML

Copy

It’s also supported in script or automation `condition` actions:

```yaml
- condition: "{{ is_state('device_tracker.iphone', 'away') }}"
```

YAML

Copy

## Time condition

The time condition can test if it is after a specified time, before a specified time or if it is a certain day of the week.

```yaml
conditions:
  - alias: "Time 15~02"
    condition: time
    # At least one of the following is required.
    after: "15:00:00"
    before: "02:00:00"
    weekday:
      - mon
      - wed
      - fri
```

YAML

Copy

Valid values for `weekday` are `mon`, `tue`, `wed`, `thu`, `fri`, `sat`, `sun`.
Note that if only `before` key is used, the condition will be `true` _from midnight_ until the specified time.
If only `after` key is used, the condition will be `true` from the specified time _until midnight_.
Time condition windows can span across the midnight threshold if **both**`after` and `before` keys are used. In the example above, the condition window is from 3pm to 2am.

Tip

A better weekday condition could be by using the [Workday Binary Sensor](https://www.home-assistant.io/integrations/workday/).

For the `after` and `before` options a time helper (`input_datetime` entity), a `time` entity,
or another `sensor` entity containing a timestamp with the “timestamp” device
class, can be used instead.

```yaml
conditions:
  - alias: "Example referencing a time helper"
    condition: time
    after: input_datetime.house_silent_hours_start
    before: input_datetime.house_silent_hours_end

  - alias: "Example referencing a time entity"
    before: time.dnd_start

  - alias: "Example referencing another sensor"
    after: sensor.groceries_delivery_time
```

YAML

Copy

Note

Note that the time condition only takes the time into account. If
a referenced sensor or helper entity contains a timestamp with a date, the
date part is fully ignored.

## Trigger condition

The trigger condition can test if an automation was triggered by a certain trigger, identified by the trigger’s `id`.

```yaml
conditions:
  - condition: trigger
    id: event_trigger
```

YAML

Copy

For a trigger identified by its index, both a string and integer is allowed:

```yaml
conditions:
  - condition: trigger
    id: "0"
```

YAML

Copy

```yaml
conditions:
  - condition: trigger
    id: 0
```

YAML

Copy

It is possible to give a list of triggers:

```yaml
conditions:
  - condition: trigger
    id:
      - event_1_trigger
      - event_2_trigger
```

YAML

Copy

## Zone condition

Zone conditions test if an entity is in a certain zone. For zone automation to work, you need to have set up a device tracker platform that supports reporting GPS coordinates.

```yaml
conditions:
  - alias: "Paulus at home"
    condition: zone
    entity_id: device_tracker.paulus
    zone: zone.home
```

YAML

Copy

It is also possible to test the condition against multiple entities at once.
The condition will pass if all entities are in the specified zone.

```yaml
conditions:
  - condition: zone
    entity_id:
      - device_tracker.frenck
      - device_tracker.daphne
    zone: zone.home
```

YAML

Copy

Testing if an entity is matching a set of possible zones;
The condition will pass if the entity is in one of the zones.

```yaml
conditions:
  - condition: zone
    entity_id: device_tracker.paulus
    state:
      - zone.home
      - zone.work
```

YAML

Copy

Or, combine multiple entities with multiple zones. In the following example,
both entities need to be either in the home or the work zone for the condition
to pass.

```yaml
conditions:
  condition: zone
  entity_id:
    - device_tracker.frenck
    - device_tracker.daphne
  state:
    - zone.home
    - zone.work
```

YAML

Copy

## Examples

```yaml
conditions:
  - condition: numeric_state
    entity_id: sun.sun
    value_template: "{{ state.attributes.elevation }}"
    below: 1
  - condition: state
    entity_id: light.living_room
    state: "off"
  - condition: time
    before: "23:00:00"
    after: "14:00:00"
  - condition: state
    entity_id: script.light_turned_off_5min
    state: "off"
```

YAML

Copy

## Disabling a condition

Every individual condition can be disabled, without removing it.
To do so, add `enabled: false` to the condition configuration.

This can be useful if you want to temporarily disable a condition, for example,
for testing. A disabled condition will behave as if it were removed.

For example:

```yaml
# This condition will always pass, as it is disabled.
conditions:
  - enabled: false
    condition: state
    entity_id: sun.sun
    state: "above_horizon"
```

YAML

Copy

Conditions can also be disabled based on limited templates or blueprint inputs.

```yaml
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

  conditions:
    - condition: state
      entity_id: sun.sun
      state: "above_horizon"
      enabled: !input input_boolean
    - condition: state
      entity_id: sun.sun
      state: "below_horizon"
      enabled: "{{ _enable_number < 50 }}"
```

YAML

Copy

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/scripts/conditions.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fscripts%2Fconditions%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fscripts%2Fconditions%2F%22&in=body "View given feedback for this page")
