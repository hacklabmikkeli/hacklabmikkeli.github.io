---
layout: post
cover: 'http://i.imgur.com/ZRf5UBK.jpg'
title: Car voltage meter
date:   2016-03-17 22:46:41
tags: project
subclass: 'post tag-project'
categories: 'casper'
---

Part of this bigger project, car computer, I wanted sepatate meter for voltage, in case of alternator fault.
Idea is simple; voltage divider circuit converts voltage for more suitable level for AtTiny85 that can handle up to 5 volts to ADC (analog to digital converter
and Attiny then converts this data and shows it in 7-segment display. Also there is bargraph display to give another perspective, easier to look on-road that charge level is in "green"
region, not too much or too low.
![voltagemetercircuit](http://i.imgur.com/hHYGoGx.jpg)

Once again, prototyping started at breadboard, and I also made AtTiny programming shield for easier coding sessions, no need to play that much with jumper wires.
![voltagemeterbreadboard](http://i.imgur.com/QUHLYzB.jpg)
![voltagemetershield](http://i.imgur.com/RMdzoNE.jpg)

There was quite chore to place all stuff in confined area (inline fuse is also coming in final installation):
![voltagemeterproto](http://i.imgur.com/oflhAzT.jpg)
![voltagemeterproto1](http://i.imgur.com/vHHT4UJ.jpg)

Another trouble was finding suitable enclosure, but recently bought 52mm dashboard meter casings, and all that was needed was meter panel, solution was 3d-printer.
![voltagemeter3dprint](http://i.imgur.com/AFH2g7X.jpg)
And in the end, it looks quite good in dark too:
![voltagemeterdark](http://i.imgur.com/kgAxl9h.jpg?1)
