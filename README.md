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
| Components (per 1 PCB) | Specs | Notes | Recommended Purchase Link | Approximate Min. Cost (USD, per 5 PCBs) |
|------------------------|-------|-------|---------------------------|-----------------------------------------|
|1x Raspberry Pi Pico|Any, however WiFi/Bluetooth is currently unsupported|Can be soldered with pin headers or surface mounted.|[Link](https://www.digikey.ca/en/products/detail/raspberry-pi/SC0915/13624793)|$4|
|JST XH connectors|<ul><li>10x 4 Pin</li><li>1x 3 Pin</li><li>1x 6 Pin</li></ul>|Designed with vertical headers in mind, but horizontal ones may also work. Untested.|TBD|TBD|
|10x BSS138 MOSFET|SOT23 Package|Required for button LEDs. Recommendation - buy extras.|[Link](https://www.lcsc.com/product-detail/MOSFET_ON-Semicon_BSS138_ON-Semicon-ON-BSS138_C52895.html)|$0.85|
|10x Resistors|10K Ohm, 0805 Surface Mount|Required for button LEDs. Recommendation - buy extras.|[Link](https://www.lcsc.com/product-detail/Chip-span-style-background-color-ff0-Resistor-span-Surface-Mount_Viking-Tech-AR05DTC1001_C416059.html)|$1|
