---
layout: post
title: 7-band equalizer
date: '2016-02-05 15:41:41'
---

Not yet FFT, but getting close, this is simple 7-band graphic equalizer. Microphone amplifier, which has fixed gain of 20db, measures
surrounding noises. These noises are then fed to msgeq7-chip, made by MSI. Bit expensive chip, and so far only sparkfun seems to sell them.
What it does, is creates 7-band of different frequency regions, all are peak-detected and well filtered. Also, it creates 20db amplification.
This dc-voltage from msgeq7 is then fed to teensy 3.2, microcontroller that does rest of magic; controls msgeq7, reads and stores values, as well controls i2c 
bus OLED screen (128x64, blue colour). There is also bit conversion made before showing data, and that is just simple mapping function.
I don't have audio shield yet, but couple of those should arrive next week, and with that is possible to manipulate/mix and stuff like that real time at 16bit/44khz (cd quality)
as well as control real time FFT. But, even this simple version works well:
