# Kodi-webOS-3.x-Test-Build

https://github.com/Diniboy1123/xbmc-webos/releases/download/before-rebase/org.xbmc.kodi_20.90.101_arm_wayland1_minimal.ipk

# Attention very important:
Immediately after installation, enter the following command in Terminal or SSH and only then start Kodi:

`cp /usr/lib/libwayland-egl.so /media/developer/apps/usr/palm/applications/org.xbmc.kodi/lib/libwayland-egl.so.1`


Since the memory of some TVs is very limited, you should mount the `.kodi` folder on a USB stick.

Install Kodi, copy the entire .kodi folder on USB to `/tmp/usb/sda/sda1/` and then delete the entire contents of the `.kodi` folder on the TV. The folder must remain empty.

The .kodi folder must be mounted with the following single commands (one after the other) in terminal/PuTTY SSH:


`#!/bin/sh`

`jailer -S -t native_devmode -p /media/developer/apps/usr/palm/applications/org.xbmc.kodi -i org.xbmc.kodi`

`mount -o bind /tmp/usb/sda/sda1/.kodi /var/palm/jail/org.xbmc.kodi/media/developer/apps/usr/palm/applications/org.xbmc.kodi/.kodi`

To make this permanent, you must copy the kodi file/script to `/var/lib/webosbrew/init.d/`. 

# Attention! 
The kodi script file must have the authorization 775 in order to be executed. If this is not the case, make the file (kodi) executable with chmod +x, or set the permission to 775 directly in the `ininit.d` folder with FileZilla.

Known issues:

When Kodi encounters an error, it creates “core dump” files ranging in size from 300 to 500 MB without you noticing. Sometimes three to five such files accumulate and take up all the storage space. In this case, Kodi cannot be started at all. Therefore, check the directory regularly and delete all “core.xxxx” files. These “core dump” image data are stored in the directory ```/media/developer/apps/usr/palm/applications/org.xbmc.kodi/```. See image.

![11](https://github.com/user-attachments/assets/23036543-0a1e-47bb-ad4c-2dcb971d84c6)

Note:
If there is no storage space available on your device for the Kodi installation, check the ```/media/preload/storedemo/``` directory for demonstration videos that are often used in retail stores to showcase the devices and delete them.

Source: https://github.com/Diniboy1123/xbmc-webos
