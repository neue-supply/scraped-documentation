An area in Home Assistant is a logical grouping of devicesA device is a model representing a physical or logical unit that contains entities. and entitiesAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) that are meant to match areas (or rooms) in the physical world of your home.
For example, the “Living room” area groups devices and entities in your living room. Areas allow you to target an entire group of devices with an action. For example, turning off all the lights in the living room. Areas can be assigned to floorsA floor in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of areas that are meant to match the physical floors in your home. Devices & entities are not assigned to floors but to areas. Floors can be used in automations and scripts as a target for actions. For example, to turn off all the lights on the downstairs floor when you go to bed.[ [Learn more]](https://www.home-assistant.io/docs/organizing/floors/). Areas can also be used to automatically generate cards, such as the [Area card](https://www.home-assistant.io/dashboards/area/).
## Creating an area 
Follow these steps to create a new area from the **Areas** view.
  1. Go to [**Settings** > **Areas, labels & zones**](https://my.home-assistant.io/redirect/areas) and select **Create area**.
  2. In the dialog, enter the area details:
     * Give the area a **Name** (required).
     * Add an icon (We use [Material icons](https://pictogrammers.com/library/mdi/)).
     * Assign the area to a floor. 
       * If you have not created floors yet, you can [create a new floor](https://www.home-assistant.io/docs/organizing/floors/#creating-a-floor).
       * The number can be negative. For example for underground floors.
       * This number can later be used for sorting.
     * Add an image representing that area.
     * Add an **Alias**. 
       * Aliases are alternative names used in [voice assistants](https://www.home-assistant.io/voice_control/aliases/) to refer to an area, entity, or floor.
  3. Select **Add**.
**Result** : A new area is created.


## Assigning areas to floors and add labels 
If an area has not yet been assigned to a floorA floor in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of areas that are meant to match the physical floors in your home. Devices & entities are not assigned to floors but to areas. Floors can be used in automations and scripts as a target for actions. For example, to turn off all the lights on the downstairs floor when you go to bed.[ [Learn more]](https://www.home-assistant.io/docs/organizing/floors/), it is shown in the **Unassigned areas** section. Follow these steps to assign an area to a floor.
  1. Go to [**Settings** > **Areas, labels & zones**](https://my.home-assistant.io/redirect/areas) and select **Create area**.
  2. On the area card, select the edit 
  3. In the dialog, select the floorA floor in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of areas that are meant to match the physical floors in your home. Devices & entities are not assigned to floors but to areas. Floors can be used in automations and scripts as a target for actions. For example, to turn off all the lights on the downstairs floor when you go to bed.[ [Learn more]](https://www.home-assistant.io/docs/organizing/floors/) and add labelsLabels in Home Assistant allow [grouping](https://www.home-assistant.io/docs/organizing/) elements irrespective of their physical location or type. Labels can be assigned to areas, devices, entities, automations, scenes, scripts, and helpers. Labels can be used in automations and scripts as a target for actions. Labels can also be used to filter data.[ [Learn more]](https://www.home-assistant.io/docs/organizing/labels/) if you like.


## Assigning an area to multiple items 
You can assign an area to multiple items at once in the automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/), sceneScenes capture the states you want certain entities to be. For example, a scene can specify that light A should be turned on and light B should be bright red.[ [Learn more]](https://www.home-assistant.io/integrations/scene/), scriptScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on.[ [Learn more]](https://www.home-assistant.io/docs/scripts/), and deviceA device is a model representing a physical or logical unit that contains entities. pages.
  1. Depending on what you want to assign, go to one of the following pages:
     * For automations, scripts, or scenes [**Settings** > **Automations & Scenes**](https://my.home-assistant.io/redirect/automations) and open the respective tab.
     * For devices, go to [**Settings** > **Devices & services** > **Devices**](https://my.home-assistant.io/redirect/devices).
  2. In the list, [select all the items](https://www.home-assistant.io/docs/organizing/tables#selecting-multiple-items-in-a-table) you want to assign to an area.
  3. In the top right corner, select **Move to area** and select the target area from the list.


## Editing an area 
Follow these steps to edit an area.
  1. Go to [**Settings** > **Areas, labels & zones**](https://my.home-assistant.io/redirect/areas) and on the area card, select the edit 
  2. In the dialog, adjust the area details you want to change: 
     * Edit the area **Name**.
     * Add an icon (We use [Material icons](https://pictogrammers.com/library/mdi/)).
     * Assign the area to a floor. 
       * If you have not created floors yet, you can [create a new one](https://www.home-assistant.io/docs/organizing/floors/#creating-a-floor).
       * The number can be negative. For example for underground floors.
       * This number can later be used for sorting.
     * Add an image representing that area.
     * Add an **Alias**. 
       * Aliases are alternative names used in [voice assistants](https://www.home-assistant.io/voice_control/aliases/) to refer to an area, entity, or floor.


## Using the Areas dashboard 
Once you have assigned your entities to areas, you can use the **Areas** dashboard. The **Areas** dashboard is a pre-populated dashboard that shows your entitiesAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) grouped by areas. To learn how, refer to the documentation on the [Areas dashboard](https://www.home-assistant.io/dashboards/dashboards/#areas-dashboard).
Screenshot of the Areas default dashboard. 
## Deleting an area 
Follow these steps to delete an area. It will be removed from all the floors it was assigned to. All the devices that were assigned to this area will become unassigned. If you used this area in automations or script as targets, or with voice assistant, these will no longer work.
  1. Go to [**Settings** > **Areas, labels & zones**](https://my.home-assistant.io/redirect/areas) and select the area card.
  2. In the top right corner, select the three dots **Delete**.
  3. If you used this area in automations or script as targets, or with voice assistant, they will no longer work.
     * You can adjust or delete the related scripts or automations.
  4. If you still had devices in that area, they are no longer assigned to any room.
     * If you have moved the devices, you can now reassign them to a new area.


## Related topics 
  * [ Grouping your assets ](https://www.home-assistant.io/docs/organizing/)
  * [ Using areas in template ](https://www.home-assistant.io/docs/configuration/templating/#areas)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
