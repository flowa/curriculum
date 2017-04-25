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
> Murtoluvut sensijaan ovat aina tarkkoja.

> Finally, we have fractions, which are also called ratios. Computers
> cannot perfectly represent all floats, but ratios are always exact.
> We write them with a slash, like so:
{: ng-show="block101" .description}

> Note that, just like with pen-and-paper math, the [denominator](http://en.wikipedia.org/wiki/Fraction_%28mathematics%29) of your ratio cannot be equal to `0`.
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

> You can add, subtract, multiply, and divide numbers. In Clojure,
> arithmetic looks a little different than it does when you write it
> out with pen and paper. Look at these examples:
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

> In Clojure, `+`, `-`, `*` and `/` appear before two numbers. This is
> called _prefix notation_. What you're used to seeing is called
> _infix notation_, as the arithmetic operator is in-between the two
> operands.
{: ng-show="block121" .description}

> Languages such as **JavaScript** use **infix** notation,
> while **Clojure** only uses **prefix** notation.
> Prefix notation is useful for many reasons. Look at this example of
> an infix expression and the prefix equivalent:
{: ng-show="block122" .description}

```clojure
Infix:  1 + 2 * 3 / 4 + 5 - 6 * 7 / 8 + 9

Prefix: (+ (- (+ (+ 1 (/ (* 2 3) 4)) 5) (/ (* 6 7) 8)) 9)
```
</section>

<section ng-controller="NarrativeController">
### Miksi prefix on parempi?

#### Eksplisiittinen arvojärjestys <button class="link" ng-bind-html="details" ng-model="block131" ng-click="block131=!block131"></button>

> Imagine both are unclear, but notice that in the prefix version,
> you do not have to ever think about the precedence of operators.
> Because each expression has the operator before all the operands and
> the entire expression is wrapped in parentheses, all precendence is
> explicit.
{: ng-show="block131" .description}

```clojure
Infix:  1 + 2 / 3
Prefix: (+ 1 (/ 2 3))
```

#### Vähemmän toistoa <button class="link" ng-bind-html="details" ng-model="block132" ng-click="block132=!block132"></button>

> Another reason prefix notation can be nice is that it can make long
> expressions less repetitive.
> With prefix notation, if we plan to use the same operator on many
> operands, we do not have to repeat the operator between them.
{: ng-show="block132" .description}

```clojure
Infix:  1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9
Prefix: (+ 1 2 3 4 5 6 7 8 9)
```
</section>

<section ng-controller="NarrativeController">
### Laskemista eri tyyppisillä arvoilla

<button class="link" ng-bind-html="details" ng-model="block141" ng-click="block141=!block141"></button>

> So far, we looked at arithmetic operations by integers only.
> However, we can use floats or ratios for those operations as well.
> See these examples:
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

> If we had to type the same values over and over, it would be very
> hard to write a program. What we need are names for values, so we
> can refer to them in a way we can remember. This is called
> assignment. 
{: ng-show="block161" .description}
</section>

<section ng-controller="NarrativeController">
#### Arvojen nimeäminen: `def`

#### <button class="link" ng-bind-html="details" ng-model="block171" ng-click="block171=!block171"></button>

> We can assign a name to value using `def`.
> When a name is assigned a value, that name is called a *symbol*.
{: ng-show="block171" .description}

> Reference: [Assignment def](http://clojurebridge.github.io/community-docs/docs/clojure/def/)
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

> You can assign more than simple values to symbols. Try the following.
> Look at the last line, and see how we can use symbols by themselves to refer to a value.
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

* Muunna 1000 seconds to minuuteiksi ja sekunneiksi
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
