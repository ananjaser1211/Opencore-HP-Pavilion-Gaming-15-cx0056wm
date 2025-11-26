# Opencore-HP-Pavilion-Gaming-15-cx0056wm

<B>OpenCore Hackintosh - HP Pavilion Gaming 15-cx0056wm</B>

## Specifications

| Specifications      | Detail                                      |
| ------------------- | ------------------------------------------- |
| Computer model      | HP Pavilion Gaming 15-cx0056wm              |
| CPU                 | Intel Core i5-8300H                         |
| Memory              | 8GB/8GB Crucial / SK Hynix                  |
| SSD                 | Samsung SSD 970 EVO 500GB (PM981)           |
| HDD                 | Seagate ST2000LM007-1R817 2TB               |
| Integrated Graphics | Intel® UHD Graphics 630                     |
| Dedicated Graphics  | NVIDIA GeForce GTX 1050 Ti                  |
| Monitor             | FHD 1920x1080 (15.6 inch)                   |
| Sound Card          | Realtek ALC295                              |
| Wireless Card       | Intel® Wireless-AC 9560 802.11b/g/n/ac      |
| Ethernet/LAN        | Realtek RTL8168/8111 PCI-E Gigabit Ethernet |
| Card Reader         | AU6625 PCI-E Flash card reader              |

# Supported MacOS Version
- Sequoia 15.x.x (tested)
- Tahoe 26.x.x (Un-Tested but will work)
- Require [Heliport](https://github.com/OpenIntelWireless/HeliPort) for WiFi
- Initial Setup requires Internet via ethernet if using offline installers

## Screenshots

| About this Mac                                                                                                | neofetch                                                                                                      |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| <img width="1920" height="1080" alt="Screenshot 2025-11-26 at 12 01 23 AM" src="https://github.com/user-attachments/assets/6fca9457-bfcb-4385-9177-862dc0503f78" /> | <img width="1920" height="1080" alt="Screenshot 2025-11-26 at 12 01 00 AM" src="https://github.com/user-attachments/assets/b15ec480-22f1-416e-9272-337871572809" /> |

## Working

- Intel UHD 630 Acceleration
- CPU Power Management
- IGPU Power Management
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
- Apple GUC firmware
- Type-C HDMI Out ([No Audio](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/issues/5))

## Not Working

- DRM (No HD playback on Netflix etc.)
- SDXC Card Reader (Not supported in MacOS)
- Dedicated GPU (Disabled in SSDT)
- HDMI Port output (Seems to be hooked to the dedicated GPU)
- Type-C HDMI does not have Audio

## Quick Installation

- Follow [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) and create a bootable macOS recovery USB
- Download the EFI and place it onto your USB drive
- Boot to OpenCore and setup your disk in Disk Utility
- The system is expected to reboot 4-5 times in total.

> [!IMPORTANT]  
> For macOS **Sequoia+** Installation/Update:
>
> 1. **Before Installation**: Set `Misc` -> `Security` -> `SecureBootModel` to `Disabled` in Config.plist.
> 2. **After Successfully Installing**: Change `SecureBootModel` back to `Default`.
>
>    ⚠️ Only change back to `Default` after **successfully reaching the desktop**, otherwise boot may fail!

## Generating your own serial and SMBIos Info
> This is required to have functional Apple services

Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate a serial for *MacBookPro15,2*

Use Xcode, [ProperTree](https://github.com/corpnewt/ProperTree) or any decent plist editor to manually enter the details in the following sections of the config (as shown in the video): (SystemSerialNumber, MLB, UUID and ROM)

https://github.com/user-attachments/assets/abbf3bc2-af5b-479c-a9a1-886ba14315f9.mp4

or load the config.plist in [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools) and have it generate and update the config.

## Dualbooting Notes

- To install along side Windows make sure you have a GPT formatted disk, resize your Windows partition using tools such as Easeus Partition Master then while in macOS Disk Utility, make the unallocated space into APFS.
- I utilize Gparted Live ISO to change the unallocated space into HFS+ Which later can be upgraded to APFS in MacOS Disk Utility.
- Create a 500MB+ EFI partition using gparted on Linux with the flags: ESP / boot flags
- Copy the EFI from the repo to your disk EFI partition that you created and boot from it with the F9 key

> [!IMPORTANT]  
> HP Bios Notes:
>
> HP Bios does not auto detect OpenCore EFI Partition with Windows installed, For auto-boot / default MacOS Look into chainloading OpenCore, otherwise just boot with F9 Key.


## Kexts

| Kext                                                                                  | Version | Details | Usage                                                           |
| ------------------------------------------------------------------------------------- | ------- | ------- | --------------------------------------------------------------- |
| [Itlwm](https://github.com/OpenIntelWireless/itlwm)                                   | v2.3.0  | Release | Intel Wi-Fi Adapter Kext for macOS                              |
| [AppleALC](https://github.com/acidanthera/AppleALC)                                   | v1.9.6  | Release | Native macOS HD audio for not officially supported codecs       |
| [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM)                          | v2.7.1  | Release | Monterey Bluetooth Firmware fix-up                              |
| [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys)                       | v1.0.3  | Release | Handler for brightness keys without DSDT patches                |
| [ECEnabler](https://github.com/1Revenger1/ECEnabler)                                  | v1.0.5  | Release | Allows reading Embedded Controller fields over 1 byte long      |
| [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware) | v2.5.0  | Release | Intel Bluetooth Drivers for macOS                               |
| [IntelBTPatcher](https://github.com/OpenIntelWireless/IntelBluetoothFirmware)         | v2.4.0  | Release | Intel Bluetooth Firmware Uploader                               |
| [Lilu](https://github.com/acidanthera/Lilu)                                           | v1.7.1  | Release | Arbitrary kext and process patching on macOS                    |
| [NVMeFix](https://github.com/acidanthera/NVMeFix)                                     | v1.1.3  | Release | Set of patches for the Apple NVMe storage driver                |
| [RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)                    | v2.5.0  | Release | OS X open source driver for the Realtek RTL8111/8168 family     |
| [RestrictEvents](https://github.com/acidanthera/RestrictEvents)                       | v1.1.6  | Release | Suppresses unwanted notifications in macOS                      |
| [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC)                        | v1.3.6  | Release | Battery Management For Laptops                                  |
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC)                             | v1.3.6  | Release | Improved CPU measurement                                        |
| [SMCSuperIO](https://github.com/acidanthera/VirtualSMC)                               | v1.3.6  | Release | Measurement of Fans For Laptops                                 |
| [USBToolBox](https://github.com/USBToolBox/kext)                                      | v1.2.0  | Release | USB Mapping                                                     |
| [UTBMap](https://github.com/USBToolBox/kext)                                          | v1.1    | Gen     | Generated USB Map                                               |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC)                               | v1.3.7  | Release | Advanced Apple SMC emulator in the kernel                       |
| [VoodooPS2](https://github.com/acidanthera/VoodooPS2)                                 | v2.3.7  | Release | Controller For various PS2 Gestures                             |
| [VoodooRMI](https://github.com/VoodooSMBus/VoodooRMI)                                 | v1.4.3  | Release | A port for macOS of Synaptic's RMI Trackpad driver from Linux   |
| [VoodooSMBUS](https://github.com/VoodooSMBus/VoodooRMI)                               | v3.0    | Release | VoodooRMI Extension for PS2 Trackpad                            |
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen)                         | v1.7.0  | Release | Various patches necessary for certain ATI/AMD/Intel/Nvidia GPUs |

## OpenCore

- OpenCore v1.0.6 (Release)

## ACPI Patch list

- SSDT-AWAC: System Clock fix
- SSDT-dGPU-Off: Disables dedicated GPU (Optimus Method)
- SSDT-EC-USBX-LAPTOP: Embedded Controller fix
- SSDT-GPRW: Instant wake fix
- SSDT-HP-FixLidSleep: Screen LID Sleep Fix
- SSDT-PLUG-DRTNIA: Power Management Fix
- SSDT-PMC: NVRAM Fix (Optional on H370)
- SSDT-PNLF: Brightness Fix

## Misc information

- Audio Layout ID: 13
- [Backlight Register](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/5b8c3a12f79ddb463ffe774c052cf00ad6dda0d8) fix is needed to fix black screen on bootup
- USB Port Map: [info](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/e6eb9aa1a21bef35153f1993c7ae1534bd0b33ad)
- Quirks adjusted to fix kernel panic on boot [commit](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/8258d55462a9d0fe94edc516f2be52b85ebb0799)
- XhciPortLimit is broken since MacOS 11.3. The quirk has been disabled to avoid kernel panics.
- Bootup Chime and Theme Enabled
- SMBIOS MacBookPro15,2 is used
- dGPU is disabled via SSDT edit
- Card Reader is spoofed but does not work
- iGPU power management is handeled by [Apple GUC](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/471b26d67147d0fa8871a69b448f73835302dfeb)

## Credits

- @1Revenger1 for ECEnabler
- @acidanthera for bootloader, VirtualSMC, NVMeFix, Lilu and other kexts
- @Apple for macOS
- @dortania for guides
- @OpenIntelWireless for WiFi & Bluetooth
- @SkyrilHD for massive help and tips / fixes
- @TECHNIKVERBOT for Monterey patches
- @USBToolBox Team for USB mapping
- @Voodoo Team for TrackPad
