# Homebridge UniFi Occupancy Sensor

This Homebridge plugin will provide an occupancy sensor accessory to HomeKit based on the devices connected to WiFi access points managed by a [UniFi Controller](https://www.ubnt.com/download/unifi).

The plugin connects to the UniFi Controller event web socket to get instant notifications of connecting devices - which can then be used to trigger HomeKit actions like turning on the lights.

## Requirements

* Node.js v4 or later
* [UniFi Controller](https://www.ubnt.com/download/unifi) v5

## Homebridge Config

```javascript
"accessories": [
  {
    "accessory": "UniFi Occupancy Sensor",
    "name": "Occupancy Sensor",
    "unifi": {
      "controller": "https://demo.ubnt.com:8443",  // Required. The url of the UniFi Controller.
      "username": "superadmin",                    // Required. A read-only user is fine.
      "password": "password",                      // Required.
      "site": "default",                           // Optional. The UniFi site to connect to.
      "secure": false                              // Optional. Set true to validate the SSL certificate.
    },
    "watch": ["44:00:10:f0:3e:66"]                 // Required. An array of device MAC addresses to watch for.
    "watchGuests": true                            // Optional. Set false to not monitor guest networks.
  }
]
```