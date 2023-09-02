Capture App is designed to capture I/Q data to a file on the SD card. Captured data is stored as pairs of 16-bit signed values in a .C16 file (complex 16 bit), or optionally 8-bit signed values in a .C8 file (complex 8 bit). C16 values are stored in little-endian format. The Metadata (“Center frequency” and Bandwidth) is stored in a .TXT file with the same name.In GRC, the "file source" and "ishort to complex" blocks can be used to process the data.

The Sampling rate used may not be supported by some MicroSD cards, it is best to use high speed class SD cards. The HackRF PortaPack Capture/Replay functionality is  based on Havoc firmware version.

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Frequency:** The setting of the frequency using the keypad can be completed and is stored in persistant memory so can be returned to when the App is used again.
* **Step Size:** The selected step size of frequency adjustment carried out by the Rotary encoder. 
* **Gain:**  Amp  (0dB or 14dB), LNA(IF) (0-40),VGA(Baseband)(0-62)
* **Rate:** The sample rate, which by its nature set the set bandwidth of capture. This is shown in the markers around the centre line of the waterfall display. The sample rate is variable from 12k5 to 2750K (*)  in many steps. You need to ensure that the sample rate is more than twice the bandwidth of the signal  you want to capture see [(Nyquist Principle / also called Shannon’s Law)  ](https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem)
* **Format:** The user can select two file formats, of the recorded IQ data 16 / 8 bits :  C16 (complex 16)  or C8 (complex 8), and its related file extension ".C16" or "C8".   (By default we are preselecting C16).

Note (*)  : Currently , **for correct reliable Replay application ,you should ONLY use Capture App selecting any Bandwith capture <= 1Mhz  (but 500Khz is the recommended for majority micro SD cards compatibility because it requieres a quite common average write speed in our system >2MB/sec,C16)**. From 600khz till 1Mhz (and 1.25 MHz) , you will need more fast and good quality micro sd card (with min average write speed in our system >3MB/sec (for BW=750khz,C16)  , and >4MB/sec (for BW=1Mhz ,C16), (>5MB/sec for BW=1.25Mhz ,C16) and with as small as possible write random latency. (In the GUI , those correct bandwidth capture options appear with the Normal usual "REC" icon Background colour, as user recomended BW capture options). If you face too much % dropped samples when recording , you can retry it reducing C16 to C8 , that also reduces the needed average write speed :2 (example 1Mhz rec will need average sd interface speed of 4MB/sec in C16 or 2MB/sec in C8).

Recently, thanks to x4 Oversampling and /4 Decimation introduction , we have also added 1.25Mhz BW REC , but it is in the limit of our hardware System and it starts to have some M4 sample drops. (It is still experimental). 

Above 1.25Mhz till 5.5Mhz bandwith options (with YELLOW REC button background Icon), in current fw version , the recorded files have periodical sample drops  , and therefore it can  not record all full original samples content and therefore it is NOT useful for the Replay App , just useful to check the spectrum image, example using the linux tool "inspectrum" or "Audacity") . Anyway when replaying those captured files , the replay time will be shorter than real . but normally you should still get a correct  modulation, but in case of voice contents, it would sound , unnatural , "like with accelerated playing speed" , because in fact,due to Hackrf One System (HW+SW) limitations, those  recorded files (under those high speed BW with YELLOW icon) have decimated its  content - when recorded there were skipped some real time samples. 

![image](https://user-images.githubusercontent.com/86470699/162581344-446a1a0b-325e-4bb6-a451-f47ecc91d8e3.png)




* **Record Button:** The red button shows as Rec or Stop. If record is selected then it will record the I/Q file. To the side of the Record Button is additional information that is shown for the recording file, % of Dropped Samples, total Recording Time Remaining. (As we mentioned above, for correct Replay operatons, please make sure to select a proper Capture bandwith option  , with normal black background "REC" icon , not the yellow one.)

![image](https://github.com/eried/portapack-mayhem/assets/86470699/f92f0133-5a9b-48ba-8980-024c343d6f21)

  
     * File Name (as above example , BBD_0109.C16, based on the selected format C16)
     * % of Dropped Samples (recording error rate, due to SD card write latency, above sample 0%)
     * Total Recording Time Remaining (based on available SD card capacity , above example 0h: 13min: 42 secs)

From nightly 23-08-19 onwards, we revised and  extended a good functionality of  all low bit rate bandwith REC options 
If you adjust correctly the GAIN and LNA  and center freq. it is possible to capture good bit streams in C16 / C8 format , 
Pls. find attached some screenshot examples , capturing the same tuned AM MF band broadcasting with a BW aprox of 16Khz , using an upconverter ,

![image](https://github.com/eried/portapack-mayhem/assets/86470699/3c9c851f-a311-4411-a2a3-09920ce34797)
![image](https://github.com/eried/portapack-mayhem/assets/86470699/d4aa10f5-1155-4924-a35b-c44dd12dc8bc)

Depending on the tuned frequency, (mainly visible in 25k, 32k, 50k and 75k)  we may got a random strange left picture effect -on the screen, it seems not affecting to the recorded files.C16 or .C8 -   with “vertical stripes” , this can be easily corrected, just readjusting the center frequency  some Hz up or down ,  till trying to have full convergence of these vertical red carriers to the central unique one , with +-10Hz steps.

![IMG_4636](https://github.com/eried/portapack-mayhem/assets/86470699/d11b4380-7654-4812-a431-790d14ff6fad)


Please check the video below for HackRF PortaPack Capture/Replay functionality.

  [![HackRF PortaPack Capture/Replay functionality](http://img.youtube.com/vi/Pe30Jvyhmzk/0.jpg)](http://www.youtube.com/watch?v=Pe30Jvyhmzk "HackRF PortaPack Capture/Replay functionality")