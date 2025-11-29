The `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI.[ [Learn more]](https://www.home-assistant.io/docs/configuration/) file is a plain-text file, thus it is readable by anyone who has access to the file. The file contains passwords and API tokens which need to be redacted if you want to share your configuration.
By using `!secret` you can remove any private information from your configuration files. This separation can also help you to keep easier track of your passwords and API keys, as they are all stored at one place and no longer spread across the `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI.[ [Learn more]](https://www.home-assistant.io/docs/configuration/) file or even multiple YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files.[ [Learn more]](https://www.home-assistant.io/docs/configuration/yaml/) files if you [split up your configuration](https://www.home-assistant.io/docs/configuration/splitting_configuration/).
## Using secrets.yaml 
The workflow for moving private information to `secrets.yaml` is very similar to the [splitting of the configuration](https://www.home-assistant.io/docs/configuration/splitting_configuration/). Create a `secrets.yaml` file in your Home Assistant [configuration directory](https://www.home-assistant.io/docs/configuration/).
The entries for password and API keys in the `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI.[ [Learn more]](https://www.home-assistant.io/docs/configuration/) file usually looks like the example below.
```
rest:
  - authentication: basic
    username: "admin"
    password: "YOUR_PASSWORD"
    ...
```

YAML
Copy
Those entries need to be replaced with `!secret` and an identifier.
```
rest:
  - authentication: basic
    username: "admin"
    password: !secret rest_password
    ...
```

YAML
Copy
The `secrets.yaml` file contains the corresponding password assigned to the identifier.
```
rest_password: "YOUR_PASSWORD"
```

YAML
Copy
## Debugging secrets 
When you start splitting your configuration into multiple files, you might end up with configuration in sub folders. Secrets will be resolved in this order:
  * A `secrets.yaml` located in the same folder as the YAMLYAML is a human-readable data serialization language. It is used to store and transmit data in a structured format. In Home Assistant, YAML is used for configuration, for example in the `configuration.yaml` or `automations.yaml` files.[ [Learn more]](https://www.home-assistant.io/docs/configuration/yaml/) file referencing the secret,
  * next, parent folders will be searched for a `secrets.yaml` file with the secret, stopping at the folder with the main `configuration.yaml`The configuration.yaml file is the main configuration file for Home Assistant. It lists the integrations to be loaded and their specific configurations. In some cases, the configuration needs to be edited manually directly in the configuration.yaml file. Most integrations can be configured in the UI.[ [Learn more]](https://www.home-assistant.io/docs/configuration/).


To see where secrets are being loaded from, you can add an option to your `secrets.yaml` file.
Print where secrets are retrieved from to the Home Assistant log by adding the following to `secrets.yaml`:
```
logger: debug
```

YAML
Copy
This will not print the actual secret’s value to the log.
## Related topics 
  * [ Configuration.yaml file ](https://www.home-assistant.io/docs/configuration/)
  * [ Splitting the configuration ](https://www.home-assistant.io/docs/configuration/splitting_configuration/)
  * [ Securing your instance ](https://www.home-assistant.io/docs/configuration/securing/)


####  **Help us improve our documentation**
Suggest an edit to this page, or provide/view feedback for this page. 
