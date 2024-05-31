<h1 align="center">GameMod_ESP32-S2-S3_PS4_Server_900u</h1>

<div align="center">
<img src="./images/ps4serverlogo.png" alight-itens="center">
</div>

[![GitHub contributors](https://img.shields.io/github/contributors/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u)](https://github.com/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/graphs/contributors)
[![GitHub All Releases](https://img.shields.io/github/downloads/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/total)](https://github.com/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/releases)
[![Latest release](https://img.shields.io/github/v/release/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u)](https://github.com/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/releases)
[![GitHub issues](https://img.shields.io/github/issues/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u)](https://github.com/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/issues)

Modded PS4 900FW Auto Host For ESP32-S2/S3 Boards Based on Stooged's ["ESP32 Server 9.00u"](https://github.com/stooged/ESP32-Server-900u) and MUXI's ["MUXI900u"](https://psxtools.de/forum/index.php?thread/89778-ps4-exploit-muxi900u-mit-usb-emulation-f%C3%BCr-esp32-s2-s3/).


This is a project designed for the [ESP32-S2](https://www.espressif.com/en/products/socs/esp32-s2), *[ESP32-S3](https://www.espressif.com/en/products/socs/esp32-s3) and [ESP32](https://www.espressif.com/en/products/socs/esp32) boards to provide a WiFi HTTP server, DNS server and *<b>USB storage emulation</b>.
It was designed for the [PS4 9.00 OOB Exploit](https://github.com/ChendoChap/pOOBs4) and combined with [PsFree](https://wololo.net/2023/12/04/psfree-webkit-exploit-for-ps4-6-00-to-9-60-and-ps5-1-00-to-5-50-quickhen-toolkit-announced).

The only files required on the storage of the ESP32 are the .bin payloads, everything else is handled internally including generating a list of payloads.

You can modify the HTML by uploading your own index.html, and if there is no index.html on the storage the internal pages will be used.

If you have problems compiling the sketch make sure the [ESP32 library](https://github.com/stooged/ESP32-Server-900u#libraries) is up to date.

The firmware and payloads files can be managed via HTTP.

If you select a `No OTA` partition the firmware update via HTTP will not be available.

You can access the main page from the userguide or the consoles web browser using any hostname.

 
## ESP32 Boards
If you're using a <b>ESP32</b> board `the usb emulation will not be available` so you'd need to wire a USB drive up to it like it's shown in Stooged's project [PS4-Server-900u](https://github.com/stooged/PS4-Server-900u), or you could manually plug and unplug a USB drive containing the <b>exfathax</b>.
This is the [wiring diagram](https://github.com/stooged/ESP32-Server-900u/blob/main/Images/esp32_diag.jpg) for the ESP32 boards.


## ESP32-S2 Boards
If you're using a <b>ESP32-S2</b> you'd not need a USB drive with this project as it emulates an USB mass storage device to the console and triggers the filesystem bug to leverage the exfathax exploit.


## ESP32-S3 Boards
If you're using a <b>ESP32-S2</b> you'd not need a USB drive with this project as it emulates an USB mass storage device to the console and triggers the filesystem bug to leverage the exfathax exploit.


## Libraries needed to compile this project
This project is built using [<b>ESPAsyncWebSrv</b>](https://github.com/me-no-dev/ESPAsyncWebServer) and [<b>AsyncTCP</b>](https://github.com/me-no-dev/AsyncTCP) so you need to add these libraries to your Arduino IDE.

Install or update the ESP32 core by adding [this URL](https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json) to the Additional Boards Manager URLs section in the Arduino IDE "<b>Preferences</b>".
Then go to the "<b>Boards Manager</b> and install or update the "<b>ESP32</b>" core.

If you have problems with the board being identified/found in windows then you might need to install the [USB to UART Bridge](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers) drivers.


PS: As of today (May, 29th 2024, changes in the `mbedtls` lybrary caused this project to not compile correctly and some changes in the <b>ESPAsyncWebSrv</b> need to be made:<br>
-Inside <b>WebAuthentication.cpp</b> change the `mbedtls_md5_starts_ret` call to `mbedtls_md5_starts`.<br>
-Inside <b>WebAuthentication.cpp</b> change the `mbedtls_md5_update_ret` call to `mbedtls_md5_update`.<br>
-Inside <b>WebAuthentication.cpp</b> change the `mbedtls_md5_finish_ret` call to `mbedtls_md5_finish`.<br>
-Inside <b>AsyncWebSocket.cpp</b> change the `mbedtls_sha1_starts_ret` call to `mbedtls_sha1_starts`.<br>
-Inside <b>AsyncWebSocket.cpp</b> change the `mbedtls_sha1_update_ret` call to `mbedtls_sha1_update`.<br>
-Inside <b>AsyncWebSocket.cpp</b> change the `mbedtls_sha1_finish_ret` call to `mbedtls_sha1_finish`.<br>
-Inside <b>AsyncEventSource.cpp</b> comment out the line `ets_printf("ERROR: Too many messages queued\n");`.


## Using this project in your ESP32 board
<b>Programming de ESP32 board:</b><br>
-Go to the [latest release](https://github.com/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/releases/latest) page, download the most recent <b>GameMod_ESP32S2-S3_PS4Server900u_DDMMYYYY.zip</b>, extract it to your computer.<br>
-Download the [latest NodeMCU-PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases/latest) and flash the <b>GameMod_ESP32-S2-S3_PS4_Server_900u.ino.merged.bin</b> file to your board using the parameters in the image below.<br>
<img src=https://github.com/gamemoddesignbr/GameMod_ESP32-S2-S3_PS4_Server_900u/blob/main/images/nodemcu_pyflasher.png>


<b>Uploading the necessary files:</b><br>
-Connect to the board WiFi access point with a PC/laptop (<b>GameMod_PS4_WiFi</b> is the default SSID and <b>123456789</b> is the default password).<br>
-Use a web browser and go to http://10.1.1.1/admin.html (http://ps4.local).<br>
-On the side menu of the admin page select <b>File Uploader</b>, then click <b>Select Files</b> and locate the <b>data</b> folder inside the <b>GameMod_ESP32-S2-S3_PS4_Server_900u</b> folder.<br>
-Select all files and click <b>Upload Files</b>.


## Configuring the project in your ESP32 board
You can access the admin page and your ESP32 to be used as a Access Point (AP) and have your PS4 completely offline, or configure the ESP32 to connect to your WiFi (specifiying a static IP) so your PS4 could be connected to the same WiFi and still use the ESP32 for exploit and keep access to the internet.


## Board LED configuration
The project allows you to have a LED to inform you the board status.<br>
Depending on the board you're using it could have a built in LED you could use. If the board doesn't have any built in LED, just mod it and use one of the I/O pins to drive the LED you added.<br>
Then configure the board to use the I/O PIN you want (or the built in I/O pin the built in LED is using) and enable the LED usage.<br><br>
The LED status will be as the following:
-Three quick blinks: the board is booting<br>
-Intermitently blinking: the board finished booting and it's configured as Access Point<br>
-Solid: the board finished booting and it's configured as WiFi connection.


## Tested Boards
:white_check_mark: These [ESP32-S2](https://www.espressif.com/en/products/socs/esp32-s2) boards can be used for a plug and play setup (no wiring)

4MB boards<br>
:ok: [S2 Mini](https://www.wemos.cc/en/latest/s2/s2_mini.html)<br>
:ok: [TinyS2](https://unexpectedmaker.com/tinys2)<br>
:ok: [Adafruit QT Py ESP32-S2](https://www.adafruit.com/product/5325)<br>
:ok: [ESP32-S2-DevKitC-1](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/hw-reference/esp32s2/user-guide-s2-devkitc-1.html)<br>
:ok: [LILYGO TTGO T8 ESP32-S2 WOOR](http://www.lilygo.cn/prod_view.aspx?TypeId=50063&Id=1320&FId=t3:50063:3)<br>
:ok: [LILYGO TTGO T8 TF Card Slot](http://www.lilygo.cn/prod_view.aspx?TypeId=50063&Id=1300&FId=t3:50063:3)<br>

16MB boards<br>
:ok: [FeatherS2](https://feathers2.io/)

:white_check_mark: These [ESP32-S2](https://www.espressif.com/en/products/socs/esp32-s2) boards will need a USB type A plug wired up to them.<br>

4MB boards<br>
:ok: [ESP32-S2-DevKitM-1](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/hw-reference/esp32s2/user-guide-devkitm-1-v1.html) Wiring [Diagram](https://github.com/stooged/ESP32-Server-900u/blob/main/Images/esp32-s2-devkitm-1.jpg)<br>
:ok: [ESP32-S2-Saola-1](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/hw-reference/esp32s2/user-guide-saola-1-v1.2.html) Wiring [Diagram](https://github.com/stooged/ESP32-Server-900u/blob/main/Images/esp32-s2-saola-1.jpg)<br>
:ok: [Ai-thinker ESP 12K](https://docs.ai-thinker.com/en/12k_development_board_esp32-s2) Wiring [Diagram](https://github.com/stooged/ESP32-Server-900u/blob/main/Images/ai-thinker-esp12k.jpg)<br>

:white_check_mark: These [ESP32-S3](https://www.espressif.com/en/products/socs/esp32-s3) boards can be used for a plug and play setup (no wiring)

:ok: [ESP32-S3-DevKitC-1](https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/hw-reference/esp32s3/user-guide-devkitc-1.html)


## Internal pages
* <b>admin.html</b> - the main landing page for administration.
* <b>index.html</b> - if no index.html is found the server will generate a simple index page and list the payloads automatically.
* <b>info.html</b> - provides information about the esp board.
* <b>upload.html</b> - used to upload files(<b>.bin</b>) to the esp board for the webserver.
* <b>update.html</b> - used to update the firmware on the esp board (<b>fwupdate.bin</b>).
* <b>fileman.html</b> - used to <b>view</b> / <b>download</b> / <b>delete</b> files on the internal storage of the esp board.
* <b>config.html</b> - used to configure wifi ap and ip settings.
* <b>format.html</b> - used to format the internal storage of the esp board.
* <b>reboot.html</b> - used to reboot the esp board


## 3D Cases
Stooged has created some basic printable cases for the following boards.
These cases can be printed in PLA without supports.

### ESP32-S2 Boards
[Adafruit QT Py](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/Adafruit_QT_Py)<br>
[UM FeatherS2](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/UM_FeatherS2)<br>
[UM TinyS2](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/UM_TinyS2)<br>
[Wemos S2 Mini](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/Wemos_S2_Mini)<br>
[DevKitM-1](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/DevKitM_1)<br>
[ESP32-S2-Saola-1](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/ESP32_S2_Saola_1)<br>
[LILYGO-TTGO-T8-TF-Card-Slot](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/LILYGO_TTGO_T8_TF_Card_Slot)<br>
[LILYGO-TTGO-T8-WOOR](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/LILYGO_TTGO_T8_WOOR)<br>


### ESP32-S3 Boards
[S3_DevKitC_1](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/S3_DevKitC_1)


### ESP32 Boards
[NodeMCU-32](https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/NodeMCU_32)

If you wish to edit the cases you can import the `.stl` files into [Tinkercad](https://www.tinkercad.com/) and edit them to suit your needs.