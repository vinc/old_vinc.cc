---
layout: post
title: "Oximon 0.0.2 released"
date: 2013-05-22 08:30
comments: false
categories: [Announce, Project]
---

[Oximon][1] is a very simple command line tool written in Python to record data
from [pulse oximeters][2]. It follows the [KISS Principle][3] and its output
makes it easy to be used by other programs:

    $ oximon --port /dev/ttyUSB0 
    #date   heart rate  oxygen saturation
    2012-01-03 07:22:14.951777  54  97
    2012-01-03 07:22:15.499333  54  97
    2012-01-03 07:22:16.534203  54  97
    2012-01-03 07:22:17.870198  54  97
    2012-01-03 07:22:19.073182  54  97
    2012-01-03 07:22:20.392127  54  97

Oximon is shipped with a [Gnuplot script][4] that shows how to use this output
to generate graphs. In version 0.0.2, they got much prettier:

![gnuplot sample result](/images/gnuplot.png)

The next step is probably to do something about the [REM sleep][5] stages that
are surprisingly easy to spot.

As usual the source code is available at [GitHub][6].

[1]: /projects/oximon
[2]: https://en.wikipedia.org/wiki/Pulse_oximetry
[3]: http://en.wikipedia.org/wiki/KISS_Principle
[4]: https://github.com/vinc/oximon/blob/master/scripts/graph-session.plt
[5]: http://en.wikipedia.org/wiki/Rapid_eye_movement_sleep
[6]: https://github.com/vinc/oximon
