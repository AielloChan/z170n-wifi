# z170n-wifi
Gigabyte Z170n-wifi hackintosh

This is not actually a new build. I built this hack for my son a little over 2 years ago. He mainly uses it for writing music on GarageBand. Back then, the recommendation was still to use Nvidia with web drivers, so he's been stuck on High Sierra ever since with a GTX 750ti.

I decided to post this here as a success story because of just how difficult it was to get it upgraded to Catalina - it was basically like starting a new hack from scratch. There's a problem with USB injection to the macOS installer (the actual OS works completely fine for some reason, the bug only affects booting the recovery environment from USB) on any version of macOS after High Sierra that causes a "still waiting on root device" error when plugged into a USB 3 port, and there are only 5 onboard ports, all of which are USB 3 with the exception of a single USB C port. All USB ports work fine with USBInjectAll + custom SSDT + clover 15 port limit patch. I ended up working around this the dumbest way possible - I installed Catalina on a separate hard drive on one of my other computers, then swapped the hard drive into my son's computer, booted the recovery and reinstalled to the SSD.

My initial attempt to install Catalina by trying to do an in place upgrade from High Sierra to Catalina resulted in a thoroughly corrupted Fusion Drive (has a 256gb m.2 SSD + 1TB SATA HD). After being burned by the corrupted fusion drive, I decided to just throw /Users on the 1TB HD and the OS on the SSD.

For graphics, I bought him an XFX RX 560 which turned out to be an enormous pain in the ass to get working. First of all, the XFX RX 560 is not actually a 560, it is a 560D. In order to get the hack to boot up, I had to flash the Sapphire Pulse RX 560D 4GB vBIOS in Windows. which required me to spin up a copy of Windows 10 on this computer. Despite everyone's dire warnings about not flashing in Windows, I could not flash the bios with ATIFLASH in DOS for love nor money. I ended up having to just do it in Windows anyway and say f*** it, if I brick it I'll just send this POS card back because at that point I was pretty fed up with it. Luckily, the flash went fine and afterwards, the system boots right up. You just need Whatevergreen and Lilu and it works pretty much as expected. The Display Port and HDMI outputs work fine, but the DVI port does not work. it will detect that there is a third monitor plugged in, but it will not display anything on it. But that's fine since my son's rig is only a dual monitor setup.

I was using a Dell DW1560 for wifi and bluetooth. The wifi works just fine on Catalina, but absolutely nothing will get Bluetooth working on this card, so I just went ahead and ordered an official Apple Card + NGFF to m.2 adapter and I'll never have to worry about it again.

Before upgrading from High Sierra to Catalina, I was just using the latest version of VoodooHDA for audio and it worked fine. But no version of Voodoo works on Catalina for some reason. Normally, I would never use anything Tonymac, but I decided to give their ALC audio patched AppleHDA a try and it worked on the first shot.

So there you have it. this hack was by far the biggest PITA hack I've ever done. I don't really recommend the Z170 board as a good hack candidate. Once I get the new wifi card his computer will be back up to 100% functional. Right now its just missing bluetooth. that DW1560 just doesn't work on Catalina.




To get it to boot, I had to change some settings in BIOS. Basically did a reset to default, disabled vt-d and some weird "149 entries" setting under chooser iirc. After that I could boot from SATA, but not USB. make sure you're on the latest clover. I'm not home rn but I'll throw my EFI on GitHub or something later

Make sure you have XHCI Handoff enabled
