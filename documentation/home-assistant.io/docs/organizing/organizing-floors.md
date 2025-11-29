A floor in Home Assistant is a logical grouping of areasAn area in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of devices and entities that are meant to match areas (or rooms) in the physical world: your home. For example, the `living room` area groups devices and entities in your living room.[ [Learn more]](https://www.home-assistant.io/docs/organizing/areas/) meant to match your home’s physical floors.
Devices and entities cannot be assigned to floors directly but to areas. Floors can be used in automationsAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/) and scriptsScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on.[ [Learn more]](https://www.home-assistant.io/docs/scripts/) as a target for actionsActions are used in several places in Home Assistant. As part of a script or automation, actions define what is going to happen once a trigger is activated. In scripts, an action is called _sequence_.[ [Learn more]](https://www.home-assistant.io/docs/automation/action/). For example, to turn off all the lights on the downstairs floor when you go to bed.
## Creating a floor 
Follow these steps to create a new floor.
  1. Go to [**Settings** > **Areas, labels & zones**](https://my.home-assistant.io/redirect/areas) and select **Create floor**.
  2. In the dialog, enter the floor details:
     * Give the floor a **Name** (required).
     * Add a floor **Level**. 
       * The number can be negative. For example for underground floors.
       * This number can later be used for sorting.
     * Add an icon (We use [Material icons](https://pictogrammers.com/library/mdi/)).
     * Add an **Alias**. 
       * Aliases are alternative names used in [voice assistants](https://www.home-assistant.io/voice_control/aliases/) to refer to an entity, area, or floor.
  3. Select **Add**.
**Result** : A new floor is created.
  4. You can now [assign areas to that floor](https://www.home-assistant.io/docs/organizing/areas/#assigning-areas-to-floors-and-add-labels).


## Deleting a floor 
Follow these steps to delete a floor. Areas that are assigned to a floor will become unassigned. AutomationsAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/) and scriptsScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on.[ [Learn more]](https://www.home-assistant.io/docs/scripts/) or voice assistants that used a floor as a target will no longer work as they no longer have a target.
  1. Go to [**Settings** > **Areas, labels & zones**](https://my.home-assistant.io/redirect/areas).
  2. Next to the floor, select the three dots **Delete floor**.
  3. If you have automationsAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home.[ [Learn more]](https://www.home-assistant.io/docs/automation/), scriptsScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on.[ [Learn more]](https://www.home-assistant.io/docs/scripts/), or voice assistants that used floors as a target, you will need to update these.


## Related topics 
  * [ Grouping your assets ](https://www.home-assistant.io/docs/organizing/)
  * [ Using floors in templates ](https://www.home-assistant.io/docs/configuration/templating/#floors)
  * [ Using floor alias for voice assistants ](https://www.home-assistant.io/voice_control/aliases/)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
