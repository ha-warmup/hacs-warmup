# Deprecated

**This project is no longer being maintained**, 
as the contributors have now worked to 
integrate HACS compatibility into the main
ha-warmup repo at <https://github.com/ha-warmup/warmup/>

Please update your Home Assistant Community Store 
settings so that the Custom Repository for the Warmup integration now points to 

```
https://github.com/ha-warmup/warmup/
```

# Introduction

This software is a Home Assistant Community Store ([HACS](https://hacs.xyz/)) integration for Warmup devices.

[Warmup](https://www.warmup.co.uk/) manufacture underfloor heating and
control systems and their wifi-enabled home thermostat, [warmup
4IE](https://www.warmup.co.uk/thermostats/smart/4ie-underfloor-heating),
has an API. This software enables communication via this API, and allows
Home Assistant to read and control the device (currently just this one
model).

For instructions on how to **install** this component please keep
reading below.

There is more detailed documentation on the API and the information
returned from the device on the [main ha-warmup documentation
wiki](https://github.com/ha-warmup/warmup/wiki). If you have issues
using this software then please check our [Issue
list](https://github.com/ha-warmup/hacs-warmup/issues) and if someone else
has not already, then do raise a new issue. If you wish you become more
involved with the project then please see our [guide to
contributing](https://github.com/ha-warmup/hacs-warmup/blob/master/CONTRIBUTING.md).

## History

This code is derived from some great work by
[\@robchandhok](https://github.com/robchandhok) to convert the original [Warmup
Custom Component and Python
Package](https://github.com/ha-warmup/warmup), based on work by
[\@alex0103](https://github.com/alex-0103) to create a [Home Assistant
Custom Component and Python
Package](https://github.com/alex-0103/warmup4IE). This has been improved
by a number of coders, notably
[\@foxy82](https://github.com/foxy82/warmup4IE) and the code was
origianlly inspired by [\@alyc100](https://github.com/alyc100)\'s
project for SmartThingsHub
[here](https://github.com/alyc100/SmartThingsPublic/blob/master/devicetypes/alyc100/warmup-4ie.src/warmup-4ie.groovy).
Many Thanks to all the contributors who helped us get here.!

Warmup Plc was not involved in the creation of this software and has not
sanctioned or endorsed it in any way. 4IE is a registered trademark of
Warmup Plc.

## License

This software is published under Apache 2.0 license. Please see LICENSE.md.

# Usage

<need to change this section to reflect the fact it's now a HACS integration>

## Home Assistant Community Store

<for now see https://hacs.xyz/ >

### Register with My Warmup

To setup this component, you need to register to warmup first. see
<https://my.warmup.com/login>

### Deploy HACS integration 
Add this repo (https://github.com/ha-warmup/hacs-warmup) to HACS by following [the HACS custom repositories guide](https://hacs.xyz/docs/faq/custom_repositories)

#### Warnings in logs

Note that once you have successfully 
deployed the custom component and restarted you Home Assistant, 
you should see the following warning in the logs:

    WARNING [homeassistant.loader] 
    We found a custom integration warmup which has not been tested by Home Assistant. 
    This component might cause stability problems, be sure to disable it if you experience issues with Home Assistant

This is a positive sign, as it means 
the custom component has been successfully loaded. Great! - now carry on.

### Add the warmup platform manually via YAML

Then add to your configuration.yaml:

```yaml
climate:
  - platform: warmup
    username: YOUR_E_MAIL_ADDRESS
    password: YOUR_PASSWORD
```

-   **username** (required): the username used to login to the warmup
    web site
-   **password** (required): the password used to login to the warmup
    web site; may be moved to the secrets.yaml file. See
    [secrets](https://www.home-assistant.io/docs/configuration/secrets/)

After restarting home assistant, the component will be loaded
automatically.

### Add your devices to the dashboard

Our wiki has some [ideas on how to configure warmup
devices](https://github.com/ha-warmup/warmup/wiki/Configuration-ideas)
in your Home Assistant instance.


# Status

## Device Versions

Supported models:

-   4IE

This is currently the only model that developers and testers have
available to work on.

## Supported Features

At the moment the library supports reading current temperature, target
temperature plus other values from the thermostat and setting the target
temperature, switching between manual, automatic and frost protection
mode, switching the device off. and setting a temporary override.

For further information on versions please see the
[CHANGELOG](https://github.com/ha-warmup/warmup/blob/master/CHANGELOG.md)
