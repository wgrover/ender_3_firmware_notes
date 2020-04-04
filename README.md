# My notes from using a Mac to install Marlin firmware on the Creality Ender 3 3D printer

These are the steps I used to replace the default firmware with Marlin on Creality Ender 3 3D printers using a Mac and an Arduino Uno clone.

1. In the Arduino IDE, open **Examples / ArduinoISP**
2. Tools / Manage Libraries, install U8glib library
3. Preferences / Additional Boards Manager URLs, add https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json 
4. Tools / Boards Manager, install Sanguino
5. Connect Arduino Uno to computer with USB
6. Tools / Board select Arduino Uno
7. Tools / Programmer select “AVRISP mkII”
8. Tools / Port confirm port is selected
9. Upload the ArduinoISP sketch to board and leave connected.
10. Use jumper wires to connect Arduino to printer
11. Tools / Board select Sanguino
12. Tools / Processor select processor in printer
13. Tools / Programmer change to “Arduino as ISP”
14. Tools / Burn Bootloader.  Should get success message in Arduino IDE
15. Unplug jumper wires from printer and Arduino
16. Unplug Arduino from computer
17. Download Marlin at https://marlinfw.org/meta/download/
18. Replace files in Marlin directory with Creality Ender 3 files from Example Configurations
19. Connect printer to computer with USB
20. In the Arduino IDE, open Marlin / Marlin.ino
21. Tools / Board confirm still Sanguino
22. Tools / Programmer confirm Arduino as ISP
23. Tools / Port confirm USB connection to printer is selected
24. Upload the Marlin.ino sketch to printer.  Takes about a minute to complete
25. Disconnect USB cable and turn on printer.  Display likely says EEPROM Mismatch on bottom.
26. Connect printer to Raspberry Pi running Octoprint
27. In the Serial console send M502, then send M500
28. Power cycle printer 
