# Instructions
These instructions are used for creating the OC config and EFI

## Files
### Kexts
| Kext          | Comment       | Developer |
| ------------- | ------------- | --------- |
| [Lilu](https://github.com/acidanthera/Lilu) | Arbitrary kext and process patching on macOS | [Acidanthera](https://github.com/acidanthera)|
| [Whatevergreen](https://github.com/acidanthera/WhateverGreen) | Various patches necessary for certain ATI/AMD/Intel/Nvidia GPUs | [Acidanthera](https://github.com/acidanthera)|
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC) | SMC emulator layer | [Acidanthera](https://github.com/acidanthera)|
| [AppleALC](https://github.com/acidanthera/AppleALC) | Native macOS HD audio for not officially supported codecs | [Acidanthera](https://github.com/acidanthera)|
| [RTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X) | Driver for RTL8111/8168 family | [Mieze](https://github.com/Mieze) |
| [VoodooPS2Controller](https://github.com/RehabMan/OS-X-Voodoo-PS2-Controller) | PS2 keyboard, mouse and trackad driver. Used the Rehabman version for better trackpad buttons functioning | [RehabMan](https://github.com/RehabMan/)
| [FakeAR5B95](https://github.com/TheHackGuy/FakeAR5B95) | Needed to fake the Atheros AR5B95 card | [TheHackGuy](https://github.com/TheHackGuy) |

### ACPI
| ACPI | Comment |
| ---- | ------- |
| [SSDT-EC](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/AcpiSamples/Source/SSDT-EC.dsl) | Emebbed Controller |
| [SSDT-HPET](https://github.com/TheHackGuy/HP-DV6-3170sb/blob/main/SSDTTime.md) | Create with SSDTTime |
| [Brightness](https://www.insanelymac.com/forum/topic/287133-guide-backlight-brightness-for-intel-80860046-1st-gen-hd-gma-5700mhd/) | DSDT patch for the backlight. I didn't share my ssdt for this because the patch can be very different for different devices. |

## Config
First do an OC-Clean-Snapshot with Propertree
#### ACPI
##### Patch 
- Add the patches from [FixHPET](https://github.com/TheHackGuy/HP-DV6-3170sb/blob/main/SSDTTime.md) here.
#### Booter 
##### Quirks
| Quirk | Enabled |
| ------ | ------- |
| AvoidRuntimeDefrag | False |
| EnableSafeModeSlide | False |
| EnableWriteUnprotector | False |
| ProvideCustomSlide | False |
| RebuildAppleMemoryMap | False |
| SetupVirtualMap | False |

#### DeviceProperties
##### Add
###### PciRoot(0x0)/Pci(0x2,0x0)
| Key | Type | Value |
| --- | ---- | ----- |
| framebuffer-patch-enable | Data | 01000000 |
| framebuffer-singlelink | Data | 01000000 |

#### Kernel
##### Emulate
| Key | Type | Value |
| --- | ---- | ----- |
| DummyPowerManagement | True |
##### Quirks
| Quirk | Enabled | Comment |
| ------ | ------ | ------ |
| AppleCpuPmCfgLock | False | |
| DisableIoMapper | False | |
| LapicKernelPanic | True | Disables kernel panic on LAPIC interrupts. Mainly needed for HP machines |
| PanicNoKextDump | True | Prevent kernel from printing kext dump in the panic log |
| PowerTimeoutKernelPanic | True | Fixes kernel panic on setPowerState timeout |
| XhciPortLimit | False | Not needed, device only has 2 actual ports |

#### Misc
##### Debug 
| Key | Type | Value | Comment |
| --- | ---- | ----- | ------- |
| AppleDebug | Boolean | False | Only works on 10.15.4 and newer |
| ApplePanic | Boolean | True | Saves macOS kernel panic output to OC partition |
| DisableWatchDog | Boolean | True | Fixes some types of firmware not booting the OS quickly which will results in the watchdog timer aborting the process. This option turns off the watchdog timer. |
| Target | Number | 67 | OC debugging |
