---
layout: post
cover: 'http://i.imgur.com/JEhXoJF.png'
title: Knobs Galore, osa 3
date:   2015-03-13 12:04:00
tags: project
subclass: 'post tag-project'
categories: 'casper'
---

Nyt on jo ääninäytettä tarjolla!

<iframe width="100%" height="450" scrolling="no" frameborder="no" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/195661180&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;visual=true"></iframe>

Okei, se ei ole oikeasta vaan simuloidusta syntetisaattorista. Kyseistä näytettä varten toteutin ramppigeneraattorin, ADSR-vaippageneraattorin vaihevääristymäparametria (*"cutoff"*) varten, vaihevääristimen sekä siniaalto-look-up-taulukon. Lisäksi toteutettuna on D/A-muunnin ja rengaspuskuri, jotka tulevat lopulliseen syntetisaattoriin. Olen kasannut suunnitelmani oheiseen kuvaan, jonka mukaan toteuttamatta ovat vielä ohjaus ja vahvistus, sekä tietenkin integraatio koskettimistoon ja näppäimiin.

![Suunnitelmia](http://i.imgur.com/JEhXoJF.png)
*Suunnitelma lopullisesta systeemistä*

Nykyisellään syntetisaattorin voi myös syntetisoida *(heh)* ja ladata Papilioon, mutta se on vain monofoninen, sillä äänten allokointia ei ole toteutettu. Ajattelin aluksi, että äänet allokoitaisiin "älykkäästi" (otetaan aina seuraava vapaana oleva kanava käyttöön), mutta Xilinx ISEn raporteista kävi ilmi, että nykyisellään vain 2% sliceistä on käytettynä. Kellopulssejakin on käytössä 488 kutakin näytettä kohden, joten voin yhtä hyvin varata kullekin koskettimelle yhden kanavan, joten äänien allokoinnista tulee triviaali tehtävä, ja bonuksena syntetisaattoriin tulee täysi polyfonia!

Seuraavaksi aion kasata piirilevylle kalvokytkimistä pienen "koskettimiston", joiden avulla syntetisaattoria voi soittaakkin (: sitä seuraavana listalla ovat myös vahvistuksen toteuttaminen (ajattelin toteuttaa sen yksinkertaisena look-up taulukkona, kuten vaihevääristymän ja aaltomuotogeneroinnin) ja moniäänisyys.

---

Projektin lähdekoodit ovat saatavilla [GitHubissa](https://github.com/hacklabmikkeli/knobs-galore/).
