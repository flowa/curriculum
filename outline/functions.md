---
layout: default
title: Functions
permalink: /outline/functions.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/functions.html

http://flowa.github.io/curriculum/outline/functions.html

{% endcomment %}

<section>
Funktiot
-------------------------------
{: .slide-title .chapter}

* Mitä funktiot ovat?
* Funktioiden nimeäminen
* [bonusosio] Funktiot jotka ottavat argumentteina muita funktioita
    - `map` ja `reduce`
* [bonusosio] anonyymi funktio
* [bonusosio] Sijoitus: `let`
</section>

<section ng-controller="NarrativeController">
### Mitä funktiot ovat
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> Olet nähnyt joitain funktioita kuten `count`, `conj`,
> `first`, ja `rest`. Aiemmin tehdy laskuissa käytettiin myös funktioita: `+`, `-`, `*`, ja `/`. 
> Mitä se funktio nyt sitten tarkoittaa?
{: ng-show="block11" .description}

> *Funktio* on itsenäinen pätkä koodia, joka ottaa sisäänsä 
> joitain arvoja (näitä kutstuaan nimellä *parametrit* toisinaan myös *argumentit*) ja palauttaa arvon.
{: ng-show="block11" .description}

> Reference: [Basics of Function](http://clojurebridge.github.io/community-docs/docs/clojure/function-creation/)
{: ng-show="block11" .description}

* `count`, `conj`, `first`
* `+`, `-`, `*`, `/`
* Pätkä koodia, joka ottaa vastaan arvoja ja palauttaa arvon
</section>

<section ng-controller="NarrativeController">
#### Esimerkkifunktio <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> * `defn` kertoo, että olemme määrittämässä funktiota.
> * `forward-right` on tämän funktion *nimi*.
> * Seuraavalla rivillä oleva merkkijono on funktion dokumentaatio, joka kertoo mitä funktio tekee. Dokumentaatio ei ole pakollinen.
> * `[turtle]` on lista *parametreja*. Tässä, meillä on yksi parametri nimeltä `turtle`.
> * `(forward turtle 60) (right turtle 135)` on funktion *runko* (body). Tämä osa suoritetaan kun kutsumme funktiota.
{: ng-show="block21" .description}

```clojure
(defn forward-right
  "Moves specified turtle forward and tilts its head"
  [turtle]
  (forward turtle 60)
  (right turtle 135))
```
</section>

<section ng-controller="NarrativeController">
#### Kuinka käyttää `forward-right` funktiota <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

> Funktiota `forward-right`, käytetään *kutsumalla* (call) sitä, aivan kuten olemme tehneet kaikkien muidenkin käyttämiemme funktioiden kanssa tähän asti.
{: ng-show="block31" .description}

```clojure
(forward-right :trinity)  ;=> {:trinity {:angle 135}}
(forward-right :neo) ;=> {:neo {:angle 135}}
```
</section>

<section ng-controller="NarrativeController">
#### Funktio jolla on useita argumentteja <button class="link" ng-bind-html="details" ng-model="block41" ng-click="block41=!block41"></button>

> Funktiot voivat ottaa myös useamman kuin yhden parametrin.
> Luodaan `forward-right-with-len` funktio, joka ottaa eteenpäin kuljettavan matkan (len) kilpikonnan nimen (turtle) lisäksi
{: ng-show="block41" .description}

```clojure
(defn forward-right-with-len
  "Given turtle and length, forward the turtle and tilts its head"
  [turtle len]
  (forward turtle len)
  (right turtle 135))

(forward-right-with-len :trinity 90) ;=> {:trinity {:angle 135}}
(forward-right-with-len :neo 80)  ;=> {:neo {:angle 135}}
```
</section>

<section>
#### HARJOITUS 1: Liikuta kilpikonnia käyttäen funktiota
{: .slide_title .slide}

1. Kirjoita funktio
  * Avaa `walk.clj`
  * Kirjoita `forward-right` funktio (alla) 
  * Tallenna (Save) `walk.clj`
  * Maalaa kokonaan `forward-right` funktio ja klikkaa Eval Selection-painiketta
2. Käytä funktiota
  * Kirjoita `(forward-right :trinity)` REPLiin
  * Toista tämä ainakin 8 kertaa (paina ylänuolta ja sen jälkeen enteriä)

```clojure
(defn forward-right
  "Moves specified turtle forward and tilts its head"
  [turtle]
  (forward turtle 60)
  (right turtle 135))
```
</section>

<section>
#### HARJOITUS 2: Siirrä kilpikonnia käyttäen funktiota joka käyttää useampaa argumenttia
{: .slide_title .slide}

* Avaa `walk.clj`
* Kirjoita `forward-right-with-len-ang` funktio, joka käyttää kolmea
  parametria, kilpikonna, len (matka), ja angle (kulma) (jatkoa `forward-right-with-len` funktiolle)
* Maalaa `forward-right-with-len-ang` funktio ja paina "reload section" painiketta.
* REPL:ssä kirjoita `(forward-right-with-len-ang :trinity 60 120)`
* Toista REPL:ssä monta kertaa
</section>


<section ng-controller="NarrativeController">
### Funktioiden nimeäminen
{: .slide_title .slide}

#### Nimet ovat symboleita <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> Funktioiden nimet ovat symboleita, aivan kuten symbolit joita käytimme `def`:n kanssa,
> kun asetimme nimille arvoja.
{: ng-show="block61" .description}

> Symboleiden tulee alkaa ei-numeerisella merkillä ja ne voivat sisältää kirjaimia ja numeroita 
> sekä seuraavia merkkejä: * + ! - _ ?
> Tämä on tärkeää, koska funktioiden nimeämiseen liittyy tiettyjä käytänteitä, joissa 
> näitä merkkejä tarvitaan.
{: ng-show="block61" .description}

##### Predikaattiofunktiot <button class="link" ng-bind-html="details" ng-model="block63" ng-click="block63=!block63"></button>

> Clojuressa, `=` on ns. *predikaattifunktio*. Tämä saattaa hieman yllättää. 
> Sen lisäksi Clojuressa, kuten monessa muussakin kielessä on predikaattifunktioita, joilla voi 
> kokeilla onko arvo suurempi tai pienempi kuin jokin toinen arvo.
> Yleensä predikaattifunktiot päättyvät kysymysmerkkiin eli `?`.
{: ng-show="block63" .description}

> * `=`, `not=`
> * `>`, `<`, `>=`, `<=`
> * `true?`, `false?`, `empty?`, `nil?`, `vector?`, `map?`

</section>

<section ng-controller="NarrativeController">
#### [Bonusosio]

### Funktiot, joiden parametrina on toinen funktio
{: .slide_title .slide}

#### <button class="link" ng-model="block71" ng-click="block71=!block71">Intro</button>

> Osa kaikkein tehokkaimmista tietorakenteiden kanssa käytettävistä funktioista
> ottavat toisia funktioita parametreinaan.
> Tämä on yksi taianomaisimmista asioista Clojuressa - ja monessa muusakin ohjelmointikielessä.
> Ajatus voi tuntua ensialkuun monimutkaiselta eikä välttämättä aukene välittömästi.
> Katsotaan esimerkki ja opitaan lisää aiheesta.
{: ng-show="block71" .description}

> Reference: [Higher-order Function](http://clojurebridge.github.io/community-docs/docs/clojure/higher-order-function/)
{: ng-show="block71" .description}
</section>

<section ng-controller="NarrativeController">
#### `map` funktio

#### <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> `map` on funktio, joka ottaa toisen funktion sekä tietorakenteen.
> Se kutsuu annettua funktioita tietorakenteen jokaiselle jäsenelle
> ja palauttaa sitten uuden tietorakenteen, 
> joka sisältää em. funktiokutsujen tulokset.
> Tämä on jännä konsepti, mutta se on tärkeä osa Clojuren ja 
> funktio-ohjelmoinnin peruskäsitteistöä.
{: ng-show="block101" .description}

```clojure
(map inc [1 2 3]) ;=> (2 3 4)
(map (partial + 90) [0 30 60 90]) ;=> (90 120 150 180)
```

> Viittaus:
> [partial](http://clojuredocs.org/clojure.core/partial)
</section>

<section ng-controller="NarrativeController">
#### `reduce` funktio

#### <button class="link" ng-bind-html="details" ng-model="block111" ng-click="block111=!block111"></button>

> Let's look at another function that takes a function. This one is
> `reduce`, and it is used to turn collections into a single value.
{: ng-show="block111" .description}

> `reduce` takes the first two members of the provided collection and
> calls the provided function with those members. Next, it calls the
> provided function again--this time, using the result of the previous
> function call, along with the next member of the collection.
> `reduce` does this over and over again until it finally reaches the
> end of the collection.
{: ng-show="block111" .description}

```clojure
(reduce str (turtle-names)) ;=> ":trinity:neo:oracle:cypher"
(reduce + [30 60 90])       ;=> 180
```
</section>

<section>
#### HARJOITUS 3 [BONUS]: Keskiarvo
{: .slide_title .slide}

* Luo funktio `average` jonka argumenttina on vektori map-rakenteita.
* käytä `[{:angle 30} {:angle 90} {:angle 50}]` rakennetta syötteenä
* laske keskiarvo :angle avaimen arvoista.

* Vihje: Tarvitset funktioita `map`, `reduce` ja `count`.
</section>


<section ng-controller="NarrativeController">
#### [Bonus section]

### Anonyymit funktiot

#### Nimettömät funktiot <button class="link" ng-bind-html="details" ng-model="block201" ng-click="block201=!block201"></button>

> So far, all the functions we've seen have had names, like `+` and
> `str` and `reduce`. However, functions don't need to have names, just
> like values don't need to have names. We call functions without names
> *anonymous functions*.
> An anonymous function is created with `fn`, like so:
{: ng-show="block201" .description}

> Katso: [Anonymous Function](http://clojurebridge.github.io/community-docs/docs/clojure/anonymous-function/)
{: ng-show="block201" .description}


```clojure
(fn [s1 s2] (str s1 " " s2))
```

#### versus funktiot joilla on nimi <button class="link" ng-bind-html="details" ng-model="block202" ng-click="block202=!block202"></button>

> Before we go forward, you should understand that you can _always_
> feel free to name your functions. There is nothing wrong at all with
> doing that. However, you _will_ see Clojure code with anonymous
> functions, so you should be able to understand it.
{: ng-show="block202" .description}

```clojure
(defn join-with-space
  [s1 s2]
  (str s1 " " s2))
```
</section>

<section ng-controller="NarrativeController">
#### Esimerkkejä anonyymeistä funktioista <button class="link" ng-bind-html="details" ng-model="block203" ng-click="block203=!block203"></button>

> Why would you ever need anonymous functions?
> Anonymous functions can be very useful
> when we have functions that take other functions.
> Such as `map` or `reduce`, which we learned in Functions section.
> Let's look at usage examples of anonymous functions:
{: ng-show="block203" .description}

```clojure
(map (fn [t] (forward t 45)) (turtle-names))
;=> ({:trinity {:length 45}} {:neo {:length 45}} {:oracle {:length
45}} {:cypher {:length 45}})

(reduce (fn [x y] (+ x y)) [1 2 3]) ;=> 6

(reduce (fn [a b] (str a ", " b)) (map name (turtle-names)))
;=> "trinity, neo, oracle, cypher"
```
</section>

<section ng-controller="NarrativeController">
#### [Bonus section]

### Sijoitus: `let`
{: .slide_title .slide}

#### <button class="link" ng-model="block301" ng-click="block301=!block301">Intro</button>

> When you are creating functions, you may want to assign names to
> values in order to reuse those values or make your code more
> readable. Inside of a function, however, you should _not_ use `def`,
> like you would outside of a function. Instead, you should use a
> special form called `let`.
{: ng-show="block301" .description}
</section>

<section ng-controller="NarrativeController">
#### Arvojen nimeäminen: `let`
{: .slide_title .slide}

#### <button class="link" ng-bind-html="details" ng-model="block305" ng-click="block305=!block305"></button>

> We can assign a name to value using `let` like `def`.
> When a name is assigned to a value, the name is called a *symbol*.
{: ng-show="block305" .description}

> Reference: [Assignment let](http://clojurebridge.github.io/community-docs/docs/clojure/let/)
{: ng-show="block305" .description}

```clojure
(let [mangoes 3
      oranges 5]
  (+ mangoes oranges))
;=> 8
```
</section>

<section ng-controller="NarrativeController">
#### `let` esimerkki

<button class="link" ng-bind-html="details1" ng-model="block311" ng-click="block311=!block311"></button>
<button class="link" ng-bind-html="details2" ng-model="block312" ng-click="block312=!block312"></button>
<button class="link" ng-bind-html="details3" ng-model="block313" ng-click="block313=!block313"></button>
<button class="link" ng-bind-html="exercise" ng-model="block314" ng-click="block314=!block314"></button>

> This is the most complicated function we've seen so far, so let's go
> through each step. First, we have the name of the function, the
> documentation string, and the arguments, just as in other functions
{: ng-show="block311" .description}

> Next, we see `let`. `let` takes a vector of alternating names and
> values. `t1` is the first name, and we assign the result of
> `(first names)` to it. We also assign the result of `(last names)`
> to `t2`.
{: ng-show="block312" .description}

> After the vector of names and values, there is the body of the
> `let`. Just like a the body of a function, this executes and returns
> a value. Within the `let`, `t1` and `t2` are defined.
{: ng-show="block313" .description}

> Go to `walk.clj` and write `opposite` function.
> Then, evaluate `opposite` function at the last line of the function definition.
> Also, evaluate usage example of `opposite` function.
{: ng-show="block314" .description}

```clojure
;; function definition
(defn opposite
  "Given a collection of turtle names, moves two of them in different directions."
  [names]
  (let [t1 (first names)
        t2 (last names)]
    (forward t1 40)
    (backward t2 30)))

;; function usage
(opposite (turtle-names))
```
</section>

{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Palaa <a href="javascript:;" onClick="Reveal.slide(1);">alkuun</a>,
tai [sisällysluetteloon](/curriculum/#/1).
</section>
