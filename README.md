# TeensyCANLogger
A small open CAN logger using the Teensy 3.2, CAN, and and SD card. The system uses a low latency scheme to write blocks of memory from RAM to the SD card.
## Performance Test Results
SD card Write latency = 203 microseconds.  An extended CAN frame at 250kbps takes about 250 usec to transmit so a block write to the SD card happens as faster than a CAN frame is received.
## Prerequisites for Programming
Be sure to have these programs and libraries installed.
  * Arduino v1.6.8 (https://www.arduino.cc/en/Main/OldSoftwareReleases)
  * Teensyduino, which includes the FlexCAN library (https://www.pjrc.com/teensy/td_download.html)
  * SdFat (https://github.com/greiman/SdFat)

The chip select pin for the SD card is Arduino Pin 15.

The program is an adapted version of the LowLatencyLogger Example from the SdFat library. The other versions of Arduino and Teensyduino may work, but I haven't tested them.

##TODO
1. Add Autobaud detection so it's plug and play
2. Add 666k CAN timing
3. Add Realtime clock functionality
4. Automatic closing of files if CAN is not present
5. Adapt file size to the remaining space on the SD Card.
6. Write a binary data converter and visualizer.
7. Poll for On-Request Messages.
  
##Hardware

The hardware is designed to be as small as possible using through hole parts.

Schematics and a Bill of Materials is available.

Hardware additions include switches, LED, RTC crystal, and an RTC battery.

##Formatting the SD card
Using the SD formatter example with the correct SD card select pin results in the following:
```
This program can erase and/or format SD/SDHC cards.

Erase uses the card's fast flash erase command.
Flash erase sets all data to 0X00 for most cards
and 0XFF for a few vendor's cards.

Cards larger than 2 GB will be formatted FAT32 and
smaller cards will be formatted FAT16.

Warning, all data on the card will be erased.
Enter 'Y' to continue: Y

Options are:
E - erase the card and skip formatting.
F - erase and then format the card. (recommended)
Q - quick format the card without erase.

Enter option: F
Card Size: 59966 MB, (MB = 1,048,576 bytes)

Erasing
................................
................................
................................
................................
................................
................................
................................
................................
................................
................................
................................
................................
................................
................................
.....................
All data set to 0xff
Erase done

Formatting
Blocks/Cluster: 128
FAT32
............................................................
Format done
```
For FAT32, setting FILE_BLOCK_COUNT = 8388607; will give the maximum size.
