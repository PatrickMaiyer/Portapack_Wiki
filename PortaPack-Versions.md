**Portapack Versions**

There are many different versions of PortaPack, mainly due to Chinese’s Companies putting their own take of the design such as adding a larger screen, adding charging or changing the main chip due to price and availability. The current list is:

![image](https://user-images.githubusercontent.com/32274981/163668369-81ec10b5-a7a2-4fa0-bc46-09764819bccf.png)
 
## H1(R1/R2)
![image](https://user-images.githubusercontent.com/4393979/162888735-083d4fb5-dfd5-499c-94b1-c0fbbec0fda2.png)
![image](https://user-images.githubusercontent.com/4393979/162888869-cc9a45ed-170f-435c-a3c1-43076d0035b2.png)

### Differences:
* The H1R1 has a WM8731 audio chip
* The H1R2 has a AK4951 audio chip
* Some versions have a touch screen while a lot of the clones do not

## H2
![image](https://user-images.githubusercontent.com/4393979/162888315-85e7c7da-8bcd-4578-9195-93dd96118560.png)
![image](https://user-images.githubusercontent.com/4393979/162888233-c773743c-3231-4b06-b2f1-a5bb9988c66e.png)


### Differences:
* Bigger touch screen
* Different control/button layout
* Built in battery

## H2+R1

![image](https://user-images.githubusercontent.com/4393979/162888499-4d780cd0-2ddd-47f0-b465-2c29238af6ad.png)

### Differences:
* Similar to  H2 in early versions except claim for better TXCO spec(quesionable) and board marked as H2+.
* Battery state indicator with 4 leds under Encoder Knob for 25%,50%,75%,100%,flashing while charging, steady when that level full. 

## H2+R2

![H2+ R2](https://user-images.githubusercontent.com/32274981/163668781-3f9beec7-b670-43dd-aa97-b01a63343157.JPG)


### Differences:
* Similar to  H2+R1 except using the WM8731 Codec and  has an added audio power amp INS8002E. The front face of the board is marked as H2+ as in H2+R1 above.
* Battery state indicator with 4 leds under Encoder Knob for 25%,50%,75%,100%,flashing while charging, steady when that level full. 

## H2+R3

![H2+R3](https://user-images.githubusercontent.com/32274981/163668864-cfddc191-cdf5-418c-b8fd-7d7b16937c02.jpg)


### Differences
* Similar to  H2+R2 except
* This versions the standard CPLD 5M40ZE64CN5 was  replaced with EPM240T100C5N ( due to cost and supply issues by supplier "OpenSourceSDR Lab") which has caused some issues ( they issues their work around fixes in a version 1.4.3)  and resolved in version 1.5.x due to a lot of hard work.


## H3
Bespoke software and not compatible with mayhem software

![image](https://user-images.githubusercontent.com/4393979/162887707-27f173f3-6aa7-42cf-bd89-e0447bc0fdd5.png)

### Differences:
* Designed by Jamesshao8, contributor of Analog TV receiving, BTLE receiving, NRF receiving, GPS Sim transmitting
* Special Firmware supporting SSTV and NOAA receiving
* Built in microphone
* Built in GPS receiver
* Built in battery and level indicator
* Built in barometer
* Built in compass
* 2.4" Touch screen
* Same control/button as H1 to guarantee minimum thickness