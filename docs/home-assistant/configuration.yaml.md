---
title: Configuration.yaml - Home Assistant
description: Configuring Home Assistant via text files.
source_url: https://www.home-assistant.io/docs/configuration
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:08:52.941Z
---

While you can configure most of Home Assistant from the user interface, for some integrations, you need to edit the `configuration.yaml` file.

This file contains integrationsIntegrations connect and integrate Home Assistant with your devices, services, and more. [\[Learn more\]](https://www.home-assistant.io/getting-started/concepts-terminology/#integrations) to be loaded along with their configurations. Throughout the documentation, you will find snippets that you can add to your configuration file to enable specific functionality.

![Screenshot of an example of a configuration.yaml file, accessed using the File editor add-on on a Home Assistant Operating System installation.](https://www.home-assistant.io/images/docs/configuration/config-yaml_via-file-editor.png)
Example of a configuration.yaml file, accessed using the File editor add-on on a Home Assistant Operating System installation.

## Editing configuration.yaml

How you edit your `configuration.yaml` file depends on your editor preferences and the [installation type](https://www.home-assistant.io/installation/#about-installation-types) you used to set up Home Assistant. Follow these steps:

1. [Set up file access](https://www.home-assistant.io/docs/configuration/#to-set-up-access-to-the-files-and-prepare-an-editor).
2. [Locate the config directory](https://www.home-assistant.io/docs/configuration/#to-find-the-configuration-directory).
3. Edit your `configuration.yaml` file.
4. Save your changes and [reload the configuration](https://www.home-assistant.io/docs/configuration/#reloading-the-configuration-to-apply-changes) to apply the changes.

### To set up access to the files and prepare an editor

Before you can edit a file, you need to know how to access files in Home Assistant and setup an editor.
File access depends on your [installation type](https://www.home-assistant.io/installation/#about-installation-types). If you use Home Assistant Operating SystemHome Assistant OS, the Home Assistant Operating System, is an embedded, minimalistic, operating system designed to run the Home Assistant ecosystem on single board computers (like the Raspberry Pi) or Virtual Machines. It includes Home Assistant Core, the Home Assistant Supervisor, and supports add-ons. Home Assistant Supervisor keeps it up to date, removing the need for you to manage an operating system. Home Assistant Operating System is the recommended installation type for most users., you can use editor add-ons, for example. If you use Home Assistant ContainerHome Assistant Container is a standalone container-based installation of Home Assistant Core. Any [OCI](https://opencontainers.org/) compatible runtime can be used, but the documentation focus is on Docker. [\[Learn more\]](https://www.home-assistant.io/installation/#about-installation-types), add-ons are not available.

To set up file access on the Home Assistant Operating System, follow these steps:

- If you are unsure which option to choose, install the [file editor add-on](https://www.home-assistant.io/common-tasks/os/#installing-and-using-the-file-editor-add-on).

  - Alternatively, use the [Studio Code Server add-on](https://www.home-assistant.io/common-tasks/os/#installing-and-using-the-visual-studio-code-vsc-add-on). This editor offers live syntax checking and auto-fill of various Home Assistant entities. But it looks more complex than the file editor.
  - If you prefer to use a file editor on your computer, use the [Samba add-on](https://www.home-assistant.io/common-tasks/os/#installing-and-using-the-samba-add-on).

### To find the configuration directory

1. To look up the path to your configuration directory, go to [**Settings** \> **System** \> **Repairs**](https://my.home-assistant.io/redirect/system_health).


   - Select the three dots menu and select **System information**.

![Show system information option](https://www.home-assistant.io/images/screenshots/System_information_menu.png)

2. Find out the location of the **Configuration directory**.

![Screenshot showing the top of the system information panel](https://www.home-assistant.io/images/screenshots/system_information.png)
   - Unless you changed the file structure, the default is as follows: -
     - Home Assistant Operating SystemHome Assistant OS, the Home Assistant Operating System, is an embedded, minimalistic, operating system designed to run the Home Assistant ecosystem on single board computers (like the Raspberry Pi) or Virtual Machines. It includes Home Assistant Core, the Home Assistant Supervisor, and supports add-ons. Home Assistant Supervisor keeps it up to date, removing the need for you to manage an operating system. Home Assistant Operating System is the recommended installation type for most users.: the `configuration.yaml` is in the `/config` folder of the installation.
     - Home Assistant ContainerHome Assistant Container is a standalone container-based installation of Home Assistant Core. Any [OCI](https://opencontainers.org/) compatible runtime can be used, but the documentation focus is on Docker. [\[Learn more\]](https://www.home-assistant.io/installation/#about-installation-types): the `configuration.yaml` is in the config folder that you mounted in your container.
3. Once you located the config folder, you can edit your `configuration.yaml` file.


Note

If you have watched any videos about setting up Home Assistant using `configuration.yaml` (particularly ones that are old), you might notice your default configuration file is much smaller than what the videos show. Don’t be concerned, you haven’t done anything wrong. Many items in the default configuration files shown in those old videos are now included in the `default_config:` line that you see in your configuration file. Refer to the [default config integration](https://www.home-assistant.io/integrations/default_config/) for more information on what’s included in that line.

## Validating the configuration

After changing configuration or automation files, you can check if the configuration is valid. A configuration check is also applied automatically when you reload the configuration or when you restart Home Assistant.

The method for running a configuration check depends on your [installation type](https://www.home-assistant.io/installation/#about-installation-types). Check the common tasks for your installation type:

- [Configuration check on Operating System](https://www.home-assistant.io/common-tasks/os/#configuration-check)
- [Configuration check on Container](https://www.home-assistant.io/common-tasks/container/#configuration-check)

## Reloading the configuration to apply changes

For configuration changes to become effective, the configuration must be reloaded. Most integrations in Home Assistant (that do not interact with devicesA device is a model representing a physical or logical unit that contains entities. or servicesThe term “service” in Home Assistant is used in the sense of an **information**
**service**. For example, the municipal waste management service that provides
entities for organic, paper, and packaging waste. In terms of functionality,
the information service is like a device. It is called _service_ to avoid
confusion, as it does not come with a piece of hardware.) can reload changes made to their configuration in `configuration.yaml` without needing to restart Home Assistant.

1. Under **Settings**, select the three dots menu (top right) , select **Restart Home Assistant** \> **Quick reload**.

![Settings, three dot menu, restart Home Assistant](https://www.home-assistant.io/images/docs/configuration/settings_restart_ha.png)

2. If you find that your changes were not applied, you need to restart.


   - Select **Restart Home Assistant**.
   - Note: This interrupts automations and scripts.

![Reload and restart buttons](https://www.home-assistant.io/images/docs/configuration/reload_restart.png)

## Troubleshooting the configuration

If you run into trouble while configuring Home Assistant, refer to the [configuration troubleshooting page](https://www.home-assistant.io/docs/configuration/troubleshooting/).

## Related topics

- [Yaml syntax](https://www.home-assistant.io/docs/configuration/yaml/)
- [Creating and restoring backups](https://www.home-assistant.io/common-tasks/general/#backups)
- [Reloading the yaml configuration from developer tools](https://www.home-assistant.io/docs/tools/dev-tools/#reloading-the-yaml-configuration)
- [Configuring file access on the operating system](https://www.home-assistant.io/common-tasks/os/#configuring-access-to-files)

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/configuration.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fconfiguration%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fconfiguration%2F%22&in=body "View given feedback for this page")
