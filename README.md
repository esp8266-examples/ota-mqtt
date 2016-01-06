# ota-mqtt
ESP8266 sketch that sends data via MQTT protocol. The sketch is updateable via OTA.

For basic OTA update sketch or more OTA info see [ota-basic sketch](https://github.com/esp8266-examples/ota-basic)

#Contents
  * [Prerequisites and limitations](#prerequisites-and-limitations)
  * [Installing software with Boards Manager](#installing-software-with-boards-manager)
  * [Flashing the esp8266 for the first time](#flashing-the-esp8266-for-the-first-time)
  * [OTA programming](#ota-programming)
  * [Issues and support](#issues-and-support)
  * [Contributing](#contributing)
  * [License and credits](#license-and-credits)



#Prerequisites and limitations:
To use this sketch you need:
  - An esp8266 board
  - Arduino software 1.6.7 or later [Download here](https://www.arduino.cc/en/Main/Software)
  - An esp8266 programmer (only to flash the esp8266 the first time)

If you edit this sketch, you must consider that, to make OTA work:
  - The sketch compiled size cannot be greater than 50% of the esp8266 memory
  - If you use File System Wrapper, you maximun sketch size must be: (TotalMemory-FilesystemSize)/2

#Installing software with Boards Manager
 * Install the Arduino Software (1.6.7 version or later)
 * Update Board Manager with custom URL:Open up Arduino, then go to the Preferences (**File > Preferences**). Then, towards the bottom of the window, copy this URL into the “Additional Board Manager URLs” text box:

  http://arduino.esp8266.com/stable/package_esp8266com_index.json

 <p align="center"><img src ="./img/arduino-board-manager-link.png?raw=true"></p>

 Note: You can add multiple URLs, separating them with commas.
 
 * Open Boards Manager from **Tools > Board** menu and install esp8266 platform (and don't forget to select your ESP8266 board from **Tools > Board** menu after installation).
 
 <p align="center"><img src ="./img/arduino-board-install.png?raw=true"></p>
 <p align="center"><img src ="./img/arduino-board-select.png?raw=true"></p>

#Flashing the esp8266 for the first time
To make the esp8266 OTA ready we need to flash de initial firmware with a esp8266 flashing circuit. For example:

 <p align="center"><img src ="./img/arduino-board-flashing.png?raw=true"></p>

You'll need to edit the sketch to set some parametres:
  * WIFI configuration: Change the 'ssid' and 'password' value to match your WIFI settings
  * MQTT server/client configuration: 
    * mqtt_server:  IP of yout MQTT server
    * mqtt_user:    Client username
    * mqtt_password:Client password
  *  MQTT message configuration:
    * mqtt_client_id: Client Id
    * mqtt_base_topic:Root for topics

 <p align="center"><img src ="./img/arduino-sketch-edit.png?raw=true"></p>

And set the configutarion of your programming circuit:
 - Board: If you don't know which is yours then select 'Generic ESP8266 module'
 - Port: The COM port of your programmer
 - Speed: 115200
 
 <p align="center"><img src ="./img/arduino-upload-speed.png?raw=true"></p>

 Now, we can upload the sketch to de esp8266.
 
 #OTA programming
  Once we have flashed the firmware of the esp8266 with an OTA enabled firmware we need to restart Arduino Software and you can dissconect the programmer serial port (or maintain it connected to use serial port for debugging, for example).
  Now, in the **Tools > Port** menu we'll find a new option, starting with 'esp8266' and including a local IP address. We must select that serial port. After that, go to **Tools > Upload using** and select **OTA** option.
  
  <p align="center"><img src ="./img/arduino-sketch-ota-option.png?raw=true"></p>
  
  Just try to upload de sketch and it'll upload over WIFI. **Note that WIFI programming is A LOT faster than serial programming**.
 
#Issues and support

If you encounter an issue, you are welcome to submit it here on Github: [https://github.com/esp8266-examples/ota-basic/issues](https://github.com/esp8266-examples/ota-basic/issues). Please provide as much context as possible: version which you are using (you can check it in Boards Manager), your sketch code, serial output, board model, IDE settings (board selection, flash size, etc).

#Contributing

For minor fixes of code and documentation, go ahead and submit a pull request.

Larger changes (rewriting parts of existing code from scratch, adding new functions to the core, adding new libraries) should generally be discussed in the chat first.

Feature branches with lots of small commits (especially titled "oops", "fix typo", "forgot to add file", etc.) should be squashed before opening a pull request. At the same time, please refrain from putting multiple unrelated changes into a single pull request.

#License and credits

Arduino IDE is developed and maintained by the Arduino team. The IDE is licensed under GPL.

ESP8266 core includes an xtensa gcc toolchain, which is also under GPL.

Esptool written by Christian Klippel is licensed under GPLv2, currently maintained by Ivan Grokhotkov: [https://github.com/igrr/esptool-ck](https://github.com/igrr/esptool-ck).

Espressif SDK included in this build is under Espressif MIT License.

ESP8266 core files are licensed under LGPL.

SPI Flash File System (SPIFFS) written by Peter Andersson is used in this project. It is distributed under MIT license.
