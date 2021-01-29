# Deploy hex file on your hictop prusa i3 version 03 with auto bed leveling

You need to have arduino studio installed.

1. connct your printer to USB and Open command line of you os (cmd), or any terminal.
2. Go to 'avr' folder in your arduino installation folder, e.g. cd "c:\Program Files (x86)\Arduino\hardware\tools\avr"
3. Copy the following command and replace the <file_path> with your hex file path and <printer_port> with your printer port:
    bin\avrdude.exe -Cetc\avrdude.conf -v -patmega2560 -cwiring -P<printer_port> -b115200 -D -Uflash:w:<file_path>:i
    The result of the previous step should look somewhat like this:

    bin\avrdude.exe -Cetc\avrdude.conf -v -patmega2560 -cwiring -PCOM3 -b115200 -D -Uflash:w:C:\allProjects\firmware.hex:i

    **if your file file path contains whitespace, the command might fails in some operating systems. in that case, move the hex file to a path without spaces (e.g. c:) and update the command.

    Run the command you just edited.
5. Thats it, your firmware should be changed.
6. Run basic tests to verify your steppers and endstops are not inverted. you can do so, by moving each axis using your slicer, the lcd panel or by sending gcode commands. don't run 'Auto Home' before you verify those tests.
if any axis/endstop is inverted, update the configuration.h file and rebuild the hex file.
7. Dont forget to calibrate your printer.
7. Enjoy printing :)
