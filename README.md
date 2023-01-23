# PicoIO
An affordable, simple, and feature-rich PIU controller IO board

## What is this?
The PicoIO is an extension of the [PicoFX](https://github.com/dj505/PicoFX) that's meant for building larger hand controllers or buttonboards. It's possible to build dance pads too, but as this board lacks multiplexing and is made with 5V LED lighting in mind, it's not ideal. I may design a pad IO PCB in the future, though!

**If you're not comfortable with soldering surface mount components,** there is a second board revision in the "PicoFX-THT" directory (gerbers included) that only uses through-hole components. Check the components list to see which parts are required for which PCB!

## Use cases
* Hand controller (10 buttons, 12 if you include test/service)
* Arcade buttonboard, for machines that don't already have a buttonboard (TODO - add support in firmware)
* Simple dance pad (with limitations)
    * No multiplexing support; all sensors will need to be combined into one signal
    * Limited maximum power supply for LEDs; only designed for 10-20 LEDs total, with a maximum of ~0.7A draw
        * This can be bypassed/remedied by using the expansion IO to control external LEDs with their own external power supply and some MOSFETs. I encourage you to be creative!
* Upgrade existing hand controllers, in case of broken/defective/underperforming IO

## Components
| Components (per 1 PCB) | Specs | Notes | Recommended Purchase Link | Approximate Min. Cost of Components |
|------------------------|-------|-------|---------------------------|-----------------------------------------|
|1x Raspberry Pi Pico|Any, however WiFi/Bluetooth is currently unsupported|Can be soldered with pin headers or surface mounted.|[Link](https://www.digikey.ca/en/products/detail/raspberry-pi/SC0915/13624793)|$4|
|JST XH connectors|<ul><li>10x 4 Pin</li><li>1x 6 Pin</li><li>1x 3 Pin</li><li>1x 2 Pin</li></ul>|**2.5mm pin pitch.** Designed with vertical headers in mind. Horizontal ones may work but are untested. Recommended purchase link has a minimum order number of 50-100 depending on the connector, but they're still super cheap.|<ul><li>[2 Pin](https://www.lcsc.com/product-detail/Wire-To-Board-Wire-To-Wire-Connector_HCTL-XH-2A_C3012117.html)</li><li>[3 Pin](https://www.lcsc.com/product-detail/Wire-To-Board-Wire-To-Wire-Connector_HCTL-XH-3A_C3012118.html)</li><li>[4 Pin](https://www.lcsc.com/product-detail/Wire-To-Board-Wire-To-Wire-Connector_HCTL-XH-4A_C2908602.html)</li><li>[6 Pin](https://www.lcsc.com/product-detail/Wire-To-Board-Wire-To-Wire-Connector_HCTL-XH-6A_C2908604.html)</li></ul>|$2.50|
|10x BSS138 MOSFET \*|SOT23 Package|Required for button LEDs. Recommendation - buy extras.|[Link](https://www.lcsc.com/product-detail/MOSFETs_Yangzhou-Yangjie-Elec-Tech-BSS138_C400505.html)|$0.40|
|10x 2N7002 MOSFET \*\*|TO-92 Package|Required for button LEDs.|[Link](https://www.lcsc.com/product-detail/MOSFETs_onsemi-2N7002_C124475.html)|$0.40|
|10x Resistors \*|10k Ohm, 0805 Surface Mount|Required for button LEDs. Recommendation - buy extras.|[Link](https://www.lcsc.com/product-detail/Chip-span-style-background-color-ff0-Resistor-span-Surface-Mount_Viking-Tech-AR05DTC1001_C416059.html)|$1|
|10x Resistors \*\*|10k Ohm, 1/4W Through Hole|Required for button LEDs.|[Link](https://www.lcsc.com/product-detail/Chip-span-style-background-color-ff0-Resistor-span-Surface-Mount_Viking-Tech-AR05DTC1001_C416059.html)|$1|
|1x Pin Header \*|3 pins|**Optional, only used for debugging.**|N/A|N/A|

\* Surface mount board
\*\* Through-hole board

# Instructions
Assembly is dead simple. The surface mount PCB are as follows:  
1. Solder the surface mount components.
    * Start with the BSS138 MOSFETs as they're the smallest. Use tweezers to hold them in place, tack down *one* pin with a bit of solder. It's okay if it's messy, you can clean it up after. Once it's tacked in place, solder the remaining 2 pins, then go back and clean up the first one by reflowing it after adding a bit of flux.
        * These can only go on one way, as long as they're not upside down. Make sure the pins are pointing down, not up.
    * Once done, move onto the resistors. Polarity doesn't matter here either. As with the MOSFETs, line them up with tweezers, tack down one side, solder the other side, then clean up the first side with some flux and reflowing. Easy! It's okay if they look messy, they should work just fine as long as the connection is solid.
2. Solder the Raspberry Pi Pico.
    * Gently hold it in place, tack in one or two corners to keep it held down where you want it, and solder all the pins.
    * This can be done with or without pin headers, whichever you're more comfortable with!
3. Solder the JST headers in place.
    * Keep the side with the holes facing forward, as per the printing on the silkscreen. Hold them against the PCB while soldering to make sure they're nice and even. Don't add too much solder; your joints should look like concave cones or tents, not spheres. These don't have to be perfect as long as they're solid!
4. Flash the firmware.
    * Hold down the BOOTSEL button while plugging the PicoIO into your PC. It should show up as a storage device.
    * Drag and drop your preferred .uf2 firmware file from the [releases page](https://github.com/dj505/PicoIO/releases) onto the drive.
    * It should disconnect itself after a short moment. You're good to go!

And here are the steps for the through-hole PCB:  
1. Solder the 2N7001 MOSFETs.
    * The solder points are rather clost together, but if you use flux and don't go overboard on solder, you won't have any issues.
    * Make sure they're oriented according to the silkscreen!
2. Solder the resistors.
    * These can technically go on either side of the board. If you're mounting the PCB directly against a flat surface, solder them on the top, overlapping the arrow icons. Otherwise, solder them on the bottom.
3. Solder the Raspberry Pi Pico.
    * It's easiest to solder this before the JST connectors so they don't get in the way.
    * You can choose to surface mount it or use pin headers - both work just as well.
4. Solder the JST headers in place.
    * Keep the side with the holes facing forward, as per the printing on the silkscreen. Hold them against the PCB while soldering to make sure they're nice and even. Don't add too much solder; your joints should look like concave cones or tents, not spheres. These don't have to be perfect as long as they're solid!
5. Flash the firmware.
    * Hold down the BOOTSEL button while plugging the PicoIO into your PC. It should show up as a storage device.
    * Drag and drop your preferred .uf2 firmware file from the [releases page](https://github.com/dj505/PicoIO/releases) onto the drive.
    * It should disconnect itself after a short moment. You're good to go!

## Notes
Here are some things to keep in mind:
* LEDs require a separate power input and aren't powered by the Pico itself. Pay close attention to the positive and negative polarity! It's marked on the PCB. **LEDs up to 12V are supported but the trace width only allows approximately 0.7A of current.** Don't overdo the LEDs!
    * If you're using a **reasonable number of 5V LEDs (under 500mA total draw for the entire build),** you can jump the 5V and GND pins on the 6 pin expansion port to the LED power input and power the LEDs through USB directly. **Do not** attempt to power 12V LEDs or anything requiring above 500mA this way.
* **If your LEDs don't have current limiting resistors built in, please make sure you add some!** The resistors on this PCB are just for ensuring the MOSFETs work properly.
* This kit should work equally well with 5V or 12V LEDs, but make sure you have a way to power the LEDs you pick. A reasonable number of 5V LEDs *can* be powered over USB, but pay attention to the total current draw and don't surpass the USB spec! Doing so is not recommended and would be done at your own risk. It's a good idea to just use a separate power supply or two USB cables for extra lighting.
* The legend at the top of the PCB describes the pin layout for the 10 main 4 pin button connectors. Everything else has the pins labelled beside its respective connector.
* Each MOSFET can handle up to 2A bursts if using the recommended parts, ***but*** that doesn't mean you should max them out. The trace width used allows for approximately 1.6A of total current draw which should be more than enough to light up each button. There is a second 5V pin broken out from the Pico's USB line that may be additionally used for a small number of WS2812B or similar LEDs.
* Up to 12V lighting has been tested and works without a hitch. Once again, pay close attention to polarity!
