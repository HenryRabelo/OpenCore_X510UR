# **DISCLAIMER**

If you are new to this, please follow [Dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/). There is a lot to learn, but it is necessary to know what you are doing.

I hope these files can help, as a starting point or reference, to ˜reverse-engineer˜ your own setup and increase your knowledge (as it did for me). Also, I'm not any kind of expert nor have access to a myriad of hardwares.

Some of the info under the PlatformInfo section of the conf.plist has been scrubbed before uploading. For that, you'll actually need to create your own configuration.

# Asus Vivobook X510UR OpenCore
Files and info of my OpenCore laptop setup on an ASUS Vivobook X510UR-BQ292T.

What is OpenCore? Why, it is the special bootloader that does all the _magic_. OpenCore _boots_ your OS, as a bootloader does, but it's function is to whisper lies upon you OS shoulder. When you configure OpenCore, you are setting all the environment variables that are passed to the Operating System while it is booting, making sure it thinks it is in a familiar, safe environment for it to work, even if it might be in a completely different hardware.

That means you have to pay attention and setup everything to the best of your abilities before the system is even able to boot. If there's anything that is not oficially supported, Kernel Extensions (KExts) come to the rescue, so the system can use whatever your hardware offers. Use only what you actually need, however. Also, note that certain versions of the Operating System require a certain version of OpenCore to be able to boot.

## Bootloader

As of right now, I'm using **OpenCore 0.8.8** as bootloader, with **Monterey** installed. Before messing with the OpenCore version and OS update, The initial install used OpenCore 0.6.6, with Mojave.

Do note, it is recommended to use the latest available version of the Operating System, as up to Catalina, the HFS+ filesystem is recommended (OpenCore wouldn't find your drive reliably otherwise), and starting on Big Sur, the APFS filesystem is recommended. _However_, for the uninitiated, you cannot simply _change_ your filesystem after an install, you _have_ to reinstall.

## Status of the system

### :heavy_check_mark: Networking
I'm using [AirportItlwm](https://openintelwireless.github.io/itlwm/) to enable the Intel Wifi card (Intel(R) Dual Band Wireless AC 8275). I used **AirportItlwm** even on the Mojave install, and as of right now, the Ventura version of it is still being worked on.

#### Relevant Kexts
- AirportItlwm.kext

### :heavy_check_mark: Graphics
Only intel integrated HD620 shared memory graphics are avaible. The GeForce 930MX is explicitly deactivated. Following some [directions](https://www.reddit.com/r/hackintosh/comments/gjksrk/smbios_framebuffer_and_performance/), I configured it as as UHD617 due to performance issues.

#### Relevant Kexts:
- WhateverGreen.kext

### :heavy_check_mark: Pointing device and keyboard
You'll need a usb mouse to install the OS, as the touchpad won't work until after the install.

Do note, the built-in touchpad can stop working from time to time. Having a spare external USB or bluetooth mouse nearby is recommended. Either waiting a bit or putting the laptop in Sleep mode by closing the lid and opening again after suspension solves the problem.

#### Relevant Kexts:
- VoodooI2C.kext
- VoodooI2CHID.kext
- VoodooPS2Controller.kext

### :heavy_check_mark: Bluetooth
Working normally with the devices I use (Monterey's Bluetooth stack has gotten a rewrite, it's actually working better than before).

#### Relevant Kexts
- IntelBluetoothFirmware.kext

### :heavy_check_mark: Battery Measurement
Working normally, but reporting *Service Needed*. May be related to the battery being rather old at this point.

#### Relevant Kexts
- SMCBatteryManager.kext

#### Relevant DSDT's
- SSDT-BATT.aml

### :heavy_check_mark: Sound 
:heavy_check_mark: Internal speakers 
 
:heavy_check_mark: Internal Microphone 

:heavy_check_mark: Bluetooth Speakers 

:heavy_check_mark: USB Microphone 

:heavy_check_mark: Boot Chime 

#### Relavant Kexts
- AppleALC.kext

### ✔️ Sleep
Aparently working. Had to apply a DSDT patch so to avoid instant wake from LAN, following guide provided in [this guide](https://dortania.github.io/OpenCore-Post-Install/usb/misc/instant-wake.html). 

#### Relevant SDST's
- SSDT-GPRW.aml

# EFI
The EFI folder attached is the one used to boot the OS. The kexts attached are the ones recommended by OpenCore Install Guide, and the ones listed above. Fixes intel graphics, touchpad, battery indicator, audio, bluetooth and Wifi.

Word of caution: Some of the info under the PlatformInfo section of the conf.plist has been scrubbed before uploading. For that, you'll actually need to create your own configuration (Kudos if you actually read this far). 

# Guide

Follow the [Dortania's OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/).
