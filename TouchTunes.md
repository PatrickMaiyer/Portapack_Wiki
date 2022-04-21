# About

TouchTunes is a popular Jukebox company that can be found in various bars, pubs, and restaurants all over North America.  

TouchTunes Jukebox’s (Gen2 and above) use a wireless remote that transmits NEC encoded messages using ASK/OOK at 433.92MHz. These remotes are used for basic Jukebox functions such as On/Off, Skip Song, Volume, Etc. The wireless messages are addressed using PINs 000-255 to prevent mutable units from interfering with each other. 

**Most of the time the remote’s PIN is left as default 000**

This application emulates TouchTunes wireless remotes (Gen2 and newer) and has the ability to brute force addresses.

Original research can be found [HERE](https://github.com/notpike/The-Fonz) and on NotPike's [blog](https://bad-radio.solutions/notes).

# How To Use

* **Start the application:** Go to Transmit→TouchTune.

[[img/screenshots/Transmit_TouchTune.png]]

* **Transmit a command:** Simply press the button on the touch screen or highlight/select the button with the physical controls.

* **Change the PIN:** Highlight the 3 digits in the top left hand corner and use the jog wheel to change the value. (Default is 000)

* **Brute force a command:** Select the “Scan” option (green check mark) then transmit. This option will transmit the command 256 times starting with PIN 000 to 255. (PIN will change to 255 after all commands are transmitted)

* **EW Mode (Experimental):** EW (Electronic Warfare) Mode will prevent others from sending commands to your target jukebox while still allowing you to have control. When the "EW Mode" is selected (green check mark), a continuous CW at 433.92MHz will be transmitted in an attempt to jam the jukebox's receiver. You can still transmit commands while "EW Mode" is active. The jamming signal will automatically turn off / turn on when you transmit commands.  

# TouchTunes Message Structure

Below is all the technical data regarding the wireless message structure.

### Basic Info

* **Frequency:** 433.92MHz
* **Modulation:** ASK/OOK
* **Protocol:** NEC
* **Symbol Rate:** 1766
* **Symbol Period:** 566us

### NEC Format

* **Short(0):** 10 (OOK: ON OFF)
* **Long (1):** 1000 (OOK: ON OFF OFF OFF)

### Message Structure

* **Structure:** {PREAMBLE} {SYNC} {PIN} {COMMAND} {TAIL}
* **Preamble (Literal Symbols):** 0xFFFF00
* **Sync (Decoded NEC):** 0x5D
* **PIN 000-255 (Decoded NEC):** 0x00-0xFF (LSB)
* **Tail (Literal Symbols):** 0x8

### Commands (Pre NEC Encode)

**Note:** Commands are doubled with the 2nd half being reversed. For example, Pause 0x32 will translate to 0x3223 before being encoded to the literal symbols 0xA88A8AA2A880.

* 0x32: Pause
* 0x78: On/Off
* 0x70: P1
* 0x60: P2 Edit Queue
* 0x20: F1 Restart
* 0xF2: Up
* 0xA0: F2 Key
* 0x84: Left           
* 0x44: OK             
* 0xC4: Right          
* 0x30: F3 Mic A Mute  
* 0x80: Down           
* 0xB0: F4 Mic B Mute  
* 0xF0: 1              
* 0x08: 2              
* 0x88: 3              
* 0x48: 4              
* 0xC8: 5              
* 0x28: 6              
* 0xA8: 7              
* 0x68: 8              
* 0xE8: 9              
* 0x18: * Music_Karaoke
* 0x98: 0              
* 0x58: # Lock_Queue   
* 0xD0: Zone 1 Vol+    
* 0x90: Zone 2 Vol+    
* 0xC0: Zone 3 Vol+    
* 0x50: Zone 1 Vol-    
* 0x10: Zone 2 Vol-    
* 0x40: Zone 3 Vol- 

### Example
* **Command:** Pin 000 - On/Off
* **Literal Symbols (HEX):** ffff00 a2888a2 aaaa 8888aa2aa2220 (PREAMBLE SYNC PIN COMMAND TAIL)
* **Literal Symbols (BIN):** 11111111111111110000 10 1000 10 1000 1000 1000 10 1000 10 10 10 10 10 10 10 10 10 1000 1000 1000 1000 10 10 10 1000 10 10 10 10 1000 1000 1000 100000