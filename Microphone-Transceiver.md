Originally the Microphone App was created providing only support to Narrow Band FM Transmitter & Receiver in Half Duplex operation, 
like a walkie-talkie (two-way directional voice communication but one at a time). 

But thanks to many great contributors , currently we are supporting multi voice analogue Modulation types in half duplex TX / RX : 
* Narrow band FM (NBFM), 
* Wide band FM (WBFM), 
* Amplitude Modulation (AM), 
* Upper Side Band (USB),
* Low Side Band (LSB)
* Double Side Band with suppressed carrier (DSB). 


## # Key Controls

* **MIC. GAIN:** Cursor selection and use rotary encoder is used to select a fixed gain of x0.5, x1.0, x1.5, x2.0. The setting needs to be selected based, on the Microphone used which is connected via the Headset/ Microphone socket (standard smartphone 4 segment 3.5mm connector). The sensitivity of the microphone is shown on the lefthand side and should be configured so the range is green for most of the audio and never hits red to limit over deviation of the signal. That mic gain  adjustment is in fact a post scaling by above factors (x0.5, x1.0, x1.5, x2.0) , of each captured mic voice data . Then ,that adjustment should be only used,to make mic gain fine tuning of the non distorted voice . But  if the captured data is already distorted ,  due to too much mic sensitivity , or to close mic-mouth distance, or too loud voice ,   the ADC  saturation , should be addressed by other means (ALC or Boost adjustment (*1) , or increasing mic-mounth cms distance , or reducing the voice loudness.)  

**Automatic mic Level Control (ALC) or Boost mic adjustment  :**     (*1) 

To avoid mic ADC saturation (and consequently harmonic radiation), and adapt better to your needs , depending on the mic type sensitivity , and the distance mic-mouth from the speaker , and the user voice loudness ... we should set up the best ALC or Boost option (checking that he mic sound Vumeter < 80 - 90% )

1.  * **ALC Automatic mic volume Level Control** (available in Portapack boards that uses AK4951 audio codec platform) : 
With those "ALC" GUI options, user can adjust from +12 dB's to -12 dB's mic gain.
For instance , if we want ,to talk , like handsfree mode , and pick up all the voices and sounds inside our room (from 50 cms till several meters distance from the mic, we can select +12 dB’s ) ,
If we want to talk around 15 to 20 cms , we can select +0dB’s or -3dB’s depending on the loudness of our voice …
If we want to avoid saturation when shouting , or talking touching the mic with the lips , you can reduce it til -9, -12 dB’s
If you leave the default OFF settings , you will have exactly same Mic settings as in previous Mayhem FW versions <=1.4.3 , without activating any digital ALC block of in the AK4951.
When we saiy , “OFF - 12Khz” it just means that the audio base band output from the IC 4951 has this initial max bandwith, but obviously ,later , when it is post-processed and used for modulation , it is also reduced it.
We tried to use and combine several nice programmable digital features, like , ALC , Wind Nose Filter, LPF , and boosting peaking Equalizer, and also Pre-amp mic level.
Ex. +12dB-6Khz , means activated ALC with maximum gain of 12dB’s and with digital Low Pass Filter of 6kHz .

* ![image](https://user-images.githubusercontent.com/86470699/196059046-c706dc55-53da-4a47-9fb1-15b89d070319.png)
![image](https://user-images.githubusercontent.com/86470699/196286799-2ae86434-6e69-494c-9ec8-146acea72065.png)



 

 

2.  * **Boost mic** (in Portapack boards that uses WM8731 audio codec platform) : 
With those "Boost· GUI options, user can adjust from +12 dB's to -08 dB's mic gain. 
  we added five user "**Boost**" options , activating on/off , the  mic-boost pre-amplifier (+20 dB's) and playing with internal captured data, to allow smaller steps :
 
* ![image](https://user-images.githubusercontent.com/86470699/196058857-0d4f2695-fde1-40eb-aa6e-9d6d5b9110e1.png)
![image](https://user-images.githubusercontent.com/86470699/196281105-12c56760-a1d9-4fe2-a775-6fefcc5fccbc.png)



* **F:**  This field set the Frequency for the transmission.	

* **FM TXBW:** This field sets the FM Band Width of the transmission under normal conditions from 0-150 kHz. (In fact, it is the +/- FM deviation in Khz .

* **GAIN:** Is set for LNA(IF) and (0-47) and AMP 0dB or 14dB.Node mode is set to FM only.

* **TX Activation:**    Field can be selected for one of three settings. Off, PTT, AUTO. In the PTT setting, the PortaPack will transmit when the TX button and the bottom of the App screen is pressed on the touch screen.  In AUTO the Receiver section below is not active, but the triggering is set by the following 3 settings.

* **LVL:**  The level that triggers the transmission is set by the audio level going over the threshold value set (0-255). This can be seen as a grey dash marked next to the vu-meter and shows its current setting compared to the microphone level.

* **ATT:** This is the attack time of the microphone audio level must be above the set threshold to start transmitting (0 to 999mS). Higher attack helps avoid false triggers but might cut off the first words you say.

* **DEC:** This is the decay time of the microphone audio signal falls below the threshold level be for the transmission is stopped (0 to 9999mS). Lower decay avoids silence at the end of the message but might cut you off in the middle of a sentence. Adjust levels depending on your speaking habits.

* **TONE KEY:** The Tick box next to “Roger Beep” can be selected with effort with cursor or better to select with touch screen. This will add a roger bleep if enabled. Note the level of the Tone % compared to the Microphone setting is set in Options >Audio.

RX audio listening: The Tick box to select this item is difficult to select with cursor having to go down and up though item, and with some luck you may enable the box. It is better to select from the touch screen. If this is enabled then it will turn on the Audio Receiver and with the following setting will allow you to listen to a receive channel when not transmitting. The TX-RX timing gap is not known. The frequency can be set separately to that of the transmitter section above. The following setting can be applied to the receiver.

* **FM RX BW:** The is the narrow band FM Receiver Bandwidth setting. It can be set to either 8k5kHz,11Khz or 16kHz.

* **F:** The frequency can be set in the usual way with text pad when selected

* **SQ:**  This can be set between 0 and 99 typically 50 is threshold.

* **GAIN:** The gain setting of LNA(IF) (0-40) VGA(Baseband)(0-62) and AMP 0=0db or 1=14dB.

Note this application while performing a transmit function  may well over deviate and generate unwanted harmonics.
