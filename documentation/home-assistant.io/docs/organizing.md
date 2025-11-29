Once you have more devices, you may want to target entire groups of devices in automations. It also becomes more challenging to find items in lists.
There are a few tools to group your assets: [Areas](https://www.home-assistant.io/docs/organizing/#area), [floors](https://www.home-assistant.io/docs/organizing/#floor), [labels](https://www.home-assistant.io/docs/organizing/#labels), [categories](https://www.home-assistant.io/docs/organizing/#category) and [group integration](https://www.home-assistant.io/docs/organizing/#group-integration).
Taxonomy | Automation target | Entity can have multiple  
---|---|---  
Area  
Floor  
Label  
Category  
Group Integration  
## Area 
  * Groups devicesA device is a model representing a physical or logical unit that contains entities. and entitiesAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/).
  * Can be assigned to one floor.
  * Reflects a physical area (or room) in your home.
  * Can be used in automations: Allows targeting an entire group of devices with an action. For example, turning off all the lights in the living room.
  * Areas can also be used to automatically generate cards, such as the [Area card](https://www.home-assistant.io/dashboards/area/).


## Floor 
  * Groups areas.
  * DevicesA device is a model representing a physical or logical unit that contains entities. and entitiesAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) cannot be assigned to floors, but to areas only.
  * Can have multiple areas.
  * Can be used in automations and scripts as a target for actions. For example, to turn off all the lights on the downstairs floor when you go to bed.


## Labels 
  * Can be assigned to areas, devices, entities, automations, scenes, scripts, and helpers.
  * Can be used in automations and scripts as a target for actions.
  * Labels can also be used to filter data in tables. For example, you can filter the list of devices to show only devices with the label `heavy energy usage` or turn these devices off when there is not a lot of solar energy available.


## Category 
  * Groups items in a table.
  * Categories are unique for each table. The automations page can have different categories than the scene, scripts, or helpers settings page.


## Group Integration 
  * Designed to combine multiple entities into one entity representing the group.
  * The combined entity can also have an area and labels.
  * Can be used in automations and scripts as a target for actions.
  * Does not assist with organizing entities in the UI like the other methods above. For example, you cannot use group integration to sort or filter other entities.


## Related topics 
  * [ Group integration ](https://www.home-assistant.io/integrations/group/)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
