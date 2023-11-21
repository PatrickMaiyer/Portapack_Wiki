As of 10/31/23, the previous BLE implementation has been updated, and improved to correct some of the issues in the previous BTLE app.

This BLE app has several features which I will highlight in a brief overview.

# Main Menu:

This is the main view which provides the user with incoming packet entries captured by the BLE Scanning.

1. The BLE app upon entry will scan for BLE advertisement packets, and report them on the screen. The **Channel** knob can be used to select which advertisement channel to listen on. There is an Auto feature which will switch channels upon receiving a new packet. (Randomized from 37-39).
2. Once found the user can then select an individual MAC Address entry to pull up a more detailed view of the captured data packet.
3. The **Sort Knob** will sort the list of MAC indices by either Ascending MAC Address, dB, or by most recently updated entry.
4. The **Filter** button allows the user to filter based on the hex data of each packet. It also allows for filtering based on the ASCII name of the device (if found). More on that below.
5. The **Name** toggle allows the user to toggle off and on name display, if there is a name associated with the device. Not all devices have a name string. This name string is being parse from the Shortened and Complete Local Name packet type. See BLE Spec for information on packet types.
6. The **Clear** button allows the user to clear entries as they fill up the screen.
7. The **Export CSV** file allows the user to export the current list of packet entries into a csv style file. Upon resaving the file, the file will update the existing entries with new data, as well as append new entries to the existing file.
8. The **Tx** button allows the user to switch to the BLE Tx app. See BLETX for more information.

# Packet Detail Menu:

This menu is a more single detailed view on a specific entry selected by the Main Menu. More specific packet information is laid out here such as:

MAC Address, Packet Type, and Data

1. The **Send** button immediately moves the user to the BLE TX app, and allows the user to transmit the selected packet data.
2. The **Save** button allows the user to save a packet in the format used by the BLE TX app.
3. The **Done** button brings the user back to the Main Menu.

Below short example on using the BLE Rx App.

https://vimeo.com/886881206?share=copy

References:
https://www.bluetooth.com/wp-content/uploads/Files/Specification/Assigned_Numbers.pdf?id=3
