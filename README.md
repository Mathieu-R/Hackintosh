# Hackintosh
Mojave 10.14.6

### Bios configuration
- Load optimized default    
- Enable XMP    
- Set Overclocking/CPU Features/CFG-Lock to disabled    
- Set Overclocking/CPU Features/VT-d to disabled    

### Installation with Clover
Clover: https://github.com/CloverHackyColor/CloverBootloader/releases.   
Clover Configurator: https://www.macupdate.com/app/mac/61090/clover-configurator.   

A guide can be found here: https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/.    
Another guide: https://hackintosher.com/guides/guide-to-fresh-installing-macos-mojave-on-a-hackintosh-10-14    
Mojave 10.14.6 config plist update: https://hackintosher.com/guides/hackintosh-mojave-10-14-6-update-guide/.        

Latest kexts: https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23.    

In the clover install assistant, only select: 
- _Install Clover for UEFI booting only_.   
- _Install Clover to the ESP_.   
- Under _UEFI Drivers_:
  - OsxAptioFix3Drv.   
  - HFSPlus (or VboxHFS).    
  - ApfsDriverLoader.   
  - EmuVariableUEFI.   

Here are the kexts I installed (only in /EFI/CLOVER/kexts/Other) :     
- AppleALC.kext (version 1.5.0)    
- AtherosE2200Ethernet.kext (version 2.3.2)    
- FakePCIID.kext    
- FakePCIID_XHCIMux.kext     
- VirtualSMC.kext (1.1.4)    
- GenericUSBXHCI.kext      
- USBInjectAll.kext (version 9/11/18)    
- Lilu.kext (version 1.4.5)
- WhateverGreen.kext (version 1.4.0)     

Here's my hardware config :   
- CPU : Intel Core I5 4690 (Haswell)   
- MotherBoard : MSI H97 Gaming 3    
- Ram : 8Go Ram (DDR3 Ballistix Tactical, 2 x 4 Go, 1600 MHz, CAS 8)    
- GPU : Asus Radeon R9 280X DirectCU II Top, 3 Go     
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
