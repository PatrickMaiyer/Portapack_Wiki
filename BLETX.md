# Main Menu:

The BLETX application is intended for importing a BLE Advertisement file, parsed by the application and transmit it OTA.

The BLETX application has two modes, both which can be used after importing a file.

1. Single transmit mode. (This mode transmits a single BLE packet OTA given the file parameters.)
2. Loop Mode (This mode continuously transmits by the total number of repeats given by the file.)

A file must be present, unless moving from the BLE RX app, in order to transmit a packet. Use the **Open file** button to select which file to transmit. Information on file format is found below. Once loaded, the screen will update the UI with the current packet to send. If there are multiple packets in the file, the screen will update this information based on which packet is being transmitted.

1. The **Speed** setting allows the user to adjust how fast the transmit occurs. 
(**Note:** Values are approximate based on a 16ms timer period)

     Current Speed table is as follows:

   * **Speed 1**: 16ms per packet.
   * **Speed 2**: 32ms per packet.
   * **Speed 3**: 48ms per packet.
   * **Speed 4**: 100ms per packet.
   * **Speed 5**: 200ms per packet.

2. The **Channel** setting allows you to select which channel to transmit on.

3. The **Packet Type** setting allows you to select between various types of advertisement types.

4. The **Random** toggle allows you to randomize the MAC Address that you send out with each packet.

5. The **Save Packet** saves to file the current packet list in TX format to the name you specify.

6. The **Switch to RX** button will send you to the BLE RX App. See BLE RX App for more information.

The progress bar will update, (in Loop Mode), to show how many of the current packets are left to be transmitted. This is also seen by the **Packets Left** indicator on screen.

# **Example of file:**
Below is an example of how the text file show be formatted in order for it to be correctly parsed by the application. To get this transmission to show up on a BLE Scanner app set the toggle to ADV_NONCONNECT

010203040506 190953445220426c7565746f6f7468204c6f7720456e65726779 1000

010203040506 (MAC Address you want to be transmitted. Must be exactly 12 characters)

190953445220426c7565746f6f7468204c6f7720456e65726779 (Packet Data you want to be transmitted. Must be less than 62 characters, 31 byte max advertisement length per BLE spec.) In this case we are transmitting a packet with data: **SDR Bluetooth Low Energy**

1000 (Number of times you want the packet to be repeated.)

Its important to note all parameters must be delimited by a single space.

**Note:** Each line must follow this format for each packet.

010203040506 190953445220426c7565746f6f7468204c6f7720456e65726779 500
010203040507 190953445220426c7565746f6f7468204c6f7720456e65726779 500

# References:

See link for references on meaning of advertisement types: https://novelbits.io/bluetooth-low-energy-advertisements-part-1/