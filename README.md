Fork comments and notes:
==========

This is another fork from the main project, regarding this ESP32 MQTT client for Airthings Wave (gen1) BLE Radon sensors.

The objective is continuing to improve the project and give international users the possibility to get a precompiled binary file (ready to flash an ESP32) and report the Radon concentration in International System Units of Becquerel/cubic meter (Bq/m^3) instead of the non-SI unit pico Currie/litre (pCi/l).

TO DO:
- [ ] Precompiled binary, with WifiManager to configure a first flashed ESP32 through its configurable and own Wifi access point.
- [X] Change units from pCi/l to Bq/m^3

Airthing MQTT Bridge via an ESP32
==========

* Original Author: Stephen Beechen
* Forked from: debsahu/AirthingsMQTT
* Copyright (C) 2019 Stephen Beechen
* Released under the MIT license.

 An ESP32 arduino sketch that searches for a compatible Airthings device and publishes the radon level, temperature, and humidity to an MQTT Broker, such as Mosquitto and others.

 The sketch was created with the intention to allow Airthings devices to cheaply integrate with Home Assistant.

How to Use
----------
* Set up your Airthings following the manufacter's instructions.
* Install the [PubSubClient library](https://pubsubclient.knolleary.net/).
* Set your WiFi credentials in the sketch.
* Set your MQTT server/credentials in the sketch.
* Update the published topics in the sketch, if desired.
* Flash to any ESP32 board.  NOTE: The Bluetooth library is HUGE, so in the Arduino IDE you might need to change "Tools" -> Partition Scheme" to something like "No OTA" to create enough space for the compiled sketch.
* Watch the Serial output to make sure it works.

Usage Details
---------------------
* Regading Radon concentration, the Airthings Wave (gen1) only reports the 24 hour and lifetime averages over Bluetooth.
* The library runs once an hour to take a reading and deep sleeps in between, so feasibly this could run on a battery for a very long time.
* The library will attempt to find any airthings device to read from, picking the first it finds.  The Airthings BLE API is unauthenticated so no device configuration or pairing is necessary on the Airthings.
* The library will not interfere with your Airthings' normal upload to a phone or the cloud.
* If it fails to read, it will attempt again after 30 seconds.
* Tested only with an Airthings Wave (gen1), firmware `BLE:COR9001B.1703301, MSP 2020-6-22`
* The ESP32's bluetooth stack is a little unstable IMHO so expect this to hang for a few minutes, restart prematurely, and report errors often.


License
-------

MIT License

Copyright (c) 2019 Stephen Beechen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
