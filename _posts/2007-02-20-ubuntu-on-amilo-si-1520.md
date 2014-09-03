---
layout: post
title: Ubuntu on Amilo SI 1520
---


[![](http://farm1.static.flickr.com/166/396526427_7c5efdb471_m.jpg)](http://www.flickr.com/photos/emilerl/396526427/)

<p class="message">
  If you are  looking for a HOW TO on installation of Ubuntu, please scroll down a bit.
</p>

I recently bought a new laptop from Fujitsu-Siemens - the Amilo SI 1520. My requirements for this laptop was that it should be fairly cheap (max 1000 euros), run Linux with ease and feature a 12 inch wide screen.
After browsing through some local (Swedish) internet stores I soon concluded that I had to go with the high end consumer segment instead of the business segment, otherwise my budget requirement would have gone through the roof. I narrowed the selection down to either the Lenovo 3000 V100 or the FSC Amilo SI 1520. The Lenovo sported a higher build quality, but the FSC had better specs in almost any area (CPU, HDD, battery time etc). Both of them were proven to run Linux (Ubuntu and Gentoo), but the resources on the web was very limited (that is one of the reasons for me writing this article right now).



## Ubuntu



Installing Ubuntu 6.10 on this piece of hardware was very straightforward. I just chose to resize my Windows XP partition (want to keep it for some experimentation) to 10 GB and use the rest for Ubuntu.
After the installation was completed it was just a matter of installing the 915resolution package to get the native resolution (1280 x 800) of the screen.

The wireless network card (Intel Corporation PRO/Wireless 3945ABG, kernel module ipw3945) was detected without problems, but ipw3945 and Gnome Network Manager applet 0.6.3 did not play together. It didn't take long until I found out that 0.6.4 supports ipw3945 and is available in the development version of Ubuntu (Feisty 7.04).

I thought it could be fun to test the latest Ubuntu (and have nice wireless controls in Gnome) so I started to upgrade my Edge to Feisty. It is a very simple procedure. Simply make sure that your system is up to date. Then run the command:

`gksudo "update-manager -c -d"`

If it whines about authorization problems you must execute GPG as the super user (root) one time before running the update-manager. It is also very simple:

`sudo su
gpg
[CTRL+c]
exit`

Then run the update-manager again.



## Hardware status


I have read a few articles about Linux on the Amilo SI 1520 and the only thing that seems a bit tricky is the built-in microphone. I can confirm that it does not work out of the box, but I have not tried to get it working. Other than that all works fine, even the so called multimedia-buttons and suspend/hibernate.


[
![TuxMobil - Linux on Laptops, Notebooks, PDAs and Mobile Phones](http://tuxmobil.org/pics/tuxmobil_sticker.png)
](http://tuxmobil.org/fujitsu.html)
