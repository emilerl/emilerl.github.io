---
title: "BinOcular - Bits in Structure"
date: 2006-03-22T19:08:35+01:00
draft: false
---

I would like to take the oppertunity to talk a little about our latest project at Purple Scout.

BinOcular - Tabs featureBinOcular is the response to an ever-growing need to browse different kinds of binary files, both modern well documented formats, as well as obscure legacy ones. When developing products, the developer is frequently faced with the problem to deal with binary files in some way or the other. The reasons for having to deal with binary data formats today are many, and could for example be viewing of scientific data files, looking into image formats for specific headers, “debugging” of the output from some tool or simply having to deal with legacy data formats.

To solve these problems, Purple Scout offers a solution divided into two parts. The first part is a Java Library for usage in existing applications. It takes XML specifications of file formats as input and while parsing the binary file it builds an Abstract File Tree (AFT) containing all the information in a more processing friendly format. The AFT could then be used to generate reports via XSLT style-sheets, or via visualization which takes us into the second part of the solution – the Eclipse based viewer.

## Hexadecimal Editor
BinOcular - HexviewBinOcular is built as a set of Eclipse Plugins. The most basic part is the Multipart Editor which defines the common view of an binary editor (or reader if you will – “editor” is the Eclipse name of a component dealing with viewing and editing files). It defines two basic views: a hexadecimal view – where frequent hex editor users will feel right at home – and a tree view visualizing the AFT. The hexadecimal view lets the library express the binary file in its most raw form. The tree view showing the AFT gives the user an opportunity to easily get an overview of the file. BinOcular has support for something called “Specific editors”. They extend the plugin, by adding more views specific to a binary format. For instance, if you are working with image files, you might want an area where you can browse the actual image as well as all the meta information for the file.