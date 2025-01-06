# High-Power Pinecil LED Ring

Inspired by [Herushan's original Pinecil LED ring](https://github.com/Herushan/Pinecil_LED_Ring). See the [full project documentation here](https://blockworker.de/pinecil-led-ring-901/).

This version is designed for three ~0.2W LEDs, resulting in almost 100 lumens of light output.

Features a dedicated LED driver module (to be installed inside the Pinecil case), the LED ring itself, as well as PWM dimming using a [modified version of IronOS](https://github.com/BlockWorker/IronOS-LED).

<center>
<img src="https://github.com/user-attachments/assets/741b7bae-82a1-4358-b2cb-69f038d4e8c2" width="330">
<img src="https://github.com/user-attachments/assets/e495e39d-e188-4827-988e-97a5f990947d" width="330">
<img src="https://github.com/user-attachments/assets/2a7c52b0-cead-4afd-becd-9909a21ef621" width="330">
</center>

## Build one yourself

Of course, feel free to build your own LED ring based on the designs in this repository. Use them as they are, or modify them for your needs if you feel like it - either way, at your own risk.

The posts on my website offer a more detailed description of the project and [build process that you can follow along with](https://blockworker.de/pinecil-led-ring-build-922/).

The PCB designs are based on JLCPCB's design rules, so adjust them accordingly if you're using a different PCB service. The LED ring PCB is a 1.6mm aluminium core board, and the driver PCB is a 0.8mm 2-layer FR4 board.

Here is a table of the required components, with example parts and Mouser links:

| Reference | Description | Example Part |
| - | - | - |
| U1 | LM3407 LED Driver | [Texas Instruments LM3407MY](https://mou.sr/4eeUAvk) |
| D1 | Schottky Diode, >30V, SOD-323 | [Panjit SS0840WS](https://mou.sr/4a6Dr5q) |
| L1 | Inductor, 150µH, SMD 4 x 4 mm | [Taiyo Yuden NRS4018T151MDGJ](https://mou.sr/3PJLYSF) |
| C1 | Capacitor, 4.7µF 35V, SMD 0805 | [Murata GRM21BZ7YA475KE15](https://mou.sr/3Wa5xai) |
| C2 | Capacitor, 4.7µF 50V, SMD 1206 | [Murata GRM31CR71H475KA12](https://mou.sr/4gZpf0g) |
| C3 | Capacitor, 1µF >6.3V, SMD 0603 | [Samsung CL10B105KA8NNN](https://mou.sr/40pRb75) |
| R1 | Resistor, 4.7kΩ, SMD 0603 | [Bourns CR0603-FX-4701ELF](https://mou.sr/423VuaA) |
| R2 | Resistor, 3.09Ω, SMD 0603 | [Vishay CRCW06033R09FKEA](https://mou.sr/4fNpef5) |
| R3 | Resistor, 1kΩ, SMD 0603 | [Bourns CR0603-FX-1001ELF](https://mou.sr/3VS87BY) |
| R4 | Resistor, 40.2kΩ, SMD 0603 | [Bourns CR0603-FX-4022ELF](https://mou.sr/4h0pGrc) |
| (Ring) D1-D3 | MP-3030-120H LEDs | [Luminus MP-3030-120H-40-90](https://mou.sr/40ogQy9) |

Aside from these parts, you'll need some thin wires, a second soldering iron, and ideally a small PCB hot plate for reflow soldering (especially for soldering the LEDs to the aluminium-core ring PCB). The LM3407 chip also needs either a hot plate or a hot air gun to effectively solder its bottom thermal pad.

Equivalent replacements to these parts should work fine as well - though depending on your choice, you may need to change the PCB component footprints accordingly.

There are many LED options available in the [MP-3030-120H series](https://www.mouser.de/c/?q=mp-3030-120h), depending on your preferences. I went with 4000K colour temperature and CRI 90, for high-quality neutral white light.
Colour temperature options range from very warm 2200K to cold 6500K, and if you want some more brightness at the cost of "light quality", there are brighter CRI 80 variants available.

Of course, there are many other LED options out there that will work, though PCB adjustments may be needed for them. The design targets single-LED chips (around 3V per chip) and a current of 65mA.

If you'd like to use the LED dimming feature, you need to flash my [modified IronOS firmware](https://github.com/BlockWorker/IronOS-LED) onto your Pinecil and connect the "DIM" pad to the Pinecil PCB as shown on my website.
Alternatively, you can just force the ring to 100% brightness all the time, by connecting a jumper wire between the "DIM" pad and the "TP1" test point on the back side of the driver.

The driver circuit can be modified for up to 350mA LED current (see notes in the schematic and the [LM3407 datasheet](https://www.ti.com/lit/ds/symlink/lm3407.pdf)), but I haven't tested higher currents, and LED cooling may become a problem at higher power.

If you'd like to make the ring removable ([as seen on my website](https://blockworker.de/pinecil-led-ring-build-922/)), you'll need a very small 2-pin connector, e.g., the [Amphenol Minitek 0.8mm connector I used](https://www.amphenol-cs.com/product-series/minitek-0-80mm-wtb.html#). The header can be wired to the ring and glued onto its back using some epoxy. However, crimping the wire end of such a small connector is challenging - [I've made a post about my process for it here](https://blockworker.de/modular-audio-appendix-minitek-0-8mm-connectors-2055/). I don't recommend this for beginners though.

For questions or anything else, you can find me on the official PINE64 discord server (@blockworker).
