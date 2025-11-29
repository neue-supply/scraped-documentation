From the UI choose **Settings** which is located in the sidebar, then click on **Automations & Scenes** to go to the scene editor. Press the **Add Scene** button in the lower right corner to get started.
Choose a meaningful name for your scene.
Select all the devicesA device is a model representing a physical or logical unit that contains entities. (or entitiesAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) when advanced mode is enabled on your user profile) you want to include in your scene. The state of your devices will be saved, so it can be restored when you are finished creating your scene. Set the state of the devices to how you want them to be in your scene, this can be done by clicking on it and edit the state from the popup, or any other method that changes the state. On the moment you save the scene, all the states of your devices are stored in the scene. When you leave the editor the states of the devices are restored to the state from before you started editing. The menu on the top-right has options to **Duplicate scene** and **Delete scene**.
A scene can be called in automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/) action and scriptsScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on.[ [Learn more]](https://www.home-assistant.io/docs/scripts/) using a turn on scene actionActions are used in several places in Home Assistant. As part of a script or automation, actions define what is going to happen once a trigger is activated. In scripts, an action is called _sequence_.[ [Learn more]](https://www.home-assistant.io/docs/automation/action/):
```
action: scene.turn_on
target:
  entity_id: scene.my_unique_id
```

YAML
Copy
## Updating your configuration to use the editor 
First, check that you have activated the configuration editor.
```
# Activate the configuration editor
config:
```

YAML
Copy
The scene editor reads and writes to the file `scenes.yaml` in the root of your [configuration](https://www.home-assistant.io/docs/configuration/) folder. Currently, both the name of this file and its location are fixed. Make sure that you have set up the scene integration to read from it:
```
# Configuration.yaml example
scene: !include scenes.yaml
```

YAML
Copy
If you still want to use your old scene section, add a label to the old entry:
```
scene old:
  - name: ...
```

YAML
Copy
You can use the `scene:` and `scene old:` sections at the same time:
  * `scene old:` to keep your manual designed scenes
  * `scene:` to save the scene created by the online editor


```
scene: !include scenes.yaml
scene old: !include_dir_merge_list scenes
```

YAML
Copy
## Migrating your scenes to scenes.yaml 
If you want to migrate your old scenes to use the editor, you’ll have to copy them to `scenes.yaml`. Make sure that `scenes.yaml` remains a list! For each scene that you copy over, you’ll have to add an `id`. This can be any string as long as it’s unique.
For example:
```
# Example scenes.yaml entry
- id: my_unique_id # <-- Required for editor to work.
  name: Romantic
  entities:
    light.tv_back_light: on
    light.ceiling:
      state: on
      xy_color: [0.33, 0.66]
      brightness: 200
```

YAML
Copy
Any comments in the YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files.[ [Learn more]](https://www.home-assistant.io/docs/configuration/yaml/) file will be lost and templates will be reformatted when you update a scene via the editor.
####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
