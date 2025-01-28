# Control Wallbox Pulsar Max EV Charging from Hass.io using Node-Red

A super simple (KISS!) method to control a Wallbox Pulsar EV charger from Home Assistant using Node-Red. Scheduled, Immediate, and Solar tracking charge modes are supported. Solar tracking will continuously update the charge current to utilise available solar and includes hysteresis for passing clouds (or an appliance being switched on in the home). _This scheme could be applied to any EV charger and solar inverter that supports integration with Home Assistant._

#### Home Assistant UI:

<img src="https://github.com/colwilliamsnz/Hass-Wallbox-Charge-Control/raw/main/images/hass_ui.png" width="300">

#### Solar Tracking showing charger power output following available excess solar:

<img src="https://github.com/colwilliamsnz/Hass-Wallbox-Charge-Control/raw/main/images/solar_tracking.png" width="600">

#### Node-Red flow:

<img src="https://github.com/colwilliamsnz/Hass-Wallbox-Charge-Control/raw/main/images/node-red.png" width="1000">

#### Requirements:

1. Home Assistant
2. Node-Red
3. Home Assistant Wallbox integration
4. A Solar inverter and supporting Home Assistant integration. Sensor for "Export Power". _In my case I have a Fronius inverter._

##### Home Assistant

1. Add four helpers of type "Input Boolean": evcharger_mode_disable, evcharger_mode_immediate, evcharger_mode_schedule, evcharger_mode_solar.
2. Add scripts from the scripts folder (these are intended to toggle the above booleans on/off so that only one can be active at a time).
3. Add UI yaml to your dashboard.

##### Node-Red

1. Import the flow.
2. Update all of the blue coloured nodes to reflect your Wallbox and Solar inverter integrations.
3. Set specific configuration via the Node-Red flow using the "Set flow configuration variables" node. Eg, Min and Max charge current, hysteresis/cooldown period, etc.
4. Set desired scheduled charging time slot via the Node-Red flow using the "Schedule" node.
