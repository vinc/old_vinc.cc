---
layout: page
title: "DaSort"
comments: false
sharing: false
footer: false
github: "dasort"
---

DaSort is a CLI tool for sorting and grouping picture by date.

It is written in Python and need pyexiv2 module to read Exif data in
pictures. Argparse module is also required but it is now included in
Python 2.7.

A duplication detection algorithm is built in DaSort to skip duplicate
pictures without forgeting different versions of the same original.

Installation
------------

Installing from source: `git clone git://github.com/vinc/dasort.git; cd dasort; python setup.py install`

Usage
-----

Importing pictures to a sorted tree is as simple as:

    $ dasort /media/disk ~/pictures
    Scanning '/media/disk' ...
    Examining 31348 files ...

     100% [==================================================================]

     2884 of 31348 files imported
     27991 duplicated pictures ignored
     473 files ignored (listed in 'ignored.txt')

With the duplication detection algorithm this command can be run from multiple
sources to the same destination.

Use `dasort -s` to make symbolic links instead of copy.

Supported image formats
-----------------------

The following formats have been successfuly tested: JPEG, CR2, CRW, TIFF.

Proprietary RAW format from other brands than Canon have not been tested yet
but they should work too. Let me now.

DaSort also recognise UFRaw ID files containing all the conversion parameters
so they will be imported too.
