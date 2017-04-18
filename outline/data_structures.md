---
layout: default
title: Vectors and Maps
permalink: /outline/data_structures.html
---

{::options parse_block_html="true" /}

{% comment %}

http://clojurebridge.github.io/curriculum/outline/data_structures.html

{% endcomment %}

<section>
Tietorakenteet
----------------------------------------
{: .slide-title .chapter}

* Vektorit
* Mapit
</section>

<section>
### Nippu dataa - Kokoelmat
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> So far, we've dealt with discrete pieces of data: one number, one
string, one value. When programming, it is more often the case that
you want to work with groups of data.
{: ng-show="block11" .description}

> Clojure has great facilities for working with these groups, or
*collections*, of data. Not only does it provide four different types
of collections, but it also provides a uniform way to use all of these
collections together.
{: ng-show="block11" .description}
</section>

<section ng-controller="NarrativeController">
### Vektorit
{: .slide_title .slide}

#### Peräkkäinen kokoelma <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> A vector is a sequential collection of values. A vector may be
> empty. A vector may contain values of different types.
> Each value in a vector is numbered starting at 0, that number is
> called its index. The index is used to refer to each value when
> looking them up.
{: ng-show="block21" .description}

#### Lokeromainen rakenne <button class="link" ng-bind-html="details" ng-model="block22" ng-click="block22=!block22"></button>

> To imagine a vector, imagine a box split into some number of
> equally-sized compartments. Each of those compartments has a number.
> You can put a piece of data inside each compartment and always know
> where to find it, as it has a number.
{: ng-show="block22" .description}

> Note that the numbers start with 0. That may seem strange, but we
> often count from zero when programming.
{: ng-show="block22" .description}

![Vector](img/vector.png)

</section>

<section ng-controller="NarrativeController">
#### Syntaksi <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

>Vectors are written using square brackets with any number of pieces
>of data inside them, separated by spaces. Here are some examples of
>vectors:
{: ng-show="block31" .description}

```clojure
[1 2 3 4 5]
[56.9 60.2 61.8 63.1 54.3 66.4 66.5 68.1 70.2 69.2 63.1 57.1]
[]
```
</section>

<section ng-controller="NarrativeController">
#### Esimerkki <button class="link" ng-bind-html="details" ng-model="block41" ng-click="block41=!block41"></button>

> `(turtle-names)` komento palauttaa kilpikonnien nimet
> vektorissa.
{: ng-show="block41" .description}

```clojure
(turtle-names)
;=> [:trinity :neo :oracle :cypher]
```
</section>


<section ng-controller="NarrativeController">
#### Luominen <button class="link" ng-bind-html="details" ng-model="block61" ng-click="block61=!block61"></button>

> The next two functions are used to make new vectors. The `vector`
> function takes any number of items and puts them in a new vector.
> `conj` is an interesting function that you'll see used with all the
> data structures. With vectors, it takes a vector and an item and
> returns a new vector with that item added to the end of the vector.
> Why the name `conj`? `conj` is short for conjoin, which means to 
> join or combine. This is what we're doing: we're joining the new
> item to the vector.
{: ng-show="block61" .description}

```clojure
(vector 5 10 15)
;=> [5 10 15]

(conj [5 10] 15)
;=> [5 10 15]
```
</section>

<section ng-controller="NarrativeController">
#### Käsittely <button class="link" ng-bind-html="details" ng-model="block81" ng-click="block81=!block81"></button>

> Now, take a look at these four functions. `count` gives us a
count of the number of items in a vector. `nth` gives us the nth
item in the vector. Note that we start counting at 0, so in the
example, calling `nth` with the number 1 gives us what we'd call the
second element when we aren't programming. `first` returns the first
item in the collection. `rest` returns all except the first item.
Try not to think about that and `nth` at the same time, as they can
be confusing.
{: ng-show="block81" .description}

```clojure
(count [5 10 15])
;=> 3
(nth [5 10 15] 1)
;=> 10
(first [5 10 15])
;=> 5
(rest [5 10 15])
;=> (10 15)
```
</section>

<section>
#### HARJOITUS 1: Kilpikonnien nimet
{: .slide_title .slide}

1. Lisää kilpikonna
  * Go to `walk.clj` file
  * Lisää rivi: `(add-turtle :neo)` viimeiseksi riviksi `walk.clj` tiedostossa
  * valitse rivi ja klikkaa "Reload Selection"
2. (Optio) Lisää kilpikonna REPL:n kautta
  * kirjoita `(add-turtle :oracle)` ja paina enteriä replissä
3. Tulosta kilpikonnien nimet
  * Kirjoita `(turtle-names)` REPLissä ja katso tulosta
</section>

<section>
#### HARJOITUS 2: Tee vektori
{: .slide_title .slide}

* Mene `myproject`'n `core.clj` tiedostoon ja käynnistä REPL
* Tee Vektori seuraavan 7 päivän lämpötiloista valitsemastasi kaupungista
* Käytä sitten `nth` funktiota ja hae seuraavan tiistain lämpötila
</section>


<section ng-controller="NarrativeController">
### Mapit 

#### Avain arvo-parit <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

>Maps hold a set of keys and values associated with them. You can
>think of it like a dictionary: you look up things using a word (a
>keyword) and see the definition (its value). If you've programmed in
>another language, you might have seen something like maps--maybe
>called dictionaries, hashes, or associative arrays.
{: ng-show="block101" .description}

![Map](img/map.png)
</section>

<section ng-controller="NarrativeController">
#### Syntaksi <button class="link" ng-bind-html="details" ng-model="block102" ng-click="block102=!block102"></button>

> We write maps by enclosing alternating keys and values in curly braces, like so.
{: ng-show="block102" .description}

> Maps are useful because they can hold data in a way we normally
> think about it. Take our made up example, Sally Brown. A map can
> hold her first name and last name, her address, her favorite food,
> or anything else. It's a simple way to collect that data and make it
> easy to look up. The last example is an empty map. It is a map that
> is ready to hold some things, but doesn't have anything in it yet.
{: ng-show="block102" .description}

```clojure
{:first "Sally" :last "Brown"}
{:a 1 :b "two"}
{}
```
</section>

<section ng-controller="NarrativeController">
#### Esimerkki <button class="link" ng-bind-html="details" ng-model="block103" ng-click="block103=!block103"></button>

> kilpikonnien `forward` ja `right` komennot palauttavat 
> tuloksen mappina mäpin sisällä
{: ng-show="block103" .description}

```clojure
(forward 40)
;=> {:trinity {:length 40}}
(right 90)
;=> {:trinity {:angle 90}}
```
</section>

<section ng-controller="NarrativeController">
#### Luominen <button class="link" ng-bind-html="details" ng-model="block104" ng-click="block104=!block104"></button>

> `assoc` and `dissoc` are paired functions: they associate and disassociate items from a map. See how we add the last name "Brown" to the map with `assoc`, and then we remove it with `dissoc`. `merge` merges two maps together to make a new map.
{: ng-show="block104" .description}

```clojure
(assoc {:first "Sally"} :last "Brown")
;=> {:first "Sally", :last "Brown"}

(dissoc {:first "Sally" :last "Brown"} :last)
;=> {:first "Sally"}

(merge {:first "Sally"} {:last "Brown"})
;=> {:first "Sally", :last "Brown"}
```
</section>

<section ng-controller="NarrativeController">
#### Käsittely 1 <button class="link" ng-bind-html="details" ng-model="block105" ng-click="block105=!block105"></button>

> `count`, every collection has this function. Why do you think the
> answer is two? `count` is returning the number of associations.
{: ng-show="block105" .description}

> Since map is a key-value pair, the key is used to get a value from a
> map. One of the ways often used in Clojure is the examples below.
> We can use a keyword like using a function in order to look
> up values in a map. In the last example, we supplied the key `:MISS`.
> This works when the key we asked for is not in the map.
{: ng-show="block105" .description}

```clojure
(count {:first "Sally" :last "Brown"})
;=> 2

(get {:first "Sally" :last "Brown"} :first)
;=> "Sally"
(get {:first "Sally"} :last)
;=> nil


(get {:first "Sally"} :last :MISS)
;=> :MISS
```
</section>

<section ng-controller="NarrativeController">
#### Käsittely 2 <button class="link" ng-bind-html="details" ng-model="block106" ng-click="block106=!block106"></button>

> Then we have `keys` and `vals`, which are pretty simple: they return
> the keys and values in the map. The order is not guaranteed, so we
> could have gotten `(:first :last)` or `(:last :first)`.
{: ng-show="block106" .description}

```clojure
(keys {:first "Sally" :last "Brown"})
;=> (:first :last)

(vals {:first "Sally" :last "Brown"})
;=> ("Sally" "Brown")
```
</section>

<section ng-controller="NarrativeController">
#### Päivittäminen <button class="link" ng-bind-html="details" ng-model="block110" ng-click="block110=!block110"></button>

> After the creation, we want to save a new value associated to the
> key. The `assoc` function can be used by assigning a new value to
> the existing key.
> Also, there's handy function `update`. The function takes map and
> a key with a function. The value of specified key will be the first
> argument of the given function.
> The `update-in` function works like `update`, but takes a vector of keys
> to update at a path to a nested map.
{: ng-show="block110" .description}

```clojure
(def hello {:count 1 :words "hello"})

(update hello :count inc)
;=> {:count 2, :words "hello"}
(update hello :words str ", world")
;=> {:count 1, :words "hello, world"}


(def mine {:pet {:age 5 :name "able"}})

(update-in mine [:pet :age] - 3)
;=> {:pet {:age 2, :name "able"}}
```
</section>


<section>
### Kokoelmien kokoelmat

#### <button class="link" ng-model="block101" ng-click="block101=!block101">Intro</button>

> Simple values such as numbers, keywords, and strings are not the
> only types of things you can put into collections. You can also put
> other collections into collections, so you can have a vector of
> maps, or a list of vectors, or whatever combination fits your data.
{: ng-show="block101" .description}
</section>

<section>
#### Vektori mappeja

```clojure
(state-all)
;=> [{:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996, :angle 90, :color [106 40 126]}}
{:neo {:x 21.213202971967114, :y 21.213203899225725, :angle 45, :color [0 64 0]}}
{:oracle {:x -49.99999999999981, :y -4.3711390001862375E-6, :angle 180, :color [43 101 236]}}]

(def states (state-all))
;=> #'clojurebridge-turtle.walk/states

(first states)
;=> {:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996,
:angle 90, :color [106 40 126]}}
```
</section>

<section>
#### Mappi mappeja

```clojure
(def st (first states))
;=> #'clojurebridge-turtle.walk/st

st
;=> {:trinity {:x -1.7484556000744965E-6, :y 39.99999999999996,
;=>            :angle 90, :color [30 30 30]}}

(get st :trinity)
;=> {:x -1.7484556000744965E-6, :y 39.99999999999996,
;=>  :angle 90, :color [30 30 30]}

(get-in st [:trinity :angle])
;=> 90
```
</section>


<section>
#### HARJOTUS 3: Kilpikonnien tilat
{: .slide_title .slide}

* Avaa `walk.clj` tiedosto
* Kokeile esimerkkejä edelliseltä sivulta
* Mitä arvoja saat?

> Älä unohda painaa __enteriä__ Replissä komentojen jälkeen


```clojure
(state-all)
(def states (state-all))
(first states)
(def st (first states))
st
(get st :trinity)
(get-in st [:trinity :angle])
```
</section>

<section>
#### HARJOITUS 4: Mallinna itsesi
{: .slide_title .slide}

* Avaa `myproject`:n `core.clj` ja InstaREPL
* Tee Map-rakenne itsestäsi
* Lisää ainakin etunimesi ja sukunimesi
* Sitten lisää kotikaupunkisi käyttäen [assoc](http://grimoire.arrdem.com/1.6.0/clojure.core/assoc/) tai [merge](http://grimoire.arrdem.com/1.6.0/clojure.core/merge/) funktioita.
</section>

<section>
#### HARJOITUS 5 [BONUS]: Mallinna kurssitovereistasi
{: .slide_title .slide}

* Ota talteen aikaisemmassa harjoituksessa tekemästi Map-rakenne itsestäsi
* Luo sitten vektori joka sisältää map-rakenteet muutamasta kurssitoveristasi (ainakin etunimi, sukunimi ja kotikaupunki)
* Viimeiseksi lisää omat tietosi vektoriin käyttäen [conj](http://grimoire.arrdem.com/1.6.0/clojure.core/conj/) funktiota.
</section>

{% comment %}

:star2: A link below is for a slide only. Go to [README.md](../README.md)
instead. :star2:

{% endcomment %}

<section>
Palaa <a href="javascript:;" onClick="Reveal.slide(1);">alkuun</a>,
tai [sisällysluetteloon](/curriculum/#/1).
</section>
