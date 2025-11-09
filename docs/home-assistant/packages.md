---
title: Packages - Home Assistant
description: Describes all there is to know about configuration packages in Home Assistant.
source_url: https://www.home-assistant.io/docs/configuration/packages
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:06:40.424Z
---

Packages in Home Assistant provide a way to bundle configurations from multiple integrations. With packages, we have a way to include multiple integrations, or parts of integrations using any of the `!include` directives introduced in [splitting the configuration](https://www.home-assistant.io/docs/configuration/splitting_configuration).

Packages are configured under the core `homeassistant/packages` in the configuration and take the format of a package name (no spaces, all lower case) followed by a dictionary with the package configuration. For example, package `pack_1` would be created as:

```yaml
homeassistant:
  ...
  packages:
    pack_1:
      ...package configuration here...
```

YAML

Copy

The package configuration can include: `switch`, `light`, `automation`, `groups`, or most other Home Assistant integrations including hardware platforms.

It can be specified inline or in a separate YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/yaml/) file using `!include`.

Inline example, main `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/):

```yaml
homeassistant:
  ...
  packages:
    pack_1:
      switch:
        - platform: rest
          ...
      light:
        - platform: rpi
          ...
```

YAML

Copy

Include example, main `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/):

```yaml
homeassistant:
  ...
  packages:
    pack_1: !include my_package.yaml
```

YAML

Copy

The file `my_package.yaml` contains the “top-level” configuration:

```yaml
switch:
  - platform: rest
    ...
light:
  - platform: rpi
    ...
```

YAML

Copy

There are some rules for packages that will be merged:

1. Platform based integrations (`light`, `switch`, etc) can always be merged.

2. Integrations where entities are identified by a key that will represent the entity\_id (`{key: config}`) need to have unique ‘keys’ between packages and the main configuration file.

For example if we have the following in the main configuration. You are not allowed to re-use “my\_input” again for `input_boolean` in a package:







```yaml
input_boolean:
     my_input:
```





YAML



Copy

3. Any integration that is not a platform \[1\], or dictionaries with Entity ID keys \[2\] can only be merged if its keys, except those for lists, are solely defined once.


Tip

Integrations inside packages can only specify platform entries using configuration style 1, where all the platforms are grouped under the integration name.

## Create a packages folder

One way to organize packages is to create a folder named “packages” in your Home Assistant configuration directory. In the packages directory, you can store any number of packages in a YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/yaml/) file. This entry in your `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/) will load all YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files. [\[Learn more\]](https://www.home-assistant.io/docs/configuration/yaml/)-files in this _packages_ folder and its subfolders:

```yaml
homeassistant:
  packages: !include_dir_named packages
```

YAML

Copy

The benefit of this approach is to pull all configurations required to integrate a system into one file—rather than keeping them spread across several files.
You can use other `!include` methods for packages; for example `!include_dir_merge_named`. However, unlike `!include_dir_merge_named`, the `!include_dir_named` method uses the same indentation as the ‘configuration.yaml’. This means that you can copy and paste elements from the config file. With `!include_dir_named`, the file name is used as the package name. File names must be unique.

With the `!include_dir_merge_named` method, the package name has to be included in the file. The configuration below then needs to be indented accordingly. This means you cannot directly copy and paste from the configuration file.

```yaml
homeassistant:
  packages: !include_dir_merge_named packages/
```

YAML

Copy

and in `packages/subsystem1/functionality1.yaml`:

```yaml
subsystem1_functionality1:
  input_boolean:
  ...
  binary_sensor:
  ...
  automation:
```

YAML

Copy

## Customizing entities with packages

It is possible to [customize entities](https://www.home-assistant.io/docs/configuration/customizing-devices/) within packages. Just create your customization entries under:

```yaml
homeassistant:
  customize:
```

YAML

Copy

Important

If you are moving configuration to packages, `auth_providers` must stay within ‘configuration.yaml’. See the general documentation for [Authentication Providers](https://www.home-assistant.io/docs/authentication/providers/#configuring-auth-providers).

This is because Home Assistant processes the authentication provided early in the start-up process, even before packages are processed.

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/configuration/packages.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fconfiguration%2Fpackages%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fconfiguration%2Fpackages%2F%22&in=body "View given feedback for this page")
