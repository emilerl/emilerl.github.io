---
title: "Image Grinder Light"
date: 2006-08-30T19:20:39+01:00
draft: false
---

In my [Projects](http://buglix.org/projects) page I have a description of a tool called Image Grinder wich I’m working on. Since I’m implementing it in C++ and wxWidgets it takes some time (I don’t think C++ is a very creative language – don’t know why I chose it realy). Today I switched mode of the camera to capture both Raw and JPEG’s for each photo, and when I was about to transfer the images to my PC I realized that I need a good “Image Grinder” to copy the images to their locations. You see, I don’t want my Raw’s mixed up with the JPEG’s. I have two folders in my home directory: Pictures and RawPictures.

So I sat down for an hour or so implementing this functionality in a very simple Python script. Right now it requires a little configuration inside the script specifying an output directory per file extension (i.e. .jpg => /home/emil/Pictures etc.). It can be completely command line driven so it can be used from another script (listening on the D-Bus for USB events for instance) and simply takes a input directory and a description of the files.

Usage:  
```zsh
imagetransfer, v0.0.1 - Copyright (C) 2006 Emil Erlandsson  
Usage: imagetransfer.py [path] ([description] -d)  
Where ...  
* [path] is the location where the images are stored.  
* [description] is optional. If not given, it will  
be asked for via stdin.  
* -d is also optional. If given (last) it will remove the  
original files. Use with care!  
```

I’m not sure if I will evolve the original Image Grinder idea or if I will play with this script some more and add features.

You can download the script here:   
[http://www.buglix.org/wp-content/uploads/imagetransfer.py](http://www.buglix.org/wp-content/uploads/imagetransfer.py) and a needed utility script here:   
[http://www.buglix.org/wp-content/uploads/namefix.py](http://www.buglix.org/wp-content/uploads/namefix.py)

_Update 2006-12-31_

You can now get the code highlighted as well. Click on the links below for a prettified version:

-   [imagetransfer.py](http://hacka.mine.nu/cgi-bin/highlight.py?url=http://www.buglix.org/wp-content/uploads/imagetransfer.py&language=python&showlines=on)
-   [namefix.py](http://hacka.mine.nu/cgi-bin/highlight.py?url=http://www.buglix.org/wp-content/uploads/namefix.py&language=python&showlines=on)