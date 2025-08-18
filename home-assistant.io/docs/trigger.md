---
title: "Trigger"
source_url: "https://www.home-assistant.io/docs/automation/trigger"
crawled_date: "2025-08-18"
domain: "home-assistant.io"
categories:
  - home-assistant-io
  - documentation
  - docs
tags:
  - documentation
  - scraped
---

# Trigger

> **Source:** [https://www.home-assistant.io/docs/automation/trigger](https://www.home-assistant.io/docs/automation/trigger)  
> **Domain:** home-assistant.io  
> **Last Updated:** 2025-08-18

# Automation Trigger - Home Assistant Automations in Home Assistant allow you to
automatically respond to things that happen in and around your home. Triggers
are what start the processing of an automation rule. When any of the
automation’s triggers becomes true (trigger fires), Home Assistant will validate
the conditions, if any, and call the action. ## Key Concepts ### Triggers An
automation can be triggered by: - An **event**: Every time something happens in
Home Assistant, an event is fired. Events can be used to trigger automations or
scripts. - A certain **entity state**: The state holds the information of
interest of an entity, for example, if a light is on or off. ### Trigger Types -
**Event Trigger**: Fires when an event is received. - **Home Assistant
Trigger**: Fires when Home Assistant starts up or shuts down. - **MQTT
Trigger**: Fires when a specific message is received on a given MQTT topic. -
**Numeric State Trigger**: Fires when the numeric value of an entity’s state
crosses a given threshold. - **State Trigger**: Fires when the state of any of
the given entities changes. - **Sun Trigger**: Fires when the sun is setting or
rising. - **Tag Trigger**: Fires when a tag is scanned. - **Template Trigger**:
Fires based on the evaluation of a template. - **Time Trigger**: Fires at a
specific time or on specific dates. ## Trigger ID All triggers can be assigned
an optional `id`. If the ID is omitted, it will instead be set to the index of
the trigger. The `id` can be referenced from trigger conditions and actions. ###
Example ```yaml automation: triggers: - trigger: event: event event_type:
"MY_CUSTOM_EVENT" id: "custom_event" ``` ## Trigger Variables There are two
types of variables available for triggers: 1. Variables that are set when the
trigger fires. 2. Variables that are available when attaching a trigger. ###
Example ```yaml automation: trigger_variables: my_event: example_event triggers:
- trigger: event: event_type: "{{ my_event }}" variables: name: "{{
trigger.event.data.name }}" ``` ## Event Trigger An event trigger fires when an
event is received. You can match events on just the event name or also require
specific event data or context to be present. ### Example ```yaml automation:
triggers: - trigger: event: event_type: "MY_CUSTOM_EVENT" event_data: mood:
happy ``` ## Home Assistant Trigger Fires when Home Assistant starts up or shuts
down. ### Example ```yaml automation: triggers: - trigger: homeassistant: event:
start ``` ## MQTT Trigger Fires when a specific message is received on a given
MQTT topic. ### Example ```yaml automation: triggers: - trigger: mqtt: topic:
"living_room/switch/ac" payload: "on" ``` ## Numeric State Trigger Fires when
the numeric value of an entity’s state crosses a given threshold. ### Example
```yaml automation: triggers: - trigger: numeric_state: entity_id:
sensor.temperature above: 17 below: 25 ``` ## State Trigger Fires when the state
of any of the given entities changes. ### Example ```yaml automation: triggers:
- trigger: state: entity_id: - device_tracker.paulus -
device_tracker.anne_therese from: "not_home" to: "home" for: minutes: 1 ``` ##
Sun Trigger ### Sunset / Sunrise Trigger Fires when the sun is setting or
rising. ### Example ```yaml automation: triggers: - trigger: sun: event: sunset
offset: "-00:45:00" ``` ## Tag Trigger Fires when a tag is scanned. ### Example
```yaml automation: triggers: - trigger: tag: tag_id: "A7-6B-90-5F" ``` ##
Template Trigger Template triggers evaluate a template when any of the
recognized entities change state. ### Example ```yaml automation: triggers: -
trigger: template: value_template: "{% if is_state('device_tracker.paulus',
'home') %}true{% endif %}" for: "00:01:00" ``` ## Time Trigger The time trigger
is configured to fire once a day at a specific time. ### Example ```yaml
automation: triggers: - trigger: time: at: "15:32:00" ``` ### Input Datetime The
entity ID of an input datetime can also be used. ### Example ```yaml automation:
triggers: - trigger: state: entity_id: binary_sensor.motion to: "on" ``` ###
Multiple Times Multiple times can be provided in a list. ### Example ```yaml
automation: triggers: - trigger: time: at: - input_datetime.leave_for_work -
"18:30:00" ``` ### Weekday Filtering Time triggers can be filtered to fire only
on specific days of the week. ### Example ```yaml automation: triggers: -
trigger: time: at: "08:00:00" weekday: "mon" ```

# Automation Triggers in Home Assistant ## Time Trigger The time trigger allows
you to set automations based on specific times. ### Example ```yaml automation:
- triggers: - trigger: time at: input_datetime.turn_off_ac ``` ## Sensors of
Datetime Device Class The Entity ID of a sensor with the “timestamp” device
class can be used in automations. ### Example ```yaml automation: - triggers: -
trigger: time at: sensor.phone_next_alarm ``` ## Sensors of Datetime Device
Class with Offsets Offsets can be added to the sensor value to trigger actions
before or after a specified time. ### Example ```yaml automation: - triggers: -
trigger: time at: sensor.phone_next_alarm offset: -00:05:00 ``` ## Multiple
Times You can provide multiple times in a list for triggers. ### Example ```yaml
automation: triggers: - trigger: time at: - input_datetime.leave_for_work -
"18:30:00" - entity_id: sensor.bus_arrival offset: "-00:10:00" ``` ## Weekday
Filtering Time triggers can be filtered to fire only on specific days of the
week using the `weekday` option. ### Single Weekday Example ```yaml automation:
- triggers: - trigger: time at: "08:00:00" weekday: "mon" ``` ### Multiple
Weekdays Example ```yaml automation: - triggers: - trigger: time at: "06:30:00"
weekday: - "mon" - "tue" - "wed" - "thu" - "fri" ``` ## Time Pattern Trigger The
time pattern trigger matches if the hour, minute, or second of the current time
matches a specific value. ### Example ```yaml automation: - triggers: - trigger:
time_pattern minutes: 5 ``` ## Webhook Trigger Webhook triggers fire when a web
request is made to the webhook endpoint. ### Example ```yaml automation: -
triggers: - trigger: webhook webhook_id: "some_hook_id" allowed_methods: - POST
- PUT ``` ### Sending a Webhook You can run this automation by sending an HTTP
POST request: ```bash curl -X POST -d 'key=value&key2;=value2' http://your-home-
assistant:8123/api/webhook/some_hook_id ``` ## Zone Trigger Zone triggers fire
when an entity enters or leaves a specified zone. ### Example ```yaml
automation: - triggers: - trigger: zone entity_id: person.paulus zone: zone.home
event: enter ``` ## Geolocation Trigger Geolocation triggers fire when an entity
appears in or disappears from a zone. ### Example ```yaml automation: -
triggers: - trigger: geo_location source: nsw_rural_fire_service_feed zone:
zone.bushfire_alert_zone event: enter ``` ## Calendar Trigger Calendar triggers
fire when a calendar event starts or ends. ### Example ```yaml automation: -
triggers: - trigger: calendar event: start entity_id: calendar.light_schedule
offset: "-00:05:00" ``` ## Sentence Trigger A sentence trigger fires when a
voice assistant matches a specific sentence. ### Example ```yaml automation: -
triggers: - trigger: conversation command: - "[it's ]party time" - "happy (new
year|birthday)" ``` ## Multiple Triggers You can specify multiple triggers for
the same rule. ### Example ```yaml automation: - triggers: - trigger:
time_pattern minutes: 5 - trigger: sun event: sunset ``` ## Disabling a Trigger
You can disable individual triggers in an automation. ### Example ```yaml
automation: - triggers: - enabled: false trigger: sun event: sunset - trigger:
time at: "15:32:00" ``` ## Merging Lists of Triggers This feature allows you to
insert a second list of triggers into the main trigger list. ### Example ```yaml
blueprint: name: Nested Trigger Blueprint domain: automation input: usertrigger:
selector: trigger: triggers: - trigger: event event_type: manual_event -
triggers: !input usertrigger ```



---

## Additional Resources

- [home-assistant.io Documentation](https://home-assistant.io/docs)
- [Source Page](https://www.home-assistant.io/docs/automation/trigger)

---

*This page was automatically generated from home-assistant.io.*