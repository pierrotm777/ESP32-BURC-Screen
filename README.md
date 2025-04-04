# ESP32-BURC-Screen
This touch screen allows you to control systems compatibles with the protocol [RCUL](https://p-loussouarn-free-fr.translate.goog/arduino/exemple/RCUL/RCUL.html?_x_tr_sch=http&_x_tr_sl=auto&_x_tr_tl=en&_x_tr_hl=en) (Universal RC Box System).  
![](https://github.com/pierrotm777/ESP32-BURC-Screen/blob/main/RCUL.jpg)  

## Credits
The program managing this screen was entirely created by croby-b.  
Thanks to him :-)  

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
It's based on an LVGL compatible touchscreen, managed by an ESP32-S3.  
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