---
layout: default
title: Introduction
permalink: /outline/intro.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/intro.html

{% endcomment %}

<section>
Clojure intro
----------------------------------------
{: .slide-title .chapter}

* Miksi Clojure?
* Missä Clojure on hyvä?
* Miltä Clojure näyttää?
    - Koodi kommentit
* Mikä on "Read Eval Print Loop"?
* REPL Käytännössä
</section>

<section ng-controller="NarrativeController">
## Miksi Clojure?
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> Jos et ole koskaan ohjelmoinut et ehkä tiedä että on olemassa monia
> ohjelmointikieliä. Kuten C, Javascript, Python ja Java
{: ng-show="block11" .description}

> Miksi opetamme Clojurea? Se ei ole yhtä suosittu kuin monet muut kielet.
> Mutta Clojuressa on kolme ominaisuutta jotka tekevät siitä mahtavan
> kielen ensimmäiseksi ohjelmointikieleksi.
{: ng-show="block11" .description}

#### Clojure on _yksinkertainen_ <button class="link" ng-bind-html="details" ng-model="block12" ng-click="block12=!block12"></button>

> Clojure on _yksinkertainen_. Mutta tehokas. Clojuressa ei ole montaakaan
> hallittavaa asiaa tai konseptia, jotta voit aloittaa ohjelmoinnin. Ja ne eivät
> ole kamalan vaikeita. Huomaat, että tarvitset vain pientä osaa kielen
> ominaisuuksista hienojen asioiden tekemiseksi.
{: ng-show="block12" .description}

#### Clojure on  _yleiskäyttöinen_ <button class="link" ng-bind-html="details" ng-model="block13" ng-click="block13=!block13"></button>

> Joillain kielillä on hyvin erityinen tarkoitus. Kuten Javascript-
> kieli oli aikoinaan tarkoitettu vain selainsovellusten ja verkkosivujen
> kehittämiseen (joskin tämä ei enää aivan pidä paikkaansa). Objective-C on
> pääasiassa tarkoitettu iPhone kehittämiseen jne. Tänään me lähinnä piirrämme
> Clojurella, mutta Clojurea voi käyttää monenlaiseen tekemiseen.
{: ng-show="block13" .description}

#### Clojure on _hauskaa!_ <button class="link" ng-bind-html="details" ng-model="block14" ng-click="block14=!block14"></button>

> Clojure on _hauskaa_. Tämä on toki vain meidän mielipiteemme!
> Toivottavasti tänään huomaat saman!
{: ng-show="block14" .description}
</section>

<section ng-controller="NarrativeController">
## Missä Clojure on hyvä?
{: .slide_title .slide}

#### <button class="link" ng-model="block21" ng-click="block21=!block21">Intro</button>

> Vaikka Clojure onkin yleiskäyttöinen ohjelmointikieli, sillä on omat erityisen
> hyvät piirteensä.
{: ng-show="block21" .description}

#### Tiedon käsittelyssä <button class="link" ng-bind-html="details" ng-model="block22" ng-click="block22=!block22"></button>

> Clojure on hyvä tiedon käsittelyssä. Clojuressa on hyviä valmiita tietorakenteita ja
> siinä on sisäänrakennettuna monia ominaisuuksia jotka helpottavat erilaisen datan kanssa
> toimimista.
{: ng-show="block22" .description}

#### Samanaikaisuudessa <button class="link" ng-bind-html="details" ng-model="block23" ng-click="block23=!block23"></button>

> Samanaikaiset tapahtumat ovat usein vaikeita ohjelmointiteknisesti, vaikka
> me ihmiset olemme suhteellisen hyviä toimimaan yhtäaikaisesti.
> Clojuressa yhtäaikaisuus ei ehkä ole edelleenkään helppoa, mutta kieli sisältää
> ominaisuuksia jotka helpottavat ja yksinkertaistavat tätä rutkasti.
{: ng-show="block23" .description}

#### Kaikessa! <button class="link" ng-bind-html="details" ng-model="block24" ng-click="block24=!block24"></button>

> Clojurella on myös hauskaa piirtää
> [Quill-kirjastolla](https://github.com/quil/quil). 
> Tätä teemmekin tänään yhdessä :)
{: ng-show="block24" .description}
</section>

<section ng-controller="NarrativeController">
## Miltä Clojure näyttää?
{: .slide_title .slide}

```clojure
(print-str "Hello, World!")
(+ 3 4)
(forward :trinity 40)
```

#### Sulkeet <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Huomaat varmasti sulkeet. Sulkeiden sisällä on komentoja Clojure kielellä. Vasen sulku
> aloittaa komennon, ja vastaava oikea sulku lopettaa sen. Clojure-koodissa on paljon
> sisäkkäisiä sulkeita, eli sisäkkäisiä komentoja.
{: ng-show="block31" .description}

#### Funktiot <button class="link" ng-bind-html="details" ng-model="block32" ng-click="block32=!block32"></button>

> Sulkujen sisällä on komentoja. Näitä kutsumme useimmiten _funktioiksi_.
> Funktiot ovat Clojuren työhevosia. `print-str`, `+` ja `forward` 
> ovat funktioita.
> Clojuressa funktiot palauttavat aina arvon.
{: ng-show="block32" .description}

#### Parametrit <button class="link" ng-bind-html="details" ng-model="block33" ng-click="block33=!block33"></button>

> Monet funktiot ottavat parametreja. Parametreja voidaan käyttää
> funktion sisällä, esimerkiksi
> `print-str`:lle annetaan parametriksi "Hello World" ja se palautta merkkijonon.
> `+`:lle annetaan 3 ja 4. Se laskee ne yhteen ja palauttaa 7.
{: ng-show="block33" .description}
</section>

<section ng-controller="NarrativeController">
### Koodikommentit

<button class="link" ng-bind-html="details1" ng-model="block41" ng-click="block41=!block41"></button>
<button class="link" ng-bind-html="details2" ng-model="block42" ng-click="block42=!block42"></button>

> Haluamme että kirjoittamamme koodi on selkeää, sillä sitä luetaan
> paaaaljon useammin kuin kirjoitetaan. On helppo unohtaa, mitä tietty
> kohta koodissa itseasiassa tekeekään. Siksi me haluamme kirjoittaa
> vapaamuotoisia kommentteja, jotka selittävät koodin tarkoituksen.
{: ng-show="block41" .description}

> Clojuressa koodirivit alkavat puolipisteellä ;. Tietokone jättää huomiotta
> kaikki puolipisteen jälkeiset merkit.
{: ng-show="block42" .description}

> Reference: [Comment](http://clojurebridge.github.io/community-docs/docs/clojure/comment/)
{: ng-show="block42" .description}

```clojure
;; example functions from a previous slide
(print-str "Hello, World!")  ; a well-known hello world
(+ 3 4)                      ; why not 3 + 4? figure out later
```
</section>

<section>
## Mikä on "Read Eval Print Loop"?
{: .slide_title .slide}

#### <button class="link" ng-model="block51" ng-click="block51=!block51">Intro</button>

> "REPL" on lyhenne sanoista "Read-Eval-Print-Loop", mikä ei äkkiseltään
> tarkoita juuri mitään. Monissa ohjelmointikielissä on mahdollista ajaa
> komentoja interaktiivisesti, jotta saadaan välitöntä palautetta.
> Koodia siis luetaan, sitten se evaluoidaan ja tulos näytetään ruudulla.
> ja alusta uudelleen :)
{: ng-show="block51" .description}

**R**ead, **E**val, **P**rint, **L**oop

![Nightcode's repl](img/repl.png)

</section>

<section ng-controller="NarrativeController">
## REPL käytännössä
{: .slide_title .slide}


#### Nightcode InstaREPL <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> Leikkiäksemme hieman Clojurella, voimme käyttää Nightcoden InstaREPL 
> ominaisuutta.
{: ng-show="block61" .description}


#### REPL:n käyttö <button class="link" ng-bind-html="details" ng-model="block62" ng-click="block62=!block62"></button>

> Nightcoden REPL tietää tilanteen jossa sitä käytetään.
> kun "Run with REPL" painiketta painetaa, REPL käynnistyy.
{: ng-show="block62" .description}

> REPL:n voi käynnistää myös leiningein kautta terminaalissa
> kirjoittamalla `lein repl`.
> Mikäli tämä kirjoitetaan projektin hakemistossa, REPL näkee projektin
> asetukset automaattisesti.
{: ng-show="block62" .description}


#### Evaluoi ohjelma tai rivi <button class="link" ng-bind-html="details" ng-model="block63" ng-click="block63=!block63"></button>

<!-- TODO project_name should probably be defined somewhere, right? -->
> Nightcodessa voidaan evaluoida kokonainen ohjelma tai pelkästään valitut rivit.
> Kun REPL on käynnistetty, "Reload File" ja "Reload Selection" painikkeet toimivat.
{: ng-show="block63" .description}
</section>

<section>
#### HARJOITUS 1: Kokeile Nightcoden InstREPL:iä

1. Käynnistä Nightcode
2. Importtaa `myproject` <br/> (jonka loit aiemmin)
3. Avaa `core.clj` <br/>(`myproject` -> `src` -> `myproject` -> `core.clj`
4. Klikkaa __InstREPL__ painiketta
5. Kirjoita tekstieditoriin seuraavat rivit, ja katso mitä tapahtuu

```clojure
(print-str "Hello, World!")
(print-str "Hello, World!" " " "from Clojure")
(+ 3 4)
(- 3 4)
(* 3 4)
```
> Pidä huolta että kirjoitat rivit täsmälleen yllä kuvatusti.
> Kiinnitä erityisesti huomiota sulkeisiin.
</section>

<section>
#### HARJOITUS 2: Evaluoi tiedosto ja valitut osat - Osa 1

* Avaa tiedosto `welcometoclojurebridge/src/clojurebridge_turtle/walk.clj`
* Evaluoi koko tiedosto painamalla "Run with REPL" ja sitten "Reload File"
* Katso mitä tapahtuu
* kirjoita `(forward 40)`  `walk.clj` tiedoston viimeiseksi riviksi editorissa. Evaluoi tämä rivi maalaamalla se, ja
  painamalla "Reload Selection"
* Katso mitä tapahtuu

(Jatka harjoitukseen 3)
</section>

<section>
#### Harjoitus 3: Evaluoi tiedosto ja valitut osat - Osa 2

(Olethan tehnyt harjoituksen 2)

* Kirjoita REPL:iin (alhaalla) `(right 90)` ja paina "enter" ![Run with REPL pane](img/run-with-repl.png)
* Katso mitä kilpikonna tekee
* Katso [Turtles App API](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md) ja
[How To Walk Turtles](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md)
[section 1 and 2], ja kokeile lisää kilpikonnien komentoja.
</section>

<section>
#### Harjoitus 4: Clojure dokumentaation selaaminen

* REPL:ssä voi lukea Clojure funktioiden dokumentaatiota
* Käytä `(doc function-name)` komentoa
* Kirjoita REPL:iin `(doc +)` ja `(doc forward)`
* Kokeile selata myös muiden funktioiden dokumentaatiota, kuten: , `-`, `*`, or `doc`
</section>

{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Palaa <a href="javascript:;" onClick="Reveal.slide(1);">alkuun</a>,
tai [sisällysluetteloon](/curriculum/#/1).
</section>
