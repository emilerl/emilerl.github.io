---
title: "Jaunty Jackalope on Asus Eee Pc 1008HA"
date: 2009-07-17T20:39:23+01:00
draft: false
---

Two days ago, during a time of intensive writers block, I went out and bought an Asus 1008HA to use as a lightweight writing machine and surf station. Since I brought it home I have removed Windows XP and installed [Ubuntu Jaynty Jackalope](http://www.ubuntu.com/) (both standard desktop edition and [netbook remix](https://wiki.ubuntu.com/UNR)) and [Intel’s Moblin 2.0](http://moblin.org/documentation/test-drive-moblin) without running into any serious trouble.

![](/asus_eeepc_1008ha_ubuntu.jpg.webp)

Neither the wired or the wireless network does not work out of the box (works as a charm in Moblin though) after installing, but it was just a matter of downloading the .deb package of the linux-backports-modules (for the 2.6.28-11 kernel which is default in Jaunty Jackalope) which can be found [here](https://launchpad.net/ubuntu/jaunty/i386/linux-backports-modules-2.6.28-11-generic/2.6.28-11.11).

```bash
sudo dpkg -i http://launchpadlibrarian.net/24046277/linux-backports-modules-2.6.28-11-generic_2.6.28-11.11_i386.deb
```

After a quick reboot (it boots really fast) the wireless network worked without any fuzz (I haven’t bothered fixing the wired network yet, but there are instructions floating around on the web). Before updating the system I installed the meta package for linux-backports-modules so that the upgraded package would be installed during system upgrade. Open “System -> Administration -> Synaptic Package Manager”, select “Settings -> Repositories” and enable jaunty-backports and reload the package database. After that, open a terminal and issue the command:

```bash
sudo aptitude install linux-backports-modules-jaunty
```

After that, you can update the system without having to manually download the `.deb file and install after each kernel upgrade.

All in all I am very happy with the 1008HA and Jaunty Jackalope standard desktop edition. The netbook remix wasn’t really my cup of tea and Moblin, even though very good looking, has to much beta feeling for me to use it on a day to day basis. Almost everything I need works out of the box (sound, suspend, hibrenate, hardware keys etc).

![](/ubuntu-904-1008ha.png.webp)