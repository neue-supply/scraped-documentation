After adding a new device, you might find the automatically assigned entity ID too technical and the entity lacking a friendly name. You can personalize these elements to better fit your naming conventions or modify other attributes like the icon.
To change entity attributes, follow these steps:
  1. Go to [**Settings** > **Devices & services** > **Entities**](https://my.home-assistant.io/redirect/entities) and select the entity from the list.
  2. In the top-right corner, select the 
  3. Enter or edit the attributes:
     * For example, the entity ID here could be shortened to `binary_sensor.lumi_sensor_aq2_opening`.
       * You can use lowercase letters, numbers, and underscores.
       * The ID must not start or end with an underscore.
       * To undo the change and revert the ID to the default, select the 
         * **Note** : You can only reset the ID to the default ID for entities with a unique ID. 
           * IDs of entities that are disabled or for which the integration is not set up cannot be reverted.
       * To revert all the entity IDs for a device, on the device page, select the three dots **Recreate entity IDs**.
       * **Result** : This resets the entity ID and applies the current default naming convention.
         * The terms used to generate the entity ID depends on a few factors. Prioritization is as follows: 
           1. If you changed the friendly name of the entity, the friendly name will be used.
           2. The entity ID suggested by the integration (just a few integrations do this).
           3. The default name in the user language, if using Latin script. 
              * If the something other than Latin script is used, the entity ID is based on the English default name.
              * This is because entity IDs must use lowercase alphanumeric characters in the range of [a-z,1-9].
     * Enter or edit the friendly name.
       * In this example, this would change “Opening”.
     * If needed, from the **Shown as** menu, you can select a different [device class](https://www.home-assistant.io/integrations/homeassistant/#device-class).
     * If you like, add a [label](https://www.home-assistant.io/docs/organizing/labels/).
  4. To apply the changes, select **Update**.
  5. If you have used this entity in automations and scripts, you need to rename the entity ID there, too.
     * Go to [**Settings** > **Automations & Scenes**](https://my.home-assistant.io/redirect/automations) open the respective tab and find your automation or script.


### Customizing an entity in YAML 
If your entity is not supported, or you could not customize what you need via the user interface, you need to edit the settings in your `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI.[ [Learn more]](https://www.home-assistant.io/docs/configuration/) file. For a detailed description of the entity configuration variables and [device class](https://www.home-assistant.io/integrations/homeassistant/#device-class) information, refer to the [Home Assistant Core integration documentation](https://www.home-assistant.io/integrations/homeassistant/).
## Related topics 
  * [ Home Assistant Core Integration ](https://www.home-assistant.io/integrations/homeassistant/)
  * [ Configuration.yaml file ](https://www.home-assistant.io/docs/configuration/)
  * [ Troubleshooting your configuration ](https://www.home-assistant.io/docs/configuration/troubleshooting/)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
