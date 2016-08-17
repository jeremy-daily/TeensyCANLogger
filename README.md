# TeensyCANLogger
A small open CAN logger using the Teensy 3.2, CAN, and and SD card. The system uses a low latency scheme to write blocks of memory from RAM to the SD card.
## Performance Test Results
SD card Write latency = 203 microseconds.  An extended CAN frame at 250kbps takes about 250 usec to transmit so a block write to the SD card happens as faster than a CAN frame is received.
## Prerequisites for Programming
Be sure to have these programs and libraries installed.
  * Arduino v1.6.8 (https://www.arduino.cc/en/Main/OldSoftwareReleases)
  * Teensyduino, which includes the FlexCAN library (https://www.pjrc.com/teensy/td_download.html)
  * SdFat (https://github.com/greiman/SdFat)
The program is an adapted version of the LowLatencyLogger Example from the SdFat library. The other versions of Arduino and Teensyduino may work, but I haven't tested them.

##TODO
1. Add Autobaud detection so it's plug and play
2. Add 666k CAN timing
3. Add Realtime clock functionality
4. Automatic closing of files if CAN is not present
5. Adapt file size to the remaining space on teh SD Card.
6. Write a binary data converter and visualizer.
7. Poll for On-Request Messages.
  
