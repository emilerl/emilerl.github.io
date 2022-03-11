---
title: "Pretty code"
date: 2006-12-30T19:08:35+01:00
draft: false
---

Something I have wanted for a long time is an efficient way of highlighting syntax for an arbitrary file. Like uploading a file to some server and then execute a query like this:

`http://myserver.com/scripts/highlight?url=http://www.someserver.com/MyClass.java&language=java&showlines=false`

And it would generate a clean HTML-output with the code highlighted and pretty.

Since I have not found any site that allows me to do that (even if [this](http://www.sweetapp.com/cgi-bin/cgi-styler-form.py) one is close) I’m going to write my own service based on [SilverCity](http://silvercity.sourceforge.net/). My plan was first to use [GNU Enscript](http://www.codento.com/people/mtr/genscript/) as many other similar services do and marry that together with [Django](http://www.djangoproject.org/) and a database of code (i.e. each code snippet/file should be cached). Those ideas where just to wild, and after a little searching I found SilverCity which is a Python module for doing the same thing as Enscript, but not using external processes.

So the new design will make the code stay on different servers (where it belongs) and just colorize code upon request.