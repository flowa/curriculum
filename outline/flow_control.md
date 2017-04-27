---
layout: default
title: Flow Control
permalink: /outline/flow_control.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/flow_control.html

{% endcomment %}

<section>
Suorituksenhallinta
-------------------------
{: .slide-title .chapter}

* `if`
* `cond`
* Boolean logic
</section>

<section ng-controller="NarrativeController">
### Mitä on suorituksenhallinta (flow control)?
{: .slide_title .slide}

#### Päätös siitä kuinka reagoida <button class="link" ng-bind-html="details" ng-model="block11" ng-click="block11=!block11"></button>

> Suorituksenhallinta ("Flow control") on ohjelmointi termi joka viittaa 
> siihen miten sovellus toimii missäkin tapauksessa. Teemme jatkuvasti 
> tällaisia päätöksiä osana arkea. *Jos* on kaunis päivä, *niin* suuntaa
> puistoon, *muutoin* pysy sisällä ja pelaa lautapelejä. *Jos* autosi
> tankki on tyhjä, *niin* pysähdy bensa-asemalla, *muutoin* jatka matkaasi 
> kohti määränpäätäsi.
{: ng-show="block11" .description}

#### Reagointi ehtojen testaaminen <button class="link" ng-bind-html="details" ng-model="block12" ng-click="block12=!block12"></button>

> Myös sovellukset ovat täynnä tällaisia valintoja. *Jos* käyttäjän 
> syöte on validi, *niin* tallenna tiedot; *muutoin* näytä virheviesti.
> Tyypillinen toiminta tapa on testata ensin jotain ehtoa ja tämän jälkeen
> toimia eritavoin riippuen siitä oliko ehto *tosi* or *epätosi*.
{: ng-show="block12" .description}
</section>

<section ng-controller="NarrativeController">
### `if` (jos)
{: .slide_title .slide}

<button class="link" ng-bind-html="details1" ng-model="block21"
ng-click="block21=!block21"></button>
<button class="link" ng-bind-html="details2" ng-model="block22" ng-click="block22=!block22"></button>

> Clojuressa kaikista perustavin työkalu suorituksenhallintaan on `if`
> operaattori. Seuraava erimerkki havainnollistaa tiedon oikeellisuuden
> tarkastamista koodilla:
{: ng-show="block21" .description}

> Esimerkki. Jos lisättyäsi 40 `y`:hyn, se on edelleen alle 150, niin
> palauta `(+ y 40)`; muutoin, palauta -150. (Ajattelen turtle app:n
> kehikkoa (frame), yläreunan y on 150 ja alareunan -150.)
{: ng-show="block22" .description}

> Katso lisää: [Conditional `if`](http://clojurebridge.github.io/community-docs/docs/clojure/if/)
{: ng-show="block22" .description}

```clojure
(if (< (+ y 40) 150)
  (+ y 40)
  -150))
```
</section>

<section ng-controller="NarrativeController">
#### `if` operaattorin yleinen muoto

```clojure
(if conditional-expression
  expression-to-evaluate-when-true
  expression-to-evaluate-when-false)
```
</section>

<section ng-controller="NarrativeController">
#### `if` esimerkkejä

```clojure
(if (> 3 1)
  "3 is greater than 1"
  "3 is not greater than 1")
;=> "3 is greater than 1"

(if (> 1 3)
  "1 is greater than 3"
  "1 is not greater than 3")
  ;=> "1 is not greater than 3"
```
</section>

<section ng-controller="NarrativeController">
#### Totuusarvo <button class="link" ng-bind-html="details" ng-model="block51" ng-click="block51=!block51"></button>

> Kun testataan ilmauksen totuus arvoa, Clojure tulkitsee arvot
> `nil` ja `false` epätodeksi ja kaiken muun todeksi.
> tässä muutamia esimerkkejä:
{: ng-show="block51" .description}

> Katso: [Truthiness](http://clojurebridge.github.io/community-docs/docs/clojure/truthiness/)
{: ng-show="block51" .description}


```clojure
(if "anything other than nil or false is considered true"
  "A string is considered true"
  "A string is not considered true")
;=> "A string is considered true"

(if nil
  "nil is considered true"
  "nil is not considered true")
;=> "nil is not considered true"

(if (get {:a 1} :b)
  "expressions which evaluate to nil are considered true"
  "expressions which evaluate to nil are not considered true")
;=> "expressions which evaluate to nil are not considered true"
```
</section>

<section>
#### HARJOITUS 1: Pidä Y:n arvo kehikon sisällä
{: .slide_title .slide}

* Kirjoita funktio `y-within-frame` joka ottaa y (vertikaalinen sijainti) argumenttina.
* Voit hyödyntää esimerkkiä `if` (jos) kalvolta.
* Funktion tulisi palauttaa y:n arvo siten ettei se ylitä arvoa 150.

    - Katso: [x and y in absolute values](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md#x-and-y-in-absolute-values)

```clojure
;; if example
(if (< (+ y 40) 150)
  (+ y 40)
  -150))
```

```clojure
;; usage of y-within-frame function
(y-within-frame 80)    ;=> 120
(y-within-frame 180)   ;=> -150
```
</section>

<section ng-controller="NarrativeController">
### `cond`
{: .slide_title .slide}

<button class="link" ng-bind-html="details1" ng-model="block61" ng-click="block61=!block61"></button>
<button class="link" ng-bind-html="details2" ng-model="block62" ng-click="block62=!block62"></button>

> `if` operaattori sallii vain yhden ehdon (predikaatin)
> Kun haluamme käyttää useita ehtoja, niin `if` on huono valinta.
> Meidän täytyisi tällöin kirjoittaa useita sisäkkäisiä `if` ehtoja.
> Kun sovelluslogiikka haarautuu useiksi ehdoiksi, `cond` operattori toimii 
> huomattavasti parammin.
{: ng-show="block61" .description}

> Esimerkki. Jos lisättyäsi 40 `y`:hyn se ylittää 150, suorita ensimmäinen
> muoto. Tässä tapauksessa, sovellus palauttaa -150. Jos lisäämällä 40 `y`:hyn
> tulos on vähemmän kuin -150, suorita toinen muoto. Tässä tapauksessa, sovellus 
> palauttaa 150. Jos molemmat ehdot ovat epätoseja, suorita `:else` muoto. Tässä 
> tapauksessa sovellus palauttaa `y` + 40. Voisimme käyttää tätä funktiota turtle
> app:ssa siihen, että pidemmä kilpikonnamme kehikon ylä- ja alareunan välissä.
{: ng-show="block62" .description}

> Katso: [Conditional `cond`](http://clojurebridge.github.io/community-docs/docs/clojure/cond/)
{: ng-show="block62" .description}

```clojure
(cond
  (> (+ y 40) 150) -150
  (< (+ y 40) -150) 150
  :else (+ y 40)))
```
</section>

<section ng-controller="NarrativeController">
#### `cond` operaattorin yleinen muoto

```clojure
(cond
  predicate1 expression-to-evaluate-when-predicate1-is-true
  predicate2 expression-to-evaluate-when-predicate2-is-true
  ...
  :else expression-to-evaluate-when-all-above-are-false)
```
</section>

<section>
#### HARJOITUS 2: Y:n arvo kehikossa - osa 2
{: .slide_title .slide}

> Edellisen harjoituksen funktiossa `y-within-frame` oli yksi vika.
> Jos annetu arvo oli -1000, funktio palautti -960. Koska kehikon alareunan 
> y:n arvo oli -150, -960 on sen tuollapuolen, ja siten kilpikonnasi 
> päätyy näkymättömälle alueelle. Tehdään seuraavaksi paremmin toimiva 
> `within-frame` funktio käyttäen `cond`-operaattoria.

* Kirjoita funktio `y-within-frame-cond` joka ottaa y:n (vertikaalinen sijainti) argumenttina.
* Voit käyttää hyödyksi `cond`-operaattorin esimerkki kalvoa.
* Funktion tulisi palauttaa y:n arvo väliltä -150 ja 150.

    - Katso: [x and y in absolute values](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE.md#x-and-y-in-absolute-values)

```clojure
;; usage of y-within-frame-cond function
(y-within-frame-cond 200)    ;=> -150
(y-within-frame-cond -200)   ;=> 150
(y-within-frame-cond 0)      ;=> 40
```
</section>

<section ng-controller="NarrativeController">
### Boolean logiikka `and`, `or`, ja `not` operaattoreilla
{: .slide_title .slide}

#### <button class="link" ng-model="block81" ng-click="block81=!block81">Intro</button>

> `if` muoto ei rajoitus vain yhden asian testaamiseen. Voit testata 
> useita ehtoja käyttäen predikaatti logiikkaa. _Predikaatti logiikka_ 
> viittaa ehtojen tulosten yhdistelyyn ja muuttamiseen hyödyntäen 
> predikaatti logiikan ja (`and`), tai (`or`), ja negaatio (`not`) 
> operaatioita.
{: ng-show="block81" .description}

> Ellet ole aiemmin törmännyt tähän käsitteeseen ohjelmoinnissa, 
> muista että arkinen järkeily riittää: Milloin väittämä tämä _ja_ 
> tuo tosi? Silloin kuin molemmat ehdot ovat tosia. Milloin väittämä tämä 
> _tai_ tuo on tosi? Juuri niin, jos jompikumpi -- tai molemmat -- ovat
> tosia. Milloin väittämä 'tämä _ei_ ole tosi' on tosi? Silloin tämä on 
> epätosi.
{: ng-show="block81" .description}
</section>

<section ng-controller="NarrativeController">
### Totuusarvo taulukko <button class="link" ng-bind-html="details" ng-model="block91" ng-click="block91=!block91"></button>

> `and`, `or`, ja `not` toimivat kuten muut funktio (tarkasti 
> ottaen ne eivät ole funktioita, mutta käyttäytyvä samoin).
> Niitä käytetään _prekiksi notaatiolla_ kuten kuten olemme 
> nähneet arimeettisten funktioiden toimivan.
{: ng-show="block91" .description}

| x     | y     | (`and` x y) | (`or` x y) | (`not` x) | (`not` y) |
| ----- | ----- | --------- | -------- | ------- | ------- |
| false | false | false | false | true  | true  |
| true  | false | false | true  | false | true  |
| true  | true  | true  | true  | false | false |
| false | true  | false | true  | true  | false |

</section>

<section ng-controller="NarrativeController">
#### `and`, `or`, ja `not` kombinaatiot <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> `and`, `or`, ja `not` operaattoreita voi yhdellä. 
> Tämä saattaa tehdä koodista vaikealukuista
> Esimerkki:
{: ng-show="block101" .description}

```clojure
(defn leap-year?
  "Every four years, except years divisible by 100, but yes for years divisible by 400."
  [year]
  (and (zero? (mod year 4))
       (or (zero? (mod year 400))
           (not (zero? (mod year 100))))))
```
</section>

<section ng-controller="NarrativeController">
#### [Bonus] `cond`, `and`, `or`, ja `not` yhdistely <button class="link" ng-bind-html="details" ng-model="block110" ng-click="block110=!block110"></button>

> Olemme nyt oppineet käyttämään muotoja `cond`, `and`, `or`, ja `not`. 
> Pohditaan seuraavaksi millaisen funktion voimme niitä hyödyntäen toteuttaa.
> Tässä esimerkki:
{: ng-show="block110" .description}

```clojure
(defn true-or-false?
  "Given op, returns true or false"
  [op]
  (let [x true
        y false]
    (cond
      (= op :and) (and x y)
      :else false)))

(defn correct?
  "Given op and ans, returns message whether ans was corret or not"
  [op ans]
  (if (= ans (true-or-false? op))
      "You won"
      "You lost"))
```
</section>

<section>
#### HARJOITUS 3: [Bonus] Viimeistele `true-or-false?` funktio
{: .slide_title .slide}

> Edellisen kalvon `true-or-false?` funktio tuki vain `:and`
> operaatiota. Lisää tuki `:or` ja `:not` operaatioille.

* Use `core.clj` of `myproject` and InstaREPL
* Add `(= op :or)` and `(= op :not)` in `cond`
* For `:not`, choose either x or y for the argument

```clojure
;; usage of correct? function
(correct? :and false)   ;=> "You won"
(correct? :or false)    ;=> "You lost"
(correct? :not true)    ;=> "You won"  (this may be "You lost")
```
</section>

{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Palaa <a href="javascript:;" onClick="Reveal.slide(1);">ensimmäiselle kalvolle</a>,
tai mene [sisällysluetteloon](/curriculum/#/1).
</section>
