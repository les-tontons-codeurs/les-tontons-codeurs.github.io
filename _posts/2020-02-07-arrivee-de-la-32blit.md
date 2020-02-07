---
title:  Arrivée de la 32blit
author: [titi]
platforms: [32blit]
languages: []
tags: [microcontrôleurs]
---

{% include myassets.html %}

Après un délai un peu plus long que prévu, ma 32blit de Pimoroni est enfin arrivée à la maison !<br/>
Voyons voir ce qui se cache dans ce joli colis.

<!--more-->

Je trouve que même le colis et la boîte est joli, à l'effigie de [Pimoroni][1].
[![colis]({{ myassets }}/images/colis.jpg)](https://photos.app.goo.gl/AhaJU4AvMmDRcvwG6)
[![boite]({{ myassets }}/images/boite.jpg)](https://photos.app.goo.gl/KVACy1iiN18omDNAA)

Le contenu est riche dans cette jolie boite, à voir le contenu final, nous parlons ici de la version beta.<br/>
Nous trouvons donc :

- la 32blit elle même,
- une feuille avec quelques instructions, notament l'adresse du github de la beta,
- de nombreux autocollants,
- une petite plaque de prototypage aux couleurs de Noël

[![contenu]({{ myassets }}/images/contenu.jpg)](https://photos.app.goo.gl/6ysK6GKJD7KcAGhw5)

La 32blit a une bonne finition, même si la version beta n'a pas de coque, il y a néanmoins une plaque de plexiglas protégeant les composant sous la console.
Comme indiqué dans le [précédent article]({% post_url 2019-08-20-point-sur-la-32blit %}) sur la 32blit, la décoration du PCB utilise le [travail de Johan Vinet][2].

[![dessus 32blit]({{ myassets }}/images/32blit_face.jpg)](https://photos.app.goo.gl/nLZRitdXXxrYACVb6)
[![dessous 32blit]({{ myassets }}/images/32blit_bottom.jpg)](https://photos.app.goo.gl/3pCb9jGLxceVEjBM7)

Je vous propose d'aller voir d'autres photos dans [cet album dédié](https://photos.app.goo.gl/7uz2z58vdPEACnH76).
<br/>
<br/>
La mise en oeuvre est déjà assez bien détaillée au sein du [dépôt github de la beta](https://github.com/pimoroni/32blit-beta/).<br/>
Les projets d'exemple se compilent bien, ils sont même utilisables en mode desktop.<br/>
Il est possible de compiler en utilisant les librairies SDL.<br/>
<br/>
Le seul point qui m'a fait trébucher a été la confusion que j'ai eu entre dfu-tool et dfu-util. Seul ce dernier est a utiliser sous linux et 
 à partir de là je n'ai pas eu de problème à uploader les codes compilés.<br/><br/>

Je pense que la prochaine étape sera de vous expliquer ce que contient un projet type, mais il y a encore un peu de stabilisation en cours.<br/>
Nous verrons tout cela dès que possible.<br/>
En attendant, je vous laisse, la 32blit, la Pewpew M4 et une nouvelle carte arrivée aussi aujourd'hui m'attendent :)

[1]: http://www.pimoroni.com
[2]: https://canarigames.itch.io/canaripack-1bit-topdown
[3]: https://github.com/pimoroni/32blit-beta/