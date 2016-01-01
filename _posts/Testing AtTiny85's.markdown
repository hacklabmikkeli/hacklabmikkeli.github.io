---
layout: post
title: Testing AtTiny85's
date: '2016-01-01 20:09:41'
---
*Testing....*
![AtTiny85_test](http://i.imgur.com/sW9Hx79.jpg)
Some projects doesn't need big'n beefy microcontroller, this little one can tackle many projects like RTC clock
or say matrises & cubes with shift registers.  Clock frequency is selectable between 1Mhz-20Mhz, but 16 seems to be enough. 16 needs external crystal,
but some people have managed to install it as internal freguency.
Only problem with this chip is that there is no hardware serial (well, there is i2c bus but needs to be enabled separately, bit different than normal serial), but that can be created with code. Test code I burned was just simple
10hz led-blinker, but that's enough proof whether ic works at all, and It's fast to load this code.

After testing, better to store these accordingly, ready to be used now:
![AtTiny85__test_OK](http://i.imgur.com/i5yK14Q.jpg) 
