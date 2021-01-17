## Notes

### STM32F04

Programmed via ST-Link (CLK, GND, DIO, NRST). Easy peasy!

External low-speed crystal oscillator (32.768kHz) enables real-time clock
module to function on VBAT when VDD is disconnected.

### MAX7129

Imagine the 64 LEDs are 8 7-segment LEDs.

Pin 1 DATA: Data loaded on CLK's rising edge.

Pin 12 NCS: Data is loaded into the shift register when this is low.

Pin 13 CLK.

Pins 2, 3, 5, 6, 7, 8, 10, and 11 (the DIG pins) are pulled high when
switched off.

Pins 14, 15, 16, 17, 20, 21, 22, and 22 (the SEG and DP pins) are pulled low when
switched off.

Note that peak current is set with an external resistor on pin 18 (R1). The
datasheet has a section on how to select the correct resistor value. Note that
you need to do this whether or not you use the `intensity` configuration,
because the MAX7219 will power up into a test mode with all LEDs blazing
*before* your configurations takes effect. You could probably burn out your
nice display by accident this way. So you can tweak the 10k resistor on R1, but
don't jump it.

### Other assorted components

MCP1802: LDO voltage regulator (5V to 3V3).

USBLC6: ESD protection on the USB interface.

