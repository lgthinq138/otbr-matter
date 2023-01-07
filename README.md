# A project that launches an openthread border through docker-compose.

1. Check that the Dongle stick is connected to the port (ex: ttyACM1) specified in the configuration file.
2. If you have several sticks in the gateway (for example, one for Zigbee and the other for Thread, they can be confused). Pass them through by-id

```
root@arm-64:/opt/services/matter# ls /dev/serial/by-id/ -l
usb-Nordic_Semiconductor_nRF528xx_OpenThread_Device_********-if01 -> ../../ttyACM1
usb-Texas_Instruments_TI_CC2531_USB_CDC___******************-if00 -> ../../ttyACM0
```
3. change in docker-compose: 
```
    - /dev/ttyACM1:/dev/ttyACM0
    - /dev/serial/by-id/usb-Nordic_Semiconductor_nRF528xx_OpenThread_Device_********-if01:/dev/ttyACM1
```
