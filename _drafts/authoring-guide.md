---
title: Guide de rédaction des Tontons Codeurs
subtitle: Conseils et bonnes pratiques à adopter
author: steph
type: guide
tags: [Jekyll, Liquid, Markdown]
styled: true
---

Ce petit guide est destiné à vous présenter comment s'organise globalement le contenu rédactionnel du site pour pouvoir commencer à rédiger vos articles. La structure générale d'un article est présentée pour être conforme aux règles inhérentes au fonctionnement de Jekyll. Puis un catalogue de recettes de mise en forme est proposé pour vous guider dans la rédaction de vos articles et vous donner quelques astuces pour vous faciliter les choses.

<!---------------------------------------------------------------------------->
<!--                            nouvelle section                            -->
<!---------------------------------------------------------------------------->

# Structuration des contenus du site

Les articles du site sont répartis selon deux collections distinctes :

- les **posts**, qui correspondent grosso modo à des billets de blog,
- les **guides**, qui sont plutôt destinés à identifier des articles de fond comme les tutoriels.

Les **posts** sont rassemblés dans le dossier `_posts` et doivent respecter la nomenclature suivante :

```
YYYY-MM-DD-slugified-title.md
```

où `YYYY-MM-DD` désigne la date de publication du post au format ISO-8601, et `slugified-title` est le titre du post réécrit pour être utilisé comme une URL. L'extension `.md` désigne un fichier Markdown.

Par exemple, pour un post dont :

- le titre serait ***Guide du rédacteur***,
- et la date de publication serait le **1er juillet 2019**,

le fichier correspondant devra être nommé :

```
2019-07-01-guide-du-redacteur.md
```

Jekyll publiera automatiquement cet article avec l'URL suivante :

```
https://les-tontons-codeurs.fr/2019/07/01/guide-du-redacteur/
```

N'oubliez pas qu'une URL bien formée facilite le référencement par les moteurs de recherche  <i class="far fa-smile-wink"></i>

Les **guides**, quant à eux, sont rassemblés dans le dossier `_guides` et doivent respecter la nomenclature suivante :

```
slugified-title.md
```

<!---------------------------------------------------------------------------->
<!--                            nouvelle section                            -->
<!---------------------------------------------------------------------------->

# Comment masquer les articles en cours de rédaction

Pendant la phase de rédaction de l'article, vous pouvez travailler sur un brouillon et l'intégrer dans l'arborescence du dépôt `git` tout en faisant en sorte qu'il ne soit pas visible sur le site tant qu'il n'est pas publié. Pour cela, il vous suffit de placer votre brouillon dans le répertoire `_drafts`. Vous pouvez nommer le fichier de l'article comme bon vous semble. Jekyll fera en sorte de lui attribuer une URL provisoire de façon à ce que vous puissiez visualiser le rendu avant publication. Toutefois, cette fonctionnalité n'est possible qu'en exécutant Jekyll sur votre poste de travail. Vous ne pourrez pas visualiser vos brouillons sur le site hébergé par GitHub Pages.

Jekyll considèrera toujours qu'un **draft** est un **post** et lui attribuera automatiquement la date de dernière modification du fichier pour générer l'URL du post. **Vous ne devez pas** spécifier la date de publication dans le nom du fichier tant que l'article est enregistré dans le répertoire `_drafts`.

Vous pouvez également travailler sur un article qui sera publié comme un **guide**, même si Jekyll le considère comme un **post**. C'est précisément ce que je fais en rédigeant le guide que vous êtes en train de lire. Ce guide n'est pas destiné à être publié sur le site. Il nous est réservé, et restera donc sagement dans le répertoire `_drafts` comme doc de référence, invisible au public.

Supposons que l'on souhaite travailler sur un guide qu'on envisage d'intituler ***Comment animer un sprite***. Il suffira de créer le fichier suivant :

```
_drafts
  └─ comment-animer-un-sprite.md
```

Pour faire en sorte que Jekyll vous donne accès aux brouillons, vous devez l'exécuter sur votre poste de travail avec la commande suivante :

```
jekyll serve --drafts
```

Pointez ensuite votre navigateur sur l'adresse suivante pour accéder à la page d'accueil du site localement :

```
http://localhost:4000/
```

Vous verrez apparaître votre brouillon dans la rubrique des **news** en pole position.

Lorsque vous souhaiterez publier votre article :

- s'il s'agit d'un **post**, déplacez-le dans le répertoire `_posts` en renommant le fichier avec la règle énoncée à la rubrique précédente (préfixez le nom du fichier avec la date de publication) ;
- s'il s'agit d'un **guide**, vous devrez spécifier sa date de publication dans le préambule du fichier (cette étape est expliquée à la section suivante), et il ne vous restera plus qu'à le déplacer simplement dans le répertoire `_guides`.

<!---------------------------------------------------------------------------->
<!--                            nouvelle section                            -->
<!---------------------------------------------------------------------------->

# Structure d'un article

L'usage de Jekyll comme générateur des pages du site implique de caractériser et décrire les articles par un certain nombre de métadonnées. Ces métadonnées doivent être spécifiées dans un préambule qui doit figurer au début du fichier de l'article :

```yaml
---
métadonnées de l'article
---

corps de l'article
```

Le corps de l'article, quant à lui, est entièrement composé de texte au format Markdown. Lorsque le contenu impose une mise en forme locale complexe que Markdown n'est pas capable de décrire, vous pouvez directement injecter du code HTML pour définir la structure votre mise en forme.

Les métadonnées définies dans le préambule correspondent à la liste des propriétés suivantes :

<div class="scrollable" markdown="1">

| propriété   | description                | valeur     | requise                      | multi-valuée                 |
|:-----------:|:---------------------------|:-----------|:----------------------------:|:----------------------------:|
| `title`     | le titre de l'article      | libre      | <i class="fas fa-check"></i> |                              |
| `subtitle`  | un sous-titre              | libre      |                              |                              |
| `author`    | auteur de l'article        | normalisée | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> |
| `date`      | date de publication        | normalisée | pour les guides              |                              |
| `icon`      | icône associée à l'article | normalisée |                              |                              |
| `type`      | typologie de l'article     | normalisée |                              | <i class="fas fa-check"></i> |
| `platforms` | plateformes concernées     | normalisée |                              | <i class="fas fa-check"></i> |
| `languages` | langages concernés         | normalisée |                              | <i class="fas fa-check"></i> |
| `tags`      | mots-clés principaux       | libre      |                              | <i class="fas fa-check"></i> |

</div>

Les valeurs attribuées à ces propriétés peuvent être libres ou imposées par une nomenclature définie dans la configuration générale du site. Les propriétés normalisées et leurs domaines de valeurs sont les suivants :

```
+--------+-----------+          +--------+-----------+-----------+
| author | icon      |          | type   | platforms | languages |
+--------+-----------+          +--------+-----------+-----------+
| max    | 32blit    |          | guide  | 32blit    | c         |
| steph  | adafruit  |          | recipe | arduboy   | cpp       | c++
| titi   | gamebuino |          | test   | arduino   | js        | javascript
|        | pewpewb   | big      |        | gamebuino | lua       |
|        | pewpews   | small    |        | gameshell | mc        | makecode
|        | pixelart  |          |        | microbit  | py        | python
|        | tontons   |          |        | pewpew    |           |
|        | tontons   |          |        | pygamer   |           |
+--------+-----------+          +--------+-----------+-----------+
```

La propriété `date` doit être spécifiée au format ISO-8601 : `YYYY-MM-DD`. **Attention** : vous ne devez pas spécifier de date quand vous travaillez sur un brouillon, dans le répertoire `_drafts`.

Les propriétés `author`, `type`, `platforms`, `languages` et `tags` peuvent être multivaluées. Dans ce cas, la valeur sera exprimée sous la forme d'un tableau : `[value1, value2, ...]`.

Voici un exemple de préambule pour se fixer les idées :

```yaml
---
title: Comparatif de la Gamebuino META, du PyGamer et de la 32blit
subtitle: Des consoles de Retro-Gaming pour apprendre la programmation
author: titi
date: 2019-07-01
icon: tontons
type: test
platforms: [gamebuino, pygamer, 32blit]
languages: [c, cpp, mc, py, lua]
tags: [Banc d'essai, Architecture, Connectivité]
---
```

Les propriétés dont les valeurs sont normalisées permettent d'harmoniser le rendu du site avec des libellés standardisés et identiques d'un article à l'autre. Toutes ces métadonnées permettront de faciliter la classification des articles sur le site et de générer automatiquement des éléments graphiques pour que le visiteur puisse identifier rapidement ces critères de classification sur les listes d'articles.

Par exemple, lorsqu'une liste d'articles est construite, comme sur la page d'accueil par exemple, chaque article est automatiquement affublé d'une icône. Vous pouvez définir l'icône qui sera associée à l'article par l'intermédiaire de la propriété `icon`. Les icônes actuellement disponibles sont les suivantes :

<div class="icons">
    {% for i in site.data.icons %}
        <div class="named_icon">
            <span class="icon {{ i.class }}"></span>
            <code class="highlighter-rouge">{{ i.key }}</code>
        </div>
    {% endfor %}
</div>

Si la propriété `icon` n'est pas spécifiée dans le préambule de l'article, l'icône `tontons` lui sera automatiquement attribuée. C'est l'icône générique en quelque sorte.

> N'hésitez pas à me demander de nouvelles icônes si nécessaire  <i class="far fa-smile-wink"></i>
{: .center }

<!---------------------------------------------------------------------------->
<!--                            nouvelle section                            -->
<!---------------------------------------------------------------------------->

# Astuces de mise en forme

Nous allons maintenant examiner quelques règles de mise en forme à appliquer à la plupart des composants dont vous aurez besoin au cours de la rédaction de vos articles. Je pars du principe que vous maîtrisez le langage Markdown et ses règles syntaxiques. Je ne m'attarderai donc pas sur son usage standard. Notez que Jekyll utilise par défaut un dialecte enrichi de Markdown automatiquement interprété par le moteur [Kramdown](https://kramdown.gettalong.org/quickref.html).

## Blocs de code

Nos articles seront souvent parsemés de code et Jekyll nous permet d'effectuer leur mise en forme de manière automatique avec son module <span style="color:#a00">Rouge</span>, chargé d'appliquer une coloration syntaxique selon la grammaire des langages utilisés. Pour introduire un bloc de code, vous pouvez vous appuyer sur les règles standards de Markdown et même spécifier le langage utilisé. Par exemple, pour introduire un code C++, on écrira :

    ```cpp

    // le code...

    ```

<span style="color:#a00">Rouge</span> appliquera alors une mise en forme du code adaptée au langage C++, dont voici un exemple :

```cpp
#include <Gamebuino-Meta.h>

void setup () {
    gb.begin();
}

void loop() {
    gb.waitForUpdate();
    gb.display.clear();
    gb.display.print(2, 2, "Hello World!");
}
```

<span style="color:#a00">Rouge</span> permet également d'afficher un bloc de code avec la numérotation des lignes. Mais pour utiliser cette fonctionnalité, Markdown n'est pas suffisant. Il faudra donc introduire votre bloc de code en utilisant des directives [Liquid](https://shopify.github.io/liquid/), qui est le moteur de template de Jekyll.

Par exemple, pour introduire un bloc de code Python avec numérotation automatique des lignes, on écrira :


```
{{ '{% highlight py linenos '}}%}

# le code...

{{ '{% endhighlight '}}%}
```

<span style="color:#a00">Rouge</span> appliquera alors une mise en forme du code adaptée au langage Python, dont voici un exemple :

{% highlight py linenos %}
from gamebuino_meta import waitForUpdate, display

def draw():
    display.clear()
    display.print(2, 2, "Hello World!")

while True:
    waitForUpdate()
    draw()
{% endhighlight %}

