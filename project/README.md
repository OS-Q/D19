# Room Climate Monitor 

### Hardware
* An ESP8266 module or a development board like **WeMos D1 mini** or **NodeMcu 1.0** with at least **32Mbit Flash (equals to 4MBytes)** (ESP32 does not supported for now)
* A HTU21D Module or Si7021 Module or AM2320 module


### Software

#### Building With PlatformIO
##### Backend
The build environment is based on [PlatformIO](http://platformio.org). Follow the instructions found here: http://platformio.org/#!/get-started for installing it.

The resulting (built) image(s) can be found in the directory ```/bin``` created during the build process.

##### Frontend

You can not simply edit Web UI files because you will need to convert them to C arrays, which can be done automatically by a gulp script that can be found in tools directory or you can use compiled executables at the same directory as well (for Windows PCs only).

If you want to edit esp-rcm's Web UI you will need (unless using compiled executables):
* NodeJS
* npm (comes with NodeJS installer)
* Gulp (can be installed with npm)

Gulp script also minifies HTML and JS files and compresses (gzip) them. 

In order to test your changes without flashing the firmware you can launch websocket emulator which is included in tools directory.
* You will need to Node JS for websocket emulator.
* Run ```npm update``` to install dependencies
* Run emulator  ```node wserver.js```
* then you will need to launch your browser with CORS disabled:
* ```chrome.exe --args --disable-web-security -–allow-file-access-from-files --user-data-dir="C:\Users\USERNAME"```


### Pin Layout

The following table shows the typical pin layout used for connecting readers hardware to ESP:

| Signal    | Sensor | WeMos D1 mini | NodeMcu | Generic     |
|-----------|:------:|:-------------:|:-------:|:-----------:|
| I2C SDA   |  SDA   | D2            | D2      | GPIO-4      |
| I2C SCL   |  SCL   | D1            | D1      | GPIO-5     |
