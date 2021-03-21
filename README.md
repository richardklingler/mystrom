## myStrom WiFi Plug Version 2
Make the new myStrom WiFi plug run ESPHome firmware

![myStrom Wifi Plug 2](images/mystrom_open.jpg)

### Sponsoring

All my reverse engineering work is paid with my low little budget, so every donation is very welcome, either through the Patreon link on the side or through Paypal Me:

[Paypal Me](https://paypal.me/renderingfun)

### Update

#### 20.03.2021

- Added initial YAML file
- Initial repository

### myStrom GPIO mapping

Following GPIO signals from the ESP32-W0 chip are used on myStrom Wifi 2:

    - GPIO4    Input pulses from AD71056 energy meter
    - GPIO16   Front red LED
    - GPIO17   Front white LED
    - GPIO19   I2C SCL signal for temperature sensor
    - GPIO22   I2C SDA signal for temperature sensor
    - GPIO23   Pushbutton on the side
    - GPIO27   Relay output

### myStrom ESP32 board programming header

On the ESP32 board is an unpopulated 2x9 header which can be used for flashing the ESP32 via UART. You only need VCC, GND, TXD, RXD and GPIO0 as usual:

    GND  [] ()  TXD
    GND  () ()  RXD
    GND  () ()  GPIO0
    GND  () ()
    GND  () ()
    VCC  () ()
    VCC  () ()
         () ()
         () ()

![Ready for flashing](images/mystrom_flashing.jpg)

### Temperature sensor

The onboard temperature sensor repsonds to address 0x48 and has the label "LDEA" on its SOT23-5 package.
I am not really sure what device it is actually...but it reports a temperature when using the TMP102 component from ESPHome.

Normally it reports a temperature which is around 10 degress higher than the ambient temperature. Not sure what the purpose
is of this sensor really. myStrom advertises it as additional feature for monitoring room temperatures.

Still you might use it as a thermal protection as the sensor reports a much higher temeprature when you switch on a load.