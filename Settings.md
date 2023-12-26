This section provides a set of utilities that can be used to configure some aspects of the PortaPack and are described below.  Settings are saved in persistent memory.
## Audio
This allow the setting of the tone Key mixer setting as a percent of the audio level.
## Radio
In the radio section there are three options, 
1. Enable/disable the Clock Output. (it can be activated / deactivated by top title bar (CLKout icon) : green icon means activated, or thought that radio menu (check-box)


> Note 1 : In r9 Hackrf platform , due to our complex fw Architecture and usage of Si5351A , we have fixed the synthetized CLK out freq to 10Mhz.

> Note 2 : In all previous r1 to r8 Hackrf platforms , as we are using Si5351C, we do not have that limitation , and user can change the CLKOUT frequency between 4 kHz to 60000 kHz; press OK when the frequency is highlighted to select which digit position to modify and then use the encoder to scroll through the digit values. (it works with both clock references, the internal Hackrf (25Mhz) and the external -when available- from Portapack (TCXO 10Mhz ). 

> ![image](https://github.com/eried/portapack-mayhem/assets/86470699/5c44e075-cf84-4f8f-8ca6-a7979c1bf4aa)

> Note 3 : Zooming previous picture , when the unit detects that external CLOCK_in -usually 10Mhz reference- (from Portapack or from external source) , it is indicated in the top title CLK_in icon 
> with some top arrow below the icon (right picture) . In case of no detection , it is indicated with some "X" below the icon (left picture),and in that case, the system takes the internal 25Mhz Hackrf clock reference. 

> ![image](https://github.com/eried/portapack-mayhem/assets/86470699/820c12d9-c724-48ed-ba1d-f3c31e096a07)


> Warning note : be awared that some of current market Portapack boards may have an integrated low ppm TCXO 10Mhz clock generator mounted, and when it is built in,  it is connected in parallel to the Hackrf CLK_in port connector. So in that case , that signal is present always in the SMA  CLK in connector , and you should better to not connect any other external signal generator there (unless you remove the Portapack from Hackrf) , because otherwise, you may damage that Portapack TCXO clock IC. 

> Here below , you can see two different examples of the embedded TCXO 10Mhz ref. clock,	
>  in a PP  H1 brd (left side ) , PP  H2 brd (right side) boards : 

> ![image](https://github.com/eried/portapack-mayhem/assets/86470699/ad83b637-4532-4ea8-994b-4372a38f9d15)



2. Enable/disable the Antenna Bias voltage.  (it can be activated / deactivated by top title bar (DC bias icon) : green icon means activated, or thought that radio menu (check-box) .  If enabled, ensure that all devices attached to the antenna connector can accept a DC bias voltage.

3. Enable/disable the External TCXO Clock input. (it can be activated / deactivated by that radio menu (check-box).
      Sometimes, in low battery charge voltage, or other low output TCXO voltage amplitude , we may have some boot problems with that
      external TCXO signal and in that case, we may want to deactivate it.

## User Interface
The UI interface  setting for the following can be Enabled (tick) or Disabled (x) or selected value for the backlight timeout:
* Backlight off after 5 seconds( default) or can be set to 5,15,30 seconds or 1,3,5,10 minutes.
* Show the Splash screen at power-up.
* Show the clock - This allows the date and time to be updated by moving the cursor to the select item and use the rotary knob to adjust the value.
* Back button in menu - Enables a "Back" button on all menu screens.
* Show/Hide Status Icons - Select which status bar icons are visible or hidden.
## Date/Time
Set the date and time.
## Calibration
This provides an app for the calibration of the screen and alignment by following on screen instruction. 

You have to keep pressed for at least a second on each target for the app to guess the touch area correctly and show next target on release.
## App Settings
Settings for each app are saved in corresponding .ini files in the /SETTINGS folder to maintain persistence, if a formatted SD card is installed.  An updated .ini file is saved whenever the app is closed.  To reset an app to default settings, the corresponding .ini file may be safely deleted and a new file will be created automatically when the app is subsequently executed.  Alternatively, individual lines in the file may be deleted to reset only a subset of application settings.  For debug purposes, note that some additional configuration settings may be found in the .ini file that are not configurable in the app itself.

Note: In firmware versions prior to 1.8.0, apps use the .ini settings file ONLY if the following configuration settings are enabled (in 1.8.0+ this is the default behavior and the Settings->AppSettings screen will not appear):
 * Load app settings 
 * Save app settings

### blacklist
To disable specific apps completely, a text file named "blacklist" can be created manually in the SETTINGS folder using the Notepad application.  Unwanted applications should be listed in this file using their case-sensitive application name (text that appears under the app's screen icon), and they will be disabled (hidden) effective on the next boot.  List one application per line.  (Requires 1.8.0+ firmware and an SD card)

## Converter
![PortapackConverter](https://www.nilorea.net/wp-content/uploads/2023/03/PORTAPACK_CONVERTER.png)

Set up convert or down convert mode. Widgets:
 * show / hide icon, hiding will also disable any up / down conversion
 * enable / disable converter
 * (+) or (-) set the offset sign
 * set the offset 

When using an upconverter it's common to use an offset to access the correct frequency. As an example, if you want to use a HamItUp which is designed to listen from 60KHz to 30MHz, you'll need to tune your portapack to 125 MHz (or any other frequency used in the upconverter local oscillator) + the frequency you need.

Doing the calculation and tuning while adding the frequencies can be a bit tedious. Don't worry: just got into your portapack's settings, Radio menu, and set the shifting you need. You can set up conversion (+) or down conversion (-) in the Settings/Converter menu.

When the option is on, the displayed frequency is the one you want to tune in, and the real tuned frequency is displayed frequency plus or minus offset.
When the option is off, the displayed frequency is the one you want to tune in, and the real tuned frequency is the displayed frequency.

You can turn it on and off using the checkbox while in Radio menu, or using the top bar icon 'Freq', with an arrow telling you if it's up or down conversion.

Note:  This has the same effect as using the top bar 'Freq' icon. While in the radio menu, the synchronisation of the top bar 'Freq' status and the checkbox is not implemented when toggling the top bar 'up' icon. The status is saved, and the last to talk is setting the status.

## QR code
Set the size of the displayed QR code in the RadioSonde app.
 * show larger or not

## P.Memory Mgmt
![PORTAPACK_PMEMTOSDCARD](https://www.nilorea.net/wp-content/uploads/2023/03/PORTAPACK_PMEMTOSD.png)

Set persistent memory from/to sd card options. It's particularly useful to keep different default settings than those configured by the firmware if there is no/dead coin battery. Information messages will be displayed at each widget trigger. If loading at startup is failing, it will not show any message, the boot may continue like nothing happened. Widgets:
 * use sdcard for pmem: if checked the firmware will try to load last saved settings at startup. The checkbox is configuring a flag file under SETTINGS for it to work without coin battery. Each time you correctly exit an app using the back button, it's persistent settings, if any, are saved to the sdcard.
 * save p.mem to sdcard : save actual persistent memory onto the sdcard  
 * load p.mem from sdcard : manually load persistent memory from sdcard
 * !reset p.mem, load defaults! : reset the persistent memory to defaults

## FreqCorrect
![PORTAPACK_FREQCORRECTION](https://github.com/eried/portapack-mayhem/assets/3157857/4c313bb6-1125-4b43-8b1b-c3721f3041b1)

Set TX and or RX Frequency correction in Hz. 

A value between [-4,+4] MHz of correction is accepted, else it's truncated due to the variable used in persistent memory.

Use the '+' or '-' filed to change to correction mode (addition or subtraction ).

Use the MHz RX and MHz TX field to set the correction in each mode.

Settings are automatically saved in persistent memory.

## Encoder Dial
Allows the sensitivity of the encoder dial to be adjusted between Low, Normal, and High.