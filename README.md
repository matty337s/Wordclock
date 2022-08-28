# Wordclock
PCB controller and strip design for easy manufacture of the wordclock.
Initially based on the [Wordclock by t0mg](https://github.com/t0mg/wordclock), this project is designed to intergrate with the firmware from their project with slight modification. Check it out if you haven't already. 

The PCB panel and BOM contain all of the electronics to complete the clock. No LED strips or wiring required. 114 LEDs display the time to the minute using words for a unique, modern and functional clock.

**This is a work in progress. Please check back regularly for updates!**

# Hardware
### Where to find files
KiCad files are located in the [Hardware](https://github.com/matty337s/Wordclock/tree/main/Hardware)  folder.

Gerber and assembly files are located in the [Production](https://github.com/matty337s/Wordclock/tree/main/Hardware)  folder. The assembly files are for JLCPCBs assembly service, and all components (excluding phototransistor and pin header) can be provided and assembled by them. I am not affiated with them in any way, and the assembly files can be easily modified for other manufacturers.

### Features
* 114 RGB LEDs make up the 11x10 display, showing 110 letters for every time in 5 minute intervals and four minute LEDs for minutes between these intervals.
* PCF8563T RTC (Real Time Clock) with 70mF supercapacitor backup keeps time setting during power loss. The designed 70mF capacitor should hold backup time for ~7 days.
* Photo-transistor for dimming the clock face in low-light. RoHS compliant transistor without cadmium as found in LDRs.
* WiFi connectivity using the ESP32. Allows endless possiblity of color, brightness, time setting, and many more. 
* Three programmable buttons for manual control without WiFi. Can be used as a dumb clock without any WiFi connection by setting the time and AM/PM indicator using the pushbuttons. The buttons are located on the front of the board for cheap and easy assembly, but footprints are provided on the rear if required. Soldering to the rear allows for easy access by pen from the back of the assembled clock.
* Powered by a USB-C receptacle. This port also allows serial data to the ESP32 for easy programming and debugging using a CH340C chip.

### PCB
The PCB is panelised with 10 identical boards for the LED strips and one controller board. Boards are assembled by breaking out of the panel and soldering board to board connectors together. This reduces the overal size and cost of the panel. Be sure to select `Different Design = 2` and `Panel by Customer` to avoid unexpected charges.
The LEDs are arranged in 16.6mm intervals. This is the same as 60LEDs per meter standard strips, which can be easily subsituted in if prefered. 
Footprints are included for a 100nF capacitor next to every LED, and a logic level translator chip (U104) to convert the 3.3V ESP32 output to 5V logic for the WS2812B LEDs. If you are using V5 LEDs (WS2812B-V5), you can omit (DNP) all of the 100nF caps relating to the LEDs (C201-204 & C301-311) and U104. When populating these components, cut jumper JP101.

![Panelised PCB](https://github.com/matty337s/Wordclock/blob/main/Docs/Images/top.svg "Panelised PCB")

Image created using [TraceSpace](https://tracespace.io)
