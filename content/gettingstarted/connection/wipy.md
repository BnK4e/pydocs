---
title: "WiPy"
aliases:
    - gettingstarted/connection/wipy.html
    - gettingstarted/connection/wipy.md
    - chapter/gettingstarted/connection/wipy
    - gettingstarted/wipy.html
---

## Basic connection


{% tabs first="Exp Board 2.0", second="Exp Board 3.0", third="Pytrack/Pysense/Pyscan", forth="USB UART Adapter", fifth="WiFi" %}
{% content "first" %}
* Look for the reset button on the module (located at a corner of the board, next to the LED).
* Locate the USB connector on the expansion board.
* Insert the WiPy module on the the expansion board with the reset button pointing towards the USB connector. It should firmly click into place and the pins should now no longer be visible.

![](/gitbook/assets/expansion_board_2_wipy.png)

{% content "second" %}
* Before connecting your module to an Expansion Board 3.0, you should update the firmware on the Expansion Board 3.0. Instructions on how to do this can be found [here](../../pytrackpysense/installation/firmware).
* Look for the reset button on the module (located at a corner of the board, next to the LED).
* Locate the USB connector on the expansion board.
* Insert the WiPy module on the Expansion Board with the reset button pointing towards the USB connector. It should firmly click into place and the pins should now no longer be visible.

![](/gitbook/assets/expansion_board_3_wipy.png)

{% content "third" %}
* Before connecting your module to a Pysense/Pytrack/Pyscan board, you should update the firmware on the Pysense/Pytrack/Pyscan. Instructions on how to do this can be found [here](../../pytrackpysense/installation/firmware).
* Look for the reset button on the WiPy module (located at a corner of the board, next to the LED).
* Locate the USB connector on the Pysense/Pytrack/Pyscan.
* Insert the module on the Pysense/Pytrack/Pyscan with the reset button pointing towards the USB connector. It should firmly click into place and the pins should now no longer be visible. ![](../../.gitbook/asssets/pysense_wipy.png) ![](/gitbook/assets/pytrack_wipy.png)

{% content "fourth" %}
* Firstly you will need to connect power to your WiPy. You will need to supply `3.5v`-`5.5v` to the `Vin` pin.

Do **not** feed `3.3v` directly to the `3.3v` supply pin, this will damage the regulator.


* The connect the `RX` and `TX` of your USB UART to the `TX` and `RX` of the WiPy respectively.

Please ensure you have the signal level of the UART adapter set to `3.3v` before connecting it.


* In order to put the WiPy into bootloader mode to update the device firmware you will need to connect `P2` to `GND`. We recommend you connect a button between the two to make this simpler.

![](/gitbook/assets/uart_wipy.png)


{% content "fifth" %}
**Note:** This method of connection is not recommended for first time users. It is possible to lock yourself out of the device, requiring a USB connection.

* In order to access the WiPy via WiFi you only need to provide `3.5v` - `5.5v` on the `Vin` pin of the WiPy:

![](/gitbook/assets/bare_wipy.png)

* By default, when the WiPy boots, it will create a WiFi access point with the following credentials:
  * SSID: `wipy-wlan`
  * password: `www.pycom.io`
* Once connected to this network you will be able to access the telnet and FTP servers running on the WiPy. For both of these the login details are:
  * username: `micro`
  * password: `python`
{% endtabs %}

## Antennas

### WiFi/Bluetooth (optional)

All Pycom modules, including the WiPy, come with a on-board WiFi antenna as well as a U.FL connector for an external antenna. The external antenna is optional and only required if you need better performance or are mounting the WiPy in such a way that the WiFi signal is blocked. Switching between the antennas is done via software, instructions for this can be found [here.](/firmwareapi/pycom/network/wlan)

![](/gitbook/assets/wifi_pigtail_ant_wipy.png)

## Deep Sleep current issue

The LoPy, SiPy, and WiPy 2.0 experience an issue where the modules maintain a high current consumption in deep sleep mode. This issue has been resolved in all newer products. The cause for this issue is the DC to DC switch mode converter remains in a high performance mode even when the device is in deep sleep. The flash memory chip also does not power down. A more detailed explanation can be found [here.](https://forum.pycom.io/topic/1022/root-causes-of-high-deep-sleep-current)

## WiPy 2.0 vs WiPy 3.0

The WiPy 3.0 is an upgraded version of the WiPy 2.0 with the following changes:

* The FLASH has been upgraded from 4MB to 8MB.
* The RAM has been upgraded from 512KB to 4MB.
* The deepsleep current consumption issue has been fixed
* The antenna select pin has moved to GPIO21 (P12)

