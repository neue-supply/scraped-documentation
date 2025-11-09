---
title: Entity integration platform options - Home Assistant
description: Shows how to customize polling interval for any integration via configuration.yaml.
source_url: https://www.home-assistant.io/docs/configuration/platform_options
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:09:36.607Z
---

Important

These options are being phased out and are only available for single platform integrations.

Some integrations or platforms (those that are based on the [entity](https://github.com/home-assistant/home-assistant/blob/dev/homeassistant/helpers/entity.py) class) allow various extra options to be set.

## Entity namespace

By setting an entity namespace, all entities will be prefixed with that namespace. That way, `light.bathroom` can become `light.holiday_house_bathroom`.

```yaml
# Example configuration.yaml entry
light:
  - platform: your_lights
    entity_namespace: holiday_house
```

YAML

Copy

## Scan interval

Platforms that require polling will be polled in an interval specified by the main integration. For example, a light will check every 30 seconds for a changed state. It is possible to overwrite this scanning interval for any platform that is being polled by specifying a `scan_interval` configuration key. In the example below, we set up the `your_lights` platform but tell Home Assistant to poll the devices every 10 seconds instead of the default 30 seconds.

```yaml
# Example configuration.yaml entry to poll your_lights every 10 seconds.
light:
  - platform: your_lights
    scan_interval: 10
```

YAML

Copy

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/configuration/platform_options.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fconfiguration%2Fplatform_options%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fconfiguration%2Fplatform_options%2F%22&in=body "View given feedback for this page")
