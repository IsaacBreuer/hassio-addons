# RTL433 to MQTT Bridge hass.io addon With auto  dynamic discovery 

mqtt auto discovery for dg-r8s cheap sensor
https://www.banggood.com/search/dg-r8s.html

just add name:id and it will automatily add this sensor if you have mqtt discovery on

use unique name as discovery will not add if that name is already used
A hass.io addon for a software defined radio tuned to listen for 433MHz RF transmissions and republish the data via MQTT

This hass.io addon is based on Chris Kacerguis' project here: https://github.com/chriskacerguis/honeywell2mqtt,
which is in turn based on Marco Verleun's rtl2mqtt image here: https://github.com/roflmao/rtl2mqtt

## Usage

1) Install the addon.

2) Use addon configuration to configure:
- mqtt_host
- mqtt_user
- mqtt_password
- mqtt_topic
- protocol (see https://github.com/merbanan/rtl_433 for more details inc protocol IDs)
- list youre name of sensor you want to create and the rid for that sensor, 

i have create a automation in my hass thet will alert with the rid if the button is pressed, so when changing berrtryis you just press the button and get the new rid , enter it the the addon config restart the addon and done.

3) Copy rtl2mqtt.sh to your hass.io config dir in a subdir called rtl4332mqtt.
i.e.
.../config/rtl4332mqtt/rtl2mqtt.sh
This allows you to edit the start script if you need to make any changes

4) Start the addon


## MQTT Data
```json
{"time" : "2020-08-27 18:45:44", "model" : "Prologue sensor", "id" : 9, "rid" : 52, "channel" : 1, "battery" : "GOOD", "button" : 0, "temperature_C" : 22.700, "humidity" : 56}
```

## Troubleshooting

If you see this error:

> Kernel driver is active, or device is claimed by second instance of librtlsdr.
> In the first case, please either detach or blacklist the kernel module
> (dvb_usb_rtl28xxu), or enable automatic detaching at compile time.

Then run the following command on the host

```bash
sudo rmmod dvb_usb_rtl28xxu rtl2832
```
