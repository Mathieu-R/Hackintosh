# Monterey with OpenCore 0.8.3

![desktop](/monterey.png)

### General informations and useful links

- [x] Monterey 12.5.1

- To **install** with OpenCore [this guide](https://dortania.github.io/OpenCore-Install-Guide/) is a must
- More informations on **bios settings** can be found [here](https://dortania.github.io/OpenCore-Install-Guide/config.plist/haswell.html#intel-bios-settings)
- If you encounter any **problems**, read first [this page](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html)
- Do not forget to check [this page](https://dortania.github.io/OpenCore-Post-Install) after the installation to make the **post-install** stuff.
- A lots of **good tools** are provided by corpnewt, you can check that out [here](https://github.com/corpnewt)

### Hardware config

- CPU : Intel Core I5 4690 (Haswell)
- MotherBoard : MSI H97 Gaming 3 (Chipset Intel H97 ; Socket 1150)
- Ram : 8Go Ram (DDR3 Ballistix Tactical, 2 x 4 Go, 1600 MHz, CAS 8)
- GPU : Asus Radeon R9 280X DirectCU II Top, 3 Go (ig-platform-id: 04001204)
- Audio : Realtek ALC1150
- Network : Killer E2205

### Bios configuration

- `Settings` > `Save & Exit` > **Restore defaults**
- `Overclocking` > `CPU Features`> `CFG-Lock` > **Disable**
- `Overclocking`> `CPU Features` > `VT-d` > **Enable**
- `Settings` > `Advanced` > `Integrated Peripherals` > `Sata Mode` > **AHCI Mode**
- `Settings`> `Advanced` > `Intel Thunderbolt` > `Intel Thunderbolt Technology` > **Disable**
- `Settings` > `Advanced` > `Windows 8/8.1/10 Configuration` > `Windows 8/8.1/10 Feature` > **Disable**
- `Settings` > `Advanced` > `Windows 8/8.1/10 Configuration` > `Fast Boot` > **Disable**
- `Settings` > `Boot` > `Boot-Mode` > **UEFI**

### Installation with OpenCore

Drivers Needed:

- HFSPlus (or VboxHFS).

https://github.com/dortania/OpenCore-Install-Guide/blob/master/clover-conversion/clover-efi.md

> Note: Comparing to clover, the following drivers are already provided by OpenCore (do not need to download them): ApfsDriverLoader, AptioMemoryFix, EMUVariableUEFI

Kext Needed:

- AppleALC.kext (version 1.7.4)
- AtherosE2200Ethernet.kext (version 2.3.2)
- VirtualSMC.kext (version 1.3.0)
- USBToolbox.kext
- Lilu.kext (version 1.6.2)
- WhateverGreen.kext (version 1.6.1)

> Link to download latest kexts: https://dortania.github.io/OpenCore-Install-Guide/ktext.html

> To update your kexts : https://dortania.github.io/OpenCore-Post-Install/universal/update.html#updating-opencore

ACPI Needed:

- SSDT-PLUG
- SSDT-EC

> This part is not so easy (moreover if you can't use the automatic method). Check the guide provided above to see which SSDT you need for your CPU architecture and how to get/decompile your DSDT and compile your needed SSDT's with the help of your DSTD.

It is recommended to map USB ports before installing OSX: https://github.com/USBToolBox/tool

### What's working out of the box

- [x] Boot successful [without usb](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html).
- [x] Lan Ethernet.
- [x] AMD Radeon R9 280x Graphics (screen full resolution)
- [x] Sound [ok](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html) (_layout-id 3 works_)
- [x] DRM support seems ok.

### What need to be fixed post-install

- [x] Mouse and keyboard [freeze on wake-up](https://dortania.github.io/OpenCore-Post-Install/universal/sleep.html) [fixed by mapping USB]
- [x] Sometimes keyboard doesn't work on login screen and I get "USB port need power" when I connect a device probably due to bad USB mapping and maybe lack of an ACPI patch. [fixed by mapping USB]
- [x] Bios is reset after reboot [check [here](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html#bios-reset-or-sent-into-safemode-after-reboot-shutdown)]

### Interessting links

- [x] [USB mapping](https://dortania.github.io/OpenCore-Post-Install/usb/#macos-and-the-15-port-limit)
- [x] [CPU Power Management](https://dortania.github.io/OpenCore-Post-Install/universal/pm.html#enabling-x86platformplugin)
- [x] [Cleaner boot](https://dortania.github.io/OpenCore-Post-Install/cosmetic/verbose.html#macos-decluttering)
- [x] [Boot GUI](https://dortania.github.io/OpenCore-Post-Install/cosmetic/gui.html#setting-up-boot-chime-with-audiodxe)
- [x] [Multiboot](https://dortania.github.io/OpenCore-Post-Install/multiboot/bootstrap.html#preparation)

### Problem with audio ?

Check here: https://dortania.github.io/OpenCore-Post-Install/universal/audio.html

### Problem with ethernet ?

- It is a known problem if bios is not up to date so **update your bios**.
- It it still does not work, try _sudo softwareupdate --background_ in a terminal.

### Mount EFI in safe mode

```
sudo mkdir /kexts
sudo cp -RX /System/Library/Extensions/msdosfs.kext /kexts
sudo /usr/libexec/PlistBuddy -c "Add :OSBundleRequired string" /kexts/msdosfs.kext/Contents/Info.plist
sudo /usr/libexec/PlistBuddy -c "Set :OSBundleRequired \"Safe Boot\"" /kexts/msdosfs.kext/Contents/Info.plist
```

```
sudo kextutil /kexts/msdosfs.kext
```

```
sudo diskutil mount <disk>
```

### Prevent computer to power up at night (automatically)

### Rebuild kexts cache

```
sudo kextcache -i /
```

### If you install Monterey as dual boot with Windows and your Windows EFI entries are deleted (cannot boot on Windows)

https://www.ubackup.com/windows-10/restore-efi-partition-windows-10-8523.html
