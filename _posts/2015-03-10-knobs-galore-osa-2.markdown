---
layout: post
title: Knobs Galore, osa 2
date: '2015-03-10 15:32:11'
---

Käytän syntetisaattorin runkona saksalaisen Simban *My Music World*-lelukosketinsoitinta. Kyseisellä nimellä myydään useita soittimia, mutta minun soittimeni on kuulemma oikein [modernin tyylinen](http://simbatoys.de/en/brands__products/my_music_world/keyboard_instruments/detail.shtml?sArtNr=106835366). Kosketinsoitin on varsin sopiva tarkoituksiini: siinä on juuri sopiva määrä näppäimiä käyttöliittymää varten ja se on melko pieni, mutta sen sisään on helppo laittaa esimerkiksi Papilio (tai muu piirilevy). Ennen kaikkea kuitenkin siinä koskettimisto ja näppäimistö ovat erillään itse elektroniikasta, lattakaapelilla yhdistettynä, joten ne on helppo yhdistää omiin tekeleisiini! Soitin maksoi uutena 14 euroa Mikkelin Prismassa.

![Simba My Music World](http://i.imgur.com/mneJdTVl.jpg)

*Simba My Music World*

Mielestäni syntetisaattoreissa pitää mielellään olla paljon nuppeja; mitä enemmän, sen parempi. Nupit ja slaiderit ovat paljon intuitiivisempia mielestäni kuin valikkokäyttöliittymät, joten otan niistä inspiraatiota. Ikävä kyllä lelukosketinsoittimissa ei erinäisistä syistä ole nuppeja kuin enintään äänenvoimakkuudelle, joten joudun päätymään toisenlaiseen käyttöliittymäratkaisuun. 

Käyttöliittymä on vasta suunnitteluvaiheessa, mutta ajattelin tehdä jokaista parametria varten 2 nappia: `+`, joka kasvattaa ko. parametria, sekä `-`, joka pienentää sitä &mdash; valikoita ei siis tarvita. Teen myös hienoa ja karkeaa säätöä varten omat napit: `x10`-napin painamisen jälkeen kukin napin painallus muuttaa parametria kymmenellä, ja `x1`-napin painamisen jälkeen yhdellä. Käytän kahta nappia, jotta käyttäjän ei tarvitsisi muistaa kummassa tilassa koskettimisto on kullakin hetkellä. Parametrien näyttämiseksi ei ole näyttöä, joten ne pitää säätää korvakuulolla, mutta saatan lisätä yksinkertaisen numeronäytön myöhemmin.

![Käyttöliittymä](http://i.imgur.com/trexEFyl.jpg)

*Esimerkki siitä, millainen käyttöliittymä voisi olla*

Syntetisaattorissa ei ole kovin paljon toimintoja, joten napit riittävät varsin hyvin. Säätimiä tarvitaan ainakin

 * amplitudin verhokäyrälle (`V[ADSR]`)
 * pseudosuotimen kynnystaajuudelle (`Cutoff`)
 * pseudosuotimen verhokäyrälle (`F[ADSR]`)
 * pseudosuotimen verhokäyrän määrälle (`Env`)
 * aaltomuodolle (`WF`)
 * äänenvoimakkuudelle (`Vol`) sekä
 * ohjelmamuistille (`Preset`, `Load`, `Save`)


---

Projektin lähdekoodit ovat saatavilla [GitHubissa](https://github.com/hacklabmikkeli/knobs-galore/tree/master).