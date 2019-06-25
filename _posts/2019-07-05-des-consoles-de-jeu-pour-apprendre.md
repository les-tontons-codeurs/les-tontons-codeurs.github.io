---
title: Des consoles de jeu pour apprendre à programmer
author: [titi]
platform: [32blit, gamebuino, pygamer, microbit, pewpew]
lang: [cpp, py, lua, mc]
tags: [Matériel, Général]
---

{% include myassets.html %}


Dans notre folle jeunesse, lorsque nous voulions jouer, nous allumions une de ces machines merveilleuses au doux nom de ZX Spectrum ou Commodore 64.
La micro informatique mettait son utilisateur en contact direct avec la possibilité de coder.
Mais pour atteindre un jeu, il fallait passer par des commandes qui étaient, dès le premier caractère, du code.
Qu'en est il aujourd'hui et qu'avons nous d'intéressant à disposition ?

<!--more-->

C'est de manière inattendue que le retour de ces principes de consoles de jeu qui se programment est revenu par le monde des micro contrôleurs.

Cet univers longtemps resté un monde d'électroniciens s'est ouvert peu à peu à des makers, bricolant avec les connaissances à leur disposition.
La publication de guides et tutoriels est devenue de plus en plus fréquente, certaines marques en faisant leur cheval de bataille comme [Adafruit](https://www.adafruit.com/)

Tout en continuant les efforts d'explication, les différents acteurs se sont mis à proposer des cartes et matériels plus adaptés à la découverte.
Le démon du jeu vidéo étant souvent à roder dans les poches des makers, il ne fallut pas longtemps pour que ces cartes soient équipées de petits écrans, puis de boutons...

Cette année, c'est l'effervescence autour de différentes consoles basées sur des micro contrôleurs.

Je vais simplement vous présenter brièvement les consoles que je possède et avec lesquelles j'écrirai des articles.

> **Remarque**
> 
> Je n'ai pas de préférence, elles ont chacune leurs atouts.

## Micro:bit

<div class="multicolum" markdown="1">
![La console micro:bit]({{ myassets }}/images/microbit.jpg){: .w-50 }

![La console micro:bit]({{ myassets }}/images/microbit meow.jpg){: .w-50 }
</div>

Place à celle par qui tout à commencé pour moi. La carte micro:bit est issue d'une initiative du gouvernement anglais piloté par la BBC et a été distribuée à un million d'exemplaire dans les [écoles anglaises en 2016][1].

La micro:bit peut se programmer visuellement avec un [éditeur à base de bloc][2]. <br>
Si vous cherchez comment commencer, il y a des exemples sur le site de la [fondation Raspberry][3] (s'il y a des fautes, dites le, c'est moi le coupable ;) )

Vous pouvez également la programmer en utilisant un python adapté, [MicroPython][7]. <br>
Pour cela, je vous encourage à utiliser [l'éditeur Mu][4].

## Pew Pew

<div class="multicolum" markdown="1">
![La console pewpew (version feather wing)]({{ myassets }}/images/pewpew.jpg){: .w-50 } 

![La console pewpew de dos (version feather wing)]({{ myassets }}/images/pewpew back.jpg){: .w-50 }
</div>

Cette carte est le fruit du travail de Radomir Dopieralski ([@Deshipu][5]) <br>
Elle est simple mais pourtant déjà plus évoluée que la micro:bit.

Elle est programmable en [MicroPython][7] ou en [CircuitPython][8]. <br>
Là encore, [l'éditeur Mu][4] est conseillé pour commencer.

Pour trouver des informations sur la pewpew et sa programmation, le [site de Radomir][6] est un bon point de départ.

## Gamebuino

![La console Gamebuino](/assets/images/gamebuino-856x462.png){: .w-50 }

Plus conséquente, la [Gamebuino][9] possède un écran, des touches, une batterie et un boitier.<br>
Elle est programmable en C++ ou en CircuitPython. <br>
Les entrées sorties de son micro controleur SAMD21 sont exposées au dos, permettant des montages électroniques pilotés par la Gamebuino.

Le site Gamebuino propose des tutoriels au sein de [l'Académie][10].

## Pygamer

![La console PyGamer](/assets/images/pygamer-832x486.png){: .w-50 }

La [Pygamer][11] est une console conçue et fabriquée par [Adafruit][12].

Cette année 2019 a vu l'explosion du nombre de conférence proposant des badges interactifs à leurs participants.<br>
Adafruit a peu à peu conçu une succession de cartes, depuis la [PyPortal][13] suivi du [PyBadge][14] pour aboutir à la PyGamer.

Ces cartes sont programmables en C++, CircuitPython ou même un éditeur de jeu entièrement graphique, [Arcade Makecode][15].<br>
La partie électronique est très accessible et bien documentée, vous trouverez des montages sur notre site également.

## 32Blit

![La console 32Blit]({{ myassets }}/images/32blit-teaser-square.jpg){: .w-50 }

Un autre fabricant de produits pour makers, [Pimoroni][16] se lance dans cette aventure.<br>
Souvent comparés à Adafruit en version européenne, leur produits sont généralement très bien documentés.

Cette console est encore à découvrir même si elle a déjà un [site dédié][17].<br>
En effet, cette console est née lors d'une [campagne Kickstarter][18] et n'a pas encore été livrée.

Rassurez vous, les tontons auront leur modèle, je suis même beta testeur et pourrait vous tenir informés ici même :)

<br>
Voilà, ces quelques cartes feront notre bonheur et nous espérons le votre également.<br>
Et ne vous inquiétez pas, nous resterons à l'affût des nouveautés !

[1]: https://microbit.org/fr/history/
[2]: https://makecode.microbit.org/
[3]: https://projects.raspberrypi.org/fr-FR/projects?hardware%5B%5D=microbit
[4]: https://codewith.mu/
[5]: http://sheep.art.pl/
[6]: http://sheep.art.pl/PewPew
[7]: http://micropython.org/
[8]: https://circuitpython.org/
[9]: https://gamebuino.com/
[10]: https://gamebuino.com/academy
[11]: https://learn.adafruit.com/adafruit-pygamer
[12]: https://www.adafruit.com/
[13]: https://learn.adafruit.com/adafruit-pyportal
[14]: https://learn.adafruit.com/adafruit-pybadge
[15]: https://arcade.makecode.com/
[16]: https://shop.pimoroni.com/
[17]: https://32blit.com/
[18]: https://www.kickstarter.com/projects/pimoroni/32blit-retro-inspired-handheld-with-open-source-fi/description