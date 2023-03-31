# Level App
![Level App Menu Entry](https://www.nilorea.net/wp-content/uploads/2023/03/PORTAPACK_LEVEL.png)

# Introduction

The level app is as simple as possible and allow you to monitor available level meters in a single view. CTCSS tone showed if NFM is selected.

# Buttons

* [LNA] , [VGA] , [AMP] , [VOL] => gains, amplification on/off and volume
* [BW] , [Mode] , [STEP] => bandwidth, demodulation and step
* [FREQ] , [AUDIO] => Frequency adjustement, audio on/off
* [PEAK] => enable peak hold and timer, or disable it
* [xXX] => set the number of columns in the live history

# Informations on screen

* RSSI: min, average, max values, [CTCSS tone if NFM is selected]
* POWER: current db power level

# Right level meter

* RSSI min => blue fill
* RSSI avg => horizontal white bar
* RSSI max => red fill, peak hold in green if enable

# Graphs

* RSSI min, average, max => blue, white and red lines clipped between [ 31, 170 ] and scaled along the height of the RSSIGraph widget
* POWER => green line, clipped between [ -100 , +20 ] and scaled along the height of the RSSIGraph widget