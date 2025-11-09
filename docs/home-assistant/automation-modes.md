---
title: Automation modes - Home Assistant
description: How to use and configure automation modes.
source_url: https://www.home-assistant.io/docs/automation/modes
source_domain: www.home-assistant.io
scraped_at: 2025-11-09T20:07:33.705Z
---

An automationAutomations in Home Assistant allow you to automatically respond to things that happen in and around your home. [\[Learn more\]](https://www.home-assistant.io/docs/automation/) can be triggered while it is already running.

The automation’s `mode` configuration option controls what happens when the automation is triggered while the actionsActions are used in several places in Home Assistant. As part of a script or automation, actions define what is going to happen once a trigger is activated. In scripts, an action is called _sequence_. [\[Learn more\]](https://www.home-assistant.io/docs/automation/action/) are still running from a previous triggerA trigger is a set of values or conditions of a platform that are defined to cause an automation to run. [\[Learn more\]](https://www.home-assistant.io/docs/automation/trigger/).

| Mode | Description |
| --- | --- |
| `single` | (Default) Do not start a new run. Issue a warning. |
| `restart` | Start a new run after first stopping the previous run. The automation only restarts if the conditions are met. |
| `queued` | Start a new run after all previous runs complete. Runs are guaranteed to execute in the order they were queued. Note that subsequent queued automations will only join the queue if any conditions it may have are met at the time it is triggered. |
| `parallel` | Start a new, independent run in parallel with previous runs. |

![](https://www.home-assistant.io/images/integrations/script/script_modes.jpg)

For both `queued` and `parallel` modes, configuration option `max` controls the maximum
number of runs that can be executing and/or queued up at a time. The default is 10.

When `max` is exceeded (which is effectively 1 for `single` mode) a log message will be emitted to indicate this has happened. Configuration option `max_exceeded` controls the severity level of that log message. Set it to `silent` to ignore warnings or set it to a [log level](https://www.home-assistant.io/integrations/logger/#log-levels). The default is `warning`.

## Example throttled automation

Some automations you only want to run every 5 minutes. This can be achieved using the `single` mode and silencing the warnings when the automation is triggered while it’s running.

```yaml
automation:
  - mode: single
    max_exceeded: silent
    triggers:
      - ...
    actions:
      - ...
      - delay: 300  # seconds (=5 minutes)
```

YAML

Copy

## Example queued

Sometimes an automation is doing an action on a device that does not support multiple simultaneous actions. In such cases, a queue can be used. In that case, the automation will be executed once it’s current invocation and queue are done.

```yaml
automation:
  - mode: queued
    max: 25
    triggers:
      - ...
    actions:
      - ...
```

YAML

Copy

#### **Help us improve our documentation**

Suggest an edit to this page, or provide/view feedback for this page.


- [Edit](https://github.com/home-assistant/home-assistant.io/tree/current/source/_docs/automation/modes.markdown "Edit this page")
- [Provide feedback](https://github.com/home-assistant/home-assistant.io/issues/new?template=feedback.yml&url=https%3A%2F%2Fwww.home-assistant.io%2Fdocs%2Fautomation%2Fmodes%2F&version=2025.11.1&labels=current "Provide feedback on this page")
- [View given feedback](https://github.com/home-assistant/home-assistant.io/issues?utf8=%E2%9C%93&q=%22%2Fdocs%2Fautomation%2Fmodes%2F%22&in=body "View given feedback for this page")
