---
title: "Python Hacking Revisited"
date: 2005-07-13T19:00:25+01:00
draft: false
---

It is about a year since I last layed hands on Python, but recently my interest started to grow again. As a former Perl-hacker, I must say I really like Python in a lot of way. It has the same power as Perl, but with better structure and more readable syntax.

Anyway… While coding some utility scripts on my Windows machine I found a need for searching the PATH environment variable after some executables. I created a small utility module that searches any path (semi colon separated or not) for a specific file and returns the absolute path if it was found or None if it was not.

You can get the piece of software here: pathfind.py.

If you omit the second argument in the search function, os.environ['PATH'] will actually be used as default. You can change that to any valid path of your choice.

**NOTE!** *This script is only compatible with Win32-environments as of now.*