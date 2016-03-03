---
layout: post
cover: 'http://i.imgur.com/taSULgy.jpg?1'
title: Started doing car computer
date:   2016-03-03 22:46:41
tags: project
subclass: 'post tag-project'
categories: 'casper'
---

Long time I've longed for this project as I lacked skill. Now was great time for this project, as I've stumbled on teensy 3.2. 
Teensy 3.2 has horsepower and memory for pretty much all projects possiblse, and in this case I'm planning to combine quite many tasks
to one microcontroller; car computer data, RTC, gps tracking(which also has combined feature of theft-alarm, using SIM800L) as well as
real-time audio manipulation along FFT. First things first, I started checking simple commands, like read battery voltage, and true indeed,
it worked. The device I use for talking with car computer (ECU) is sparkfun's obd-uart board, which allows any serial capable device to serve as end-terminal
for diagnostics.
I've so far managed to put code that allows pretty much all real-time data to be checked, even throttle and stress levels, as well as draw bar display of reguested values.
In this photo is initial test which has echo as well as carbage characters, but they were ok back the initial testing whether my car's protocol is supported or not.
Also, screen is in photo 20x4 alphanumeric LCD, but currently I'm using 0,96" 128x32 OLED, it has many benefits over lcd, except size, but I'll place it anyway right on front of my eyes so 0,96" is enought.
![computer](http://i.imgur.com/taSULgy.jpg?1)
