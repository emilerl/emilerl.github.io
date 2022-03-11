---
title: "Cross Platform Tooling   the Best of Two Worlds"
date: 2006-12-31T19:22:19+01:00
draft: false
---

I have recently been working on a project where the target operating system is Windows XP. Since I do not have a Windows XP installation, I started writing code on Linux and since it worked fine in the beginning, I continued doing so throughout the development phase of the project. At a later stage when it was time to start testing and integrating on Windows I discovered one or two platform specific errors in the code, that I easily fixed.

The major benefit was that I could use free tools for validating the software, like [Valgrind](http://valgrind.org/) (with CallGrind enabled for profiling data), [KCacheGrind](http://kcachegrind.sourceforge.net/cgi-bin/show.cgi) and [GProf](http://www.gnu.org/software/binutils/manual/gprof-2.9.1/gprof.html) that would have been hard, or even impossible in some situation if I had developed only on Windows XP.  
Just for the fun of it, I tried to build it on Mac OS X 10.4 just to see if it worked – and it did! Right out of the box. That is another major benefit of multi platform development. The chances that it works right out of the box on a new platform is significantly higher than if only one target platform is used.

Since I now could build the code on three platforms without breaking a sweat, I added multiple targets to our [automatic build](http://blog.purplescout.se/2006/12/29/automatic-multiplatform-build-and-test-system/) system. That was simply to prevent that new code that would prevent the multi platform build qualities should be introduced into the system.

![](/KcgShot3.gif)