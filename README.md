# Opencore-HP-Pavilion-Gaming-15-cx0056wm

<B>Opencore Hackintosh Monterey 12.0.1 - HP Pavilion Gaming 15-cx0056wm</B>

![Screen Shot 2021-10-25 at 11 54 55 PM](https://user-images.githubusercontent.com/25624482/138761410-be67e0f2-8c03-4647-a8de-01320fe8620b.png)

![Screen Shot 2021-10-25 at 11 54 04 PM](https://user-images.githubusercontent.com/25624482/138761360-979d781a-73d7-49c5-b581-e585fa306647.png)

## Quick Installation
- Follow [Opencore](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) And create a bootable MacOS recovery USB
- Download the EFI and place it onto your USB drive
- Boot to opencore and setup your Disk in DiskUtility

## Dualbooting Notes
- To install along side windows make sure you have a GPT formatted Disk, Resize your Windows partition using tools such as Easeus partition master Then while in MacOS DiskUtility, Make the unallocated space into APFS
- I also left a 500MB unallocated space for an EFI partition. using gparted on linux earlier  i set the esp / boot flags
- Finally Copy the EFI from the repo to your disk EFI partition that you created and boot from it with the F9 key

## Specifications

| Specifications      | Detail                                      |
| ------------------- | ------------------------------------------- |
| Computer model      | HP Pavilion Gaming 15-cx0056wm              |
| Processor           | Intel Core i5-8300H Processor               |
| Memory              | 8GB/8GB Crucial / SK Hynix                  |
| SSD		              | Samsung SSD 970 EVO 500GB	PM981		          |
| HDD		              | Seagate ST2000LM007-1R817 2TB			 	        |
| Integrated Graphics | Intel® UHD Graphics 630                     |
| Dedicated Graphics  | NVIDIA GeForce GTX 1050 Ti                  |
| Monitor             | FHD 1920x1080 (15.6 inch)                   |
| Sound Card          | Realtek ALC295					                    |
| Wireless Card       | Intel® Wireless-AC 9560 802.11b/g/n/ac      |
| Ethernet/LAN        | Realtek RTL8168/8111 PCI-E Gigabit Ethernet |
| Card Reader         | AU6625 PCI-E Flash card reader              |

## Working
- Intel UHD 630 Acceleration
- CPU Power Management
- Battery Status / Time
- Intel Wireless & Bluetooth
- Ethernet LAN
- NVMe Storage
- Realtek Audio & F7/F8 keys
- Audio Combo Jack
- Keyboard & Media/Function Keys
- Trackpad & Gestures support
- USB Type-A & Type-C ports
- HP Webcam
- Sleep/Wakeup & Instant Wake
- Screen LID sleep
- Screen Brightness & F2/F3 Keys
- And pretty much everything not listed below

## Not Working
- DRM (No HD playback on Netflix etc)
- SDXC Card Reader (Not supported in MacOS)
- Dedicated GPU (Disabled in SSDT)
- HDMI Port (Seems to be hooked to the Dedicated GPU)

## Kexts
| Kext                               | Version | Details                | Usage                                                                 |
| ---------------------------------- | ------- | ---------------------- | --------------------------------------------------------------------- |
| [AirportItlwm](https://github.com/OpenIntelWireless/itlwm)                   | v2.0.0  | 25 Oct 2021 - edited [maxkernel](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/117b32345c4988f78bb91fb1df236f63bc64c2d2)    | Intel Wi-Fi Adapter Kext for macOS                                    |
| [AppleALC](https://github.com/acidanthera/AppleALC)                       | v1.6.5  | Oct 4 2021 Release     | Native macOS HD audio for not officially supported codecs             |
| [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys)                 | v1.0.2  | Jun 7 2021 Release     | Handler for brightness keys without DSDT patches                      |
| [ECEnabler](https://github.com/1Revenger1/ECEnabler)                      | v1.0.2  | Aug 2 2021 Release     | Allows reading Embedded Controller fields over 1 byte long            |
| [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)         | v2.0.1  | 25 Oct 2021 - edited [maxkernel](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/117b32345c4988f78bb91fb1df236f63bc64c2d2)    | Intel Bluetooth Drivers for macOS                                     |
| [Lilu](https://github.com/acidanthera/Lilu)                           | v1.5.6  | Sep 7 2021 Release     | Arbitrary kext and process patching on macOS                          |
| [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM)                           | v2.6.0  | Jul 5 2021 Release     | Monterey Bluetooth Firmware fix-up
| [NVMeFix](https://github.com/acidanthera/NVMeFix)                        | v2.4.2  | May 6 2021 Release     | OS X open source driver for the Realtek RTL8111/8168 family           |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC)                     | v1.7.2  | Sep 7 2021 Release     | Advanced Apple SMC emulator in the kernel                             |
| [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC)              | v1.7.2  | Sep 7 2021 Release     | Battery Management For Laptops                                        |
| [SMCLightSensor](https://github.com/acidanthera/VirtualSMC)                 | v1.7.2  | Sep 7 2021 Release     | Light Sensor For Laptops                                              |
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC)                   | v1.7.2  | Sep 7 2021 Release     | Improved CPU measurement                                              |
| [SMCSuperIO](https://github.com/acidanthera/VirtualSMC)                     | v1.7.2  | Sep 7 2021 Release     | Measurement of Fans For Laptops                                       |
| [USBToolBox](https://github.com/USBToolBox/kext)                     | v1.1.0  | May 22 2021 Release    | USB Mapping                                                           |
| [UTBMap](https://github.com/USBToolBox/kext)                         | v1.1.0  | Oct 21 2021 Gen        | Generated USB Map                                                     |
| [VoodooPS2](https://github.com/acidanthera/VoodooPS2)                      | v2.2.6  | Oct 4 2021 Release     | Controller For various PS2 Gestures                                   |
| [VoodooRMI](https://github.com/VoodooSMBus/VoodooRMI)                      | v1.3.4  | Sep 7 2021 Release     | A port for macOS of Synaptic's RMI Trackpad driver from Linux         |
| [VoodooSMBUS](https://github.com/VoodooSMBus/VoodooRMI)                    | v1.3.4  | Sep 7 2021 Release     | VoodooRMI Extension for PS2 Trackpad                                  |
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen)                  | v1.5.4  | Oct 4 2021 Release     | Various patches necessary for certain ATI/AMD/Intel/Nvidia GPUs       |

## Opencore
- OpenCore V0.7.4 Release on Oct 4 2021

## ACPI Patch list
- SSDT-AWAC : System Clock fix
- SSDT-EC-USBX-LAPTOP : Embedded Controller fix
- SSDT-GPRW : Instant wake fix
- SSDT-HP-FixLidSleep : Screen LID Sleep Fix
- SSDT-PLUG-DRTNIA : Power Management Fix
- SSDT-PMC : NVRAM Fix (Optional on H370)
- SSDT-PNLF : Brightness Fix
- SSDT-dGPU-Off : Disables Dedicated GPU (Optimus Method)

## Misc information
- Audio Layout ID : 13
- [Backlight Register](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/5b8c3a12f79ddb463ffe774c052cf00ad6dda0d8) fix is needed to fix black screen on bootup
- USB Port Map [info](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/e6eb9aa1a21bef35153f1993c7ae1534bd0b33ad)
- Quirks Adjusted to fix Kernel panic on boot [commit](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/8258d55462a9d0fe94edc516f2be52b85ebb0799)
- xhciPortLimit is broken since MacOS 11.3. Has been Disabled to avoid kernel panics
- Bootup Chime and Theme Enabled
- SMBios MacBookPro15,2 is used
- dGPU is disabled via SSDT edit
- Card Reader is spoofed but does not Work

## Credits
- @SkyrilHD For Massive help and tips / fixes
- @TECHNIKVERBOT For Monterey Patches
- @acidanthera For Bootloader, VirtualSMC, NVMEFix, Lilu And other kexts
- @dortania For guides
- @OpenIntelWireless For AC WiFi & Bluetooth
- @USBToolBox Team for Mapping
- @1Revenger1 for ECEnabler
- @Voodoo Team for TrackPad
- @Apple For MacOS
