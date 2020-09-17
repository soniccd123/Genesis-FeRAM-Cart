# Genesis FeRAM Cart
A open Sega Genesis cartridge PCB with save feature

This projects uses a 27C322 4MB EPROM Chip and a FM1808 32KB FeRAM as save storage. It was developed in KiCAD and tested in real hardware.

In the actual state, this cartridge features:

- ROM Support for up to 4MB
- Save support for all ROM sizes (Selection for <2MB/4MB by jumper)
- 32KB of FeRAM for saving
- No need for battery for saving
- Rudimentary ROM bank switch (Permits multiple games on same ROM)

This project is possible thanks to TmEE (NESdev Forums, SRAM wiring schematics) and Rene Richard (db-electronics on GitHUB, KiCAD libs for the Genesis cart connector).

# Component List:
- U1 74HC74;
- U2 FM1808B;
- U3 74HC139 (or LS);
- U4 27C322 (May use other 27CXX memories with some minor modifications);
- R1, R2, R3, R4 1K Resistors;
- SW1 4 channel DIP Switch;
- C1, C2, C3 10nF Capacitors;

# How to use:
Bank Switching: The user may write multiple roms to the same EPROM, the DIP switch controls which area of the EPROM is read by the Genesis/Mega Drive; The minimum bank size is 256KB. Each of the switches connect a memory address line between the system and the EPROM: when the switch is on, the respective address line is controlled by the Sega Genesis; When off, the EPROM adress line is pulled-up and cut from Genesis control. the address lines are A20, A19, A18, A17 (considering LSB as A0). To select the desired bank, turn the switches on and off acordingly to the begining address that the ROM occupies in the EPROM.

Examples:

ROM_x begin at 0x100000 -> Switch just A19 off (pull-up);           
ROM_y begin at 0x180000 -> Switch A19 and A18 off;

This technique may not be compatible with save supporting Genesis software.

How to make multirom file: Just use the CMD command "copy /b rom_x.bin + rom_y.bin + rom_z.bin rom_result.bin" to join them to one file. One may join how many ROMs he wants to, just be shure that the result file is smaller than the total size of the EPROM and that the ROMs fit correctly to each desired bank to make software switching possible.

JP1 jumper: This jumper is the result of some tests with varied sized Save RAM suporting software. This jumper is necessary for software bigger or smaller than 2MB to correctly save and detect the FeRAM. For software bigger than 2M, one must connect (with solder blob, 0K resistor, etc) the >2MB part of the jumper; for smaller or equal to 2MB software, one must do the same with the <2MB part of the jumper.

Other than that, just write to your EPROM and happy playing!
