This app allows you to broadcast GPS baseband signal data streams. 

## Generator
You can use [gps-sdr-sim](https://github.com/osqzss/gps-sdr-sim) to generate data for this app.  

`gps-sdr-sim -e RINEX_NAVIGATION_FILE -l LAT,LONG,HEIGHT -b 8 -o SOMENAME.C8`

That will create `SOMENAME.C8`, but note that you also need to specify its sample rate and frequency in another file, as explained below.

### RINEX navigation file for GPS ephemerides
Download the latest file for this parameter directly from Nasa: https://cddis.nasa.gov/archive/gnss/data/daily/

### Sample rate and frequency specification
Create `SOMENAME.TXT` with:
```
sample_rate=SAMPLE_RATE
center_frequency=1575420000
```

Known working values for the `SAMPLE_RATE`:
* [2600000](https://www.tiktok.com/@erwinried/video/6822750940806843654?fbclid=IwAR1vMd-CCchIdbXPudxQr5mIKXJv7cL2HaGRhUSl1iaDvCufnD1D67X31IE)
* 2500000
* [1250000](https://www.facebook.com/groups/177623356165819/permalink/648011779126972/)

This file should use the same filename as the .C8 file but with .TXT extension. It contains the sample rate and center frequency for the .C8 file. Copy the files to your PortaPack MicroSD and open the .C8 file in the GPS Sim app.

## Example 1
Create a rather small polygon with a path in KML format (i.e. a path you might want to simulate to walk). You can use Google Earth or another solution like https://www.doogal.co.uk/polylines.php. Load that file in the free [SatGen NMEA simulator](https://www.labsat.co.uk/index.php/en/free-gps-nmea-simulator-software). In the generator, change the frequency to 10 Hz and export the NMEA.

`gps-sdr-sim.exe -e brdc1180.20n -g NMEA.txt -b 8 -o TESTGPS.C8`

You also need to create `TESTGPS.TXT` as specified above.

## Example 2

For a fixed position, use
`gps-sdr-sim -e brdc1500.20n -s 1250000 -b 8 -o gpssim.C8 -l 30.286502,120.032669,100 -d 100`

Test with a `gpssim.txt` as follows:

```
sample_rate=1250000
center_frequency=1575420000
```

## Example 3
> **NOTE:** The website nmeagen may add timestamps to the output. That might be problematic for the simulation

We can create a realistic movement using a NMEA GGA stream generator like https://nmeagen.org/. In this website create several multi point lines with the positions you want. Download the NMEA file clicking "Generate NMEA file".

`gps-sdr-sim.exe -e brdc3540.14n -g OUTPUT.nmea -b 8 -d DURATION -o MYGPSWALK.C8`

You also need to create `MYGPSWALK.TXT` as specified above.

## Compatibility
Depending on several factors, results may vary. A modern device will use several sources and methods to validate the current position, so spoofing positions may not be possible in all situations. To improve your chances to receive simulated GPS data, try:
* Turn off Wifi/BT/Cellular and positioning-enhancements (best airplane mode)
* Go inside, where the device loses GPS signal
* Reboot the device after doing the previous two steps

If the device runs Android, follow your attempts with [GPS Test](https://play.google.com/store/apps/details?id=com.chartcross.gpstest).

### Known results
| Type       | Make    | Model        | Locks on spoofed GPS? | GPS acts "jammed"? | Comments                   |
|------------|---------|--------------|-----------------------|--------------------|----------------------------|
| Tablet     | Samsung | Note 7       | No                    | Yes                |                            |
| Phone      | Samsung | S8           | **Yes**               | No                 | WIFI must be off           |
| Phone      | Huawei  | P30 lite     | No                    | Yes                |                            |
| Phone      | Huawei  | Mate 10 Pro  | No                    | NO                 | 6 or 7 satelites: No fix   |
| Smartwatch | Huawei  | Amazfit Bip  | **Yes**               | No                 |                            |
| Phone      | Apple   | iPhone 6     | **Yes**               | No                 | Works with WIFI on         |
| Phone      | ZTE     | Axon 7       | **Yes**               | No                 | Works with WIFI on         |
| Phone      | Xiaomi  | Mi5          | **Yes**               | No                 | Works with WIFI on         |
| Phone      | Samsung | S20+ 4G      | **Yes**               | No                 | WIFI must be off           |
| Smartwatch | Samsung | Gear S3 WiFi | **Yes**               | No                 | Location over GPS only     |
| Phone      | OnePlus | 7 Pro        | No                    | No                 | Doesn't seem to do anything|
| Phone      | Samsung | S21 Ultra    | **Yes**               | No                 |                            |
| Tablet     | Apple   | S21 Ultra    | No                    | No                 | Doesn't seem to do anything|
| Laptop     | Apple   | MacBookPro M1| No                    | No                 | Doesn't seem to do anything|


## References
https://blog.csdn.net/shukebeta008/article/details/103270214