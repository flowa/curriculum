ClojureBridge Teacher's Guide
=============================

There are many ways to teach the ClojureBridge material, and none of them are "right." The following is a guide to working though the curriculum with students based on the experience of some workshop organizers and teachers.

There are six pieces to the curriculum: the curriculum
[slides and narrative](http://clojurebridge.github.io/curriculum),
and the capstone app part.1:
[Drawing Lines](https://github.com/ClojureBridge/drawing/blob/master/curriculum/first-program.md).
For capstone app part. 2,
[Turtles Walk](https://github.com/ClojureBridge/welcometoclojurebridge/blob/master/outline/TURTLE-SAMPLES.md)
(for function study),
[Snowflakes](https://github.com/ClojureBridge/drawing/blob/master/curriculum/create-something.md)
(another drawing app),
[Twinkle Twinkle Little Star](https://github.com/ClojureBridge/tones/blob/master/curriculum/01-piano-chords.md) (making sounds),
[Global Growth](https://github.com/ClojureBridge/global-growth)  (web app with REST API),
[Caesar Cipher](http://clojurebridge.github.io/community-docs/docs/exercises/caesar-cipher/)
(mini exercise of Strings and Characters).

You may skip bonus sections and a module to fit with a workshop
progress. However, to go over part. 2 capstone apps, some bonuses should
be covered. For example, Turtles Walk, Twinkle Twinkle Little Star, and later
steps of Snowflakes use sequences and let binding. If your students
come to these apps, it's a good idea to get back to main curriculum.

Step 1-3 of Snowflakes app are the easiest to try out. It just needs a flow
control in addition to the part. 1 app. While Global Growth is quite a high
level app and only for very advanced students. Copy&pasting code only
won't take so long, but it requires REST API and ring/compojure
knowledge. Snowflakes and Twinkle... are fun apps and worth trying out.

The slides and the narrative curriculum are the exactly the same
files. The slide forms are what you show on the projector in front of
the room, while the narrative forms are easy to read detailed
explanation of what is introduced in the slides. Students follow along
with the narrative on their own computers or use it to work on their
own.

Curriculum
----------
Fork the curriculum [repository](https://github.com/ClojureBridge/curriculum) using your chapter's GitHub account (or your own personal GitHub account). You can use your own fork to make changes or tweaks to the curriculum for your own workshop. If you make changes that would be valuable for everyone, please consider making a pull request against the main curriculum.

Schedule
--------
Friday evening: Installfest - [Getting Set Up](outline/setup.md) in the outline.

Saturday: Workshop -  [curriculum](README.md#curriculum).

Preparation
-----------
Print the ([markdown](outline/cheatsheet.md) or [pdf](ClojurebridgeCheatsheet-v2.pdf)) and hand it out to students at the beginning of the day on Saturday.

Room Setup
----------
It works best to have attendees sit around tables, facing one another. This encourages attendees to help one another and makes it easier for TAs to walk around the room, answering questions.

Presentation of the Material
----------------------------
Most workshops have both teachers and TAs. Teachers present the material at the front of the room, and TAs and teachers help students as they work through the exercises on their own and with their tablemates. This is different from how RailsBridge usually works, where students generally work through the material in groups with the help of TAs.

This is not the only way to present the material. It is just the way we have seen it done at most of the workshops so far. Please feel free to experiment.


Oracle JDK 8
-------------

#### Ubuntu
Main curriculum and most of other materials are adjusted to Nightcode 2.1.0. This version needs Oracle JDK 8. Linux OSes are normally shipped with OpenJDK. Linux students need to install Oracle Java. The setup document only explains how to do by `apt-get`. However, they have a choice to downlad JDK and setup JAVA_HOME/PATH environment variables. They may logout once to make those variables effect on a new shell.

#### El Capitan
OSX El Capitan doesn't have Java bundled anymore. El Capitan Students must install Oracle JDK 8.
Installation steps are the same as Windows, fairly easy. However, after installation, they should have `JAVA_HOME` environment variable setup. This, `export JAVA_HOME=/usr/libexec/java_home -v 1.8`, would be useful to set `JAVA_HOME`. Also, the `JAVA_HOME` setting should be in `.bash_profile` or some other shell setup file.


Nightcode
---------

As of September 2016, ClojureBridge materials are based on Nightcode 2.1.0. This version has only one REPL on the bottom and InstaREPL. However, InstREPL doesn't work well with Quil and Overton apps. For simple core Clojure only exercies, students can use `myproject` (this should be created while leningen setup) and InstaREPL.

#### Use jar archive

Since Nightcode 2.0.x, it got installers.
However, jar archive is much easier to get started.
Typing a single java command is all you need.
Tell students to download Jar archive.

#### Code in file or REPL

Students may confuse where to write code. REPL is handy, but doesn't save code.
Also, on REPL, multiline input doesn't work. When code needs to be multiline, code should be typed in editor.
Nightcode default setting is auto-save, but it would be a good practice to click save button.

[background]
ClojureBridge used LightTable previously, which allowed us to do everything in the editor with InstaREPL.

#### Keyboard shortcuts

Materials don't mention keyboard shortcuts.
We don't have much experience on Nightcode yet,
so we are not sure the same keyboard shortcut works on all platforms.
If it does, we will add in the materials.
Let us know.


Beginner and Advanced Tracks
----------------------------
You can survey the attendees ahead of time or during the Installfest to find out their levels of programming experience. If you have multiple teachers available, you could present the material in separate rooms at a different pace, or you could present separate material. Alternatively, you could keep all attendees in the same room but seat them in different tables according to ability.

Exercises
---------
Provide plenty of time for exercises. That is where the real fun happens. TAs should sit with attendees or circulate around the tables as the attendees work on exercises.

Capstone App
------------
Budget your time so that you have enough time for the part 2 project at the end of the day.

Outline
-------
TODO: add tips under each heading.

* [Getting Set Up](outline/setup.md)
* [Introduction to Programming with Clojure](outline/intro.md)
  - 20 min
* [Simple Values](outline/simple_values.md)
  - 30 min
* [Data Structures](outline/data_structures.md)
  - 60 min
* [Functions](outline/functions.md)
  - 45-60 min
* [Capstone App 1](https://github.com/flowa/drawing/blob/master/curriculum/first-program.md)
  - 60 min
* [Flow Control](outline/flow_control.md)
  - 20 min
* [[bonus] Sequences](outline/sequences.md)
  - 10 min

* [Capstone App Pt. 2]
  - 60 - 90 min each


Supporting Materials
--------------------
* [Student cheatsheet](outline/cheatsheet.md) | [PDF](ClojurebridgeCheatsheet-v2.pdf)
* [Slides](https://flowa.github.io/curriculum)


Other Curricula
---------------
The main [curriculum](https://github.com/ClojureBridge/curriculum) is well-tested, but there are a number of other curricula available. Feel free to try them out.

* [Minneapolis chatter](https://github.com/clojurebridge-minneapolis/track1-chatter)
* [Minneapolis threading](https://github.com/clojurebridge-minneapolis/track2-threading)
* [Minneapolis surviving](https://github.com/clojurebridge-minneapolis/track2-surviving)
* More to come! Add yours here.
