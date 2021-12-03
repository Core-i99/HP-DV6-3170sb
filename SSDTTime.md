# Instructions

## SSDTTime
- Download [SSDTTime](https://github.com/corpnewt/SSDTTime)

#### macOS
-   Run the SSDTTime.command
-   Give permissions for for SSDTTime to run in system preferences
#### Windows
-   Run SSDTTime.bat

## Dumping DSDT
I'm going to usb SSDTTime on WinPE for this. [There are differnet ways for dumping the DSDT](https://dortania.github.io/Getting-Started-With-ACPI/Manual/dump.html)

- Run the SSDTTime
- Pick option 8 to dump the DSDT

## FixHPET
FixHPET will help you to fix audio and the left USB ports for this device.

- Run SSDTTime
- Pick option 1 for FixPHET
- Drag & Drop the DSDT dump
- Choose option C
- Open the patches_OS.plist
- Copy the ACPI/Patch to your OC config
- Add SSDT-HPET to your config
- Copy SSDT-HPET to OC/ACPI

