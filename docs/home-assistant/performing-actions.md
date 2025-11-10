---
title: Performing actions - Home Assistant
description: Instructions on how to perform actions in Home Assistant.
source_url: https://www.home-assistant.io/docs/scripts/perform-actions/
source_domain: www.home-assistant.io
scraped_at: 2025-11-10T03:00:05.222Z
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


  * [The basics](https://www.home-assistant.io/docs/scripts/perform-actions/#the-basics)
  * [Targeting areas and devices](https://www.home-assistant.io/docs/scripts/perform-actions/#targeting-areas-and-devices)
  * [Passing data to the action](https://www.home-assistant.io/docs/scripts/perform-actions/#passing-data-to-the-action)
  * [Use templates to decide which action to perform](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-decide-which-action-to-perform)
  * [Using the Actions developer tool](https://www.home-assistant.io/docs/scripts/perform-actions/#using-the-actions-developer-tool)
  * [Use templates to determine the attributes](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-determine-the-attributes)
  * [Use templates to handle response data](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-handle-response-data)
  * [homeassistant actions](https://www.home-assistant.io/docs/scripts/perform-actions/#homeassistant-actions)


[Home](https://www.home-assistant.io/) ▸ [Documentation](https://www.home-assistant.io/docs/) ▸ [Scripts](https://www.home-assistant.io/docs/scripts/) ▸ 
#  Performing actions 
Various integrations allow performing actionsActions are used in several places in Home Assistant. As part of a script or automation, actions define what is going to happen once a trigger is activated. In scripts, an action is called _sequence_.[ [Learn more]](https://www.home-assistant.io/docs/automation/action/) when a certain event occurs. The most common one is performing an action when an automation triggerA trigger is a set of values or conditions of a platform that are defined to cause an automation to run.[ [Learn more]](https://www.home-assistant.io/docs/automation/trigger/) happens. But an action can also be called from a scriptScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on.[ [Learn more]](https://www.home-assistant.io/docs/scripts/), a dashboard, or via voice command devices such as Amazon Echo.
The configuration options to perform action are the same between all integrations and are described on this page.
Examples on this page will be given as part of an automation integration configuration but different approaches can be used for other integrations too.
Use the “Actions” tab under **Developer tools** to discover available actions.
### The basics [](https://www.home-assistant.io/docs/scripts/perform-actions/#the-basics)
Perform the action `homeassistant.turn_on` on the entityAn entity represents a sensor, actor, or function in Home Assistant. Entities are used to monitor physical properties or to control other entities. An entity is usually part of a device or a service.[ [Learn more]](https://www.home-assistant.io/docs/configuration/entities_domains/) `group.living_room`. This will turn all members of `group.living_room` on. You can also use `entity_id: all` and it will turn on all possible entities.
```
action: homeassistant.turn_on
target:
  entity_id: group.living_room
```

YAML
Copy
### Targeting areas and devices [](https://www.home-assistant.io/docs/scripts/perform-actions/#targeting-areas-and-devices)
Instead of targeting an entity, you can also target an areaAn area in Home Assistant is a [logical grouping](https://www.home-assistant.io/docs/organizing/) of devices and entities that are meant to match areas (or rooms) in the physical world: your home. For example, the `living room` area groups devices and entities in your living room.[ [Learn more]](https://www.home-assistant.io/docs/organizing/areas/) or deviceA device is a model representing a physical or logical unit that contains entities.. Or a combination of these. This is done with the `target` key.
A `target` is a map that contains at least one of the following: `area_id`, `device_id`, `entity_id`. Each of these can be a list. The values should be lower-cased.
The following example uses a single action to turn on the lights in the living room area, 2 additional light devices and 2 additional light entities:
```
action: light.turn_on
target:
  area_id: living_room
  device_id:
    - ff22a1889a6149c5ab6327a8236ae704
    - 52c050ca1a744e238ad94d170651f96b
  entity_id:
    - light.hallway
    - light.landing
```

YAML
Copy
### Passing data to the action [](https://www.home-assistant.io/docs/scripts/perform-actions/#passing-data-to-the-action)
You can also specify other parameters beside the entity to target. For example, the `light.turn_on` action allows specifying the brightness.
```
action: light.turn_on
target:
  entity_id: group.living_room
data:
  brightness: 120
  rgb_color: [255, 0, 0]
```

YAML
Copy
A full list of the parameters for an action can be found on the documentation page of each integration, in the same way as it’s done for the `light.turn_on` [action](https://www.home-assistant.io/integrations/light/#action-lightturn_on).
### Use templates to decide which action to perform [](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-decide-which-action-to-perform)
You can use [templating](https://www.home-assistant.io/docs/configuration/templating/) support to dynamically choose which action to perform. For example, you can perform a certain action based on if a light is on.
```
action: >
  {% if states('sensor.temperature') | float > 15 %}
    switch.turn_on
  {% else %}
    switch.turn_off
  {% endif %}
entity_id: switch.ac
```

YAML
Copy
### Using the Actions developer tool [](https://www.home-assistant.io/docs/scripts/perform-actions/#using-the-actions-developer-tool)
You can use the **Actions** developer tool to test data to pass in an action. For example, you may test turning on or off a ‘group’ (See [groups](https://www.home-assistant.io/integrations/group/) for more info)
To turn a group on or off, pass the following info:
  * Domain: `homeassistant`
  * Action: `turn_on`
  * Action data: `{ "entity_id": "group.kitchen" }`


### Use templates to determine the attributes [](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-determine-the-attributes)
Templates can also be used for the data that you pass to the action.
```
action: thermostat.set_temperature
target:
  entity_id: >
    {% if is_state('device_tracker.paulus', 'home') %}
      thermostat.upstairs
    {% else %}
      thermostat.downstairs
    {% endif %}
data:
  temperature: "{{ 22 - distance(states.device_tracker.paulus) }}"
```

YAML
Copy
You can use a template returning a native dictionary as well, which is useful if the attributes to be set depend on the situation.
```
action: climate.set_temperature
data: >
  {% if states('sensor.temperature_living') < 19 %}
    {"hvac_mode": "heat", "temperature": 19 }
  {% else %}
    {"hvac_mode": "auto" }
  {% endif %}
```

YAML
Copy
### Use templates to handle response data [](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-handle-response-data)
Some actions may respond with data that can be used in automation. This data is called _action response data_. Action response data is typically used for data that is dynamic or large and which may not be suited for use in entity state. Examples of action response data are upcoming calendar events for the next week or detailed driving directions.
Templates can also be used for handling response data. The action can specify a `response_variable`. This is the [variable](https://www.home-assistant.io/docs/scripts/#variables) that contains the response data. You can define any name for your `response_variable`. This example performs an action and stores the response in the variable called `agenda`.
```
action: calendar.get_events
target:
  entity_id: calendar.school
data:
  duration:
    hours: 24
response_variable: agenda
```

YAML
Copy
You may then use the response data in the variable `agenda` in another action in the same script. The example below sends a notification using the response data.
Which data fields can be used in an action depends on the type of notification that is used.
```
action: notify.gmail_com
data:
  target: "gduser1@workspacesamples.dev"
  title: "Daily agenda for {{ now().date() }}"
  message: >-
    Your agenda for today:
    <p>
    {% for event in agenda['calendar.school'].events %}
    {{ event.start}}: {{ event.summary }}<br>
    {% endfor %}
    </p>
```

YAML
Copy
### homeassistant actions [](https://www.home-assistant.io/docs/scripts/perform-actions/#homeassistant-actions)
There are four `homeassistant` actions that aren’t tied to any single domain, these are:
  * `homeassistant.turn_on` - Turns on an entity (that supports being turned on), for example an `automation`, `switch`, etc.
  * `homeassistant.turn_off` - Turns off an entity (that supports being turned off), for example an `automation`, `switch`, etc.
  * `homeassistant.toggle` - Turns off an entity that is on, or turns on an entity that is off (that supports being turned on and off)
  * `homeassistant.update_entity` - Request the update of an entity, rather than waiting for the next scheduled update, for example [Google travel time](https://www.home-assistant.io/integrations/google_travel_time/) sensor, a [template sensor](https://www.home-assistant.io/integrations/template/), or a [light](https://www.home-assistant.io/integrations/light/)


Complete action details and examples can be found on the [Home Assistant integration](https://www.home-assistant.io/integrations/homeassistant#actions) page.
####  **Help us improve our documentation**[](https://www.home-assistant.io/docs/scripts/perform-actions/#feedback_section)
Suggest an edit to this page, or provide/view feedback for this page. 
  * [](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/scripts/perform-actions.markdown "Edit this page")
  * [](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fscripts%2Fperform-actions%2F&version=2025.11.1&labels=current "Provide feedback on this page")
  * [](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fscripts%2Fperform-actions%2F%22&in=body "View given feedback for this page")


  * [Overview ](https://www.home-assistant.io/docs/) | [FAQ ](https://www.home-assistant.io/faq/) | [Glossary ](https://www.home-assistant.io/docs/glossary/)
  * [Automations ](https://www.home-assistant.io/docs/automation/)
    * [Basic automations ](https://www.home-assistant.io/docs/automation/basics/)
    * [Scenes ](https://www.home-assistant.io/docs/scene/)
    * [Blueprints ](https://www.home-assistant.io/docs/blueprint/)
    * [Scripts ](https://www.home-assistant.io/docs/scripts/)
      * [Actions ](https://www.home-assistant.io/docs/scripts/perform-actions/)
      * [Conditions ](https://www.home-assistant.io/docs/scripts/conditions/)
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


  * [The basics](https://www.home-assistant.io/docs/scripts/perform-actions/#the-basics)
  * [Targeting areas and devices](https://www.home-assistant.io/docs/scripts/perform-actions/#targeting-areas-and-devices)
  * [Passing data to the action](https://www.home-assistant.io/docs/scripts/perform-actions/#passing-data-to-the-action)
  * [Use templates to decide which action to perform](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-decide-which-action-to-perform)
  * [Using the Actions developer tool](https://www.home-assistant.io/docs/scripts/perform-actions/#using-the-actions-developer-tool)
  * [Use templates to determine the attributes](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-determine-the-attributes)
  * [Use templates to handle response data](https://www.home-assistant.io/docs/scripts/perform-actions/#use-templates-to-handle-response-data)
  * [homeassistant actions](https://www.home-assistant.io/docs/scripts/perform-actions/#homeassistant-actions)


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

