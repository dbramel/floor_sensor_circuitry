# FSR Floor Sensor Measurement POC

The schematic uses the installed KiCad library symbols for the passive parts and connectors: `Device:R`, `Device:C`, `Connector_Generic:Conn_02x08_Odd_Even` (J2), and `Connector_Generic:Conn_02x10_Odd_Even` (J1). Custom local symbols remain for ADS1256, ADG708, and REF5025.

J2 is the 2x8 FSR ribbon connector. Odd pins 1, 3, 5, 7, 9, 11, 13, and 15 share `VEXC_2V5`; even pins 2, 4, 6, 8, 10, 12, 14, and 16 carry `FSR0_NODE` through `FSR7_NODE`. Each sensor return connects to the corresponding ADS1256 AIN0–AIN7 input and U2 S1–S8.

U2 selects one sensor to `LOAD_NODE`. U3 selects a load resistor from 1 kΩ through 1 MΩ between `LOAD_NODE` and AGND. The mux address and enable signals are shared. U4 provides the 2.5 V reference for sensor excitation and ADS1256 VREFP; VREFN and AINCOM connect to AGND.

J1 is a generic 2x10 host connection for mux control, SPI, ADC control/clock/GPIO, +5VA, +3V3, and AGND. Assign footprints to match the actual build before PCB layout. See `BOM.csv` for the component summary.

Validation: KiCad CLI exported the schematic netlist successfully and ERC reported 0 errors and 0 warnings.
