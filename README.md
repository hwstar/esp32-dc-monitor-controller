# DC MONITOR / CONTROLLER MODEL DCMC2



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


This hardware will be for sale on Tindie when development is completed.
It is primarily designed to work with [ESPHome](https://github.com/esphome/esphome)

## Disclaimer

By purchasing and/or using the hardware, you indicate you are using it at your own risk. 

## Audience

The controller is shipped without firmware which can connect to your WIFI network. It will require some firmware programming and electrical knowledge to successfully implement. 
One should have some experience modifying ESPHome yaml files, reading wiring diagrams, using a Windows or Linux command line shell, using serial devices such as the FTDI serial cable,
and using the ESPHome tool to program ESPHome devices. If you are not sure how to program firmware into an ESPHome device, please study the documentation on esphome.com and become
familiar with it before purchasing a board. A link to the the programming documentation can be found [here](https://esphome.io/guides/cli.html)


## Firmware

### Provisioning

The firmware will need to be provisioned on your controller before you can use it. This is because the WIFI passwords and SSID's will need to be modified so the firmware knows how to log in to your
WIFI network.

Note: It is also possible to just upload new firmware, skipping these provisioning steps should there be any trouble with the procedure below. To skip provisioning see the Customization section. 

The firmware shipped with the device supports WiFi provisioning over the serial port (Webserial) using the Google Chrome or Microsoft Edge Broswers.

You'll need a 3.3V USB serial cable to do the provisioning.

Below is the pinout of the serial connector J301.


|PIN| Signal|
|---|------------------------- |
| 1 | Ground |
| 2 | No connection |
| 3 | No Connection |
| 4 | RXD referenced to ESP32 |
| 5 | TXD referenced to ESP32 |
| 6 | No Connection |

The location of the serial connector is shown below in Connectors, Pinouts and GPIO's.'

Connect your 3.3V serial adapter to pins 1,4, and 5.Connecting RXD of the adapter to pin 5, TXD of the adapter to pin 4, and ground to pin 1.

Next, open Chrome or Edge and navigate to the following:


[link](https://esphome.github.io/esp-web-tools/)

Press the "CONNECT" button under "Try a live demo",
then select the serial port of the 3.3V serial adapter cable.

You should then see a menu. Choose the "CHANGE WIFI" Menu option.

Enter or choose the network SSID and enter your password.

Click "CONNECT"

You should see a provisioned message after clicking CONNECT.

You are now ready to upload a custom version of ESPHome to the device.


### Customization

Clone this repository to get the source code for the DC Monitor / Controller.

The firmware consists of ESPHome platform compiled with a user-customizable YAML file and some custom components which are modifications of modules contained in ESPHome. 

Before compiling, rename secrets-sample.yaml to secrets.yaml, and change items in secrets.yaml to suit your requirements.

Once compiled the firmware is installed via a 3.3V serial cable. J201 on the board is a male header which is compatible with FTDI serial cables such as FTDI part number TTL-232R-3V3. 

For firmware upload instructions please refer to the [insert link here]


### ESPHOME yaml file 

An example YAML file is provided to aid in the implementation of the DC Monitor / Controller . It contains some examples on how to do things with the hardware. Please refer to the file esp32-dc-monitor.yaml
This file can be used as the basis for your customized yaml file. 


## Hardware

The hardware can be purchased from me directly.

Hardware included in the kit:

1. 1 ea. Main PCB.
2. 1 ea. ABS plastic enclosure and graphic overlay sticker and 4 retaining screws.
3. 1 ea. mating 12 pin screw terminal pluggable power connector.
4. 2 ea. 3 pin JST connector and pigtail.
5. 2 ea. epoxy dipped NTC Thermistors (10K, B-constant 3435).

Not supplied in the kit:

1. 3.3V serial adapter for flashing firmware onto the board and connecting cable.
3. DC power source.
4. Wire.
5. Wood screws for attaching the controller to a backboard.
6. Current Shunts/Sensing resistors.


### Connectors Pinouts and GPIO's


### Connectors

#### 12 Pin Pluggable Terminal Block

The 12 pin pluggable terminal block plugs into J101 and accepts the DC power source, the voltage and current sensing channels.

|PIN| Signal|
|---|------------------------- |
| 1 | Power |
| 2 | GROUND |
| 3 | CH0 V SENSE |
| 4 | CH0 SHUNT N |
| 5 | CH0 SHUNT P |
| 6 | CH1 V SENSE |
| 7 | CH1 SHUNT N |
| 8 | CH1 SHUNT P |
| 9 | K101 A |
| 10 | K101 B |
| 11 | K102 A |
| 12 | K102 B |


* Power - +10.8 to +30VDC. A DC power supply capable of delivering at least 200mA should be used
* Ground - Return for power and the 0 volt reference for CH0 V SENSE and CH1 V SENSE inputs. 
* V SENSE - Voltage sense inputs. Positive voltages only.
* SHUNT N - The most negative terminal of the current shunt resistor.
* SHUNT P - The most positive terminal of the current shunt resistor.
* A/B - The SPST (Form A) contacts of the internal relays.

##### Shunt Selection and Wiring Best Practices

1. Use good quality current shunts with proper mounting bases.
2. Protect the wiring from the shunt to the DC monitor controller with fuses next to the shunt.
3. Use twisted pair cable for the SHUNT_N and SHUNT_P signals.
4. Select a shunt with a twice the maximum current rating of the maximum system current.

##### Voltage Sense Wiring Best Practices

1. Since ground is shared between the power supply return and the V SENSE 0 volt reference, voltage drop on the ground wire can become an issue. Use at least a 16 AWG ground wire with a maximum length of 5 feet. Connect it to the 0 volt star point in the DC distribution system.
2. Protect the wiring from the V SENSE point with a fuse to protect the wire used.

##### Power Supply wiring Best Practices

Protect the wiring from the power supply to the Power input with the appropriately sized fuse for the wire. There is a 1 amp fuse on the printed circuit board, but this will not protect the wire if there is a fault between the power source and the printed circuit board.

##### Relay Wiring Best Practices 

The relay contacts are rated at 2 Amps and 30 VDC max. Use a fused or current limited power source when powering loads from the relay outputs. Use wire capable of handling the fault and operating currents.

#### 6 Pin Serial Connector

The Serial connector J301 is pinned out to accept an FTDI cable. It is a 1x6 2.54mm pitch header located to the right of the ESP32 module. The serial connector is used to initially upload firmware to the DC Monitor / Controller 


### NTC Thermistor Connectors

The NTC thermistor connectors are 3 pin JST XH series 2.5mm pitch connectors. These connectors are labeled J102 and J103. J102 is channel 0 and J103 is channel 1.










 


