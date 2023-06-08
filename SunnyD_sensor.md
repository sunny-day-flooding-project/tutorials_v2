# Sunny Day Flooding Sensor assembly

This will document the Sensor assembly
## Hardware

BOM or link to one

Document hardware and construction.


### Electronic Components
The sensor assembly is built around the [SparkFun OpenLog Artemis (OLA)](https://www.sparkfun.com/products/16832) module. To this are added a [Blue Robotics Bar02 Ultra High Resolution 10m Depth/Pressure Sensor](https://bluerobotics.com/store/sensors-sonars-cameras/sensors/bar02-sensor-r1-rp/), which uses the [Measurement Specialties MS5837-02BA](https://www.te.com/usa-en/product-MS583702BA01-50.html) sensor, and a bluetooth (BT) module.

**Bluetooth**

While it is expected that the [OLA firmware](https://github.com/sparkfun/OpenLog_Artemis) will eventually support BT natively, until then an external module is required to communicate with the Sunny Day Gateway via BT.

List modules used with links to purchase page and documentation.

### Power
Talk about batteries here, including Lithium vs Alkaline and expected lifespan.

### Housing
The sensor housing needs to adapt to each unique deployment situation. While there will eventually be multiple deployment types, the first few have been designed to be mounted to the underside of a storm drain grating.

**Storm Drain Mount**

The storm drain mounted housing consists of a horizontal tube housing the OLA and battery and a thin vertical tube to position the pressure sensor at the correct height. The housing needs to be water-tight when submerged, yet allow for the replacement of batteries when necessary.

## Software
Document OLA software configuration with pictures. All documentation is based on OLA Firmware version 1.11. A generic version of how to connect to and configure the OLA is available in the [OpenLog Artemis Hookup Guide](https://learn.sparkfun.com/tutorials/openlog-artemis-hookup-guide).

### How to connect to OLA
Use a teminal program like [SecureCRT](https://www.vandyke.com/products/securecrt/) (Available for free to UNC staff and students).

**Wired Connection**

OLA has USB-C port. 

**Wireless Connection**

Connecting to OLA via BT.

### OLA Menus
Main Menu:

![Main Menu](/images/hardware/MainMenu.JPG)

1. Terminal Output Menu
![Main Menu](/images/hardware/Screen1.png)
   - *Logging to microSD* should be Enabled. After communications interuptions, the gateway downloads missed data from the SD card.
   - *Logging to Terminal* should be Enabled as this is the primary way that the gateway receives data.
   - Serial Terminal Baud Rate should be set to 57600.
   - The value for *Log Rate in seconds between readings* depends on the circumstances. During deployment this will typically be set to 359 seconds, but pre-deployment, should be set to something much faster, like 4 seconds. 
   - *Enable maximum logging* should be disabled as we are no where near using the maximum sample rate.
   - *Output Actual Hertz* should be disabled. Enabling it will confuse the gateway's parser.
   - *Output Column Titles* should be enabled.
   - *Output Measurement Count* should be enabled. The gateway uses this to see if any samples have been missed.
   - *Open New Log Files After (s)* should be set to 129600 seconds (one day).
   - *Frequest logfile access timestamps* should be disabled as it is un-necessary and may increase the chances of data corruption.
   - *Use pin 11 to trigger logging* should be set to No. We use this pin for other purposes.
   - *Logging is triggered when the signal on pin 11 is* should be set to Falling. This will trigger fast logging when pin l1 is pulled to ground.
   - *Use TX and RX pins for Terminal* should be enabled. This sends the terminal to the attached BT module and allows communications with the gateway.
   - *Use pin 11 to control fast/slow logging* should be set to Yes. On system using external water level switches, this changes the logging speed from slow mode to fast mode.
   - *Log slowly when Pin 11 is* should be set to High.
   - *Use RTC to control fast/slow logging* should be set to No.
   - *Slow logging interval* should be set to 1799 after deployment, but should probably also be set to something much faster like 6 seconds before deployment.
   - *Minimum awake times between sleeps* should be set to 3000ms. 
2. Time Stamp Menu

![Main Menu](/images/hardware/Screen2.png)
   - Options and how they should be configured and why
3. IMU Logging Menu
![Main Menu](/images/hardware/Screen3.png)
   - Options and how they should be configured and why
4. Serial Logging Menu
   - We don't use serial logging. The serial port is used for communicating with the external BT module.
5. Analog Logging Menu
![Main Menu](/images/hardware/Screen5.png)
   - Options and how they should be configured and why
6. Detect / Configure Attached Devices Menu
![Main Menu](/images/hardware/Screen6.1.png)
   - Options and how they should be configured and why
7. Configure Power Options Menu

Links to hardware deployment document.
