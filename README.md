# Hackintosh
Mojave 10.14.6

### Bios configuration
- Settings/Save & Exit/Restore defaults   
- Set Overclocking/CPU Features/CFG-Lock to disabled    
- Set Overclocking/CPU Features/VT-d to disabled (_however, can let it enable as we set DisableIoMapper to True in config.plist)    
- Set Settings/Advanced/Windows 8/8.1/10 to disabled    
- Set Settings/Boot/Boot-Mode to UEFI    

More informations here: https://www.reddit.com/r/hackintosh/comments/ed0di8/msi_h97_gaming_3_i54690_gtx_650_ti_gk106_mojave/     

### Installation with OpenCore
Guide: https://dortania.github.io/OpenCore-Install-Guide/            

Drivers Needed:     
- HFSPlus (or VboxHFS) [you can use the one provided by Clover].        

https://github.com/dortania/OpenCore-Install-Guide/blob/master/clover-conversion/clover-efi.md    

> Note: Comparing to clover, the following drivers are already provided by OpenCore (do not need to download them): ApfsDriverLoader, AptioMemoryFix, EMUVariableUEFI


Kext Needed:     
- AppleALC.kext (version 1.5.0)    
- AtherosE2200Ethernet.kext (version 2.3.2)    
- FakePCIID.kext    
- FakePCIID_XHCIMux.kext     
- VirtualSMC.kext (version 1.1.4)    
- GenericUSBXHCI.kext      
- USBInjectAll.kext (version 0.7.5)    
- Lilu.kext (version 1.4.5)
- WhateverGreen.kext (version 1.4.0)     

> Link to download latest kexts: https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23    

ACPI Needed:
- SSDT-PLUG
- SSDT-EC

> This part is not so easy (moreover if you can't use the automatic method). Check the guide provided above to see which SSDT you need for your CPU architecture and how to get/decompile your DSDT and compile your needed SSDT's with the help of your DSTD.


Hardware config :   
- CPU : Intel Core I5 4690 (Haswell)   
- MotherBoard : MSI H97 Gaming 3 (Chipset Intel H97 ; Socket 1150)   
- Ram : 8Go Ram (DDR3 Ballistix Tactical, 2 x 4 Go, 1600 MHz, CAS 8)    
- GPU : Asus Radeon R9 280X DirectCU II Top, 3 Go (ig-platform-id: 04001204)         
- Audio : Realtek ALC1150  
- Network : Killer E2205.   
- Clover : Clover v2.5k_r5033    

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
