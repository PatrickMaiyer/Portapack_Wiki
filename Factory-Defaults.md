# Why a reset to factory defaults

Sometimes with an update some settings management is changed and render the actual settings set in various place not working correctly or clearly killing some apps.

To resolve this you can try to reset these settings. For that, you'll have to clear the persistent settings and clean some directories on your SDCARD.

# Guide

The best way to achieve the reset is to take out the SDCARD and do the cleanings on it on computer.
 
Boot the unit without the SDCARD (you may need to press your boot key), get into the 'Settings' / 'P.Memory Mgmt' menu and clean the persistent memory using the button. 

Shutdown. 

While you're at it update the SDCARD content to latest if not done. 

Put back the SDCARD.

Boot (may need boot key). 

You can now use your device like if it was installed first.

## SDCARD

### 'SETTINGS' directory

Delete all the files under 'SETTINGS' to reset "App Load and Save" settings as well as the configuration of the "P.Mem" menu. (note: this does not reset the persistent memory itself).

### 'hardware' directory
NOTE FIRST: this reset the saved boot config key. 
In case you think it's not booting because of a bad saved detection, delete the file under that directory.

## PERSISTENT MEMORY

Get into 'Settings' , 'P.Memory Mgmt' and click on the '! reset p.mem, load defaults !'. This reset various settings in apps like i.e Recon app.

In case the p.mem contents somehow block the startup (the screen stays black and the RX led blinks rapidly that typically happen after flashing a different build) the p.mem can be ignored during startup by holding down the left and right buttons while starting up the device.

### 