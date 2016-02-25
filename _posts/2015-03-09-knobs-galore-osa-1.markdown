---
layout: post
cover: 'http://i.imgur.com/uMUln3El.jpg'
title: Knobs Galore, osa 1
date:   2015-03-09 19:00:15
tags: project
subclass: 'post tag-project'
categories: 'casper'
---

Knobs Galore on kehitteillä oleva digitaalinen syntetisaattori, jota rakennan halvan lelupianon runkoon. Se toimii Casion CZ-linjan syntetisaattoreissaan käyttämällä vaihevääristymäsynteesitekniikalla, josta käytetään joskus lyhennettä *PD (Phase Distortion)*. PD:n voidaan kuvailla olevan jotakuinkin vaihemodulaatiosynteesin ("FM"-synteesi) ja analogisissa syntetisaattoreissa käytetyn subtraktiivisen synteesin välimaastossa. Valitsin vaihevääristymäsynteesin, koska FM:n verrattuna siinä on paljon vähemmän parametreja (joten se on helpompi oppia), ja toisin kuin subtraktiivisessa synteesissä, siinä ei tarvita digitaalisia suodattimia.

<iframe width="420" height="315" src="https://www.youtube.com/embed/W6vyCNWJVME" frameborder="0" allowfullscreen></iframe>

*Esimerkki vaihevääristymäsynteesistä*

Ajattelin aluksi toteuttaa syntetisaattorin mikrokontrolleripohjaisena, mutta huomasin pian, että ainakin 8-bittisten mikrokontrollerien tehot jäivät liian pieniksi polyfoniselle syntetisaattorille &mdash; esimerkiksi 44kHz näytteenottotaajuudella kunkin näytteen laskeminen vie 23 mikrosekuntia, jollon 1MHz prosessorilla 8 ääntä käyttäen on alle 3 kelloa aikaa kutakin näytettä varten. Tilannetta voisi helpottaa puskuroinnilla ja DMA:lla, mutta siihenkään ei pelkkä mikrokontrolleri riitä. Lopulta päätin tehdä syntetisaattorin FPGA:ta käyttämällä, jolloin kullakin kellolla voi tehdä paljon enemmän. Valitsin Papilio-merkkisen FPGA-protoilulaudan, koska se on melko halpa, siihen on saatavilla paljon lisäkrääsää, kuten valmis 3,5mm-jakkiliitinmoduli (ja MIDI-moduli), ja siinä on kattava ohjeistus.

![Papilio One](http://i.imgur.com/uMUln3El.jpg)

*Papilio One*

---

Projektin lähdekoodit ovat saatavilla [GitHubissa](https://github.com/hacklabmikkeli/knobs-galore/tree/master).
