# Genesis FeRAM Cart
A open Sega Genesis cartridge PCB with save feature

This projects uses a 27C322 4MB EPROM Chip and a FM1808 32KB FeRAM as save storage. It was developed in KiCAD and tested in real hardware.

In the actual state, this cartridge features:

-Support for 4MB of ROM
-Save support for all ROM sizes (Selection for <2MB/4MB by jumper)
-32kB of FeRAM for saving
-No need for battery for saving
-Rudimentary ROM bank switch (Permits multiple games on same ROM)

This project is possible thanks to TmEE (NESdev Forums, SRAM wiring schematics) and Rene Richard (db-electronics on GitHUB, KiCAD libs for the Genesis cart connector).
