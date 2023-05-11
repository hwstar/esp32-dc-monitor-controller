# DC MONITOR / CONTROLLER MODEL DCMC2


![alt text](https://github.com/hwstar/esp32-dc-monitor-controller/blob/main/assets/logo.png)

![alt text](https://github.com/hwstar/esp32-dc-monitor-controller/blob/main/assets/dcmc2_enclosure.jpg)

![alt text](https://github.com/hwstar/esp32-dc-monitor-controller/blob/main/assets/dcmc2_board_180.jpg)

![alt text](https://github.com/hwstar/esp32-dc-monitor-controller/blob/main/assets/made-for-esphome-black-on-white.png)


This is the code and documentation repository for a DC Monitor/Controller
controller kit based on an ESP32. It has the following features:

* ESP32 Microcontroller
* Provides 2 current/voltage monitoring channels using the Texas Instruments INA226 voltage and current monitoring chip.
* High side or low side current monitoring.
* Bidirectional current monitoring (charge/discharge).
* Provides 2 sets of normally open (Form A) dry relay contacts rated for 2 amps and 30 volts DC.
* Provides 2 NTC thermistor inputs (3 pin JST XH connector).
* TVS diode protection on the power supply input, ESD diodes on the voltage sense and current sense inputs.
* Din Rail ABS Plastic Enclosure and graphic overlay sticker.
* 12 pin  Pluggable Terminal Block for Power, Voltage Sense, Current Sense, and Relay Contact Connections.
* Runs off of 10.8 to 30VDC supplied by an external power source.


This hardware will be for sale on Tindie when testing is completed.
It is primarily designed to work with [ESPHome](https://github.com/esphome/esphome)

## Disclaimer

By purchasing and/or using the hardware, you indicate you are using it at your own risk. 

## Audience

The controller is shipped without firmware which can connect to your WIFI network. It will require some firmware programming and electrical knowledge to successfully implement. 
One should have some experience modifying ESPHome yaml files, reading wiring diagrams, using a Windows or Linux command line shell, using serial devices such as the FTDI serial cable,
and using the ESPHome tool to program ESPHome devices. If you are not sure how to program firmware into an ESPHome device, please study the documentation on esphome.com and become
familiar with it before purchasing a board. A link to the the programming documentation can be found [here](https://esphome.io/guides/cli.html)


## Firmware

### Uploading

The Wiki contains detailed firmware uploading instructions for the DCMC2. 

### Customization

Clone this repository to get the source code for the DC Monitor / Controller.

The firmware consists of ESPHome platform compiled with a user-customizable YAML file and some custom components which are modifications of modules contained in ESPHome. 

Before compiling, rename secrets-sample.yaml to secrets.yaml, and change items in secrets.yaml to suit your requirements.

Once compiled the firmware is installed via a 3.3V serial cable. J301 on the board is a male header which is compatible with FTDI serial cables such as FTDI part number TTL-232R-3V3. 

For firmware upload instructions please refer to the wiki.

### ESPHOME yaml file 

An example YAML file is provided to aid in the implementation of the DC Monitor / Controller . It contains some examples on how to do things with the hardware. Please refer to the file esp32-dc-monitor.yaml
in this repository. This file can be used as the basis for your customized yaml file. 


## Hardware

The hardware can be purchased from me directly.

Hardware included in the kit:

1. 1 ea. Main PCB.
2. 1 ea. ABS plastic enclosure, graphic overlay sticker and 4 retaining screws.
3. 1 ea. mating 12 pin screw terminal pluggable power connector.
4. 2 ea. 3 pin JST connector and pigtail.

Not supplied in the kit:

1. 3.3V serial adapter for flashing firmware onto the board and connecting cable.
3. DC power source.
4. Wire.
5. Wood screws for attaching the controller to a backboard.
6. Current Shunts/Sensing resistors.

## Wiki

The Project Wiki contains wiring diagrams, connector pinouts, and GPIO's used by the DCMC2. It can be accessed from the Wiki menu item in this repository.









 


