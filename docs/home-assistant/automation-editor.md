---
title: Automation editor - Home Assistant
description: Instructions on how to use the automation editor.
source_url: https://www.home-assistant.io/docs/automation/editor
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:09:48.988Z
---

The automation editor is an easy way of creating and editing automations from the UI.

This tutorial uses the [Random sensor](https://www.home-assistant.io/integrations/random#sensor) because it generates data (by default, values between 0 and 20). This enables us to walk through the example, even if you do not have any actual sensors connected yet. You could use any other sensor that outputs a numeric value.

1. Go to [**Settings** \> **Automations & scenes**](https://my.home-assistant.io/redirect/automations) and in the lower right corner, select the **Create Automation** button.

2. Select **Create new automation**.

![Create automation dialogue box](https://www.home-assistant.io/images/docs/automation-editor/create-automation.png)

3. Select **Add Trigger**, and in the **Search trigger** field, type “num”.


   - Select **Numeric state**.

![Add trigger](https://www.home-assistant.io/images/docs/automation-editor/add-trigger-to-automation.png)

4. Enter the trigger conditions:


   - Define the sensor: Under **Entity**, enter “sensor.random\_sensor”.
   - If the sensor value is above 10, we want the automation to trigger.
     - In the **Above** field, enter “10”.

![Automation trigger](https://www.home-assistant.io/images/docs/automation-editor/new-trigger.png)

5. Define the action that should happen:
   - In the **Then do** section, select **Add Action**.

     ![Add action](https://www.home-assistant.io/images/docs/automation-editor/add_action.png)
6. We want to create a [persistent notification](https://www.home-assistant.io/integrations/persistent_notification/).


   - Enter “No” and select **Notifications: send a persistent notification**.

![Automation action](https://www.home-assistant.io/images/docs/automation-editor/send-notification.png)

7. As the message, we want a simple text that is shown as part of the notification.







```yaml
message: Sensor value greater than 10
```





YAML



Copy

8. Select **Save**, give your automation a meaningful name, and **Save** again.

![New automation editor](https://www.home-assistant.io/images/docs/automation-editor/new-automation.png)
   - **Result**: Automations created or edited via the user interface are activated immediately after saving the automation.
   - To learn more about automations, read the documentation for [Automating Home Assistant](https://www.home-assistant.io/getting-started/automation/).

## Troubleshooting missing automations

When you’re creating automations using the GUI and they don’t appear in the UI, make sure that you add back `automation: !include automations.yaml` from the default configuration to your `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/).

## Related topics

- [Automating home assistant](https://www.home-assistant.io/getting-started/automation/)

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/automation/editor.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fautomation%2Feditor%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fautomation%2Feditor%2F%22&in=body "View given feedback for this page")
