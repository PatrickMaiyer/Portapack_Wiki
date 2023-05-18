[Tire Pressure Monitoring System (TPMS)](https://en.wikipedia.org/wiki/Tire-pressure_monitoring_system) operate in the ISM Licence free bands. In USA and most of the world they use 315mHz, in Europe the frequency is 433.92mHz. The TPMS App work well with many common standards used in the automotive industry particularly from [Schrader TPMS sensors.](https://www.schradertpms.com), and this seems a common standard used in the automotive industry.

The TPMS App display is configured to display the decoded data received from the tire pressure sensors. The interval of the data being sent by each tire varies from every few seconds to minutes depending on the car and sensors, often triggered by wheel movement or rapid pressure changes. Most Schrader sensors can also be triggered to transmit data using a TPMS test tool (which transmits a signal on 125 kHz).

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:
Title bar: The usual Items may be changed and displayed.
* **Frequency:**  Either 315mHz or 433.92mHz
* **kPa/PSI :**  By highlighting this item the units of pressure displayed can be changed between kPA and PSI.
* **C/F :**  By highlighting this item the units of temperature displayed can be changed between Celsius and Fahrenheit.
* **Gain:** Setting are shown in order of Amp 0=0db or 1=14dB, LNA(IF) (0-40) and VGA (Baseband Gain) (0-62). 

## Data fields are:
* **Tp:** This is the type of the tire sensor decoded the following are coded in the App. Some types of TPMS sensors are not supported.
    * 0 = None
    * 1= FLM_64
    * 2= FLM_72
    * 3= FLM_80
    * 4= Schrader
    * 5= GMC_96
* **ID:** The ID of the tire sensor being 8 hexadecimal characters. Note that sometimes the label printed on the actual temperature sensor is in decimal format.
* **Pres:** This is the pressure in either kilo Pascals (kPa) or Pounds Per Square Inch (PSI).
* **Temp:** The temperature of the tire in either degrees Celsius (C) or Fahrenheit (F).  Note Spurious data has been seen and may be due to receive errors, unsupported protocols, or failed sensors.  Pressure and temperature ranges may vary depending on sensor model, so best to compare to dash readings, if available.
* **Cnt:** This is the count of messages received from each sensor.
* **Flags:** Information on the type of sensor is only for Schrader and have decode for: fsk_19k, ook_8k192, ook_8k4.

If a FAT-formatted micro SD card is present when this mode is entered, the receiver will log received packets to a file named "TPMS.TXT". The log file contains one line per packet received. Each line consists of a timestamp in sortable "YYYYMMDDHHMMSS" format, receiver frequency, modulation, deviation, symbol rate, and data. The data field consists of Manchester-decoded data bits, a "/", and a per-bit Manchester coding error indicator ("1" if the data bit is in error).