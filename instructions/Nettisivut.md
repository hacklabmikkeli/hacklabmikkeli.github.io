---
layout: page
title: Nettisivujen päivitys
navigation: True
logo: 'assets/images/alien_pink.svg'
category: instructions
---

Hacklabin jäsenet voivat päivittää yhdistyksen nettisivuja, esim. esitelläkseen kiinnostavia projekteja tai tapahtumia joihin ovat osallistuneet.
Hacklabin nettisivut löytyvät [Githubista](https://github.com/hacklabmikkeli/hacklabmikkeli.github.io/). Jos sinulla ei ole kirjoitusoikeutta yhdistyksen Github tilille, voit pyytää sitä:

* [ircissä](http://webchat.freenode.net/?nick=vieras_...&channels=hacklabmikkeli&prompt=1)
* [facebookissa](https://www.facebook.com/groups/280542002155902/) 
* tai sähköpostilla (hallitus аt mikkeli dоt hacklab dоt fi).

Pävitykseen tarvitset seuraavat työkalut: (Klikkaa työkalun nimeä päästäksesi asennusohjeisiin.)

* [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [Jekyll](http://jekyllrb.com/docs/installation/) (jos haluat kokeilla muutoksia lokaalisti ennen julkaisua)

### Nettisivujen päivitys:

1.Kloonaa repository
    git clone git@github.com:hacklabmikkeli/hacklabmikkeli.github.io.git

2.Vaihda oikeaan branchiin
    git checkout source

3.Tee haluamasi muokkaukset / lisäykset. Voit kokeilla muutoksia ajamalla komennon `jekyll serve` joka kääntää sivuston ja hostaa sen paikallisesti osoitteessa [http://localhost:4000](http://localhost:4000)

4.Tee commit
    git commit -m 'Tein sitä ja tätä ja tuota'

5.Puske muutokset takaisin githubiin. (huomioi tässäkin nimenomaan 'source' branchin käyttö)
    git push origin source

Muutaman minuutin kuluttua travis kääntää uuden version nettisivusta ja julkaisee käännetyn html:än master branchiin jolloin muutokset ovat nähtävissä nettisivuilla.