# ESP32-BURC-Screen
This touch screen allows you to control systems compatibles with the protocol [RCUL](https://p-loussouarn-free-fr.translate.goog/arduino/exemple/RCUL/RCUL.html?_x_tr_sch=http&_x_tr_sl=auto&_x_tr_tl=en&_x_tr_hl=en) (Universal RC Box System).  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/RCUL.jpg)  

## Credits
RCUL is a protocol created by [Rc-Navy](http://p.loussouarn.free.fr/).  
The Sotware managing this screen was entirely created by croby-b.  
Thanks to them :-)  

## Compatibles modules usable with BURC
This screen was developed specifically to control the [Teensy 4.0 based sound module](https://github.com/pierrotm777/SoundModule_Teensy4.0-version).  
It works like the BURC encoder you can find [here](https://github.com/pierrotm777/BURC_Encoder) but with many more functions.  

All the modules below are compatible with this screen:  
- [Ms8 v2](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/MutltiSwitch_Sw8_V2)  
- [Ms16](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/MultiSwitch_Sw16-ProMicro)  
- [Sound&SmokeModule](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/Sound%26SmokeModule)  
- [Xany2Msx](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/Xany2Msx/Firmware_Msx)  
- [Xany2Misc](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/Xany2Msx/Firmware_Misc)  
- Hall sensor:  
  * [Hall I2C sensor](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/Capteur_Hall_I2C)  
  * [Hall I2C sensor mini](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/Capteur_Hall_I2C_Mini)  
- [MultiSwitch_MosFet](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/MultiSwitch_MosFet)  
- [Ms8 Pulseq](https://github.com/Ingwie/OpenAVRc_Hw/tree/V3/PulseSeq) 
- [Servo 360°]()  

## Appearance
It's based on an LVGL compatible touchscreen 4.3" 800x480 pixels ([Model：DX80480043E-WB-A](https://viewedisplay.com/product/esp32-4-3-inch-800x480-rgb-ips-tft-display-touch-screen-arduino-lvgl/)), managed by an ESP32-S3.  
<table border="2">
<tr>
<td><img src="https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Screen_Top.png" border="0"/></td>
<td><img src="https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Screen_Bottom.png" border="0"/></td>
</tr>
</table>

## Schematic
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Screen_Shematic.png)  

## How to wire the screen
For use this screen, you need a compatible SBUS or PPM handset.  
The screen use the trainer feature for transmit its orders.  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Screen_Connections.png)  
Connections to do between the screen and your handset:  
- +5v just before the diode.  
- GND to J2-GND.  
- CPPM output or SBUS output to J2-17.  
- CPPM input or SBUS input to ESP32-S3 pin 18 (not use J2-18).  

## Your handset
Not all Handset/Receiver system are compatible. 
Your handset need to have a **trainer input as Master**.  
We have tried several RC systems:  
- All **Frsky** receivers X or D8 or D16.  
- **Flysky** FS-ia6B or FS-ia10B.  
- **Spektrum** AR6610T.  
- **Hitec** Optima 7.  

## Screen's features
Three types of screen are available:  
- screen with 8 buttons.  
- screen with 8 buttons + 1 slider. 
- screen with 16 buttons.  
- custom screen (3 types of buttons).  
- Teensy screen (used for command the [Teensy sound module](https://github.com/pierrotm777/SoundModule_Teensy4.0-version)).  
- 10 models.
- models and screen configurations are saved on a sd card (4GB by example).  

## How to configure the screen
- select the **parameters** button on top left.  
- select witch protocol you want to use, **CPPM_OUT** or **SBUS_OUT**.  
	CPPM:
	- select CPPM modulation, **NEG** or **POS**.  
	- select CPPM stubborn, always 300.  
	- select number of maximum channels, 8, 10, 12 or 16 (prefer 8).  
	- select RCUL channel (channel used for transmit RCUL/X-Any orders to the compatibles modules).  
	- select number of repeats 0 to 6.  

	SBUS:
	- select SBUS speed (NORMAL or QUICK).  
	- select number of repeats 0 to 6.  
	
- select witch type of screen.  
	SCREEN 1 type:
	- select MOM, PERM or MOM/PERM (MOM=TEMPORARY, PERM=PERMANENT, MOM/PERM=TEMPORARY and PERMANENT).  
	- select message type (C1_C8, C1-C8_ANA, C1_C16, TEENSY, **CUSTOM**).
	- this screen use the RCUL message on RCUL.VOIE(1) channel.  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Config_Screen1.png) 

	SCREEN 2 type:
	- select MOM, PERM or MOM/PERM (MOM=TEMPORARY, PERM=PERMANENT, MOM/PERM=TEMPORARY and PERMANENT).  
	- select message type (C1_C8, C1-C8_ANA, C1_C16, TEENSY).  
	- this screen use:
		- the RCUL2 message on RCUL2.VOIE channel.  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Config_Screen2.png) 
		- the RCUL3 message on RCUL3.VOIE channel (AXE X/Y).  
		- the RCUL4 message on RCUL4.VOIE channel (AXE X2/Y2).  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Config_Screen1.png) 
	- if TEENSY in use:  
		- the RCUL5 message use RCUL5.VOIE channel:  
		for *On/Off* commands, motor, fog, anchor, ambient and smoke.  
		for *slider* command, volume.  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Screen_TEENSY.png) 

	SCREEN CUSTOM type:
	- select type for each button (BUTTON, TOGGLE, SWITCH). 
	- select slider or not.  
	- this screen use the RCUL1 message on RCUL6.VOIE channel.  
	**Only usable with the SCREEN 1**.  
	
## Upload firmware
Download the Espressif [Flash Dowload Tool](https://dl.espressif.com/public/flash_download_tool.zip).  
- Open the flash_download_tool_3.9.8_w1.exe.  
- Donwload the firmware [here](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Firmware_ESP32S3_screen/BURC_ESP32TS_CROKY_B_Version1_4_5.zip)  
- Select *ESP32S3* and *UART*.  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Firmware_ESP32S3_screen/ESP32-UART.png)  
- Select the four files, bootloader, partitions, boot_app, ino.bin.
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Firmware_ESP32S3_screen/Upload_ESP32_Firmware.png)  
- Select com port and 921600 bauds and click on START button.  
- Shutdown screen and restart it again.  

## Case for this screen
You will find a case build by croby-b [here](https://github.com/pierrotm777/ESP32-BURC-Screen).  

# ESPNOW (Wifi) feature
With the version 1.8, it's now possible to read some information from the sound module Teensy over a wifi connection.  
This feature use a little [ESP32C3 LCD board](https://www.google.com/search?client=firefox-b-d&q=ESP32C3+LCD).  
This board must be connected:
  - behind Teensy on pins ![+3,3v, GND and PIN 28](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/Teensy_Serial7.png).  
  - behind the ESP32 C3 on pins ![+3,3v, GND and PIN RX](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/ESP32C3.png). I 

## Firmware ESPNOW feature
Use the same methode for the ESP32 screen.
  - Select *ESP32C3* and *UART*.  
  - Use firmware files [here](https://github.com/pierrotm777/ESP32-BURC-Screen/tree/main/Firmware_ESP32C3_interface).  
