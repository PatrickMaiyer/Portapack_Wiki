## **This is a potentially dangerous App. The HackRF could be used to generate valid ADS-B messages and if these are radiated then it could effect both how aircraft and navigation systems see each other. Therefore, it should only be used in a closed RF environment or when there is no direct transmission.**

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Tab pages:** The Tab pages for the settings that are can be selected are **Position, Callsign, Speed, Squawk**. This data is not held in persistent memory except for the frequency.

## Position Tab
**ICAO24:**  This code is selected with rotary encoder to enter the 6 digit numeric  number. This is sometimes called the Mode S code and is a 24-bit unique number that is assigned to each vehicle or object that can transmit ADS-B messages. It is usually transmitted by aircraft but some airport ground vehicles and multi-lateration towers also have ICAO24 codes assigned to them.
Transmit position: this is a tick box to enable the transmission of Alt. Lat. Lon
* **Alt:** Sets height in feet.
* **Lat:**  Setting of Latitude is in Degrees Minutes and Second and set with encoder knob. The numeric value is given to the right hand side 
* **Lon:** Setting of Longitude is in Degrees Minutes and Second and set with encoder knob. The numeric value is given to the righthand side.
* **Set from Map:** the Lat and long can be set form the map view and using the touch screen if desired. Note to save the value is a “OK” button but this is hidden behind the Digital values of the Lat and Lon. But if you touch this, are it will appear.

## Callsign Tab
* **Transmit callsign:** This is a tick box to turn on the transmission of the [Callsign](https://en.wikipedia.org/wiki/Aviation_call_signs). The callsign is entered in the text pad and is 8 characters long. 

## Speed Tab
* **Transmit speed:** This is a tick box to turn on the transmission of the speed. 
* **Speed:** The value is selected and the rotary encoder is used to select the value 0-999kn, unit: knots.
* **Bearing:** The value is selected and the rotary encoder is used to select the value 0-359 Degrees. (to be more friendly user, the input bearing angle direction is also displayed in the top right Compas circle UI)
* **Vertical Rate:** The value is selected and the rotary encoder is used to select the value -4096 to +4096 ft/min in steps of 64 (following the encoding standard). It indicates the vertical rate speed of the plane (+) climbing , (-) descending. In real plane ,that Vr source data information can come from GNSS or Barometric altitude equipment. In mayhem fw , we are simulating a fix source from GNSS. Example about climb vert. rate (+) : The [Cessna 172](https://en.wikipedia.org/wiki/Cessna_172) is a four-seat aircraft. At maximum weight it has a VY of 75 kn (139 km/h) [indicated airspeed](https://en.wikipedia.org/wiki/Indicated_airspeed)[[4]](https://en.wikipedia.org/wiki/Rate_of_climb#cite_note-4) providing a rate of climb of 721 ft/min (3.66 m/s) ). Example about descend vert. rate (-): The profile varies from airport to airport, but generally, around five miles from the runway, the airplane is at landing speed, with slats/flaps in the landing position, vertical descent speed less than 1,000 feet per minute and the engines powered up properly.

## Squawk Tab 
* **Transmit squawk:** This is a tick box to turn on the transmission of the [Squawk](https://en.wikipedia.org/wiki/List_of_transponder_codes) code. 
* **Squawk:** A discrete transponder code (often called a squawk code), can be selected with rotary encoder and has specific meanings. The system identifies an aircraft through a four-digit octal number. (each digit number from 0-7), which provides up to 4.096 possilbe codes.  The squawk code range is from 0-7777.  
Squawk codes are usually random, but there are a handful of specialized squawk codes that are reserved for unique or specialized situations or aircraft.  https://en.wikipedia.org/wiki/List_of_transponder_codes

Some public  pilot user interface equipment examples (from Wikipedia),

 
![image](https://user-images.githubusercontent.com/86470699/210870176-ab71e12e-90ce-42a2-a90d-762e878aa835.png)
![image](https://user-images.githubusercontent.com/86470699/210870689-397eed6d-dba5-4664-bbd6-ca0afbba5e92.png)



## Common to all Tabs 
* **Frequency:** At the lower part of the App is the Frequency setting. This is stored in persistent memory 
* **Step size:** This is next to the frequency and allows the selection of the standard step sizes.
* **Gain:** The gain setting are below the frequency and marked (0-47) LNA(IF) and AMP 0=0db or 1=14dB.
* **Start:** This button starts the transmission and if pressed again can stop the transmission.
