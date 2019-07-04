# DIY-Thermocam Firmware #

GNU General Public License v3.0, copyright by Max Ritter

----------


**THIS GUIDE IS ONLY REQUIRED, IF YOU WANT TO MAKE CHANGES TO THE FIRMWARE ON YOUR OWN!**

If you just want to flash the newest version of the firmware to your device, follow the Firmware Update Guide in the Document section and use one of the pre-compiled versions (*.hex) from **[here](https://github.com/maxritter/diythermocam_firmware/releases)**.

----------

You can find **older firmware versions prior to 2.46** here: **[http://diy-thermocam.bplaced.net/Firmware/](http://diy-thermocam.bplaced.net/Firmware/)**

----------

This guide should work on **all common operating systems** (**Windows, Linux & Mac OSX**).

**Download** and **install** the following programs:

1. **[Arduino 1.8.9+](https://www.arduino.cc/en/Main/Software)** (install to a short path like C:\Dev\Arduino)
2. **[Teensyduino 1.44+](https://www.pjrc.com/teensy/td_download.html)**
3. **[Sloeber Eclipse](https://github.com/Sloeber/arduino-eclipse-plugin/releases/tag/4_2)** (linked version 4.2 works)

Then **clone this repo** to a path without empty spaces (f. ex. "C:\Sandbox\DIYThermocam_Firmware\") with `git clone https://github.com/maxritter/diythermocam_firmware.git`.

Now **start Sloeber Eclipse**.

Go to Windows -> Preferences -> Arduino and **set the Private Library Path** to the folder of your Arduino library installation (f. ex. "C:\Program Files (x86)\Arduino\libraries"). Also **set the Private Hardware Path** to the path of your Arduino hardware installation (f. ex. "C:\Program Files (x86)\Arduino\hardware").

**Import the project** with File -> Import -> General -> Existing Projects into Workspace, select the root directory of this repo and click Finish.

**Update the project properties** by right clicking the project and changing the following:
* Under **Arduino**:
    * Set Board to "Teensy 3.6"
    * Set Keyboard Layout to "US International"
    * Set Optimize to "Debug"
    * Set CPU Speed to "240 MHz (Overclock)"
    * Set USB Type to "Serial"
* Under **C/C++ Build** -> **Environment**:
    * Update each environment variable to match your installation
* Under **C/C++ General** -> **Paths and Symbols**:
    * Update each entry to match your installation under **Assembly**, **GNU C** and **GNU C++**.

Now you should be able to build the project with Arduino -> Verify and upload it to the Thermocam with Arduino -> Upload Sketch. Have fun!

----------

If you are using the DIY-Thermocam V1, you need to unlock the overclock option first. Go to the Teensy avr folder (f. ex. "C:\Program Files (x86)\Arduino\hardware\teensy\avr\"), open the file "boards.txt" and remove the hash (#) symbol in front of this line: "teensy31.menu.speed.144=144 MHz (overclock)", then save the file. The default build settings are made for the DIY-Thermocam V2. If you want to build for the DIY-Thermocam V1, right click on the project and select Properties -> Arduino. For the board, select Teensy 3.2 / 3.1 and for the CPU speed 144 MHz.
