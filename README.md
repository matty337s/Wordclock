# Wordclock
PCB hardware design for controller and LED strips for easy manufacture of a wordclock.

Initially based on the [Wordclock by t0mg](https://github.com/t0mg/wordclock), this project is designed to intergrate with the firmware from their project with slight modification. Check it out if you haven't already. 

The PCB panel and BOM contain all of the electronics to complete the clock. No LED strips or wiring required. 114 LEDs display the time to the minute using words for a unique, modern and functional clock.

This is a hobby for me, although it does take a lot of time and effort! If you like the project, please consider buying me a coffee by clicking [donate](https://www.paypal.com/donate/?hosted_button_id=GT76NKYH2WRKS). It is very much appreciated.

Kits and/or assembled and programmed PCBs may be avalible in the future. Let me know if this is something you would be interested in.

**This is a work in progress. Please check back regularly for updates!**

# Where to find files
KiCad files are located in the [Hardware](https://github.com/matty337s/Wordclock/tree/main/Hardware)  folder.

Gerber and assembly files are located in the [Production](https://github.com/matty337s/Wordclock/tree/main/Hardware)  folder. The assembly files are for JLCPCBs assembly service, and all components (excluding phototransistor and pin header) can be provided and assembled by them. I am not affiated with them in any way, and the assembly files can be easily modified for other manufacturers.

CAD files for laser cutting the clockface and internal structure are located in the [CAD](https://github.com/matty337s/Wordclock/tree/main/CAD)  folder. **WIP**

Firmware files for the ESP32 microcontroller are located in the [Firmware](https://github.com/matty337s/Wordclock/tree/main/Firmware)  folder. **WIP**

# Hardware
### Features
* 114 RGB LEDs make up the 11x10 display, showing 110 letters for every time in 5 minute intervals and four minute LEDs for minutes between these intervals.
* PCF8563T RTC (Real Time Clock) with 70mF supercapacitor backup keeps time setting during power loss. The designed 70mF capacitor should hold backup time for ~7 days.
* Photo-transistor for dimming the clock face in low-light. RoHS compliant transistor without cadmium as found in LDRs.
* WiFi connectivity using the ESP32. Allows endless possiblity of color, brightness, time setting, and many more. 
* Three programmable buttons for manual control without WiFi. Can be used as a dumb clock without any WiFi connection by setting the time and AM/PM indicator using the pushbuttons. The buttons are located on the front of the board for cheap and easy assembly, but footprints are provided on the rear if required. Soldering to the rear allows for easy access by pen from the back of the assembled clock.
* Powered by a USB-C receptacle. This port also allows serial data to the ESP32 for easy programming and debugging using a CH340C chip. USB power supply must be rated for about 2.5A.

![Schematic](https://github.com/matty337s/Wordclock/blob/main/Docs/Schematic-1.png "Schematic")

### PCB
The PCB is panelised with 10 identical boards for the LED strips and one controller board. Boards are assembled by breaking out of the panel and soldering board to board connectors together. This reduces the overal size and cost of the panel. Be sure to select `Different Design = 2` and `Panel by Customer` to avoid unexpected charges.
The LEDs are arranged in 16.6mm intervals. This is the same as 60LEDs per meter standard strips, which can be easily subsituted in if prefered. 
Footprints are included for a 100nF capacitor next to every LED, and a logic level translator chip (U104) to convert the 3.3V ESP32 output to 5V logic for the WS2812B LEDs. If you are using V5 LEDs [WS2812B-V5](http://www.world-semi.com/DownLoadFile/141), you can omit (DNP) all of the 100nF caps relating to the LEDs (C201-204 & C301-311) and U104. When populating these components, cut jumper JP101.

The assembled PCB has a maximum size of approximatly 190mm x 220mm. The panelised PCB, including edge rails, has a size of approximatly 212mm x 150mm. It is designed to fit in a 300mm x 300mm (12in x 12in) picture frame (I used [this](https://www.kmart.co.nz/product/photo-frame-12in-x-12in-black-42613893/) one here) but the outside cut line of the CAD files can be increased (or decreased slightly) to accomodate different size frames.

![Panelised PCB](https://github.com/matty337s/Wordclock/blob/main/Docs/Images/top.svg "Panelised PCB")

Image created using [TraceSpace](https://tracespace.io)

# CAD
The clockface and internal structure is very similar to the design by [t0mg](https://github.com/t0mg/wordclock), having added a cutout shape for the PCB, minute LEDs
and strain relief for the USB cable. 

It is comprimised of two or three layers of laser cut MDF for the structure and one sheet of laser engraved material for the face.

Layer 3.  The back layer contains the cutout for the PCB and LEDs. Ideally 3mm thick.
Layer 2.  The middle layer/s contain cutout for the USB cable and larger openings for the LEDs to diffuse and light each letter evenly. Ideally 6mm thick, or 2x 3mm. Two sheets of baking paper can be sandwiched between these layers to further enhance the diffusion and even lighting.
Layer 1.  The clockface can be created either using the excelent painted and engraved glass tutorial [here (again from t0mg)](https://github.com/t0mg/wordclock/blob/main/hardware/faceplate/README.md) or more simply and reliably but also more expensive by using a commercial solution called "reverse engravable laminate". 

It is the same concept as the painted glass but using a laminated clear and black plastic. I have had some fantastic results using it. IPI has their version [here](https://www.inoplas.com/laserables-reverse) and Trotec has their version [here](https://www.trotec-materials.com/laser-materials/plastic/trolase-reverse.html). I'm sure there are many others, let me know what you find works well.

I will hopefully get up some assembly guides and images in the coming months.

