Receives pager messages using the POCSAG protocol.

This protocol operates in the VHF/UHF bands using FSK modulation.
More technical details can be found by following the links in the References section.

# UI Overview

![POCSAG_UI](https://github.com/eried/portapack-mayhem/assets/3761006/bb4795e7-1b1f-4b31-8663-ddc71d1535d4)

![POCSAG_UI_Detail](https://github.com/eried/portapack-mayhem/assets/3761006/1c0faccf-aec3-4a44-b183-8731d24642f1)

### Settings
- **Frequency**: Sets the frequency to receive pager messages on. Can be adjusted with the [encoder thumb wheel](Hardware-overview), on-screen numpad, or loaded from frequencies saved on an SD card. 439.9875 MHz is the most popular worldwide frequency used by Amateur radio for POCSAG. Amateur radio POCSAG uses 1200bps.
- **RF amplifier** (0 or 1): Enables/disables the internal RF amplifier.
- **LNA gain** (0, 8, 16, 24, 32, 40): Sets the LNA gain. Further information: [Description of the gain settings](Help!-Im-not-receiving-anything!---Receive-Quality-Issues#description-of-the-gain-settings)
- **VGA gain** (0 to 62): Sets the VGA gain. Further information: [Description of the gain settings](Help!-Im-not-receiving-anything!---Receive-Quality-Issues#description-of-the-gain-settings)
- **RSSI/Audio**: Top bar indicates signal strength. Bottom bar indicates the audio level. The audio bar can be useful for tuning settings without headphones/speaker to hear the tone.
- **Squelch** (0-99): Sets the signal to noise threshold. 0 disables squelch. Higher values allow more noise. Should be set so that strong signals are clearly received without any dropped audio.
- **Volume**: Output volume for the received audio. Can be used to monitor received signal quality.

### Information
- **Decoder Status**: Indicates the status of the decoder state machine. White: Idle, Cyan: Clear, Yellow: Waiting for message start, Green: Waiting for rest of message.
- **Batch Count**: Number of message batches that have been received. A batch has 16 codewords.
- **Bits**: Displays the bits that are being decoded into codewords.
- **Sync**: Green when the frame decoder has received a "sync" frame. Messages are not decoded unless a sync frame is found.
- **Codewords**: Shows the number of codewords in the current batch. When the bar fills, the batch is complete and is processed.
- **Baud Rate**: The detected rate of the current message. 05: 512bps, 12: 1200bps, 24: 2400bps.

### Buttons
- **Ignore Last**: Enables "Ignore" mode for the last received address.
- **Config**: Enters the settings page to configure options.

## Config

![POCSAG_Config](https://github.com/eried/portapack-mayhem/assets/3761006/96ca160b-5672-4169-b90d-85a433cbb39d)

- **Enable Log**: Logs messages to the SD Card at "LOGS/POCSAG.TXT"
- **Log Raw Data**: Logs the batch codewords as hexadecimal. Useful for debugging decoder bugs.
- **Use Small Font**: Uses the 5x8 font in the UI to show more messages on the screen.
- **Hide Bad Data**: Don't show (or log) codewords that fails checksum validation.
- **Hide Addr Only**: Don't show (or log) codewords that don't contain a message.
- **Enable Ignored Address**: Don't show (or log) codewords sent to the specified address.
- **Beta**: Enable the new POCSAG baseband processor. The app *must* be restarted for this to take effect.
- **Save**: Save any settings changes.

## Message Display

Typical message:
```plaintext
12:34 1200 #432123 F2
This is a test message
```

Description (from top-left):

- `12:34` - **Time**: The time that the message was received (time from PortaPack).
- `1200` - **Data rate**: The data rate used to receive the message.
- `#432123` - **Address**: The address of the intended pager recipient.
- `F2` - **Function**: (0 to 3) Indicates the type or source of message sent (can be used to provide a category of sorts).
- `This is a test message` - **Message**: The message data displayed as ASCII.

# References

The following resources provide more technical information about the POCSAG protocol:

- [POCSAG - Signal Identification Wiki](https://www.sigidwiki.com/wiki/POCSAG) - Provides frequencies commonly used in different countries and regions
- [POCSAG - WikiPedia](https://en.wikipedia.org/wiki/POCSAG)
