# CharcuteriESPHome
Port of my initial RPi based dry curing chamber controller platform to be ESPHome based.
Intention is control and remote monitoring/logging via Home Assistant (inside of my efforts anyway) and maybe a basic local screen for status display.

The system is anchored round a 3 member group of temp/Humidity sensors with some quorum sensing to have stable and reliable monitoring. (I got bit by failing sensors more than once and having this was foundational to my design criteria.).  My original criteria required wired Lan in case the controller was inside the chamber but this iteration I'm dropping that and generally assuming the controller is outside and wireless is suitable.

Hardware components:
- AHT20 family Temp/Humi sensors. (Starting with what is indeed a more expensive option for sensing than available but as mentioned, I've been bitten by cheaper options and am quite done with that.)
- TCA9548A I2C MUX, all 3 sensors and I2C to GPIO (TCA9555 or similar).  Don't need an 8 port mux but they seem to be easier to find than a 4 port.
- Logic driven relays (4 minumum for Heat, Cooling, Humidification, Humidification  and optional relay for air exchange) it is assumed air circulation is always on.  Went with more generic logic driven to appow more options/flexibility in selection to meet various locally available options, also means you don't need a 6/8 relay unit if you just want the basic 4 controls.
- ESPHome supported mcu, dev will likely start with RPi Pico W as I happen to have one on hand but may look at other options, especially if I can get wired Ethernet options in here.
