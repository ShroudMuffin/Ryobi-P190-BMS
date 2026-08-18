# Ryobi-P190-BMS
PCB reverse engineered schematics and backup data on Ryobi P190 BMS

This should be quite a complete schematic for the BMS PCB on Ryobi P190 battery pack.

For testing purposes only!

Research notes:

- The AFE IC (marked as 3705T) I believe (98% confidence) is an earlier variant of O2Micro's 3705 AFE chip. The internal LDO voltage is pretty much the only thing that differs with public datasheets (3v3 on datasheets, 2v5 on the BMS). I have requested the datasheet from the manufacturer, but I am not holding my breath.
- The schematics are based on rev. W of the board. There are some minor differences between revisions at a quick glance, like for instance R27 (near T1 terminal).
- Flash contents are different between revisions, I suspect it's due to microcode changes that reflect differences between resistor values across different revisions.
- Any issues, questions etc... let me know.
