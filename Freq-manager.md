# Freqman file format

Starting from nightly 12/05/2023 the freqman file support empty lines, comment lines, anything which is not matching one of the described fields is ignored.

In case you hit the maximum number of entries in a list, (was 60 entries at some point) files is truncated. 

Truncated files list are displayed in yellow.

## Description of the fields
`'f=freq' for one Single frequency entry`

`'a=start_frequency,b=end_frequency' for a Range entry`

`'r=ham_relay_rx_freq,t=ham_relay_tx_freq' for a HamRadio entry`

`'l=repeater_listening_freq,t=repeater_tx_freq' for a Repeater entry`

`m=modulation`

`bw=bandwidth`

`s=step`

`d=description`

**All fields except [f=], [a=,b=], [r=,t=] and [l=,t=] are mandatory**.

If nothing specified actual value is used, even if actual value is 'not set'

Any application using the original load_freqman_file will only load frequencies, and will try to populate a range in the list instead of manually stepping in. For developers: I've made a new load_freqman_file_ex func which do return an old list format depending on the parameters

The Recon app is using the old as the new format, taking informations in account when they exist.

## Freqman file example 

`f=468000000`

`f=468000000,d=Single Freq`

`f=468000000,m=AM,d=Single Freq AM`

`f=468000000,m=NFM,d=Single Freq NFM`

`f=468000000,m=WFM,d=Single Freq WFM`

`f=468000000,m=AM,bw=DSB 9k,d=Single Freq AM DSB`

`f=468000000,m=AM,bw=USB,d=Single Freq AM USB`

`f=468000000,m=AM,bw=LSB,d=Single Freq AM LSB`

`a=87000000,b=110000000`

`a=87000000,b=110000000,m=AM,s=100kHz,d=AM radio search`

`a=87000000,b=110000000,m=AM,bw=DSB 9k,s=250kHz,d=AM radio search LSB`

`a=87000000,b=110000000,m=WFM,bw=200k,s=50kHz,d=WFM radio search s=50kHz`

`r=430150000,t=430550000`

`r=430150000,t=430550000,d=HAM radio`

`r=430150000,t=430550000,m=AM,bw=DSB 9k,d=HAM radio`

`l=430150000,t=430150000,m=SPEC,bw=150k,d=100k repeat`

`l=430150000,t=430150000,m=SPEC,bw=1000k,d=1000k repeat`

`l=430150000,t=431150000,m=SPEC,bw=1000k,d=1000k repeat txoffset 1MHz`

## Possible values for modulation/bandwidth

* AM  ( DSB 9k , DSB 6k , USB+3k , LSB-3k , CW )
* NFM ( 8k5 , 11k , 16k )
* WFM ( 200k , 180k , 40k )
* SPEC ( 12k5 , 16k , 25k , 32k, 50k , 75k,  100k , 150k , 250k , 500k , 600k , 750k , 1000k , 1250k, 1500k , 1750k , 2000k , 2250k, 2500k , 3000k, 3500k, 4000k, 4500k, 5000k, 5500k )

## Possible values for Steps

* 5kHz , 6.25kHz , 8.33kHz , 9kHz , 10kHz , 12.kHz , 15kHz , 25kHz , 50kHz , 100kHz , 250kHz , 500kHz , 1MHz

