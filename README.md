# NP7400  

## Processor Card

### Docs
[g4pinout.pdf](/docs/g4pinout.pdf) contains the pinout of the connector used on
Power Mac G4 computers. Some important notes regarding the pinout:

* Pin assignments were determined by first sanding/filing down the processor
card (8 layers) from a 667MHz Digital Audio G4, and then using the card from
a 400MHz AGP Graphics G4, intact, albeit with the processor desoldered,
to verify that all the connections were correct.
* None of the cards involved in this process were dual-processor cards, so any
assignments unique to dual-processor systems have not been recorded.
* As written, the pin assignments are representative of how an MPC7450-series
MPU would be interfaced to the Power Mac motherboard -- for instance, only address
bits A4-A35 are present on the connector. Unlike earlier G4 processors, the 7450
features an extended 36-bit address bus, however, the four most significant bits
(A0-A3) are not used in Power Mac systems. Bearing in mind that PowerPC datasheet
conventions specify bit zero as the most-significant bit, a processor card design
featuring an earlier 7400/7410 MPU with a 32-bit address bus would need to have the
MPU's bit A31 connected to the pin labelled "A35" on the pinout, A30 connected to
"A34," and so on. The same applies to the DTI (Data Transaction Index) signals, of
which there are less on MPUs predating the 7450.

Regarding pins marked "special":
* Pins marked "R" are connected only to resistor straps, most of which go to ground.
I am still trying to understand the purpose of most of these. Some straps are
unpopulated on every board in my possession, whereas others vary between boards.
* SDA and SCL are connected only to the SPD I<sup>2</sup>C EEPROM on every board.
* Pins B2 and K30 are connected only to each other on every board. I assume this is
intended for the motherboard to sense whether or not the processor card is fully
seated.
* CKSTP# on the connector is directly connected to both CKSTP_IN# and CKSTP_OUT# on
the MPU.
* D63 is pulled to ground by a 1kΩ resistor on every board for some reason.
* The length of the SYSCLK track in particular is critical (tangentially, it appears
that on cards built for Power Macs witha 167MHz FSB, most track lengths become
tightly controlled).

## VRM

### Docs
[820-1152-A.pdf](/docs/820-1152-A.pdf) contains a poor schematic of the
original VRM board in the Power Mac G4 Cube, drawn only to verify whether or not
there was anything "unusual" about the OEM design (for all intents and purposes,
there isn't).
[np7400_VRM.pdf](/docs/np7400_VRM.pdf) contains the KiCad schematic of the
upgraded VRM board in PDF.

### Schematic and Board Layout
Schematic/layout files are provided as a complete KiCad project. As of the time
of this writing, schematic has been somewhat revised and does not reflect the
older revision of the layout included.

The newer schematic has not been thouroughly proofread. The older layout has not
been tested extensively and should not be used; there is considerable room for
improvement. Most planned changes are regarding optimization of routing, and ease
of assembly.


<img src="https://github.com/nickposting/NP7400/blob/main/assets/board_top.png" align="left" width="400">