Conditions are an optional part of an automation rule. They can be used to prevent the automation’s actions from being run. After a triggerA trigger is a set of values or conditions of a platform that are defined to cause an automation to run.[ [Learn more]](https://www.home-assistant.io/docs/automation/trigger/) occurred, all conditions will be checked. The automation will be executed if all conditions return `true`. If any of the conditions returns `false`, the automation won’t start.
Conditions look very similar to triggers, but they are very different — a trigger will look at events happening in the system, while a condition only looks at how the system looks right now. A trigger can observe that a switch is being turned on. A condition can only see if a switch is currently on or off.
The available conditions for an automation are the same as for the script syntax so see that page for a [full list of available conditions](https://www.home-assistant.io/docs/scripts/conditions/).
Example of using condition:
```
automation:
  - alias: "Turn on office lights"
    triggers:
      - trigger: state
        entity_id: sensor.office_motion_sensor
        to: "on"
    conditions:
      - or:
        - condition: numeric_state
          entity_id: sun.sun
          attribute: elevation
          below: 4
        - condition: numeric_state
          entity_id: sensor.office_lux_sensor
          below: 10
    actions:
      - action: scene.turn_on
        target:
          entity_id: scene.office_lights
```

YAML
Copy
The `condition` option of an automation, also accepts a single condition template directly. For example:
```
automation:
  - alias: "Turn on office lights"
    triggers:
      - trigger: state
        entity_id: sensor.office_motion_sensor
        to: "on"
    conditions: "{{ state_attr('sun.sun', 'elevation') < 4 }}"
    actions:
      - action: scene.turn_on
        target:
          entity_id: scene.office_lights
```

YAML
Copy
####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
