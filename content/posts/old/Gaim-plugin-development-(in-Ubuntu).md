---
title: "Gaim Plugin Development (in Ubuntu)"
date: 2006-05-19T19:12:15+01:00
draft: false
---

I recently remembered that [Gaim](http://gaim.sourceforge.net/) has a nice [Perl API](http://gaim.sourceforge.net/api/perl-howto.html) for writing plugins (or actually I was rembembered by a friend). I decided to test it out by writing a plugin for displaying the current playing song in [Rhythmbox](http://www.gnome.org/projects/rhythmbox/) in instant messages when the keyword ‘%rb’ is found (I know there is a [plugin](http://gaim-rhythmbox.sourceforge.net/) for that already, but I did not get that to work).

The first step was to download the small source for the Perl API example from the Gaim site and try to get it to work. I placed the script in _~/.gaim/plugins_, but sadly it did not load when I started Gaim. Time to start to debug the supposed-to-work-sample-code … how I love that.  
The first thing that hits you when you are starting to read the debug messages from a Gaim session is that many of them are a bit strange, like these two:

`dns[30097]: Oops, father has gone, wait for me, wait...!`
`dns[742]: nobody needs me... =(`

After firering up Gaim with the _-d_ flag I started to realize that the version of Gaim I was using was not compiled with the Perl extension. Or actually, the Ubuntu package I use does not include it (I probably will check out why later on and submit a bug because I think it should be there).  
Fortunately it was pretty straight forward to build the Perl extension by hand and just moving to _/usr/lib/gaim_ without disturbing anything else in my system.

So when the Perl extension was available and _Gaim.pm_ was ready in _@INC_ I could finally load the sample script into Gaim. I thought this was going to be easy. I had already prepared the script that reads information from Rhythmbox by executing the command line interface with different flags. How hard could it be to just plug that in when a message was sent? Pretty hard I tell you 🙂

I understod from the API that I could connect my callback functions to different signals, but I could not find any complete listing of these signals. I finally found this test file _signals-test.c_ in the Gaim source tree containing test calls for all the supported signals. From there I got a fairly good idea of how the signals was implemented in C and which signal I should use (_sending-im-msg_).  
The next headache was this anoying little message in the debug log of Gaim:

`signals: Signal data for sending-im-msg not found.`

The code snippet below is the one generating this irritating message. All the examples (which are few) of how to use the _Gaim::signal_connect_ function passes in either an empty variable or _undef_ as the last “data” parameter.

```perl
Gaim::signal_connect( Gaim::Conversations::handle, "sending-im-msg", $plugin, \&signal_sending_im_cb, undef);  
```

However, the sending-signals requires this variable to be a Perl hash. This took some time to figure out. I had to go to the Gaim plugin repository at Sourceforge.net and find another Perl plugin to compare with. So after changing “undef” to \%data (which is some undefined variable by the way) it all worked out nicely.  
After entering the magic string _%rb_ in a Gaim IM conversation, my counterpart got these magic words:  
**Emil** is playing “**Nutshell**” by **Alice in Chains** from **Unplugged** at **2:22**(**5:00**).

The conclusion from this small coding adventure is that the API for writing Perl plugins for Gaim is fairly weak. The introduction tuturial is quite good, but lacks certain details. If I get some time over sometime I could perhaps help out with that.  
If you would like to see the result, you can get it [here](http://www.buglix.org/code/box.txt) (or see it syntax highlighted by VIM [here](http://www.buglix.org/code/box.html)).