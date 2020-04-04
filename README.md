# My notes from using a Mac to install Marlin firmware on the Creality Ender 3 3D printer

These are the steps I use to replace the default firmware with [Marlin](https://marlinfw.org) on (Creality Ender 3 3D printers)[https://www.creality3d.shop/products/creality3d-ender-3-pro-high-precision-3d-printer] using a Mac, an Arduino Uno clone (for installing the firmware), and a [Raspberry Pi](http://raspberrypi.org) running [OctoPrint](https://octoprint.org) (not strictly necessary for the firmware instalalation, but I use Octoprint on the Pi to control the printer).

1. In the [Arduino IDE](https://www.arduino.cc/en/main/software) (*not* the "web editor"), open **Examples / ArduinoISP**.
2. Under **Tools / Manage Libraries**, install **U8glib** library.
3. Under **Preferences / Additional Boards Manager URLs**, add https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json
4. Under **Tools / Boards Manager**, install **Sanguino**.
5. Connect Arduino Uno to computer with USB cable.
6. Under **Tools / Board** select **Arduino Uno**.
7. Under **Tools / Programmer** select **AVRISP mkII**.
8. Under **Tools / Port** confirm that the port connected to the Arduino is selected.
9. Upload the ArduinoISP sketch to board.  When finished, leave the Arduino connected.
10. Use jumper wires to connect the Arduino to printer.
11. Under **Tools / Board** select **Sanguino**.
12. Under **Tools / Processor** select the processor used by the printer.  My two Ender 3s use **ATmega1284P (16 MHz)**.
13. Under **Tools / Programmer** change to **Arduino as ISP**.
14. Select **Tools / Burn Bootloader**.  After a few seconds you should see a success message in Arduino IDE.
15. Disconnect jumper wires from printer and Arduino.
16. Disconnect Arduino USB cable from computer.
17. Download Marlin at https://marlinfw.org/meta/download/.
17. Download Marlin Example Configurations at https://github.com/MarlinFirmware/Configurations/archive/release-2.0.5.zip.
18. Replace files in Marlin directory with Creality Ender 3 files from Example Configurations.
19. Connect printer to computer with USB cable.
20. In the Arduino IDE, open **Marlin / Marlin.ino**.
21. Under **Tools / Board** confirm that **Sanguino** is still selected.
22. Under **Tools / Programmer** confirm **Arduino as ISP**.
23. Under **Tools / Port** select the USB connection to the printer.
24. In the Arduino IDE, upload the **Marlin.ino** sketch to printer.  This can take a couple minutes to finish.
25. Disconnect the USB cable and turn on the printer.  The LCD screen likely says **EEPROM Mismatch**.
26. Connect printer to Raspberry Pi running Octoprint.
27. In Octoprint's Terminal, send **M502**, then send **M500**.
28. Power cycle printer.  The EEPROM error should be gone.
