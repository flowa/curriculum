---
layout: default
title: Simple Values
permalink: /outline/simple_values.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/simple_values.html

{% endcomment %}

<section>
Yksinkertaiset arvot
----------------------------------------
{: .slide-title .chapter}

* Tekstijonot
* Totuusarvot ja nil
* Avainsanat
* Numerot
  - Aritmetiikka

* Alustus: `def`
</section>

<section>
## Yksinkertaiset arvot

#### <button class="link" ng-model="block71" ng-click="block71=!block71">Intro</button>

> Tehdäksemme jotain, meillä täytyy olla arvoja joilla tehdä jotain.
> Clojuren yksinkertaiset arvot ovat numerot, merkkijonot, totuusarvot,
> nil ja avainsanat (keyword).
{: ng-show="block71" .description}
</section>

<section ng-controller="NarrativeController">
### Merkkijonot
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> Merkkijono on tekstiä. Merkkijono luodaan laittamalla merkkejä
> lainausmerkkien sisään. Katso esimerkkiä:
> Jotta saamme lainausmerkin merkkijonon sisään, täytyy meidän
> laittaa kenoviiva ennen sitä.
> Älä myöskään yritä tehdä merkkijonoa heittomerkeillä.
{: ng-show="block21" .description}

> Viite: [String](http://clojurebridge.github.io/community-docs/docs/clojure/string/)
{: ng-show="block21" .description}

```clojure
"Hello, World!"
"This is a longer string that I wrote for purposes of an example."
"Aubrey said, \"I think we should go to the Orange Julius.\""
```
</section>

<section ng-controller="NarrativeController">
### Totuusarvot ja nil
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Totuusarvot ovat tosia tai epätosia. Ne esitetään kirjoittamalla
> `true` ja `false`. Ohjelmoidessa joudutaan usein vastaamaan kysymykseen
> onko joku asia totta vai ei. Vastaus näihin kysymyksiin on totuusarvo.
{: ng-show="block31" .description}

> `nil` on erityinen arvo, joka toimii totuuksien suhteen, vertailuissa, kuten totuusarvo.
> mutta `nil` tarkoittaa myös "ei arvoa lainkaan", joka ei ole totuusarvo.
{: ng-show="block31" .description}

> Viite: [Truthiness](http://clojurebridge.github.io/community-docs/docs/clojure/truthiness/)
{: ng-show="block31" .description}


```clojure
true
false
nil
```
</section>

<section ng-controller="NarrativeController">
### Avainsanat (Keyword)
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block41" ng-click="block41=!block41"></button>

> Avainsanat ovat ehkä kummallisimpia perus arvojen tyypeistä. Joissain
> ohjelmointikielissä on vastaavia arvoja joihin olet ehkä törmännyt.
> Avainsanoilla ei ole vastinetta oikeassa maailmassa, kuten numeroilla,
> merkkijonoilla tai totuusarvoilla.
> Avainsanoja voi ajatella eräänlaisina merkkijonoilla, joita käytetään lähinnä
> asioiden nimeämiseen. Erityisesti näitä käyteään avaimina taulukoissa (maps).
> Näistä kerrotaan myöhemmin lisää.
{: ng-show="block41" .description}


```clojure
:trinity
:first
:last
```
</section>

<section ng-controller="NarrativeController">
### Numerot

#### Kokonaisluvut <button class="link" ng-bind-html="details" ng-model="block81" ng-click="block81=!block81"></button>

> Clojuressa on eri tyyppisiä numeroita.
{: ng-show="block81" .description}

> Kokonaisluvut sisältävät positiiviset ja negatiiviset kokonaisluvut,
> mukaanlukien nollan. Ne kirjoitetaan normaalisti lukuina.
{: ng-show="block81" .description}

```clojure
0
12
-42
```
</section>

<section ng-controller="NarrativeController">
#### Desimaaliluvut <button class="link" ng-bind-html="details" ng-model="block91" ng-click="block91=!block91"></button>

> Desimaalilukuja (myös "float") kuvataan myös melkonormaalisti, desimaalipisteen kanssa.
{: ng-show="block91" .description}

```clojure
0.0000072725
10.5
-99.9
```
</section>

<section ng-controller="NarrativeController">
#### Murtoluvut <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> Tietokone ei pysty esittämään kaikkia desimaalilukuja täydellisesti.
> Murtoluvut sensijaan ovat aina tarkkoja. Murtoluvut esitetään
> kauttaviivan avulla.
{: ng-show="block101" .description}

> Huomaa, että kuten oikeassa maailmassakaan, nollalla ei saa jakaa.
{: ng-show="block101" .description}

```clojure
1/2
-7/3
```
</section>

<section>
### Laskeminen
{: .slide_title .slide}

#### <button class="link" ng-model="block111" ng-click="block111=!block111">Intro</button>

> Numeroita voi lisätä, vähentää, kertoa ja jakaa. Clojuressa laskeminen
> näyttää hieman erilaiselta kuin normaalisti. Katsotaanpa esimerkkejä:
{: ng-show="block111" .description}

```clojure
(+ 1 1)  ;=> 1 + 1 = 2
(- 12 4) ;=> 12 - 4 = 8
(* 13 2) ;=> 13 * 2 = 26
(/ 27 9) ;=> 27 / 9 = 3
```
</section>

<section ng-controller="NarrativeController">
### Infix vs. prefix notaatio
{: .slide-title .slide}

<button class="link" ng-bind-html="details1" ng-model="block121" ng-click="block121=!block121"></button>
<button class="link" ng-bind-html="details2" ng-model="block122" ng-click="block122=!block122"></button>

> Clojuressa operaattorit `+`, `-`, `*` ja `/` esiintyvät ennen numeroita.
> Tämä on niin sanottu _prefix-notaatio_. Olet tottunut näkemään _infix-notaatio_ esitystavan,
> jossa operaattori sijaitsee numeroiden välissä.
{: ng-show="block121" .description}

> Ohjelmointikielet kuten **JavaScript** käyttävät **infix** esitystapaa.
> Clojure käyttää vain **prefix** esitystapaa.
> Tämä on monintavoin hyödyllistä, katsotaanpa esimerkkejä.
> Tässä sama asia kummallakin tavalla esitettynä.
{: ng-show="block122" .description}

```clojure
Infix:  1 + 2 * 3 / 4 + 5 - 6 * 7 / 8 + 9

Prefix: (+ (- (+ (+ 1 (/ (* 2 3) 4)) 5) (/ (* 6 7) 8)) 9)
```
</section>

<section ng-controller="NarrativeController">
### Miksi prefix on parempi?

#### Eksplisiittinen arvojärjestys <button class="link" ng-bind-html="details" ng-model="block131" ng-click="block131=!block131"></button>

> Molemmat ovat hieman epäselviä, mutta huomaathan että prefix-versiossa
> ei tarvitse miettiä operaattoreiden arvojärjestystä. Jokaisessa
> ilmauksessa operaattori on aina ennen operoitavia arvoja.
> Koska ilmaus on sulkeiden sisällä, on arvojärjestys eksplisiittinen.
{: ng-show="block131" .description}

```clojure
Infix:  1 + 2 / 3
Prefix: (+ 1 (/ 2 3))
```

#### Vähemmän toistoa <button class="link" ng-bind-html="details" ng-model="block132" ng-click="block132=!block132"></button>

> Toinen hyvä syy käyttää prefix-esitystapaa on se, että se mahdollistaa toisteisuuden
> vähentämisen. Prefix notaation avulla voidaan käytää yhtä operandia monen
> operoitavan numeron käsittelemiseen, ilman että sitä tarvitsee toistaa 
> numeroiden välillä.
{: ng-show="block132" .description}

```clojure
Infix:  1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9
Prefix: (+ 1 2 3 4 5 6 7 8 9)
```
</section>

<section ng-controller="NarrativeController">
### Laskemista eri tyyppisillä arvoilla

<button class="link" ng-bind-html="details" ng-model="block141" ng-click="block141=!block141"></button>

> Olemme tähän asti laskeneet pelkästään kokonaisluvuilla.
> Muita tyyppejä kuten desimaaleja ja murtolukuja voidaan käyttää yhtälailla.
> Esimerkiksi:
{: ng-show="block141" .description}

```clojure
(+ 4/3 7/8)   ;=> 53/24
(- 9 4.2 1/2) ;=> 4.3
(/ 27/2 1.5)  ;=> 9.0
```
</section>


<section ng-controller="NarrativeController">
## Alustus: `def`

#### <button class="link" ng-model="block161" ng-click="block161=!block161">Intro</button>

> Ohjelmien kirjoittaminen olisi todella vaikeaa, jos meidän täytyisi
> kirjoittaa samat arvot uudestaan ja uudestaan. Voimme asettaa arvoillemme
> nimiä.
{: ng-show="block161" .description}
</section>

<section ng-controller="NarrativeController">
#### Arvojen nimeäminen: `def`

#### <button class="link" ng-bind-html="details" ng-model="block171" ng-click="block171=!block171"></button>

> `def`-komennolla voimme asettaa arvolle nimen.
> kun arvolle asetetaan nimi, tätä nimeä kutsutaan *symboliksi*.
{: ng-show="block171" .description}

> Viite: [Assignment def](http://clojurebridge.github.io/community-docs/docs/clojure/def/)
{: ng-show="block171" .description}

```clojure
(def mangoes 3)
(def oranges 5)
(+ mangoes oranges)
;=> 8
```
</section>

<section ng-controller="NarrativeController">
#### Tulosten asettaminen symboleihin <button class="link" ng-bind-html="details" ng-model="block181" ng-click="block181=!block181"></button>

> Symboleihin voi asettaa muutakin kuin yksinkertaisia arvoja. Katso seuraavaa:
> Viimeisellä rivillä näät, kuinka symboli viittaa arvoon.
{: ng-show="block181" .description}

```clojure
(def fruit (+ mangoes oranges))
(def average-fruit-amount (/ fruit 2))
average-fruit-amount
;=> 4
```
</section>

<section>
#### HARJOITUS 1: Perusaritmetiikka

* Kuinka monta minuuttia on kulunut saapumisestasi työpajaan?
* Muutta tämä arvo minuuteista sekunneiksi
</section>

<section>
#### HARJOITUS 2 [BONUS]: Minuutit ja sekunnit

* Muunna 1000 sekuntia minuuteiksi ja sekunneiksi
* Minuutit ja sekunnit ovat eri arvoja
* `(quot x y)` saat kokonaisluvun x jaettuna y:llä.
* `(rem x y)` saat jakojäännöksen x jaettuna y:llä.
</section>

{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Palaa <a href="javascript:;" onClick="Reveal.slide(1);">alkuun</a>,
tai [sisällysluetteloon](/curriculum/#/1).
</section>
