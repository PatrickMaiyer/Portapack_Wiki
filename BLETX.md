The BLETX application is intended for importing a BLE Advertisement file, parsed by the application and transmit it OTA.

The BLETX application has two modes, both which can be used after importing a file.

1. Single transmit mode. (This mode transmits a single BLE packet OTA given the file parameters.)
2. Loop Mode (This mode continuously transmits by the total number of repeats given by the file.)

The **Speed** setting allows the user to adjust how fast the transmit occurs. (This is still a WIP as I have not yet defined literal speeds to the numbers, but **Speed 1** seems to transmit close to 100ms a packet.)

The **Channel** setting allows you to select which channel to transmit on.

Both setting can be used during transmit to simulate a change in channel and speed.

The progress bar will update, (in Loop Mode), to show how many of the current packets are left to be transmitted. This is also seen by the **Packets Left** indicator on screen.

**Example of file:**
Below is an example of how the text file show be formatted in order for it to be correctly parsed by the application.

010203040506 190953445220426c7565746f6f7468204c6f7720456e65726779 1000

010203040506 (MAC Address you want to be transmitted. Must be exactly 12 characters)

190953445220426c7565746f6f7468204c6f7720456e65726779 (Packet Data you want to be transmitted. Must be less than 62 characters, 31 byte max advertisement length per BLE spec.) In this case we are transmitting a packet with data: **SDR Bluetooth Low Energy**

1000 (Number of times you want the packet to be repeated.)

Its important to note all parameters must be delimited by a single space.

**TODO:** I want to eventually add support for multiple packets from a file, but current it only supports one packet per file.

**Disclaimer:** I've tested this transmission with a BLE device which seems to receive packets successfully. However the transmission seem to have trouble showing up on my Android phone. I have not tested iPhone. There is still more research to be done, but updates will be provided as they happen. As far as I can tell BLE data is being transmitting through captures of a Spectrum Analyzer.