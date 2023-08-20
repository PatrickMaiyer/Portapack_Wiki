[[img/title-bar.png]]

The PortaPack Mayhem title bar consists of a number of icons, some of which trigger actions and some of which are used to indicate the status of certain subsystems. In some older versions, the title bar also contained either the application name or firmware name and version in the form **MAYHEM vX.Y.Z** where the versioning is consistent with the standard semantic versioning (major.minor.release) format. This was moved to the footer in latest versions.

Actionable icons can be accessed by touch, or by using the directional buttons (H2) or the directional ring (H1) to move the highlight that indicates which icon is selected. If the highlight is on the main menu, using the *up* button will move it to the title bar.

Infrequently used icons may be hidden using Settings -> User Interface, if desired.

The sections of the title bar, along with their functionality, are (from left to right):

|Image|Function|Actionable|
|-----|--------|----------|
|Back |Back arrow to previous screen/Return to menu| Yes |
|Name|Application name, when click -> same with Back| Yes |
|![icon_camera](https://github.com/eried/portapack-mayhem/assets/129641948/de4c98c5-ef15-4d83-980b-c9b69ecf3ca2)|Take [screenshot](screenshots)  | Yes |
|![MoonIcon](https://github.com/eried/portapack-mayhem/blob/master/firmware/graphics/icon_sleep.png)|Activate [sleep mode](sleep-mode) | Yes |
|![icon_stealth](https://github.com/eried/portapack-mayhem/assets/129641948/95ee64ef-f532-4c57-b07b-963028fec204)|Toggle [stealth mode](stealth-mode). Green if selected | Yes |
|![icon_upconvert](https://github.com/eried/portapack-mayhem/assets/129641948/9e8e7d5c-25cc-46aa-ae7e-fffb5742a2ce) / ![icon_downconvert](https://github.com/eried/portapack-mayhem/assets/129641948/8e699c14-0269-426a-9b7b-60814be5fd7b)|Toggle [Up conversion or Down conversion](https://github.com/eried/portapack-mayhem/wiki/Settings#converter). Green if activated. | Yes |
|![icon_biast_on](https://github.com/eried/portapack-mayhem/assets/129641948/333a819b-ec41-4f2a-89e4-addb9c795c80) / ![icon_biast_off](https://github.com/eried/portapack-mayhem/assets/129641948/555e08a9-6e4f-447f-8879-05f185cd6c41) |Toggle DC power on antenna port. Yellow if selected | Yes |
|![ExtClockOffIcon](https://github.com/eried/portapack-mayhem/blob/master/firmware/graphics/icon_clk_ext.png)|Indicate status of external clock. Green if selected | Yes |
|![icon_speaker_and_headphones](https://github.com/eried/portapack-mayhem/assets/129641948/6bbbaaf0-9977-43aa-b664-19d1570e5fca) / ![icon_speaker_and_headphones_mute](https://github.com/eried/portapack-mayhem/assets/129641948/6634c52f-f208-4033-b66b-976e0b776829)|Enable/mute audio (speaker & headphone)|Yes|
|![icon_speaker](https://github.com/eried/portapack-mayhem/assets/129641948/0ec4d2c5-c487-4519-b68b-0df9628651a9) / ![icon_speaker_mute](https://github.com/eried/portapack-mayhem/assets/129641948/07526e75-612b-4b02-b7de-424fb39b6f03) |Enable speaker output on PortaPack with AK4951 codec. Green if activated. Warning: Do not enable if speaker already works when disabled, as on OpenSourceSDRLab PortaPack H2.| Yes |
|![SDCardOKIcon](https://github.com/eried/portapack-mayhem/blob/master/firmware/graphics/sd_card_ok.png)|Indicate presence of SD card. Green if SD card was found | No |
