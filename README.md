# Hackintosh Mojave 

### General informations and useful links

- [x] Mojave 10.14.6

- To **install** with OpenCore [this guide](https://dortania.github.io/OpenCore-Install-Guide/) is a must 
- More informations on **bios settings** can be found [here](https://dortania.github.io/OpenCore-Install-Guide/config.plist/haswell.html#intel-bios-settings)    
- If you encounter any **problems**, read first [this page](https://dortania.github.io/OpenCore-Install-Guide/troubleshooting/troubleshooting.html)    
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
- `Settings` > `Advanced` > `Windows 8/8.1/10` > **Disable**    
- `Settings` > `Boot` > `Boot-Mode` > **UEFI**    

### Installation with OpenCore

Drivers Needed:     
- HFSPlus (or VboxHFS).        

https://github.com/dortania/OpenCore-Install-Guide/blob/master/clover-conversion/clover-efi.md    

> Note: Comparing to clover, the following drivers are already provided by OpenCore (do not need to download them): ApfsDriverLoader, AptioMemoryFix, EMUVariableUEFI

Kext Needed:     
- AppleALC.kext (version 1.5.0)    
- AtherosE2200Ethernet.kext (version 2.3.2)    
- VirtualSMC.kext (version 1.1.4)    
- USBInjectAll.kext (version 0.7.5)    
- Lilu.kext (version 1.4.5)
- WhateverGreen.kext (version 1.4.0)     

> Link to download latest kexts: https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23    

ACPI Needed:
- SSDT-PLUG
- SSDT-EC

> This part is not so easy (moreover if you can't use the automatic method). Check the guide provided above to see which SSDT you need for your CPU architecture and how to get/decompile your DSDT and compile your needed SSDT's with the help of your DSTD.  

### What's working

### Problem with audio
Check here: https://hackintosher.com/guides/get-hackintosh-audio-working.              

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
