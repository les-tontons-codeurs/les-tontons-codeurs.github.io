---
title:  PewPew M4 prototype
author: [titi]
platforms: [pewpew]
languages: []
tags: [microcontrôleurs]
---

{% include myassets.html %}

Alors que la 32blit est arrivée chez moi, mais nécessite un bon investissement technique, j'ai eu la joie de recevoir 
un prototype de la nouvelle venue dans la famille PewPew : la PewPew M4

<!--more-->

Toujours dans sa quête de proposer un appareil simple mais complet, [Radomir Dopieralski][1], souvent connu par son 
pseudo [Deshipu][2], a encore conçu une nouvelle possibilité.<br/>

Je ne vous fait pas plus attendre, voici la très jolie [PewPew M4][3].
[![PewPew M4]({{ myassets }}/images/pewpewM4kit.jpg)](https://photos.app.goo.gl/2W5np8p7Wa58p8Gy6)
[![PewPew M4]({{ myassets }}/images/pewpewM4_pcdface.jpg)](https://photos.app.goo.gl/APME4m6EY9tJeuk59)

Voilà donc une petite console bien équipée :

- écran TFT de 160 par 128
- 7 boutons disposés en une croix directionnelle à gauche et 3 boutons d'action à droite
- microcontrôleur SAMD51 ARM Cortex M4
- buzzer de 7 mm
- interrupteur marche/arrêt
- bloc d'accueil pour 2 piles AAA
- accès à des broches pour étendre la partie matérielle

<br/>
Ce qui est intéressant avec cette pewpew c'est qu'elle est entièrement contrôlable par Circuit Python, mais également 
par [Arcade Makecode][4]<br/>
<br/>
Pour Arcade, aucun souci technique ça fonctionne déjà, mais il faut que l'équipe qui gère l'ajout de nouvelles cartes valide la demande.<br/>
En attendant, il est possible d'utiliser en choisissant la pygamer comme console cible.
<br/>
<br/>
Côté Circuit Python, ça fonctionne déjà très bien.<br/>
Par défaut, un menu semblable dans l'esprit à celui des pewpew de base permet de voir une liste des fichiers python présent et de choisir celui que l'on souhaite exécuter.<br/>
[![Menu]({{ myassets }}/images/pewpewM4menu.jpg)](https://photos.app.goo.gl/cpZFFxg1TfkpwsFN8)

Mais le fonctionnement normal de CircuitPython est toujours là, vous pouvez élaborer votre code dans le fichier code.py, qui a priorité sur main.py, ou bien
décider de tout remplacer et développer avec main.py


Tout ça s'annonce très bien pour cette jolie petite console.<br/>
<br/>
Pour se la procurer, soit Deshipu en produit une nouvelle série et la vend par le biais de [Tindie][5], soit vous patientez
 et vous utilisez le site [MakerFabs][6] dont je vous met ici la page d'une autre version de PewPew.<br/>
<br/>
J'ai maintenant hâte de me mettre à écrire un petit jeu pour la Pewpew M4 et je vais essayer de vous faire rapidement une
 présentation vidéo de cette charmante console.<br/>
<br/>
Encore bravo à Radomir pour tout ce travail, la famille PewPew est passionnante !

[1]: http://sheep.art.pl/
[2]: https://hackaday.io/deshipu
[3]: https://hackaday.io/project/165032-pewpew-m4
[4]: https://arcade.makecode.com/
[5]: https://www.tindie.com/products/deshipu/pewpew-m4-prototype/
[6]: https://www.makerfabs.com/pewpew-standalone.html