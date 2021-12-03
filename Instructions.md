# Instructions
These instructions are used for creating the OC config and EFI

## Kexts
| Kext          | Comment       | Developer |
| ------------- | ------------- | --------- |
| [Lilu](https://github.com/acidanthera/Lilu) | Arbitrary kext and process patching on macOS | [Acidanthera](https://github.com/acidanthera)|
| [Whatevergreen](https://github.com/acidanthera/WhateverGreen) | Various patches necessary for certain ATI/AMD/Intel/Nvidia GPUs | [Acidanthera](https://github.com/acidanthera)|
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC) | SMC emulator layer | [Acidanthera](https://github.com/acidanthera)|
| [AppleALC](https://github.com/acidanthera/AppleALC) | Native macOS HD audio for not officially supported codecs | [Acidanthera](https://github.com/acidanthera)|
| [RTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X) | Driver for RTL8111/8168 family | [Mieze](https://github.com/Mieze) |
| [VoodooPS2Controller](https://github.com/RehabMan/OS-X-Voodoo-PS2-Controller) | PS2 keyboard, mouse and trackad driver. Used the Rehabman version for better trackpad buttons functioning | [RehabMan](https://github.com/RehabMan/)
| [FakeAR5B95](https://github.com/TheHackGuy/FakeAR5B95) | Needed to fake the Atheros AR5B95 card | [TheHackGuy](https://github.com/TheHackGuy) |

## ACPI
| ACPI | Comment |
| ---- | ------- |
| [SSDT-EC](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/AcpiSamples/Source/SSDT-EC.dsl) | Emebbed Controller |
| [SSDT-HPET](https://github.com/TheHackGuy/HP-DV6-3170sb/blob/main/SSDTTime.md) | Create with SSDTTime |
| [Brightness](https://www.insanelymac.com/forum/topic/287133-guide-backlight-brightness-for-intel-80860046-1st-gen-hd-gma-5700mhd/) | DSDT patch for the backlight. I didn't share my ssdt for this because the patch can be very different even for the same model |
