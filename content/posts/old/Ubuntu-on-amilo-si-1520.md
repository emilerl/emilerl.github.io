---
title: "Ubuntu on Amilo Si 1520"
date: 2007-02-20T19:43:12+01:00
draft: false
---

![](/amilo.jpg)

_If you are looking for a HOW TO on installation of Ubuntu, please scroll down a bit._

I recently bought a new laptop from Fujitsu-Siemens – the Amilo SI 1520. My requirements for this laptop was that it should be fairly cheap (max 1000 euros), run Linux with ease and feature a 12 inch wide screen.  
After browsing through some local (Swedish) internet stores I soon concluded that I had to go with the high end consumer segment instead of the business segment, otherwise my budget requirement would have gone through the roof. I narrowed the selection down to either the Lenovo 3000 V100 or the FSC Amilo SI 1520. The Lenovo sported a higher build quality, but the FSC had better specs in almost any area (CPU, HDD, battery time etc). Both of them were proven to run Linux (Ubuntu and Gentoo), but the resources on the web was very limited (that is one of the reasons for me writing this article right now).

## Ubuntu

Installing Ubuntu 6.10 on this piece of hardware was very straightforward. I just chose to resize my Windows XP partition (want to keep it for some experimentation) to 10 GB and use the rest for Ubuntu.  
After the installation was completed it was just a matter of installing the 915resolution package to get the native resolution (1280 x 800) of the screen.

The wireless network card (Intel Corporation PRO/Wireless 3945ABG, kernel module ipw3945) was detected without problems, but ipw3945 and Gnome Network Manager applet 0.6.3 did not play together. It didn’t take long until I found out that 0.6.4 supports ipw3945 and is available in the development version of Ubuntu (Feisty 7.04).

I thought it could be fun to test the latest Ubuntu (and have nice wireless controls in Gnome) so I started to upgrade my Edge to Feisty. It is a very simple procedure. Simply make sure that your system is up to date. Then run the command:

`gksudo "update-manager -c -d"`

If it whines about authorization problems you must execute GPG as the super user (root) one time before running the update-manager. It is also very simple:

```bash
sudo su  
gpg  
[CTRL+c]  
exit
```

Then run the update-manager again.

## Hardware status

I have read a few articles about Linux on the Amilo SI 1520 and the only thing that seems a bit tricky is the built-in microphone. I can confirm that it does not work out of the box, but I have not tried to get it working. Other than that all works fine, even the so called multimedia-buttons and suspend/hibernate.

### lspci – for reference

```bash
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)  
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)  
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)  
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)  
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)  
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)  
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)  
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)  
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)  
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)  
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)  
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)  
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)  
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)  
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)  
01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)  
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)  
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832  
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)  
07:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)  
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)  
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```