# PicoIO
An affordable, simple, and feature-rich PIU controller IO board

## What is this?
The PicoIO is an extension of the [PicoFX](https://github.com/dj505/PicoFX) that's meant for building larger hand controllers or buttonboards. It's possible to build dance pads too, but as this board lacks multiplexing and is made with 5V LED lighting in mind, it's not ideal. I may design a pad IO PCB in the future, though!

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
|10x BSS138 MOSFET|SOT23 Package|Required for button LEDs. Recommendation - buy extras.|[Link](https://www.lcsc.com/product-detail/MOSFETs_Yangzhou-Yangjie-Elec-Tech-BSS138_C400505.html)|$0.40|
|10x Resistors|10K Ohm, 0805 Surface Mount|Required for button LEDs. Recommendation - buy extras.|[Link](https://www.lcsc.com/product-detail/Chip-span-style-background-color-ff0-Resistor-span-Surface-Mount_Viking-Tech-AR05DTC1001_C416059.html)|$1|
|1x Pin Header|3 pins|**Optional, only used for debugging.**|N/A|N/A|

## Notes
Until I can write proper instructions, here are some things to keep in mind:
* LEDs require a separate power input. Pay close attention to the positive and negative polarity! It's marked on the PCB. **LEDs up to 12V are supported but the trace width only allows approximately 0.7A of current.** Don't overdo the LEDs!
* This kit should work equally well with 5V or 12V LEDs, but make sure you have a way to power the LEDs you pick. A reasonable number of 5V LEDs *can* be powered over USB, but pay attention to the total current draw! It's a good idea to just use a separate power supply or two USB cables for lighting.
* The legend at the top of the PCB describes the pin layout for the 10 main button connectors. Everything else has the pins labelled beside its respective connector.
* As of writing, **this design is untested and may have issues!** I will update this readme once I've confirmed everything works as it should. It *should* work okay, but this is currently a "use at your own risk" project until further notice.
