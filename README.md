This is the source code for the J6502 emulator. Project files are not included.

License
=======

J6502 is licensed under the GNU Lesser General Public License, version 3. See `LICENSE.md` in this repository for the text of the license.

J6502 Emulator
=============

This is a Java-based cycle-accurate W65C02 emulator. It is believed to support every instruction that is valid on a real W65C02, including NOPs. However, the new CMOS instructions other than `WAI`, `STP`, and the Rockwell extensions are not exhaustively tested.

It's pretty much a Java translation of the core of my ET ARS emulator. The cycle accuracy has not yet been tested against the real hardware, but that is in the works; when that happens, both emulator cores will be updated if necessary.

To embed the emulator into your own project, you need only the classes in the
`src/name/bizna/j6502` directory.

In spite of the name, this currently only emulates the W65__C__02 (and its static cousin). It the future, it would be easy to generate a non-WDC 65C02 core, an NMOS 6502 core, or even more obscure variants such as a 2A03 core.

Klaus Dormann's 6502 Functional Tests
--------------------------------------

Also included in this repository is a _very_ hacky test program that loads and runs Klaus Dormann's 6502 Functional Test suite. It uses a slightly modified core, since the test suite relies on some behavior that changed between the 6502 and 65C02.

The test is based on a similar test for the ET ARS core, and incorporates the ROM image from that test. (The source code is not included, as the ROM program is trivial.)

If the test succeeds, it should take 77 759 251 cycles, and end up at `$3B1C`. (Assuming you're using the exact build of the test suite I am; if you build your own, consult the `lst` file for the address of the "success" trap jump.)

The test suite, unlike everything else in the repo, is copyright Klaus Dormann. The source code as well as a prebuilt binary are included. The command line given in the source file won't work with this test program; use `-s` instead of `-s2`.