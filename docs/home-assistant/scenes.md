---
title: Scenes - Home Assistant
description: Instructions on how to setup scenes within Home Assistant.
source_url: https://www.home-assistant.io/docs/scene
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:08:04.335Z
---

You can create scenes that capture the states you want certain entities to be. For example, a scene can specify that light A should be turned on and light B should be bright red. Scenes are available as an entity through the standalone [Scene integration](https://www.home-assistant.io/integrations/scene/) but can also be embedded in automationsAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home. [\[Learn more\]](https://www.home-assistant.io/docs/automation/) and scriptsScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on. [\[Learn more\]](https://www.home-assistant.io/docs/scripts/).

```yaml
# Example configuration.yaml entry
scene:
  - name: Romantic
    entities:
      light.tv_back_light: "on"
      light.ceiling:
        state: "on"
        xy_color: [0.33, 0.66]
        brightness: 200
  - name: Movies
    entities:
      light.tv_back_light:
        state: "on"
        brightness: 125
      light.ceiling: off
      media_player.sony_bravia_tv:
        state: "on"
        source: HDMI 1
```

YAML

Copy

## How to configure your scene

In the scene you define in your YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/yaml/) files, please ensure you use
all required parameters as listed below.

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

name stringRequired

Friendly name of the scene.

entities listRequired

Entities to control and their desired state.

As you can see, there are two ways to define the states of each `entity_id`:

- Define the `state` directly with the entity. Be aware, that `state` needs to be defined.
- Define a complex state with its attributes. You can see all attributes available for a particular entity under `developer-tools -> state`.

Scenes can be activated using the action `scene.turn_on` (there is no ‘scene.turn\_off’ action).

```yaml
# Example automation
automation:
  triggers:
    - trigger: state
      entity_id: device_tracker.sweetheart
      from: "not_home"
      to: "home"
  actions:
    - action: scene.turn_on
      target:
        entity_id: scene.romantic
```

YAML

Copy

## Applying a scene without defining it

With the `scene.apply` action you are able to apply a scene without first defining it via configuration. Instead, you pass the states as part of the data. The format of the data is the same as the `entities` field in a configuration.

```yaml
# Example automation
automation:
  triggers:
    - trigger: state
      entity_id: device_tracker.sweetheart
      from: "not_home"
      to: "home"
  actions:
    - action: scene.apply
      data:
        entities:
          light.tv_back_light:
            state: "on"
            brightness: 100
          light.ceiling: off
          media_player.sony_bravia_tv:
            state: "on"
            source: "HDMI 1"
```

YAML

Copy

## Using scene transitions

Both the `scene.apply` and `scene.turn_on` actions support setting a transition,
which enables you to smoothen the transition to the scene.

This is an example of an automation that sets a romantic scene, in which the
light will transition to the scene in 2.5 seconds.

```yaml
# Example automation
automation:
  triggers:
    - trigger: state
      entity_id: device_tracker.sweetheart
      from: "not_home"
      to: "home"
  actions:
    - action: scene.turn_on
      target:
        entity_id: scene.romantic
      data:
        transition: 2.5
```

YAML

Copy

Transitions are currently only support by lights, which in their turn, have
to support it as well. However, the scene itself does not have to consist of
only lights to have a transition set.

## Reloading scenes

Whenever you make a change to your scene configuration, you can call the `scene.reload` action to reload the scenes.

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/scene.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fscene%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fscene%2F%22&in=body "View given feedback for this page")
