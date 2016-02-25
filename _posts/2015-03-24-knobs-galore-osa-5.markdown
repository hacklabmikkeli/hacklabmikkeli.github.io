---
layout: post
cover: false
title: Knobs Galore, osa 5
date:   2015-03-24 15:30:11
tags: project
subclass: 'post tag-project'
categories: 'casper'
---

Tein äänisimulaation muutamista soundeista:

<iframe width="100%" height="450" scrolling="no" frameborder="no" style="margin-bottom: 2em;" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/197454385&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;visual=true"></iframe>

Kuten näytteestä kuuluu, äänet ovat vielä karuja verrattuna esimerkiksi *CZ-101*:n, mutta niissä alkaa olla jo hieman vaihtelua. Yritin saada ääneen lämpöä omalla tavallani: pitkissä "jousi"soundeissa joka toisen aallon taajuus on moduloitu LFO:lla, jolloin syntyy eräänlainen chorusing-efekti.

"Resonanssi" niin ikään on toteutettu samankaltaisella tekniikalla: joka toisen aallon taajuus ei tulekaan koskettimistolta, vaan se on laskettu "suodattimen" rajataajuus. Resonanssiin käytetty aalto on aaltomuodoltaan tietenkin siniaalto, jollon spektriin muodostuu resonanssipiikki. Molemmissa tapauksissa muokkaamaton "perusaalto" tulee aina tasaisin väliajoin, joten äkillisten signaalihyppyjen välttämiseksi muokatut aallot kerrotaan ikkunafunktiolla. Tätä tekniikkaa voi verrata kahteen, synkronoituun oskillaattoriin, mutta se lisää ääneen lisäksi oktaavin verran perustaajuutta matalamman ääneksen.
