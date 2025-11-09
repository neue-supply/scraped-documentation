---
title: Selectors - Home Assistant
description: Documentation on available selectors.
source_url: https://www.home-assistant.io/docs/blueprint/selectors
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:04:51.517Z
---

Selectors can be used to specify what values are accepted for a blueprint
input. The selector also defines how the input is shown in the user interface.

Some selectors can, for example, show a toggle button to turn something
on or off, while another select can filter a list of devices to show
only devices that have motion-sensing capabilities.

Having good selectors set on your blueprint automation inputs makes a
blueprint easier to use from the UI.

The following selectors are currently available:

- [Action selector](https://www.home-assistant.io/docs/blueprint/selectors/#action-selector)
- [Add-on selector](https://www.home-assistant.io/docs/blueprint/selectors/#add-on-selector)
- [Area selector](https://www.home-assistant.io/docs/blueprint/selectors/#area-selector)
- [Attribute selector](https://www.home-assistant.io/docs/blueprint/selectors/#attribute-selector)
- [Assist pipeline selector](https://www.home-assistant.io/docs/blueprint/selectors/#assist-pipeline-selector)
- [Backup location selector](https://www.home-assistant.io/docs/blueprint/selectors/#backup-location-selector)
- [Boolean selector](https://www.home-assistant.io/docs/blueprint/selectors/#boolean-selector)
- [Color temperature selector](https://www.home-assistant.io/docs/blueprint/selectors/#color-temperature-selector)
- [Condition selector](https://www.home-assistant.io/docs/blueprint/selectors/#condition-selector)
- [Config entry selector](https://www.home-assistant.io/docs/blueprint/selectors/#config-entry-selector)
- [Constant selector](https://www.home-assistant.io/docs/blueprint/selectors/#constant-selector)
- [Conversation agent selector](https://www.home-assistant.io/docs/blueprint/selectors/#conversation-agent-selector)
- [Country selector](https://www.home-assistant.io/docs/blueprint/selectors/#country-selector)
- [Date selector](https://www.home-assistant.io/docs/blueprint/selectors/#date-selector)
- [Date & time selector](https://www.home-assistant.io/docs/blueprint/selectors/#date--time-selector)
- [Device selector](https://www.home-assistant.io/docs/blueprint/selectors/#device-selector)
- [Duration selector](https://www.home-assistant.io/docs/blueprint/selectors/#duration-selector)
- [Entity selector](https://www.home-assistant.io/docs/blueprint/selectors/#entity-selector)
- [Floor selector](https://www.home-assistant.io/docs/blueprint/selectors/#floor-selector)
- [Icon selector](https://www.home-assistant.io/docs/blueprint/selectors/#icon-selector)
- [Label selector](https://www.home-assistant.io/docs/blueprint/selectors/#label-selector)
- [Language selector](https://www.home-assistant.io/docs/blueprint/selectors/#language-selector)
- [Location selector](https://www.home-assistant.io/docs/blueprint/selectors/#location-selector)
- [Media selector](https://www.home-assistant.io/docs/blueprint/selectors/#media-selector)
- [Number selector](https://www.home-assistant.io/docs/blueprint/selectors/#number-selector)
- [Object selector](https://www.home-assistant.io/docs/blueprint/selectors/#object-selector)
- [QR code selector](https://www.home-assistant.io/docs/blueprint/selectors/#qr-code-selector)
- [RGB color selector](https://www.home-assistant.io/docs/blueprint/selectors/#rgb-color-selector)
- [Select selector](https://www.home-assistant.io/docs/blueprint/selectors/#select-selector)
- [State selector](https://www.home-assistant.io/docs/blueprint/selectors/#state-selector)
- [Statistic selector](https://www.home-assistant.io/docs/blueprint/selectors/#statistic-selector)
- [Target selector](https://www.home-assistant.io/docs/blueprint/selectors/#target-selector)
- [Template selector](https://www.home-assistant.io/docs/blueprint/selectors/#template-selector)
- [Text selector](https://www.home-assistant.io/docs/blueprint/selectors/#text-selector)
- [Theme selector](https://www.home-assistant.io/docs/blueprint/selectors/#theme-selector)
- [Time selector](https://www.home-assistant.io/docs/blueprint/selectors/#time-selector)
- [Trigger selector](https://www.home-assistant.io/docs/blueprint/selectors/#trigger-selector)

Interactive demos of each of these selectors can be found on the
[Home Assistant Design portal](https://design.home-assistant.io/#components/ha-selector).

If no selector is defined, a text input for a single line will be shown.

## Action selector

The action selector allows the user to input one or more sequences of actions.
On the user interface, the action part of the automation editor will be shown.
The value of the input will contain a list of actions to perform.

![Screenshot of an action selector](https://www.home-assistant.io/images/blueprints/selector-action.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
action:
```

YAML

Copy

The output of this selector is a list of actions. For example:

```yaml
# Example action selector output result
- action: scene.turn_on
  target:
    entity_id: scene.watching_movies
  metadata: {}
```

YAML

Copy

## Add-on selector

This can only be used on a Home Assistant Operating SystemHome Assistant OS, the Home Assistant Operating System, is an embedded, minimalistic, operating system designed to run the Home Assistant ecosystem on single board computers (like the Raspberry Pi) or Virtual Machines. It includes Home Assistant Core, the Home Assistant Supervisor, and supports add-ons. Home Assistant Supervisor keeps it up to date, removing the need for you to manage an operating system. Home Assistant Operating System is the recommended installation type for most users. installation. For Home Assistant ContainerHome Assistant Container is a standalone container-based installation of Home Assistant Core. Any [OCI](https://opencontainers.org/) compatible runtime can be used, but the documentation focus is on Docker. [\[Learn more\]](https://www.home-assistant.io/installation/#about-installation-types) installations, an error will be displayed.

The add-on selector allows the user to input an add-on slug.
On the user interface, it will list all installed add-ons and use the slug of the
selected add-on.

![Screenshot of an add-on selector](https://www.home-assistant.io/images/blueprints/selector-addon.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
# Example add-on selector
addon:
```

YAML

Copy

The output of this selector is the slug of the selected add-on.
For example: `core_ssh`.

## Area selector

The area selector shows an area finder that can pick a single or multiple areas
based on the selector configuration. The value of the input will be the area ID,
or a list of area IDs, based on if `multiple` is set to `true`.

An area selector can filter the list of areas, based on properties of the devices
and entities that are assigned to those areas. For example, the areas list could
be limited to areas with entities provided by the [ZHA](https://www.home-assistant.io/integrations/zha)
integration.

In its most basic form, this selector doesn’t require any options, which will show
all areas.

![Screenshot of an area selector](https://www.home-assistant.io/images/blueprints/selector-area.png)

```yaml
area:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

device list (Optional)

When device options are provided, the list of areas is filtered by areas that at least provide one device that matches the given conditions. Can be either a object or a list of object.

integration string (Optional)

Can be set to an integration domain. Limits the list of areas that provide devices by the set integration domain, for example, [`zha`](https://www.home-assistant.io/integrations/zha).

manufacturer string (Optional)

When set, it limits the list of areas that provide devices by the set manufacturer name.

model string (Optional)

When set, it limits the list of areas that provide devices that have the set model.

model\_id string (Optional)

When set, the list of areas is limited to areas with devices that have the set model ID.

entity list (Optional)

When entity options are provided, the list of areas is filtered by areas that at least provide one entity that matches the given conditions. Can be either a object or a list of object.

integration string (Optional)

Can be set to an integration domain. Limits the list of areas that provide entities by the set integration domain, for example, [`zha`](https://www.home-assistant.io/integrations/zha).

domain string \| list (Optional)

Limits the list of areas that provide entities of a certain [domain(s)](https://www.home-assistant.io/docs/configuration/entities_domains/#domains), for example, [`light`](https://www.home-assistant.io/integrations/light) or [`binary_sensor`](https://www.home-assistant.io/integrations/binary_sensor). Can be either a string with a single domain, or a list of string domains to limit the selection to.

device\_class [device\_class](https://www.home-assistant.io/integrations/homeassistant/#device-class) \| list (Optional)

Limits the list of areas to areas that have entities with a certain device class(es), for example, `motion` or `window`. Can be either a string with a single device\_class, or a list of string device\_class to limit the selection to.

supported\_features list (Optional)

Limits the list of areas to areas that have entities with a certain supported feature, for example, `light.LightEntityFeature.TRANSITION` or `climate.ClimateEntityFeature.TARGET_TEMPERATURE`. Should be a list of features.

multiple boolean (Optional, default: false)

Allows selecting multiple areas. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

The output of this selector is the area ID, or (in case `multiple` is set to
`true`) a list of area IDs.

```yaml
# Example area selector output result, when multiple is set to false
living_room

# Example area selector output result, when multiple is set to true
- living_room
- kitchen
```

YAML

Copy

### Example area selectors

An example area selector only shows areas that provide one or more lights or
switches provided by the [ZHA](https://www.home-assistant.io/integrations/zha) integration.

```yaml
area:
  entity:
    integration: zha
    domain:
      - light
      - switch
```

YAML

Copy

Another example uses the area selector, which only shows areas that provide one
or more remote controls provided by the [deCONZ](https://www.home-assistant.io/integrations/deconz)
integration. Multiple areas can be selected.

```yaml
area:
  multiple: true
  device:
    - integration: deconz
      manufacturer: IKEA of Sweden
      model: TRADFRI remote control
```

YAML

Copy

## Attribute selector

The attributes selector shows a list of state attributes from a provided entity
of which one can be selected.

This allows for selecting, e.g., the “Effect” attribute from a light entity, or the
“Next dawn” attribute from the `sun` entity.

![Screenshot of an attribute selector](https://www.home-assistant.io/images/blueprints/selector-attribute.png)

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

entity\_id stringRequired

The entity ID of which an state attribute can be selected from.

The output of this selector is the selected attribute key (not the translated or
prettified name shown in the frontend).
For example: `next_dawn`.

## Assist pipeline selector

The assist pipeline selector shows all available assist pipelines (assistants) of which one can be selected.

![Screenshot of an assist pipeline selector](https://www.home-assistant.io/images/blueprints/selector-assist-pipeline.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
assist_pipeline:
```

YAML

Copy

## Backup location selector

This can only be used on an installation with a Home Assistant Operating SystemHome Assistant OS, the Home Assistant Operating System, is an embedded, minimalistic, operating system designed to run the Home Assistant ecosystem on single board computers (like the Raspberry Pi) or Virtual Machines. It includes Home Assistant Core, the Home Assistant Supervisor, and supports add-ons. Home Assistant Supervisor keeps it up to date, removing the need for you to manage an operating system. Home Assistant Operating System is the recommended installation type for most users.. For Home Assistant ContainerHome Assistant Container is a standalone container-based installation of Home Assistant Core. Any [OCI](https://opencontainers.org/) compatible runtime can be used, but the documentation focus is on Docker. [\[Learn more\]](https://www.home-assistant.io/installation/#about-installation-types) installations, an error

will be displayed.

The backup location selector shows a list of places a backup could go, depending
on what you have configured in [storage](https://my.home-assistant.io/redirect/storage/).

![Screenshot of an assist pipeline selector](https://www.home-assistant.io/images/blueprints/selector-backup-location.png)

The output of this selector is the name of the selected network storage. It may
also be the value `/backup`, if the user chooses to use the local data disk option
instead of one of the configured network storage locations.

```yaml
backup_location:
```

YAML

Copy

## Boolean selector

The boolean selector shows a toggle that allows the user to turn on or off
the selected option.

![Screenshot of a boolean selector](https://www.home-assistant.io/images/blueprints/selector-boolean.png)

The boolean selector is suitable for adding feature switches
to, for example, blueprints.

This selector does not have any other options; therefore, it only has its key.

```yaml
boolean:
```

YAML

Copy

The output of this selector is `true` when the toggle is on, `false` otherwise.

## Color temperature selector

The color temperature selector allows you to select a color temperature from a gradient using a slider.

![Screenshot of the Color temperature selector](https://www.home-assistant.io/images/blueprints/selector-color-temp.png)

```yaml
color_temp:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

unit string (Optional, default: mired)

The chosen unit for the color temperature. This can be either `kelvin` or `mired`. `mired` is the default for historical reasons.

min integer (Optional)

The minimum color temperature in the chosen unit.

Default:

2700 for kelvin 153 for mired

max integer (Optional)

The maximum color temperature in the chosen unit.

Default:

6500 for kelvin 500 for mired

The output of this selector is the number representing the chosen color temperature for the unit used.

## Condition selector

The condition selector allows the user to input one or more conditions.
On the user interface, the condition part of the automation editor will be shown.
The value of the input will contain a list of conditions.

![Screenshot of an condition selector](https://www.home-assistant.io/images/blueprints/selector-condition.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
condition:
```

YAML

Copy

The output of this selector is a list of conditions. For example:

```yaml
# Example condition selector output result
- condition: numeric_state
  entity_id: "sensor.outside_temperature"
  below: 20
```

YAML

Copy

## Config entry selector

The config entry selector allows the user to select an integration
configuration entry. The selector returns the entry ID of the selected
integration configuration entry.

![Screenshot of the Configuration entry selector](https://www.home-assistant.io/images/blueprints/selector-config-entry.png)

```yaml
config_entry:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

integration string (Optional)

Limits the list of selectable configuration entries to a single integration domain.

The output of this selector is the entry ID of the config entry, for example, `6b68b250388cbe0d620c92dd3acc93ec`.

## Constant selector

The constant selector shows a toggle that allows the user to enable the selected option.
This is similar to the [boolean selector](https://www.home-assistant.io/docs/blueprint/selectors/#boolean-selector), the difference
is that the constant selector has no value when it’s not enabled.

![Screenshot of a constant selector](https://www.home-assistant.io/images/blueprints/selector-constant.png)

The selector’s value must be configured, and optionally, a label.

```yaml
constant:
  value: true
  label: Enabled
```

YAML

Copy

The output of this selector is the configured value when the toggle is on, it has no output otherwise.

## Conversation agent selector

The conversation agent selector allows picking a conversation agent.

![Screenshot of a conversation agent selector](https://www.home-assistant.io/images/blueprints/selector-conversation-agent.png)

The selector has 1 option, `language`. This filters the conversation agents shown, depending on the language.

```yaml
conversation_agent:
  language: en
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

language string (Optional)

Limits the list of conversation agents to those supporting the specified language.

The output of this selector is the ID of the conversation agent.

## Country selector

The country selector allows a user to pick a country from a list of countries.

![Screenshot of a country selector](https://www.home-assistant.io/images/blueprints/country_selector.png)

```yaml
country:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

countries list (Optional)

A list of countries to pick from, this should be ISO 3166 country codes.

Default:

The available countries in the Home Assistant frontend

no\_sort boolean (Optional, default: false)

Should the options be sorted by name, if set to true, the order of the provided countries is kept.

The output of this selector is an ISO 3166 country code.

## Date selector

The date selector shows a date input that allows the user to specify a date.

![Screenshot of the Date selector](https://www.home-assistant.io/images/blueprints/selector-date.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
date:
```

YAML

Copy

The output of this selector will contain the date in Year-Month-Day
(`YYYY-MM-DD`) format, for example, `2022-02-22`.

## Date & time selector

The date selector shows a date and time input that allows the user to specify a
date with a specific time.

![Screenshot of the Date & time selector](https://www.home-assistant.io/images/blueprints/selector-datetime.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
datetime:
```

YAML

Copy

The output of this selector will contain the date in Year-Month-Day
(`YYYY-MM-DD`) format and the time in 24-hour format, for example:
`2022-02-22 13:30:00`.

## Device selector

The device selector shows a device finder that can pick a single or multiple
devices based on the selector configuration. The value of the input will contain
the device ID or a list of device IDs, based on if `multiple` is set to `true`.

A device selector can filter the list of devices, based on things like the
manufacturer, model, or model ID of the device, the entities the device provides or based
on the domain that provided the device.

![Screenshot of a device selector](https://www.home-assistant.io/images/blueprints/selector-device.png)

In its most basic form, this selector doesn’t require any options, which will show
all devices.

```yaml
device:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

entity list (Optional)

When entity options are provided, the list of devices is filtered by devices that at least provide one entity that matches the given conditions. Can be either a object or a list of object.

integration string (Optional)

Can be set to an integration domain. Limits the list of devices that provide entities by the set integration domain, for example, [`zha`](https://www.home-assistant.io/integrations/zha).

domain string (Optional)

Limits the list of devices that provide entities of a certain [domain(s)](https://www.home-assistant.io/docs/configuration/entities_domains/#domains), for example, [`light`](https://www.home-assistant.io/integrations/light) or [`binary_sensor`](https://www.home-assistant.io/integrations/binary_sensor). Can be either a string with a single domain, or a list of string domains to limit the selection to.

device\_class [device\_class](https://www.home-assistant.io/integrations/homeassistant/#device-class) \| list (Optional)

Limits the list of devices to devices that have entities with a certain device class(es), for example, `motion` or `window`. Can be either a string with a single device\_class, or a list of string device\_class to limit the selection to.

supported\_features list (Optional)

Limits the list of devices to devices that have entities with a certain supported feature, for example, `light.LightEntityFeature.TRANSITION` or `climate.ClimateEntityFeature.TARGET_TEMPERATURE`. Should be a list of features.

filter list (Optional)

When filter options are provided, the list of devices is filtered by devices that at least provide one entity that matches the given conditions. Can be either a object or a list of object.

integration string (Optional)

Can be set to an integration domain. Limits the list of devices to devices provided by the set integration domain.

manufacturer string (Optional)

When set, it limits the list of devices to devices provided by the set manufacturer name.

model string (Optional)

When set, it limits the list of devices to devices that have the set model.

model\_id string (Optional)

When set, the list of devices is limited to devices that have the set model ID.

multiple boolean (Optional, default: false)

Allows selecting multiple devices. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

The output of this selector is the device ID, or (in case `multiple` is set to
`true`) a list of devices IDs.

```yaml
# Example device selector output result, when multiple is set to false
faadde5365842003e8ca55267fe9d1f4

# Example device selector output result, when multiple is set to true
- faadde5365842003e8ca55267fe9d1f4
- 3da77cb054352848b9544d40e19de562
```

YAML

Copy

### Example device selector

An example entity selector that, will only show devices that are:

- Provided by the [deCONZ](https://www.home-assistant.io/integrations/deconz) integration.
- Are a Philips Hue Remote of Model RWL021.
- Provide a battery [sensor](https://www.home-assistant.io/integrations/sensor).

And this is what is looks like in YAML:

```yaml
device:
  filter:
    - integration: deconz
      manufacturer: Philips
      model: RWL021
  entity:
    - domain: sensor
      device_class: battery
```

YAML

Copy

## Duration selector

The duration select allow the user to select a time duration. This can be
helpful for, e.g., delays or offsets.

![Screenshot of the Duration selector](https://www.home-assistant.io/images/blueprints/selector-duration.png)

```yaml
duration:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

enable\_day boolean (Optional, default: false)

When `true`, the duration selector will allow selecting days.

enable\_millisecond boolean (Optional, default: false)

When `true`, the duration selector will allow selecting milliseconds.

The output of this selector is a mapping of the time values the user selected.
For example:

```yaml
days: 1 # Only when enable_day was set to true
hours: 12
minutes: 30
seconds: 15
milliseconds: 500 # Only when enable_millisecond was set to true
```

YAML

Copy

## Entity selector

The entity selector shows an entity finder that can pick a single entity or a
list of entities based on the selector configuration. The value of the input
will contain the entity ID, or list of entity IDs, based on if `multiple` is
set to `true`.

An entity selector can filter the list of entities, based on things like the
class of the device, the domain of the entity or the domain that provided the
entity.

![Screenshot of an entity selector](https://www.home-assistant.io/images/blueprints/selector-entity.png)

In its most basic form, this selector doesn’t require any options, which will show
all entities.

```yaml
entity:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

exclude\_entities list (Optional)

List of entity IDs to exclude from the selectable list.

include\_entities list (Optional)

List of entity IDs to limit the selectable list to.

filter list (Optional)

When filter options are provided, the entities are limited by entities that at least match the given conditions. Can be either an object or a list of objects.

integration string (Optional)

Can be set to an integration domain. Limits the list of entities to entities provided by the set integration domain, for example, [`zha`](https://www.home-assistant.io/integrations/zha).

domain string \| list (Optional)

Limits the list of entities to entities of a certain [domain(s)](https://www.home-assistant.io/docs/configuration/entities_domains/#domains), for example, [`light`](https://www.home-assistant.io/integrations/light) or [`binary_sensor`](https://www.home-assistant.io/integrations/binary_sensor). Can be either a string with a single domain, or a list of string domains to limit the selection to.

device\_class [device\_class](https://www.home-assistant.io/integrations/homeassistant/#device-class) \| list (Optional)

Limits the list of entities to entities that have a certain device class(es), for example, `motion` or `window`. Can be either a string with a single device\_class, or a list of string device\_class to limit the selection to.

supported\_features list (Optional)

Limits the list of entities to entities that have a certain supported feature, for example, `light.LightEntityFeature.TRANSITION` or `climate.ClimateEntityFeature.TARGET_TEMPERATURE`. Should be a list of features.

multiple boolean (Optional, default: false)

Allows selecting multiple entities. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

reorder boolean (Optional, default: false)

Allows reordering of entities (only applies if `multiple` is set to `true`).

The output of this selector is the entity ID, or (in case `multiple` is set to
`true`) a list of entity IDs.

```yaml
# Example entity selector output result, when multiple is set to false
light.living_room

# Example entity selector output result, when multiple is set to true
- light.living_room
- light.kitchen
```

YAML

Copy

### Example entity selector

An example entity selector that, will only show entities that are:

- Provided by the [ZHA](https://www.home-assistant.io/integrations/zha) integration.
- From the [Binary sensor](https://www.home-assistant.io/integrations/binary_sensor) domain.
- Have presented themselves as devices of a motion device class.
- Allows selecting one or more entities.

And this is what it looks like in YAML:

```yaml
entity:
  multiple: true
  filter:
    - integration: zha
      domain: binary_sensor
      device_class: motion
```

YAML

Copy

## Floor selector

The floor selector shows a floor finder that can pick
floors based on the selector configuration. The value of the input will be the
floor ID. If `multiple` is set to `true`, the value is a list of floor IDs.

A floor selector can filter the list of floors based on the properties of the
devices and entities assigned to the areas on those floors.
For example, the floor list could be limited to floors with entities
provided by the [ZHA](https://www.home-assistant.io/integrations/zha) integration, based on the areas they are in.

In its most basic form, this selector doesn’t require any options.
It will show all floors.

![Screenshot of a floor selector](https://www.home-assistant.io/images/blueprints/selector-floor.png)

```yaml
floor:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

device list (Optional)

When device options are provided, the list of floors is filtered by floors that have at least one device matching the given conditions. Can be either an object or a list of objects.

integration string (Optional)

Can be set to an integration domain. Limits the list of floors that have devices by this integration domain. For example, [`zha`](https://www.home-assistant.io/integrations/zha).

manufacturer string (Optional)

When set, the list only includes floors that have devices by the set manufacturer name.

model string (Optional)

When set, the list only includes floors that have devices which have the set model.

model\_id string (Optional)

When set, the list only includes floors with devices that have the set model ID.

entity list (Optional)

When entity options are provided, the list only includes floors that at least have one entity that matches the given conditions. Can be either an object or a list of objects.

integration string (Optional)

Can be set to an integration domain. Limits the list of floors that have entities by the set integration domain. For example, [`zha`](https://www.home-assistant.io/integrations/zha).

domain string \| list (Optional)

When set, the list only includes floors that have entities of certain [domains](https://www.home-assistant.io/docs/configuration/entities_domains/#domains), for example, [`light`](https://www.home-assistant.io/integrations/light) or [`binary_sensor`](https://www.home-assistant.io/integrations/binary_sensor). Can be either a string with a single domain, or a list of string domains to limit the selection to.

device\_class [device\_class](https://www.home-assistant.io/integrations/homeassistant/#device-class) \| list (Optional)

When set, the list only includes floors that have entities with a certain device class, for example, `motion` or `window`. Can be either a string with a single device\_class, or a list of string device\_class to limit the selection.

supported\_features list (Optional)

When set, the list only includes floors that have entities with a certain supported feature, for example, `light.LightEntityFeature.TRANSITION` or `climate.ClimateEntityFeature.TARGET_TEMPERATURE`. Should be a list of features.

multiple boolean (Optional, default: false)

Allows selecting multiple floors. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

The output of this selector is the floor ID, or (in case `multiple` is set to
`true`) a list of floor IDs.

```yaml
# Example floor selector output result, when multiple is set to false
first_floor

# Example floor selector output result, when multiple is set to true
- first_floor
- second_floor
```

YAML

Copy

### Example floor selectors

An example floor selector only shows floors that have one or more lights or
switches provided by the [ZHA](https://www.home-assistant.io/integrations/zha) integration.

```yaml
floor:
  entity:
    integration: zha
    domain:
      - light
      - switch
```

YAML

Copy

Another example using the floor selector, which only shows floors that
have one or more remote controls provided by the [deCONZ](https://www.home-assistant.io/integrations/deconz)
integration. Multiple floors can be selected.

```yaml
floor:
  multiple: true
  device:
    - integration: deconz
      manufacturer: IKEA of Sweden
      model: TRADFRI remote control
```

YAML

Copy

## Icon selector

The icon selector shows an icon picker that allows the user to select an icon.

```yaml
icon:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

placeholder string (Optional)

Placeholder icon to show, when no icon is selected.

The output of this selector is a string containing the selected icon,
for example: `mdi:bell`.

## Label selector

The label selector shows a label finder that can pick labels. The value of the
input is the label ID. If `multiple` is set to `true`, the value is a list
of label IDs.

![Screenshot of the label selector](https://www.home-assistant.io/images/blueprints/selector-label.png)

In its most basic form, this selector doesn’t require any options.
It will show all labels.

```yaml
label:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

multiple boolean (Optional, default: false)

Allows selecting multiple labels. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

The output of this selector is the label ID, or (in case `multiple` is set to
`true`) a list of label IDs.

```yaml
# Example label selector output result, when multiple is set to false
energy_saving

# Example label selector output result, when multiple is set to true
- energy_saving
- christmas_decorations
```

YAML

Copy

## Language selector

The language selector allows a user to pick a language from a list of languages.

![Screenshot of an language selector](https://www.home-assistant.io/images/blueprints/selector-language.png)

```yaml
language:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

languages list (Optional)

A list of languages to pick from, this should be RFC 5646 languages codes.

Default:

The available languages in the Home Assistant frontend

native\_name boolean (Optional, default: false)

Should the name of the languages be shown in the language of the user, or in the language itself.

no\_sort boolean (Optional, default: false)

Should the options be sorted by name, if set to true, the order of the provided languages is kept.

The output of this selector is a RFC 5646 language code.

## Location selector

The location selector allow a user to pick a location from a map and returns
the matching longitude and latitude coordinators. Optionally it supports
selecting the radius of the location.

![Screenshot of the Location selector](https://www.home-assistant.io/images/blueprints/selector-location.png)

```yaml
location:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

icon string (Optional)

An optional icon to show on the map.

radius boolean (Optional, default: false)

Allow selecting the radius of the location. If enabled, the radius will be returned in meters.

The output of this selector is a mapping containing the latitude and longitude
of the selected location, and, if enabled, the radius.
For example:

```yaml
latitude: 50.935
longitude: 6.95
radius: 500 # Only provided when radius was set to true.
```

YAML

Copy

## Media selector

The media selector is a powerful selector that allows a user to easily select
media to play on a media device. Media can be a lot of things, for example,
cameras, local media, text-to-speech, Home Assistant Dashboards, and many more.

You are prompted to select the device used to play media. Once the device is selected, the media selector only shows media that is suitable for this device.

![Screenshot of the Media selector](https://www.home-assistant.io/images/blueprints/selector-media.png)

To ask the user to select a media device and suitable media, you can use the
media selector without any options:

```yaml
media:
```

YAML

Copy

You can also use the media selector with an optional `accept` filter to limit the
media types that can be selected. The user will not be asked to pick a device.

```yaml
media:
  accept:
    - image/*
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

accept list (Optional)

List of media types the user is allowed to select.

The output of the media selector, is an mapping with information about
the selected media device and the selected media to play. There is also
metadata, which is used by the frontend and should not be used in the
backend.

Example output:

```yaml
entity_id: media_player.living_room
media_content_id: media-source://tts/cloud?message=TTS+Message&language=en-US&gender=female
media_content_type: provider
metadata:
  title: TTS Message
  thumbnail: https://brands.home-assistant.io/_/cloud/logo.png
  media_class: app
  children_media_class: null
  navigateIds:
    - {}
    - media_content_type: app
      media_content_id: media-source://tts
    - media_content_type: provider
      media_content_id: >-
        media-source://tts/cloud?message=TTS+Message&language=en-US&gender=female
```

YAML

Copy

Example output if accept filter is used. Note that the `entity_id` is not present:

```yaml
media_content_id: media-source://tts/cloud?message=TTS+Message&language=en-US&gender=female
media_content_type: provider
metadata:
  title: TTS Message
  thumbnail: https://brands.home-assistant.io/_/cloud/logo.png
  media_class: app
  children_media_class: null
  navigateIds:
    - {}
    - media_content_type: app
      media_content_id: media-source://tts
    - media_content_type: provider
      media_content_id: >-
        media-source://tts/cloud?message=TTS+Message&language=en-US&gender=female
```

YAML

Copy

## Number selector

The number selector shows either a number input or a slider input, that allows
the user to specify a numeric value. The value of the input will contain
the select value.

![Screenshot of a number selector](https://www.home-assistant.io/images/blueprints/selector-number.png)

On the user interface, the input can either be in a slider or number mode.
Both modes limit the user input by a minimum and maximum value, and can
have a unit of measurement to go with it.

In its most basic form, this selector requires a minimum and maximum value:

```yaml
number:
  min: 0
  max: 100
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

min integer \| float (Optional)

The minimum user-settable number value.

max integer \| float (Optional)

The maximum user-settable number value.

step integer \| float \| any (Optional, default: 1)

The step size of the number value. Set to `"any"` to allow any number.

unit\_of\_measurement string (Optional)

Unit of measurement in which the number value is expressed in.

mode string (Optional)

This can be either `box` or `slider` mode.

Default:

slider if min and max are set, otherwise box

translation\_key string (Optional)

Allows translations provided by an integration where `translation_key` is the translation key that is providing the unit\_of\_measurement string translation. See the documentation on [Backend Localization](https://developers.home-assistant.io/docs/internationalization/core/#selectors) for more information.

The output of this selector is a number, for example: `42`

### Example number selectors

An example number selector that allows a user a percentage, directly in a
regular number input box.

```yaml
number:
  min: 0
  max: 100
  unit_of_measurement: "%"
```

YAML

Copy

A more visual variant of this example could be achieved using a slider.
This can be helpful for things like allowing the user to select a
brightness level of lights. Additionally, this example changes the brightness
in incremental steps of 10%.

```yaml
number:
  min: 0
  max: 100
  step: 10
  unit_of_measurement: "%"
  mode: slider
```

YAML

Copy

## Object selector

The object selector can be used to input arbitrary data in YAML form. This is useful for e.g. lists and dictionaries containing data for actions. The value of the input will contain the provided data.

When used without options, the selector will accept any valid YAML content, such as objects, arrays, strings, or other YAML types. The input box is displayed as an editor with syntax highlighting.

![Screenshot of an object selector](https://www.home-assistant.io/images/blueprints/selector-object.png)

```yaml
object:
```

YAML

Copy

When used with `fields` specified, the selector will force the object to be in this format by displaying a form.

![Screenshot of an object selector](https://www.home-assistant.io/images/blueprints/selector-object-schema.png)

```yaml
object:
  label_field: name
  description_field: percentage
  multiple: true
  fields:
    name:
      label: Name
      selector:
        text:
    percentage:
      label: Percentage
      selector:
        number:
          unit_of_measurement: "%"
```

YAML

Copy

The output of this selector is a YAML object.

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

fields map (Optional)

List of fields of the object.

label string (Optional)

The label of the field

required boolean (Optional, default: false)

If set to true, the field must be present.

selector stringRequired

The selector to use for this field. It can be any available selector.

label\_field string (Optional)

The field to use as a label. By default, it will be the first field defined. This option is only used if `fields` option set.

description\_field string (Optional)

The field to use as a description. This option is only used if `fields` option set.

translation\_key string (Optional)

Allows translations provided by an integration where `translation_key` is the translation key that is providing the selector option strings translation. See the documentation on [Backend Localization](https://developers.home-assistant.io/docs/internationalization/core/#selectors) for more information.

multiple boolean (Optional, default: false)

Allows adding multiple objects. If set to `true`, the resulting value of this selector will be a list instead of a single YAML object. This option is only used if `fields` option set.

## QR code selector

The QR code selector shows a QR code. It has no return value.

![Screenshot of a QR code selector](https://www.home-assistant.io/images/blueprints/selector-qr-code.png)

The QR code’s data must be configured, and optionally, the scale, and error correction level can be set.
The scale makes the QR code bigger or smaller.

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

data anyRequired

The data that should be represented in the QR code.

scale integer (Optional, default: 4)

The scale factor to use, this will make the QR code bigger or smaller.

error\_correction\_level string (Optional, default: medium)

The error correction level of the QR code, with a higher error correction level the QR code can be scanned even when some pieces are missing. Can be “low”, “medium”, “quartile” or “high”.

```yaml
qr_code:
  data: "https://home-assistant.io"
  scale: 5
  error_correction_level: quartile
```

YAML

Copy

## RGB color selector

The RGB color selector allows the user to select an color from a color picker
from the user interface, and returns the RGB color value.

![Screenshot of the RGB Color selector](https://www.home-assistant.io/images/blueprints/selector-color-rgb.png)

```yaml
color_rgb:
```

YAML

Copy

This selector does not have any other options; therefore, it only has its key.

The output of this selector is a list with the three (RGB) color value, for example: `[255, 0, 0]`.

## Select selector

The select selector shows a list of available options from which the user can choose. The value of the input contains the value of the selected option. Only a single option can be selected at a time.

![Screenshot of a select selector](https://www.home-assistant.io/images/blueprints/selector-select.png)

The selector requires a list of options that the user can choose from.

```yaml
select:
  options:
    - Red
    - Green
    - Blue
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

options listRequired

List of options that the user can choose from. Small lists (5 items or less), are displayed as radio buttons. When more items are added, a dropdown list is used.

multiple boolean (Optional, default: false)

Allows selecting multiple options. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

custom\_value boolean (Optional, default: false)

Allows the user to enter and select a custom value (or multiple custom values in addition to the listed options if `multiple` is set to `true`).

mode string (Optional)

This can be either `list` (radio buttons) or `dropdown` (combobox) mode. When not specified, small lists (5 items or less), are displayed as radio buttons. When more items are added, a dropdown list is used. If `custom_value` is `true`, this setting will be ignored and the frontend will use a `dropdown` input.

translation\_key string (Optional)

Allows translations provided by an integration where `translation_key` is the translation key that is providing the selector option strings translation. See the documentation on [Backend Localization](https://developers.home-assistant.io/docs/internationalization/core/#selectors) for more information.

sort boolean (Optional, default: false)

Display options in alphabetical order.

Alternatively, a mapping can be used for the options. When you want to return
a different value compared to how it is displayed to the user.

```yaml
select:
  options:
    - label: Red
      value: r
    - label: Green
      value: g
    - label: Blue
      value: b
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

options mapRequired

List of options that the user can choose from. Small lists (5 items or less), are displayed as radio buttons. When more items are added, a dropdown list is used.

label stringRequired

The description to show in the UI for this item.

value stringRequired

The value to return when this label is selected.

When `multiple` is `false`, the output of this selector is the string of
the selected option value. When selecting `Green` in the last example,
it returns: `g`, in the first example it would return `Green`.

When `multiple` is `true`, the output of this selector is the list of selected
option values. In this case, if `Green` was selected, in the first example it
would return \[“Green”\] and in the last example it returns \[“g”\].

## State selector

The state selector shows a list of states for a provided entity of which
one or more can be selected.

![Screenshot of an state selector](https://www.home-assistant.io/images/blueprints/selector-state.png)

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

entity\_id string (Optional)

The entity ID of which an state can be selected from.

hide\_states list (Optional)

The states to exclude from the list of options

multiple boolean

Allows selecting multiple states. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

The output of this selector is the select state (not the translated or
prettified name shown in the frontend), or a list of states if `multiple` is true.

For example: `heat_cool`.

## Statistic selector

The statistic selector selects the statistic ID of an entity that records
Long-term statisticsHome Assistant saves long-term statistics for a sensor if the entity has a state\_class of measurement, total, or total\_increasing. For short-term statistics, a snapshot is taken every 5 minutes. For long-term statistics, an hourly aggregate is stored of the short-term statistics. Short-term statistics are automatically purged after a predefined period (default is 10 days). Long-term statistics are never purged. [\[Learn more\]](https://www.home-assistant.io/blog/2021/08/04/release-20218/#long-term-statistics). It may resemble an entity ID (like `sensor.temperature`),
or an external statistic ID (like `external:temperature`).

![Screenshot of a statistic selector](https://www.home-assistant.io/images/blueprints/selector-statistic.png)

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

multiple boolean (Optional, default: false)

If set to true, the selector returns a list of statistic IDs.

The output of this selector is a string representing a statistic ID, or
a list of statistic IDs if `multiple` is set to `true`.

## Target selector

The target selector is a rather special selector, allowing the user to select
targeted entities, devices, or areas for actions. The value of
the input will contain a special target format, that is accepted by
actions.

The selectable targets can be filtered, based on entity or device properties.
Areas are only selectable as a target, if some entities or devices match
those properties in those areas.

![Screenshot of a target selector](https://www.home-assistant.io/images/blueprints/selector-target.png)

In its most basic form, this selector does not require any options, which will allow the
user to target any entity, device or area available in the system.

```yaml
target:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

entity list (Optional)

When entity options are provided, the targets are limited by entities that at least match the given conditions. Can be either a object or a list of object.

integration string (Optional)

Can be set to an integration domain. Limits targets to entities provided by the set integration domain, for example, [`zha`](https://www.home-assistant.io/integrations/zha).

domain string \| list (Optional)

Limits the targets to entities of a certain [domain(s)](https://www.home-assistant.io/docs/configuration/entities_domains/#domains), for example, [`light`](https://www.home-assistant.io/integrations/light) or [`binary_sensor`](https://www.home-assistant.io/integrations/binary_sensor). Can be either a with a single domain, or a list of string domains to limit the selection to.

device\_class [device\_class](https://www.home-assistant.io/integrations/homeassistant/#device-class) \| list (Optional)

Limits the targets to entities with a certain device class(es), for example, `motion` or `window`. Can be either a string with a single device\_class, or a list of string device\_class to limit the selection to.

Important

Targets are meant to be used with the `target` property of an action in
a script sequence. For example:

```yaml
actions:
  - action: light.turn_on
    target: !input lights
```

YAML

Copy

### Example target selectors

An example target selector that only shows targets that at least provide one
or more lights, provided by the [ZHA](https://www.home-assistant.io/integrations/zha) integration.

```yaml
target:
  entity:
    - integration: zha
      domain: light
```

YAML

Copy

## Template selector

The template selector can be used to input a Jinja2 template. This is useful
for allowing more advanced user-input that use Jinja2 templates.

![Screenshot of an template selector](https://www.home-assistant.io/images/blueprints/selector-template.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
template:
```

YAML

Copy

The output of this selector is a template string.

## Text selector

The text selector can be used to enter a text string. It can also be used to enter a list of text strings; if `multiple` is set to `true`. The value of the input will contain the selected text. This can be used in shopping lists, for example.

![Screenshot of text selectors](https://www.home-assistant.io/images/blueprints/selector-text.png)

Unless `multiline` is set to `true`, this selector behaves exactly like if no selector at all was specified, and will display a single line text input box on the user interface.

```yaml
text:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

multiline boolean (Optional, default: false)

Set to true to display the input as a multi-line text box on the user interface.

prefix string (Optional)

An optional prefix to show before the text input box.

suffix string (Optional)

An optional suffix to show after the text input box.

type string (Optional, default: text)

The type of input. This supplies the [HTML `type` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types), which controls how the browser displays and validates the field. A subset of types available to the attribute are supported, since some are handled by other selectors. Possible types are: `color`, `date`, `datetime-local`, `email`, `month`, `number`, `password`, `search`, `tel`, `text`, `time`, `url`, `week`.

autocomplete string (Optional)

Guides the browser on the type of information which should automatically fill the field. This supplies the [HTML `autocomplete` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete). Any value supported by the HTML attribute is valid.

multiple boolean (Optional, default: false)

Allows adding list of text strings. If set to `true`, the resulting value of this selector will be a list instead of a single string value.

The output of this selector is a single string value.

## Theme selector

The theme selector allows for selecting a theme from the available themes
installed in Home Assistant.

![Screenshot of the Theme selector](https://www.home-assistant.io/images/blueprints/selector-theme.png)

```yaml
theme:
```

YAML

Copy

#### Configuration Variables

[Looking for your configuration file?](https://www.home-assistant.io/docs/configuration/)

include\_default boolean (Optional, default: false)

Includes Home Assistant default theme in the list.

The output of this selector will contain the selected theme, for example:
`waves_dark`.

## Time selector

The time selector shows a time input that allows the user to specify a time
of the day.

![Screenshot of a time selector](https://www.home-assistant.io/images/blueprints/selector-time.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
time:
```

YAML

Copy

The output of this selector will contain the time in 24-hour format,
for example, `23:59:59`.

## Trigger selector

The triggers selector allows the user to input one or more triggers.
On the user interface, the trigger part of the automation editor is shown.
The value of the input contains a list of triggers.

![Screenshot of an trigger selector](https://www.home-assistant.io/images/blueprints/selector-trigger.png)

This selector does not have any other options; therefore, it only has its key.

```yaml
trigger:
```

YAML

Copy

The output of this selector is a list of triggers. For example:

```yaml
# Example trigger selector output result
- trigger: numeric_state
  entity_id: "sensor.outside_temperature"
  below: 20
```

YAML

Copy

### Example - Merging with existing triggers

If the trigger(s) should exist within a blueprint that already has some default triggers defined, and an additional customizable trigger should be merged, you need to use the `- triggers` syntax in the blueprint.

```yaml
# Example trigger selector
input:
  my_trigger_input:
    selector:
      trigger:
triggers:
  - triggers: !input my_trigger_input
  - platform: numeric_state
  [...]
```

YAML

Copy

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/blueprint/selectors.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fblueprint%2Fselectors%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fblueprint%2Fselectors%2F%22&in=body "View given feedback for this page")
