# Hackintosh
Mojave 10.14.6

### Installation with Clover
Clover: https://github.com/CloverHackyColor/CloverBootloader/releases.   
Clover Configurator: https://www.macupdate.com/app/mac/61090/clover-configurator.   

A guide can be found here: https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/.
Another guide: https://hackintosher.com/guides/guide-to-fresh-installing-macos-mojave-on-a-hackintosh-10-14
Mojave 10.14.6 config plist update: https://hackintosher.com/guides/hackintosh-mojave-10-14-6-update-guide/.   

Latest kexts: https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23.

Here are the kexts I installed (only in /EFI/CLOVER/kexts/Other) :     
- AppleALC.kext (version 1.3.9)    
- AtherosE2200Ethernet.kext (version 2.2.2)    
- FakePCIID.kext    
- FakePCIID_XHCIMux.kext     
- FakeSMC.kext      
- GenericUSBXHCI.kext      
- USBInjectAll.kext (version 9/11/18)    
- Lilu.kext (version 1.3.0)
- WhateverGreen.kext (version 1.3.7)     

Here's my hardware config :   
- CPU : Intel Core I5 4690 (Haswell)   
- MotherBoard : MSI H97 Gaming 3    
- Ram : 8Go Ram (DDR3 Ballistix Tactical, 2 x 4 Go, 1600 MHz, CAS 8)    
- GPU : Asus Radeon R9 280X DirectCU II Top, 3 Go    
- Clover : Clover v2.5k_r5033    

### Problem with audio
Check here: https://www.reddit.com/r/hackintosh/comments/4sil5p/audio_mechanic_old_patchfix_removal_applealc/.    

### Problem with ethernet ?
- It is a known problem if bios is not up to date so **update your bios**.    
- It it still does not work, try _sudo softwareupdate --background_ in a terminal.    
