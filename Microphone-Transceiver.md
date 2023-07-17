Checking Portapack-Havoc repository , we can see , that this excellent app was initially developped by Furrtek in 2017.
* "**Microphone FM transmit with CTCSS**",   providing support to Narrow Band FM Transmitter + CTCSS  & Receiver in Half Duplex operation, like a walkie-talkie (two-way directional voice communication but one at a time). 

Later on , thanks to many other great sw developpers , gradually it has been added many more nice functionalities (VOX control, Roger Beep,...) ,and improving it day by day ... 
And from Sept -2020, it was also added the support of multi  analogue mic  Modulation types in half duplex TX / RX, highly appreciated specially by all ham amateur radio community.  Those mod types are widely used in LF, HF , VHF, 2m band ,  maritime communications ,airport airband communications,  UHF PMR446,... 
And since them we are currently supporting those following ones  (valid from , [Nightly Release - 2022-10-17](https://github.com/eried/portapack-mayhem/releases/tag/nightly-tag-2022-10-17) onwards) :
 
* Narrow and normal band FM (NBFM/FM), 
* Wide band FM (WBFM), 
* Double side band AM  with carrier,(DSB-C,AM), 
* Upper Side Band (USB),
* Low Side Band (LSB)
* Double Side Band with suppressed carrier (DSB-SC). 


## # Key Controls
* **VU-meter:** Just launching that Mic App, the left side  peak audio  VU-meter is active, and you can plug your head mic set and confirm its sensitivity and correct operation.
The sensitivity of the microphone is shown on the lefthand side of the LCD screen,  and should be configured so the range is green for most of the audio and never hits red to limit over deviation of the signal.
Note, this feature is not working once we activate below "Rx audio listen" ; but in any case, when pressing PTT, in TX mode, it always works.

* ![image](https://user-images.githubusercontent.com/86470699/196791487-ac26671d-5e84-4374-8eef-5027f475ecdb.png)
![image](https://user-images.githubusercontent.com/86470699/196540348-cbee30a7-b4fb-4ba5-8242-b65fec585a9e.png)
![image](https://user-images.githubusercontent.com/86470699/196541644-3fd9d7bd-7dfa-49c4-af0c-7be9ce7547d6.png)

![IMG_4376](https://github.com/eried/portapack-mayhem/assets/86470699/7cd3ac45-d43d-454e-9ff0-4369414881cf)


* **MIC. GAIN:** Cursor selection and use rotary encoder is used to select a fixed gain of x0.5, x1.0, x1.5, x2.0. The setting needs to be selected based, on the Microphone used which is connected via the Headset/ Microphone socket (standard smartphone 4 segment 3.5mm connector). 



That mic gain  adjustment is in fact a post scaling by above factors (x0.5, x1.0, x1.5, x2.0) , of each captured mic voice data . Then ,that adjustment should be only used,to make mic gain fine tuning of the non distorted voice . But  if the captured data is already distorted ,  due to too much mic sensitivity , or to close mic-mouth distance, or too loud voice ,   the ADC  saturation , should be addressed by other means (ALC or Boost adjustment (*1) , or increasing mic-mounth cms distance , or reducing the voice loudness.)  

If you want to know the audio codec IC of your Portapack board, you do not need to dissassembly the boards, just go to the  "debug" -> peripherals menu , and you will see which peripheral device, you can explore, looking its register map values. In the audio block icon , you will see the audio codec IC name , mounted on your Portapack board : AK4951 or WM8731. (see annexed photo of both two devices)

* ![image](https://user-images.githubusercontent.com/86470699/196536085-5e024d25-74c9-4415-948b-64ca311183c8.png)
   ![image](https://user-images.githubusercontent.com/86470699/196536894-df0c02c9-8c0e-40f1-8ca3-ec31e0c99618.png)





**Automatic mic Level Control "ALC" (AK4951 sound codec IC)  or "Boost" pre-amplifier mic control adjustment (WM8731 audio codec IC) :**     (*1) 

To minimize that mic ADC saturation (and consequently, audio distortion , and  spectrum harmonics radiation), we introduced ALC(AK4951)  and Boost(WM8731) control options.  
* ![image](https://user-images.githubusercontent.com/86470699/196547451-91bc4b30-ae66-4506-b8a8-490d280f79da.png)
![image](https://user-images.githubusercontent.com/86470699/196548467-50852c3b-e4e5-47c4-b047-6efb7b0d6dea.png)


With proper adjustment , we can solve that mic ADC saturation, and adapt correctly to our  mic gain sensitivity , and the distance mic-mouth from the speaker , and the user voice loudness ... That proper settings , can be done, selecting the best ALC or Boost option (checking that the mic voice sound Vumeter (left mic volume peak bar indication)  is below 80-90%, in the green area, see annexed pictures )
(example LSB with low modulation index)



1.  * **ALC Automatic mic volume Level Control** (available in Portapack boards that uses AK4951 audio codec platform) : 
With those "ALC" GUI options, user can adjust from +12 dB's to -12 dB's mic gain.
For instance , if we want ,to talk , like handsfree mode , and pick up all the voices and sounds inside our room (from 50 cms till several meters distance from the mic, we can select +12 dB’s ) ,
If we want to talk around 15 to 20 cms , we can select +0dB’s or -3dB’s depending on the loudness of our voice …
If we want to avoid saturation when shouting , or talking touching the mic with the lips , you can reduce it til -9, -12 dB’s
If you leave the default OFF settings , you will have exactly same Mic settings as in previous Mayhem FW versions <=1.4.3 , without activating any digital ALC block of in the AK4951.
When we saiy , “OFF - 12Khz” it just means that the audio base band output from the IC 4951 has this initial max bandwith, but obviously ,later , when it is post-processed and used for modulation , it is also reduced it.
We tried to use and combine several nice programmable digital features, like , ALC , Wind Nose Filter, LPF , and boosting peaking Equalizer, and also Pre-amp mic level.
Ex. +12dB-6Khz , means activated ALC with maximum gain of 12dB’s and with digital Low Pass Filter of 6kHz .

* ![image](https://user-images.githubusercontent.com/86470699/196533221-4236b929-0635-497b-a2a4-bce3304f083b.png)
![image](https://user-images.githubusercontent.com/86470699/196291161-b456a257-587d-42fc-8457-ee180c82ac83.png)




 

 

2.  * **Boost mic** (in Portapack boards that uses WM8731 audio codec platform) :
 
With those "Boost· GUI options, user can adjust from +12 dB's to -08 dB's mic gain.
We have added five user "**Boost**" options , activating on/off , the  mic-boost pre-amplifier (+20 dB's) and playing with internal captured data, to allow smaller steps. In order to avoid mic distortion,  We only  recommend to use the pre-amplifier boost on , when we are using low sensitivity mics or when we are keeping  some distance (example >15 cms) to the mic  :
 
* ![image](https://user-images.githubusercontent.com/86470699/196534083-4bdb19f8-4c8c-40e8-a587-d328b2d8c8c4.png)
![image](https://user-images.githubusercontent.com/86470699/196281105-12c56760-a1d9-4fe2-a775-6fefcc5fccbc.png)

From [Nightly Release - 2023-04-05] onwards it has been added a new check box (next to Roger beep)  to the user to be able to select Separated (default) ) / Common freq. RX tuning control respect TX freq. (see attached new updated GUI pictures): 

![IMG_4379](https://github.com/eried/portapack-mayhem/assets/86470699/8796a489-36e0-46b3-8eaa-027a9738229d)

![IMG_4377](https://github.com/eried/portapack-mayhem/assets/86470699/1029d2c6-f998-4dbc-ad60-69d00b3408b7)



* **F:**  This field set the TX Frequency for the transmitter .	
* **F_RX:**  This field set the RX Frequency for the receiver.

* **FM TXBW:** This field sets the FM Band Width of the transmission under normal conditions from 0-150 kHz. (In fact, it is the +/- FM deviation in Khz.)

* **GAIN:** Is set for TX LNA(IF) and (0-47) 

* **AMP:** RF TX amplifier , 0dB or 14dB.

* **MOD:**  to set the selected  analogue TX & RX  modulation type :  NFM-FM // WFM // AM // USB // LSB // DSB 

> * Narrow band FM (NFM-FM) TX ,and supporting NFM-FM RX : BW: 8K5 (8K50F3E) , 11Khz (11K0F3E) ,and FM RX BW :16Khz (16K0F3E)

> * Wide band FM (WBFM) TX ,  and  supporting WFM RX of the following BW: 200kHz (Emissions Designator 200KF3E), 180khz and 40khz (see more details below)

> * Amplitude Modulation (AM) TX fixed to the standard  AM-6K00A3E, but supporting AM RX with two selectable receiver bandwidth filters, BW : 9 and 6kHz (covering both side lateral bands, AM DSB with carrier  AM-9K00A3E / AM-6K00A3E) 
>  
> * Upper Side Band (USB) TX , supporting USB RX with BW : 3kHZ (SSB-3K00J3E)

> * Lower Side Band (LSB) TX, supporting LSB RX with BW : 3kHZ (SSB-3K00J3E)

> * Double Side Band with suppressed carrier (DSB), supporting DSB RX with BW : 6 kHZ (covering both side lateral bands)  

* **TX Activation:**    Field can be selected for one of three settings. Off, PTT, AUTO. In the PTT setting, the PortaPack will transmit when the TX button and the bottom of the App screen is pressed on the touch screen. The AUTO is also known as a VOX control (automatic PTT transmission activated by voice). In AUTO the Receiver section below ("Rx audio listening")  is not available , but the triggering is set by the following 3 settings.

> * **LVL:**  The level that triggers the transmission is set by the audio level going over the threshold value set (0-255). This can be seen as a grey dash marked next to the vu-meter and shows its current setting compared to the microphone level.

> * **ATT:** This is the attack time of the microphone audio level must be above the set threshold to start transmitting (0 to 999mS). Higher attack helps avoid false triggers but might cut off the first words you say.

> * **DEC:** This is the decay time of the microphone audio signal falls below the threshold level be for the transmission is stopped (0 to 9999mS). Lower decay avoids silence at the end of the message but might cut you off in the middle of a sentence. Adjust levels depending on your speaking habits.

* **TONE KEY (CTCSS) :** Continuous Tone-Coded Squelch System or CTCSS is one type of in-band signaling that is used to reduce the annoyance of listening to other users on a shared two-way radio communication channel, sometimes referred to as tone squelch.

* Note1 the level of the Tone % compared to the Microphone setting is set in Options >Audio.

* Note2, that feature is only available in both FM modes (NFM-FM / WFM).

* **Check box Roger beep:**  This tick is activating an ending sequence of six consecutive digital synthesized audio tones , to indicate that the operator has concluded speaking. 
* Note: that feature is not available in SSB modes (USB , LSB)

* **Check box F = F_RX:**  (Added from [Nightly Release - 2023-04-05] It allows to the user to select Separated / Common  tuning frequency from Receiver(RX) to the Transmitter(TX).
Once is marked , we have a common same frequency (F = F_TX) and therefore, to not confuse to the user , we hide the bottom independent F_RX field . (as you could see in the two above GUI pictures) 
 

* **Check box RX audio listening:** The Tick box to select this item is difficult to select with cursor having to go down and up though item, and with some luck you may enable the box. It is better to select from the touch screen. If this is enabled then it will turn on the Audio Receiver and with the following setting will allow you to listen to a receive channel when not transmitting. The TX-RX timing gap is not known. The frequency can be set separately or Common  to that of the transmitter section above. The following setting can be applied to the receiver.

* Note : this feature is not available when we are in AUTO VOX control .

* **VOL :** Audio receiver volume control.

* **RX BW:** This GUI option , allows several analogue demodulation options :

> in NFM-FM mode to set up the receiver Bandwidth setting. It can be set to either 

> * 8k5kHz- NFM (delta FM deviation +/- 1,25 khz, FM index modulation:0,4) 
> * 11Khz - NFM (delta FM deviation +/- 2,50 khz, FM index modulation:0,75)
> * 16kHz -  FM (delta FM deviation +/- 5,0  khz,  FM index modulation:1,6)

> In WFM mode 
> * 200Khz FM bandwidth , for commercial FM stations with soft band pass  transition.  And recently also added the bandwiths BW: 180khz and 40khz (that last one, mainly for NOAA analog FM APT - 137 Mhz reception), both  with sharp stop band transition.

> In AM 
> * DSB1 -9Khz, DSB2-6Khz bandwidth. 

> In USB , upper +3khz single side band.

> In LSB , lower -3khz single side band.

> In DSB-SC , we can select to demodulate any of both SSB bands (LSB, USB). In DSB-SC mod type , both side bands has exactly the same modulated content, but sometimes we may have more particular interference signals in one side than the other.  

* **F:** The RX frequency can be set in the usual way with text pad when selected

* **SQ:**  This can be set between 0 and 99 typically 50 is threshold.

* **GAIN:** The RX gain setting of LNA(IF) (0-40) 

* **VGA:** RX (Baseband)(0-62) 

* **AMP:** RX LNA pre-amplifer  0=0dB or 1=14dB.

Note this application while performing a transmit function  may well over deviate and generate unwanted harmonics.
