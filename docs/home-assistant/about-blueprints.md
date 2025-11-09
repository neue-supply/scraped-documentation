---
title: About blueprints - Home Assistant
description: Introduction to blueprints.
source_url: https://www.home-assistant.io/docs/blueprint
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:08:46.120Z
---

This section gives a high-level introduction to blueprints. To view a description of the YAML-schema used to create a valid blueprint, refer to the section [About the blueprint schema](https://www.home-assistant.io/docs/blueprint/schema/).

## What is a blueprint?

A blueprint is a scriptScripts are components that allow users to specify a sequence of actions to be executed by Home Assistant when turned on. [\[Learn more\]](https://www.home-assistant.io/docs/scripts/), automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home. [\[Learn more\]](https://www.home-assistant.io/docs/automation/) or [template entity](https://www.home-assistant.io/integrations/template/) configuration with certain parts marked as configurable. This allows you to create different scripts, automations or template entities based on the same blueprint.

Imagine you want to control lights based on motion. A blueprint provides the generic automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home. [\[Learn more\]](https://www.home-assistant.io/docs/automation/) framework, while letting you select one specific motion sensor as a triggerA trigger is a set of values or conditions of a platform that are defined to cause an automation to run. [\[Learn more\]](https://www.home-assistant.io/docs/automation/trigger/), and the exact light to control. This blueprint makes it possible to create two automations. Each automation has their own configuration and act completely independently. Yet, they share some basic automation configuration so that you do not have to set this up every time.

Automations inherit from blueprints, which means that changes made to a blueprint will be reflected in all automations based on that blueprint the next time the automations are reloaded. This occurs as part of Home Assistant starting. To manually reload the automations, go to [**Developer tools** \> **YAML**](https://my.home-assistant.io/redirect/server_controls) and reload the automations.

Blueprints are shared by the community in the [blueprint community forum](https://www.home-assistant.io/get-blueprints).

## Related topics

- [About the blueprint schema](https://www.home-assistant.io/docs/blueprint/schema/)
- [About the blueprint selectors](https://www.home-assistant.io/docs/blueprint/selectors/)
- [Using blueprints in automations](https://www.home-assistant.io/docs/automation/using_blueprints/)
- [Tutorial: create an automation blueprint](https://www.home-assistant.io/docs/blueprint/tutorial/)

## Related links

- [Blueprint community forum](https://www.home-assistant.io/get-blueprints)

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/blueprint.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fblueprint%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fblueprint%2F%22&in=body "View given feedback for this page")
