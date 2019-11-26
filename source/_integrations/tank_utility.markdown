---
title: "Tank Utility Sensor"
description: "How to integrate Tank Utility sensors within Home Assistant."
logo: tank_utility.png
ha_category:
  - Energy
ha_release: 0.53
---

Add [Tank Utility](https://www.tankutility.com/) propane tank monitors to Home Assistant.

## Setup

### Authentication

Authentication for the Tank Utility API is performed with the same email and password credentials used at [https://app.tankutility.com](https://app.tankutility.com).

### Devices

Each item in the list of devices is a 24 character string. You can get your device string by:


Going to https://data.tankutility.com/api/getToken
Log in with your tank utility credentials. 
This will give you a token string in the browser window that you need for the next step.
In a new browser window, paste this link into the navigation bar.
https://data.tankutility.com/api/devices?token=TOKEN_STRING
The device string will now be shown in the browser. 

## Configuration

To enable the component, add the following lines to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: tank_utility
    email: YOUR_EMAIL_ADDRESS
    password: YOUR_PASSWORD
    devices:
      - 000000000000000000000000
```

{% configuration %}
email:
  description: "Your [https://app.tankutility.com](https://app.tankutility.com) email address."
  required: true
  type: string
password:
  description: "Your [https://app.tankutility.com](https://app.tankutility.com) password."
  required: true
  type: string
unit_of_measurement:
  description: All devices to monitor.
  required: true
  type: map
{% endconfiguration %}
