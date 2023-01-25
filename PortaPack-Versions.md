**Portapack Versions**

There are many different versions of PortaPack, mainly due to Chinese’s Companies putting their own take of the design such as adding a larger screen, adding charging or changing the main chip due to price and availability. The current list is:

 Version|Compatible|Screen size|  AK4951 Codec|  WM8731 SSOP Codec|  WM8731L QFN Codec|  CPLD|  INS8002E Audio amp|  LTK8002D Audio amp|
|-------|---|-------------|------|------|------|------|------|------|
|[H1 R1](#h1r1r2)|:+1:|2.4"||:heavy_check_mark:||QFP64|||
|[H1 R2](#h1r1r2)|:+1:|2.4"|:heavy_check_mark:|||QFP64|||
|[H2](#h2)|:+1:|3.2"|:heavy_check_mark:|||QFP64|||
|[H2 (maxgeek)](#maxgeek-h2)|:-1:|3.2"||||QFP64|||
|[H2 R1](#h2r1)|:+1:|3.2"|:heavy_check_mark:|||QFP64|||
|[H2 R2](#h2r2)|:+1:|3.2"||:heavy_check_mark:||QFP64|||
|[H2 R3](#h2r3)|:+1:|3.2"||:heavy_check_mark:||QFP100|:heavy_check_mark:||
|[H2 R4](#h2r4)|:+1:|3.2"|||:heavy_check_mark:|QFP100||:heavy_check_mark:|
|[H3/H2 Plus](#h3)|:shit:|3.2"|:heavy_check_mark:|||QFP64|||

_(Note: The H3 is Incompatible, do not buy it as it's a scam)_
 
## H1(R1/R2)
<img src="https://user-images.githubusercontent.com/4393979/162888735-083d4fb5-dfd5-499c-94b1-c0fbbec0fda2.png" height="300">
<img src="https://user-images.githubusercontent.com/4393979/162888869-cc9a45ed-170f-435c-a3c1-43076d0035b2.png" height="300">

### Differences:
* The H1R1 has a WM8731 audio chip
* The H1R2 has a AK4951 audio chip
* Some versions have a touch screen while a lot of the clones do not

## H2
<img src="https://user-images.githubusercontent.com/4393979/162888315-85e7c7da-8bcd-4578-9195-93dd96118560.png" height="300">
<img src="https://user-images.githubusercontent.com/4393979/162888233-c773743c-3231-4b06-b2f1-a5bb9988c66e.png" height="300">


### Differences:
* Bigger touch screen
* Different control/button layout
* Built in battery

## H2+R1

<img src="https://user-images.githubusercontent.com/4393979/162888499-4d780cd0-2ddd-47f0-b465-2c29238af6ad.png" height="300">

### Differences:
* Similar to  H2 in early versions except claim for better TXCO spec(quesionable) and board marked as H2+.
* Battery state indicator with 4 leds under Encoder Knob for 25%,50%,75%,100%,flashing while charging, steady when that level full. 

## H2+R2

<img src="https://user-images.githubusercontent.com/32274981/163668781-3f9beec7-b670-43dd-aa97-b01a63343157.JPG" height="300">


### Differences:
* Similar to  H2+R1 except using the WM8731 Codec and  has an added audio power amp INS8002E. The front face of the board is marked as H2+ as in H2+R1 above.
* Battery state indicator with 4 leds under Encoder Knob for 25%,50%,75%,100%,flashing while charging, steady when that level full. 

## H2+R3

<img src="https://user-images.githubusercontent.com/32274981/163668864-cfddc191-cdf5-418c-b8fd-7d7b16937c02.jpg" height="300">


### Differences
* Similar to  H2+R2 except
* This versions the standard CPLD 5M40ZE64CN5 was  replaced with EPM240T100C5N ( due to cost and supply issues by supplier "OpenSourceSDR Lab") which has caused some issues ( they issues their work around fixes in a version 1.4.3)  and resolved in version 1.5.x due to a lot of hard work.


## H2+R4

<img src="https://user-images.githubusercontent.com/4393979/170891015-6c9517bf-ee0b-49b9-b7bf-8d9f4049c721.png" height="300">



### Differences
* Similar to the H2+R3 except it now uses the AG256SL100 IC as well as the 28 pin QFN WM8731L instead of the 38 pin QFN AK4951. Marked as "PCB v3.6 mmdvm.club". 
* 3W LTK8002D SOP8 Class D amplifier for the speaker (INS8002e clone?).
* Power IC IP5306 SOP8.

## H3
Uses custom close source firmware. **Not compatible with Mayhem. Do not buy or support as it's a scam**

<img src="https://user-images.githubusercontent.com/1091420/214587249-48608cf2-195e-47a9-aa31-3dd2feb2abea.png" height="300">

This also exists as H2 Plus. Uses custom close source firmware ([Ref.](https://user-images.githubusercontent.com/24917424/198536040-e573b98c-e327-4e69-9448-83cea52b02e3.jpg)). **Not compatible with Mayhem([Ref.](https://user-images.githubusercontent.com/24917424/198536040-e573b98c-e327-4e69-9448-83cea52b02e3.jpg)).

## Maxgeek H2 
Maxgeek H2 has an issue with a frozen application on their portapack. Even when they show this firmware in their product description:

<img src="https://user-images.githubusercontent.com/1091420/214588783-ed2f7efb-1897-416f-b42d-9cf66540de86.png" height="300">

They have acknowledged that only their firmware works. **Not compatible with Mayhem!([Ref.](https://user-images.githubusercontent.com/5009021/204222733-a82aa404-9949-4de3-b6b3-4265e7d81f32.jpg)). Do not buy or support as it's a scam**


