

# GameMod_ESP32-S2-S3_PS4_Server_900u
Modded PS4 900FW Auto Host For ESP32-S2/S3 Boards Based on Stooged's ["ESP32 Server 9.00u"](https://github.com/stooged/ESP32-Server-900u) and MUXI's ["MUXI900u"](https://psxtools.de/forum/index.php?thread/89778-ps4-exploit-muxi900u-mit-usb-emulation-f%C3%BCr-esp32-s2-s3/).<br><br>
This is a project designed for the [ESP32-S2](https://www.espressif.com/en/products/socs/esp32-s2), *[ESP32-S3](https://www.espressif.com/en/products/socs/esp32-s3) and [ESP32](https://www.espressif.com/en/products/socs/esp32) boards to provide a WiFi HTTP server, DNS server and *<b>USB storage emulation</b>.
It was designed for the [PS4 9.00 OOB Exploit](https://github.com/ChendoChap/pOOBs4) and combined with [PsFree](https://wololo.net/2023/12/04/psfree-webkit-exploit-for-ps4-6-00-to-9-60-and-ps5-1-00-to-5-50-quickhen-toolkit-announced).<br>
The only files required on the storage of the ESP32 are the .bin payloads, everything else is handled internally including generating a list of payloads.<br>
You can modify the HTML by uploading your own index.html, and if there is no index.html on the storage the internal pages will be used.<br>
If you have problems compiling the sketch make sure the [ESP32 library](https://github.com/stooged/ESP32-Server-900u#libraries) is up to date.<br>
The firmware and payloads files can be managed via HTTP.<br>
If you select a `No OTA` partition the firmware update via HTTP will not be available.<br>
You can access the main page from the userguide or the consoles web browser using any hostname.<br><br> 
## ESP32 Boards
If you're using a <b>ESP32</b> board `the usb emulation will not be available` so you'd need to wire a USB drive up to it like it's shown in Stooged's project [PS4-Server-900u](https://github.com/stooged/PS4-Server-900u), or you could manually plug and unplug a USB drive containing the <b>exfathax</b>.<br>This is the [wiring diagram](https://github.com/stooged/ESP32-Server-900u/blob/main/Images/esp32_diag.jpg) for the ESP32 boards.<br><br>
## ESP32-S2 Boards
If you're using a <b>ESP32-S2</b> you'd not need a USB drive with this project as it emulates an USB mass storage device to the console and triggers the filesystem bug to leverage the exfathax exploit.<br><br>
## ESP32-S3 Boards
If you're using a <b>ESP32-S2</b> you'd not need a USB drive with this project as it emulates an USB mass storage device to the console and triggers the filesystem bug to leverage the exfathax exploit.<br><br>
## Libraries
This project is built using <b><a href=https://github.com/me-no-dev/ESPAsyncWebServer>ESPAsyncWebServer</a></b> and <b><a href=https://github.com/me-no-dev/AsyncTCP>AsyncTCP</a></b> so you need to add these libraries to your Arduino IDE.<br>
Install or update the ESP32 core by adding this URL to the <a href=https://docs.arduino.cc/learn/starting-guide/cores>Additional Boards Manager URLs</a> section in the Arduino IDE "<b>Preferences</b>".
Then go to the "<b>Boards Manager</b> and install or update the "<b>ESP32</b>" core.<br>
If you have problems with the board being identified/found in windows then you might need to install the <a href=https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers>USB to UART Bridge</a> drivers.<br><br>
## Tested Boards
These <a href=https://www.espressif.com/en/products/socs/esp32-s2>ESP32-S2</a> boards can be used for a plug and play setup (no wiring)<br><br>
4MB boards<br>
:ok: <a href=https://www.wemos.cc/en/latest/s2/s2_mini.html>S2 Mini</a><br>
:ok: <a href=https://unexpectedmaker.com/tinys2>TinyS2</a><br>
:ok: <a href="https://www.adafruit.com/product/5325">Adafruit QT Py ESP32-S2</a><br>
:ok: <a href=https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/hw-reference/esp32s2/user-guide-s2-devkitc-1.html>ESP32-S2-DevKitC-1</a><br>
:ok: <a href="http://www.lilygo.cn/prod_view.aspx?TypeId=50063&Id=1320&FId=t3:50063:3">LILYGO TTGO T8 ESP32-S2 WOOR</a><br>
:ok: <a href="http://www.lilygo.cn/prod_view.aspx?TypeId=50063&Id=1300&FId=t3:50063:3">LILYGO TTGO T8 TF Card Slot</a><br>
16MB boards<br>
:ok: <a href=https://feathers2.io/>FeatherS2</a><br>
<hr>These <a href=https://www.espressif.com/en/products/socs/esp32-s2>ESP32-S2</a> boards will need a USB type A plug wired up to them.<br><br>
4MB boards<br>
:ok: <a href=https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/hw-reference/esp32s2/user-guide-devkitm-1-v1.html>ESP32-S2-DevKitM-1</a> Wiring <a href=https://github.com/stooged/ESP32-Server-900u/blob/main/Images/esp32-s2-devkitm-1.jpg>Diagram</a><br>
:ok: <a href=https://docs.espressif.com/projects/esp-idf/en/latest/esp32s2/hw-reference/esp32s2/user-guide-saola-1-v1.2.html>ESP32-S2-Saola-1</a> Wiring <a href=https://github.com/stooged/ESP32-Server-900u/blob/main/Images/esp32-s2-saola-1.jpg>Diagram</a><br>
:ok: <a href=https://docs.ai-thinker.com/en/12k_development_board_esp32-s2>Ai-thinker ESP 12K</a> Wiring <a href=https://github.com/stooged/ESP32-Server-900u/blob/main/Images/ai-thinker-esp12k.jpg>Diagram</a><br><br>
<hr>These <a href=https://www.espressif.com/en/products/socs/esp32-s3>ESP32-S3</a> boards can be used for a plug and play setup (no wiring)<br><br>
:ok: <a href=https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/hw-reference/esp32s3/user-guide-devkitc-1.html>ESP32-S3-DevKitC-1</a>.<br><br>

## Uploading to board

The installation is simple! You just use the Arduino IDE to flash the sketch/firmware to the ESP32 board.<br>
Next you connect to the WiFi access point with a pc/laptop, <b>GameMod_PS4_WiFi</b> is the default SSID and <b>123456789</b> is the default password.<br>
Then use a web browser and go to http://10.1.1.1/admin.html <b>10.1.1.1</b> is the default webserver IP or http://ps4.local<br>
On the side menu of the admin page select <b>File Uploader</b>, then click <b>Select Files</b> and locate the <b>data</b> folder inside the <b>GameMod_ESP32-S2-S3_PS4_Server_900u</b> folder. Next select all files and click <b>Upload Files</b>.
The you can go to <b>Config Editor</b> and change the password for the WiFi AP.
Alternatively, if you install this <a href=https://github.com/stooged/arduino-esp32fs-plugin>plugin</a> to your Arduino IDE you can upload the files to the board storage with it by selecting <b>Tools > ESP32 Sketch Data Upload</b>.
<img src=https://github.com/stooged/ESP32-Server-900u/blob/main/Images/dataup.jpg><br><br>
The files uploaded using this method are found in the <b>data</b> folder inside the <b>GameMod_ESP32-S2-S3_PS4_Server_900u</b> folder.<br><br>
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

<br><br>

## Cases

Stooged has created some basic printable cases for the following boards.<br>
These cases can be printed in PLA without supports.

### ESP32-S2 Boards

<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/Adafruit_QT_Py>Adafruit QT Py</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/UM_FeatherS2>UM FeatherS2</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/UM_TinyS2>UM TinyS2</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/Wemos_S2_Mini>Wemos S2 Mini</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/DevKitM_1>DevKitM-1</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/ESP32_S2_Saola_1>ESP32-S2-Saola-1</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/LILYGO_TTGO_T8_TF_Card_Slot>LILYGO-TTGO-T8-TF-Card-Slot</a><br>
<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/LILYGO_TTGO_T8_WOOR>LILYGO-TTGO-T8-WOOR</a><br>



### ESP32-S3 Boards

<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/S3_DevKitC_1>S3_DevKitC_1</a><br>


### ESP32 Boards

<a href=https://github.com/stooged/ESP32-Server-900u/tree/main/3D_Printed_Cases/NodeMCU_32>NodeMCU-32</a><br>

<br>

If you wish to edit the cases you can import the `.stl` files into <a href=https://www.tinkercad.com/>Tinkercad<a/> and edit them to suit your needs.

<br>

