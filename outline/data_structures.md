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
* Hakemistot (Map)
</section>

<section>
### Nippu dataa - Kokoelmat
{: .slide_title .slide}

#### <button class="link" ng-model="block11" ng-click="block11=!block11">Intro</button>

> Tähän asti, olemme pelannet yksittäisillä, pienillä palasilla dataa: 
yksi numero, yksi merkkijono, yksi arvo. Ohjelmoitaessa tyypillisesti 
haluamme käsitellä joukko tällaisia pieni palasia.
{: ng-show="block11" .description}

> Clojuressa on erinomaiset työkalut tällaisten datajoukkojen - tai 
kokoelmien -  käsittelyyn. Sen lisäksi että clojure tarjoaa neljän erillaista 
koelmatyyppiä kokoelma, kieli tarjoaa myös yhtenäisen tavan käsitellä näitä 
rakentaita. 
{: ng-show="block11" .description}
</section>

<section ng-controller="NarrativeController">
### Vektorit
{: .slide_title .slide}

#### Peräkkäinen kokoelma <button class="link" ng-bind-html="details" ng-model="block21" ng-click="block21=!block21"></button>

> Verkori on perkkäinen kokoelma arvoja. A vektori voi olla tyhjä ja sen sisältämät arvo voivat 
olla erityyppiä.  jokainen arvo on numeroitu alkaen nollasta. Tätä numero kutustaan arvon indeksiksi.
Indeksiä käyteään kun haluataan käsitellä jotain tiettyä arvoon vektorissa.
{: ng-show="block21" .description}

#### Lokeromainen rakenne <button class="link" ng-bind-html="details" ng-model="block22" ng-click="block22=!block22"></button>

> voit ajatella vextorin laatikkona joka on jaettu samankokoisiin lokeroihin. Jokaisella lokerolla on numero, jota voit hyödyntää lattaaksesi dataa lokeroon, ja numeron avulla löydät aina sinne laittamasi datan.
{: ng-show="block22" .description}

> Huomaa että lokeron numeroinnnissa ensimmäinen lokeron indeksi on 0. Tämä voi tuntua aluksi omituisella, mutta ohjelmoitaessa laskeminen aloitetaan usein nollasta.
{: ng-show="block22" .description}

![Vector](img/vector.png)

</section>

<section ng-controller="NarrativeController">
#### Syntaksi <button class="link" ng-bind-html="details" ng-model="block31" ng-click="block31=!block31"></button>

>Vektorit esitellään käyttäen hakasulkeita ja pistämällä sulkeiden sisään halutut palaset dataa välilyönnillä erotettua. Tässä esimerkki vektorin käytöstä:
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

> Seuraavien kahden funktion avulla voit luoda uuden vektorin. `vector`
> funktio ottaa parameterina miten monta palasta dataa tahansa ja palauttaa
uuden vektorin josta data löytyy siinä järjestyksessä kuin ne olivat funktio kutsussa. 
> `conj` funktiota käytetään useiden eri tietorakenteiden kanssa. Vektoreiden tapauksessa, 
se ottaa vastaan ensimmäisenä parameterina vektorin ja palasen dataa, ja palauettaa 
vektorin, jonka viimeiseksi elementiksi toisena parametrina annettu pala dataa löytyy.

> Mistä nimi `conj` tulee? `conj` on lyennyt sanasta conjoin, mikä tarkoittaa 
kirjalimellisesti liittää yhteen tai yhdeksi. Juuri tähän sitä käytämme: liiteämme 
yhteen uuden palan dataan vektoriin.
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

> Tarkestellaanpa seuraavaksi neljää perusfunktio koelmien käsittelyyn:
`count` palauttaa vektorissa olevien elementtien lukumäärän. 
`nth` palauttee järjestyksessä n:nnen elementin kun laskeminen aloitetaan nollasta. Toisin sanoen kun kutsut funktiota nth numerolla 1 saat itse asiassa toisen elementin kokelmasta, et ensimmäistä. 
`first` palauttee ensimmäisen, eli indeksissä 0, olevan elementin. 
`rest` palauttaa kaikki muut elementi uutena vektorina lukuunottamatta ensimmäistä palasta dataa. Se miten `nth` toimii voi tuntua aluksi hämmentävältä etenkin, kun `first` toimii kuten luontevasti oletat sen toimivan.
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
  * Avaa `walk.clj` tiedosto
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
### Hakemistot (Map) 

#### Avain arvo-parit <button class="link" ng-bind-html="details" ng-model="block101" ng-click="block101=!block101"></button>

> Hakemisto (map) koostuu joukosta toisiinsa linkitettyjä avaimia ja
arvoja. Voi ajatella sen sanakirjana: löydyt sieltä avaimena käyttämällesi
sanalle määritelmän (arvo). Jos  sinulla on entuudestaan kokemusta jostain
muusta kielestä, niin vastaava tietorakenne löytyy niistä yleensä vaihtelevilla 
nimillä: dictionary, hajautustaulukko (hashtable), assosiatiivinen taulukko (associative array).
{: ng-show="block101" .description}

![Map](img/map.png)
</section>

<section ng-controller="NarrativeController">
#### Syntaksi <button class="link" ng-bind-html="details" ng-model="block102" ng-click="block102=!block102"></button>

> Hakemisto (map) esitellään laittamalla kaarisulkeiden sisään vuorollen avaimia ja arvoja.
{: ng-show="block102" .description}

> Hakemistot ovat luontevia monenessa arkisessa tilanteeseen. Otetaanpa 
keskitty esimerkki, Sally Brown. Hakemistoa (map) voi käyttää etunimen, 
tai sukunimen hakemiseen, tai yhdistämään nimi osoitteeseen - tai suosikki 
ruokaan, tai mihin tahansa muuhun. Kaikessa yksinkertaisuudessaan 
hakamisto (map) on kokoelma, josta on helppo löytää arvo kun tietää avaimen. 
Alla viiminen esimerkki on tyhjä hakemisto; hakemiston vektorin tapaan ei 
tarvitse sisältää dataa lainkaan.
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
> tuloksen sisäkkäiseinä hakemistoina
{: ng-show="block103" .description}

```clojure
(forward 40)
;=> {:trinity {:length 40}}
(right 90)
;=> {:trinity {:angle 90}}
```
</section>

<section ng-controller="NarrativeController">
#### Käsittely 1 <button class="link" ng-bind-html="details" ng-model="block104" ng-click="block104=!block104"></button>

> `assoc` ja `dissoc` muodostavat funktio parin: ensinnän mainittu liittää hakemistoon uuden arvon (associate) ja jälkimmäinen erottaa hakemistosta johokin avoin arvo parin.

Alla olevassa esimerkissä lisäämme ensin hakemistoon (map), josta löytyy jo tieto etunimestä ("Sally") sukunimen "Brown" käyttäen `assoc` funktiota, tämän jälkeen poistamme sen `dissoc` funktiolla. Lopuksi käyämme `merge` fuktiota kahden hakemiston yhdistämiseen.
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
#### Käsittely 2 <button class="link" ng-bind-html="details" ng-model="block105" ng-click="block105=!block105"></button>

> Jokaiselta koelmalla on `count` funktio. Katso alle olevaa esimerkkiä. Mistä syystä arvelet `count` funktion palauttavan arvon 2? `count` palauttaa avain-arvo parien määrän hakemistolle. (Vektorillehan `count` palautti arvojen määrän). 
{: ng-show="block105" .description}

> Voit yrittää hakea arvojoa hakemistosta (map) käytteän `get` funktiota. Funktio ottaa vastaan ensimmäisenä parametrina hakemiston, josta arvoja haetaan, toisena parametrina avaimen, minkä arvoa haet, ja kolmantane optionaalisena parametrina arvon, mikä palautetaan jos hakemisosta ei löydykään arvoa avaimelle. Alla oleva esimerkki havainnollistaa kunka `get`funktio toimii, jos aivamelle löytyy arvo funktio palauttaa sen, ellei sitä löyty palauteaan joko nil tai kolmantena parametrina annettu arvo :MISS.
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
#### Käsittely 3 <button class="link" ng-bind-html="details" ng-model="block106" ng-click="block106=!block106"></button>

> Voit myös kysyä mitä avaimia hakemisossa on `keys` funktiolla ja vastaavasti sen arvoja `vals` funktiolla funktio palauttavat avaimet jar arvot listana. Järjestys saattaa vaihdella, eli voi olla että all olevassa esimerkissä tulos on `(:first :last)` tai `(:last :first)`.
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

> Aiemmin käytimme `assoc` funtiota hakemiston muodostamiseen. Tokihan joskus avaimen arvoa on tarpeen päivittää. Tähän tarkoitukseen soveltuu parhaiten `update` funktio. Se ottaa ensimmäisenä parameterina hakemiston toisena avaimen jonka arvoa on tarkoitus päivittää ja viimeisenä funktion, jolla jolla arvoa pävitetään (alla olevissa esimerkeissä `inc` ja `str ", world` 
> `update-in` funktio toimii samaan tapaan kuin `update` sillä erotuksella että yksittäisen avaimen asemesta sille voi antaa parametrina "polun" useammasta sisäkkäisestä hakemisista koostuavan tietorakenteen arvoon. 
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

> Voi koelmiin mutakinn kuin vain yksittäisiä arvoja kuten numeroita, avainsanoja, tai merkkijonoja.
Voit pistää sinen myös kokelmia. Tietorakenteesi voi olla vaikkapa vektori hakemistoja, tai list
vektoreita, tai mikä tahansa ydistelmä, mikä soveltuu datasi esittämiseen. 
</section>

<section>
#### Vektori hakemistoja

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
#### Hakemisto hakemistoja

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
#### HARJOITUS 5 [BONUS]: Mallinna kurssitovereitasi
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
