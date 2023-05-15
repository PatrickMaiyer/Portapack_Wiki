The MGA-81563 can be damaged easily, but you can buy (relatively cheap: https://s.click.aliexpress.com/e/_Dl4U7Yl) and replace them yourself. For more information about this procedure, please check https://www.onesdr.com/2020/04/09/how-to-fix-a-broken-hackrf/

The previous link has a very good reference picture:

![image](https://github.com/eried/portapack-mayhem/assets/1091420/88b9ab27-59e5-48d1-964d-79e72d32657b)


# RX problems

If you find on a strong signal such as an broadcast FM station that you select Amp as "0" and you get a signal and then select Amp "1" and you do not then this is a good sign that the RF Preamplifier u13 (MGA-81563) is damaged. This can happen if you use a stronger transmitter near to your HackRF.

It is possible to replace the damaged IC with simple tools (soldering iron, solder wick). First solder flood the damaged component to remove it, preferably protecting the surrounding. Clean the pads and replace the component: 

<img src="img/preamp-1.jpg" height="400"> 

# TX problems

The same component is used for TX, which also can be damaged. Below is an example of the replacement procedure. First remove and clean the pads. This can be done with hot air or normal soldering iron:

![image](https://github.com/eried/portapack-mayhem/assets/1091420/28bdbccc-ba8a-4016-bdd9-fc8ce7db4d59)

For the orientation, you could use the text of the chip itself. It should be "up", pointing to the antenna jack of the HackRF:

![image](https://github.com/eried/portapack-mayhem/assets/1091420/b6ccd68b-e261-4810-8e0f-dea8a2ff5b95)

