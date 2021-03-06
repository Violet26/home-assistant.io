---
title: "Logger"
description: "Instructions on how to enable the logger integration for Home Assistant."
logo: home-assistant.png
ha_category:
  - Utility
ha_qa_scale: internal
ha_release: 0.8
---

The `logger` integration lets you define the level of logging activities in Home
Assistant.

To enable the `logger` integration in your installation,
add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
logger:
```

To log all messages and ignore events lower than critical for specified
components:

```yaml
# Example configuration.yaml entry
logger:
  default: info
  logs:
    homeassistant.components.yamaha: critical
    custom_components.my_integration: critical
```

To ignore all messages lower than critical and log event for specified
components:

```yaml
# Example configuration.yaml entry
logger:
  default: critical
  logs:
    # log level for HA core
    homeassistant.core: fatal
    
    # log level for MQTT integration
    homeassistant.components.mqtt: warning
    
    # log level for SmartThings lights
    homeassistant.components.smartthings.light: info

    # log level for a custom component
    custom_components.my_integration: debug

    # log level for the `aiohttp` Python package
    aiohttp: error

    # log level for both 'glances_api' and 'glances' integration
    homeassistant.components.glances: fatal
    glances_api: fatal
```

The log entries are in the form  
*timestamp* *log-level* *thread* [**namespace**] *message*  
where **namespace** is the *<component_namespace>* currently logging. 

{% configuration %}
  default:
    description: Default log level. See [log_level](#log-levels).
    required: false
    type: string
    default: debug
  logs:
    description: List of integrations and their log level.
    required: false
    type: map
    keys:
      '&lt;component_namespace&gt;':
        description: Logger namespace of the component. See [log_level](#log-levels).
        type: string
{% endconfiguration %}

In the example, do note the difference between 'glances_api' and 'homeassistant.components.glances' namespaces, 
both of which are at root. They are logged by different APIs.

### Log Levels

Possible log severity levels, listed in order from most severe to least severe, are:

- critical
- fatal
- error
- warning
- warn
- info
- debug
- notset

## Services

### Service `set_default_level`

You can alter the default log level (for integrations without a specified log
level) using the service `logger.set_default_level`.

An example call might look like this:

```yaml
service: logger.set_default_level
data:
  level: info
```

### Service `set_level`

You can alter log level for one or several integrations using the service
`logger.set_level`. It accepts the same format as `logs` in the configuration.

An example call might look like this:

```yaml
service: logger.set_level
data:
  homeassistant.core: fatal
  homeassistant.components.mqtt: warning
  homeassistant.components.smartthings.light: info
  custom_components.my_integration: debug
  aiohttp: error
```

The log information are stored in the
[configuration directory](/docs/configuration/) as `home-assistant.log`
and you can read it with the command-line tool `cat` or follow it dynamically
with `tail -f`.

If you are a Hass.io user, you can use the example below, when logged in through
the [SSH add-on](/addons/ssh/):

```bash
$ tail -f /config/home-assistant.log
```
