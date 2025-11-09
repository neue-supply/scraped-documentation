---
title: Automation actions - Home Assistant
description: Automations result in action.
source_url: https://www.home-assistant.io/docs/automation/action
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:04:38.726Z
---

The action of an automation is what is being executed when an automation fires. The action part follows the [script syntax](https://www.home-assistant.io/docs/scripts/) which can be used to interact with anything via other actions or events.

For actions, you can specify the `entity_id` that it should apply to and optional parameters (to specify for example the brightness).

You can also perform the action to activate [a scene](https://www.home-assistant.io/integrations/scene/) which will allow you to define how you want your devices to be and have Home Assistant perform the right action.

```yaml
automation:
  # Change the light in the kitchen and living room to 150 brightness and color red.
  triggers:
    - trigger: sun
      event: sunset
  actions:
    - action: light.turn_on
      target:
        entity_id:
          - light.kitchen
          - light.living_room
      data:
        brightness: 150
        rgb_color: [255, 0, 0]

automation 2:
  # Notify me on my mobile phone of an event
  triggers:
    - trigger: sun
      event: sunset
      offset: -00:30
  variables:
    notification_action: notify.paulus_iphone
  actions:
    # Actions are scripts so can also be a list of actions
    - action: "{{ notification_action }}"
      data:
        message: "Beautiful sunset!"
    - delay: 0:35
    - action: notify.notify
      data:
        message: "Oh wow you really missed something great."
```

YAML

Copy

Conditions can also be part of an action. You can combine multiple actions and conditions in a single action, and they will be processed in the order you put them in. If the result of a condition is false, the action will stop there so any action after that condition will not be executed.

```yaml
automation:
- alias: "Office at evening"
  triggers:
    - trigger: state
      entity_id: sensor.office_occupancy
      to: "on"
  actions:
    - action: notify.notify
      data:
        message: "Testing conditional actions"
    - condition: or
      conditions:
        - condition: numeric_state
          entity_id: sun.sun
          attribute: elevation
          below: 4
        - condition: state
          entity_id: sensor.office_illuminance
          below: 10
    - action: scene.turn_on
      target:
        entity_id: scene.office_at_evening
```

YAML

Copy

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/automation/action.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fautomation%2Faction%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fautomation%2Faction%2F%22&in=body "View given feedback for this page")
