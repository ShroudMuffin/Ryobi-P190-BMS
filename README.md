# Ryobi-P190-BMS
PCB reverse engineered schematics and backup data on Ryobi P190 BMS

This should be quite a complete schematic for the BMS PCB on Ryobi P190 battery pack.

For testing purposes only!

Research notes:

- The AFE IC (marked as 3705T) I believe (98% confidence) is an earlier variant of O2Micro's 3705 AFE chip. The internal LDO voltage is pretty much the only thing that differs with public datasheets (3v3 on datasheets, 2v5 on the BMS). I have requested the datasheet from the manufacturer, but I am not holding my breath.
- The schematics are based on rev. W of the board. There are some minor differences between revisions at a quick glance, like for instance R27 (near T1 terminal).
- Flash contents are different between revisions, I suspect it's due to microcode changes that reflect differences between resistor values across different revisions.
  -   Exceptions: Atleast Rev T and W share identical microcode
- Any issues, questions etc... let me know.
- Flash dump between a "firmware locked" and a working pack (identical revision) is identical. If there is a lock bit, it's not in the flash area of Attiny88.
  - Overwriting the EEPROM with an image from a working pack helps neither
- Pack reactivation after re-celling has been achieved with the instructions below:

  #Pack reactivation
  These instructions have enabled the reactivation of a P190 pack in cases where Ryobi chargers reject the pack (~20 red blinks on charger, then solid green).
  * Charge the cells manually to ~4.05V
  * Measure voltage from tool connector. If you measure around 20.3V you should be good to proceed. If not, check the troubleshooting section.
  * Attach the assembled pack to a Ryobi device (I use a drill, Ryobi R18DD3)
  * Pull the trigger. If the drill starts up, keep it running for several minutes. Measure the pack voltage every few minutes, until you drop to around 19.8V
  * If the drill did NOT start, check the troubleshooting section
  * Once the pack is around 19.8V, connect it to a charger. The charger should blink red a few times and then start charging the pack (blinking the green led)
 
#Troubleshooting

The pack voltage, measured from the tool connector positive and negative should equal the voltage measured between GND of first cell and positive of last cell. If there is a discrepancy, one or more of the PCB components might be broken. In one of the available tested packs the "raw" voltage between the pack cells was at 18.8V, but only 14.7V when measured at the connector. Research still ongoing, but it seems that one of the cell voltage sensing resistors (R4) is broken. By markings it's a 51ohm resistor, but measures only 25.8ohm. I will replace it with a resistor from a donor board to see if the pack returns to normal.
