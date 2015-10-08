---
layout: post
title: Knobs Galore, osa 4
date: '2015-03-14 11:44:52'
---

Rakensin pienen "koskettimiston" breadboardille, joten nyt härpäkettä voi soittaakin!

<iframe style="margin-bottom: 2em;" width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLXbye9qrKoGMEYXIAMA_NOajRKy-63R59" frameborder="0" allowfullscreen></iframe>

Soitin on vielä monofoninen, mutta lisäsin siihen ohjatun vahvistimen, joten se ei kuulosta enää yhtä karulta kuin aikaisemmin. Vahvistimen lisääminen tosin lisäsi piirin viemää tilaa FPGA:lla melkoisesti, joten jouduin hieman laskemaan sen tarkkuutta tulevaisuutta ajatellen. Myöhemmin pitää keksiä vahvistimelle vähemmän tilaa vievä ratkaisu. Julkaisin projektin GNU GPL 3-lisenssin alaisuudessa, jossa tosin puhutaan vain ohjelmistosta, mutta eikö teknisesti ottaen FPGA:n muistiin ladattu bitfile ole jonkin sortin ohjelmisto, vaikka sitä ei mikroprosessorilla ajetakaan?

---

Projektin lähdekoodit ovat saatavilla [GitHubissa](https://github.com/hacklabmikkeli/knobs-galore).