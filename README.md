# Isolated_USB-UART
A simple isolated USB-UART converter.

This design uses a CH340N USB-UART converter in combination with a B0505S-1W (Isolated DC-DC converter) and a CMT8022 (2x Unidirectional Data Isolator) to implement an isolated USB-UART link for 30 to 3M bps.

The schematic is still a prototype version (see notes!) and a one-off was assembled on a prototyping board. 

## DANGER!
Please do not trust this with high voltage circuits. Particularly as constructed, the 'isolation' is not reliable for any voltage capable of causing damage to humans. Use it only for extra low voltage applications, and read the below notes. Also, do your own research when your safety is involved!

## Notes:
1. Use a proper level shifter solution if you decided to add 3V3 support - I don't think the input levels of the CMT8022 support 3V3 logic. A normal MOSFET-based solution (or even simpler, just use an IC) will give you support down to 1V8 or even lower, and you won't have the high source impedance on the TX line that is otherwise imposed by the resistor divider
2. To take this a step above cheapo units you find online, add some proper input and output protection. TVS diodes, voltage clamping, preventing TX from being driven are all good ideas.
3. The rated isolation voltage for the unit I've constructed is (drumroll) ... a few handfuls of volts. Not that it doesn't work, because it definitely does, but assembled on a prototyping board it is hard to trust the isolation for actually high voltages. Much better would be designing a PCB and actually watching your creepage/clearances. As built, it is unsafe for high voltages and should be relied upon for safety isolation. You have been warned.
