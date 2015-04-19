# OpenBCI_32
Firmware modification of 32 Bit ChipKit OpenBCI Board
Last README update: April 18 2015

## Why use this firmware upgrade?
The default openBCI firmwave, as of writing, doesn't send the timestamp of when the EEG sample data was recorded. All timestamps for the channel data are calculated at the time they are recieved by the computer. This is problematic because accurate timestamps are crucially important for EEG signal processing. This update sends a milliseconds count over the auxiliary data array instead of accelerometer data.

The milliseconds count is produced by the millis() function, which stores the data as an unsinged long. This update breaks up the unsinged long in to a two element array of unsigned shorts (ChipKit stores values in BigEndian represetnation, so the MSB will be the rightmost byte). 

To best take advantage of this upgrade, consider using this python library: 
https://github.com/alxrsngrtn/OpenBCI_Python/tree/new_firmware

## How to install
To learn how to install this new firmware, please follow this tutorial, specifically the 32 bit section:
http://docs.openbci.com/tutorials/02-Upload_Code_to_OpenBCI_Board

