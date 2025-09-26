pio run -e mega2560
scp .pio/build/mega2560/firmware.hex octoprint2:.


backup
avrdude -p atmega2560 -c wiring -P /dev/ttyUSB0 -b 115200 -U flash:r:backup.hex:i
avrdude -p atmega2560 -c wiring -P /dev/ttyUSB0 -b 115200 -U eeprom:r:backup.eep:i

flash
avrdude -p atmega2560 -c wiring -P /dev/ttyUSB0 -b 115200 -D -U flash:w:./firmware.hex:i
