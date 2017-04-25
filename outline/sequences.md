---
layout: default
title: Sequences
permalink: /outline/sequences.html
---

{::options parse_block_html="true" /}

{% comment %}

http://flowa.github.io/curriculum/outline/sequences.html

{% endcomment %}

<section>
[BONUS]

Sekvenssit
-------------------------
{: .slide-title .chapter}

* Mitä sekvenssit ovat
* Funktioita sekvensseille
    * `doseq`
    * `dotimes`
</section>

<section ng-controller="NarrativeController">
### Mitä sekvenssit ovat?
{: .slide_title .slide}

#### Clojuren tietorakenteita <button class="link" ng-bind-html="lisätietoa" ng-model="block11" ng-click="block11=!block11"></button>

> Clojuressa voidaan sanoa, että kaikki tietorakenteet ovat sekvenssejä.
> Tähän asti olemme oppineet, että `vektori` ja `mapit` (avain-arvoparit) ovat sekvenssejä.
> Myös merkkijono on sekvenssi. Mikä tahansa on Clojuressa sekvenssi, jos se on **sekvenssimäinen** (seq-able).
{: ng-show="block11" .description}

#### Sisältää ensimmäisen `first` tai sitten ei  <button class="link" ng-bind-html="lisätietoa" ng-model="block12" ng-click="block12=!block12"></button>

> Jos jokin on **sekvenssimäinen**, siitä saadaan ensimmäinen jäsen `first` funktion avulla.
> Tämä on hyvä testi sille onko kyseessä sekvenssi vai ei.
{: ng-show="block12" .description}
</section>

<section ng-controller="NarrativeController">
#### Results of `first`

```clojure
(turtle-names)
;=> [:trinity :neo :oracle :cypher] ; vektori
(first (turtle-names))
;=> :trinity                        ; ensimmäinen jäsen

(:trinity (state))
;=> {:x 0, :y 0, :angle 90, :color [30 30 30]}  ; map
(first (:trinity (state)))
[:x 0]                                          ; ensimmäinen jäsen

(first "Hello, World!")  ; merkkijono
;=> \H                   ; ensimmäinen jäsen

(first :trinity)         ; keyword eli avainsana ei ole sekvenssimäinen
;=> IllegalArgumentException Don't know how to create ISeq from:
clojure.lang.Keyword  clojure.lang.RT.seqFrom (RT.java:528)
```
</section>

<section ng-controller="NarrativeController">
### Functions for sequences
<button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> Clojure is very good at *iterate* over a sequence.
> There are many functions that interact on sequences.
> For example, `doseq`, `dotimes`, `for`, `loop`, `doall`, or `dorun`.
>
> We already saw `map` and `reduce` functions in "Functions that takes
> other functions" section. These are also functions for sequences.
{: ng-show="block21" .description}
</section>

<section ng-controller="NarrativeController">
#### `doseq`

<button class="link" ng-bind-html="details1" ng-model="block31" ng-click="block31=!block31"></button>
<button class="link" ng-bind-html="details2" ng-model="block32" ng-click="block32=!block32"></button>

> The `doseq`(for **do a sequence**) is one of well-used functions
> for sequences, and works quite similar to `map` function. The
> function repeatedly evaluates given body form with each element in
> the given sequence.
{: ng-show="block31" .description}

> The `doseq` function takes bindings as arguments. The arguments might be
> an odd-looking vector: `[name sequence]`. When each element of a sequence
> is iterated over, the element is assigned to the name one by one.
{: ng-show="block32" .description}

```clojure
;; doseq example
(doseq [n (turtle-names)] (forward n 40))
```
</section>

<section>
#### EXERCISE 1

* [Turtles Walk](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md) (more function study)
    - section 5 and later
* [Snowflakes](https://github.com/ClojureBridge/drawing/blob/master/curriculum/create-something.md) (animation)
    - step 4 and later
* [Twinkle Twinkle Little Star](https://github.com/ClojureBridge/tones/blob/master/curriculum/01-piano-chords.md) (making sounds)
    - `chord` function and later
</section>

<section ng-controller="NarrativeController">
#### `dotimes`

<button class="link" ng-bind-html="details1" ng-model="block41" ng-click="block41=!block41"></button>
<button class="link" ng-bind-html="details2" ng-model="block42" ng-click="block42=!block42"></button>

> The `dotimes`(for **do number of times**) is another well-used
> function for sequences. Like `doseq`, the function repeatedly
> evaluates given body form. The difference is the binding in the
> argument. The `dotimes` takes: `[name max-integer]`.
{: ng-show="block41" .description}

> The `dotimes` function is the closest to so-called for-loop in other
> programming languages. This function allows us an index access to
> the given sequence by a combination with `nth`.
{: ng-show="block42" .description}

```clojure
;; assuming there are multiple turtles
(def names (turtle-names))
(dotimes [n (count names)] (right (nth names n) (* 45 n)))
```
</section>

<section>
#### EXERCISE 2

* [Turtles Walk](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md) (more function study)
    - section 6 and later
* [Snowflakes](https://github.com/ClojureBridge/drawing/blob/master/curriculum/create-something.md) (animation)
    - step 5-4 and later
* [Twinkle Twinkle Little Star](https://github.com/ClojureBridge/tones/blob/master/curriculum/01-piano-chords.md) (making sounds)
    - complete Twinkle Little Star section
</section>


{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Return to the <a href="javascript:;" onClick="Reveal.slide(1);">first slide</a>,
or go to the [curriculum outline](/curriculum/#/1).
</section>
