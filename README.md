# Hackintosh
Mojave 10.14.6

### Installation
1. Download Mojave through App Store and create USB key with Unibeast (https://www.unibeast.com/).     
2. Boot on USB key and install Mojave.    
3. Boot on Mojave through the USB key and do the post-installation with Multibeast (screenshot of my multibeast config below).

![multibeast configuration](/Multibeast.png)

Here are the kexts I installed (only in /EFI/CLOVER/kexts/Other) :     
- AppleALC.kext (version 1.3.9)    
- AtherosE2200Ethernet.kext (version 2.2.2)    
- FakePCIID.kext    
- FakePCIID_XHCIMux.kext     
- FakeSMC.kext      
- GenericUSBXHCI.kext      
- USBInjectAll.kext     
- Lilu.kext (version 1.3.0)
- WhateverGreen.kext (version 1.3.7)     

Here's my hardware config :   
- CPU : Intel Core I5 4690    
- MotherBoard : MSI H97 Gaming 3    
- Ram : 8Go Ram (DDR3 Ballistix Tactical, 2 x 4 Go, 1600 MHz, CAS 8)    
- GPU : Asus Radeon R9 280X DirectCU II Top, 3 Go    
- Clover : Clover v2.5k_r5033    

### Clover Configurator
Multibeast is not much reliable, a better way to install kexts is to use Clover Configurator: https://www.macupdate.com/app/mac/61090/clover-configurator.   
A guide can be found here: https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/.   
Latest kexts: https://onedrive.live.com/?authkey=%21APjCyRpzoAKp4xs&id=FE4038DA929BFB23%21455036&cid=FE4038DA929BFB23.    

### Problem with audio
Check here: https://www.reddit.com/r/hackintosh/comments/4sil5p/audio_mechanic_old_patchfix_removal_applealc/.    

### Problem with ethernet ?
- It is a known problem if bios is not up to date so **update your bios**.    
- It it still does not work, try _sudo softwareupdate --background_ in a terminal.    
