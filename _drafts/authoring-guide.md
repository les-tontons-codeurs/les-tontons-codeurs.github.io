---
title: Guide de rédaction des Tontons Codeurs
subtitle: Conseils et bonnes pratiques à adopter
author: steph
type: guide
tags: [Jekyll, Liquid, Markdown]
styled: true
---

{% include myassets.html %}

Ce petit guide est destiné à vous présenter comment s'organise globalement le contenu rédactionnel du site pour pouvoir commencer à rédiger vos articles. La structure générale d'un article est présentée pour être conforme aux règles inhérentes au fonctionnement de Jekyll. Puis un catalogue de recettes de mise en forme est proposé pour vous guider dans la rédaction de vos articles et vous donner quelques astuces pour vous faciliter les choses.

<!--more-->


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

Nous verrons un peu plus loin qu'il est possible d'associer des ressources à votre article, comme des images, des vidéos, des styles personalisés ou même des codes JavaScript. Des mécanismes automatisés sont mis en place pour que vous puissiez accéder aux ressources spécifiques d'un articles simplement, tout en conservant une bonne organisation des contenus, et éviter que ça devienne le bazar au fur et à mesure de nos contributions. Vous devrez donc respecter l'organisation suivante :

```
article-assets
 `-- slugified-title
     |-- css
     |    `-- styles.scss
     |-- images
     |    |-- image1.gif
     |    |-- image2.png
     |    `-- image3.jpg
     |-- js
     |    `-- myscript.js
     `-- videos
          |-- video1.mp4
          `-- video2.webm
```

1. `article-assets` est le repertoire situé à la racine du dépôt.
2. Vous devez créer un répertoire `slugified-title` spécifique à votre article.
3. Votre feuille de styles personnalisés doit impérativement se nommer `styles.scss` et se trouver dans un répertoire `css`. L'extension `.scss` signifie que vous pouvez coder votre feuille de syles en utilisant le langage [Sass][sass]. Si vous ne maîtrisez pas ce langage, vous pouvez vous contenter du langage **CSS**... mais l'extension du fichier doit nécessairement rester `.scss`. Dernière chose : pour que Jekyll compile votre feuille de styles, vous devez **nécessairement** ajouter un préambule vide en début de fichier :

```yaml
---
# préambule vide mais nécessaire
---

.myclass {
    ...
}
```

Vous pouvez examiner le contenu actuel du répertoire `article-assets` pour voir comment j'ai organisé les choses en ce qui concerne le présent guide.

> **Remarque importante**
> 
> Lorsque vous aurez besoin de faire référence à ces ressources locales, vous devrez en spécifier le chemin. Pour cela, j'ai défini une variable `myassets` à utiliser **systématiquement** pour faire référence au répertoire de ressources de **votre** article. Pour charger la définition de cette variable dans le scope de votre article, vous devez ajouter la directive Liquid suivante en début de fichier, juste après le préambule :
> 
> 
> ```liquid
> {{ '{% include myassets.html' }} %}
> ```


{% comment %}
--------------------------------------------------------------------------------
--                              nouvelle section                              --
--------------------------------------------------------------------------------
{% endcomment %}


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


{% comment %}
--------------------------------------------------------------------------------
--                              nouvelle section                              --
--------------------------------------------------------------------------------
{% endcomment %}


# Structure d'un article

La structure générale d'un article se décompose de la façon suivante :

```yaml
---
# Préambule
métadonnées de l'article
---

résumé de l'article

<!--more-->

corps de l'article
```

L'usage de Jekyll comme générateur des pages du site implique de caractériser et décrire les articles par un certain nombre de métadonnées. Ces métadonnées doivent être spécifiées dans un **préambule** qui doit figurer au début du fichier de l'article.

---

Vient ensuite un petit texte introductif qui doit être considéré comme le **résumé** de l'article. C'est ce petit texte qui sera affiché en page d'accueil, par exemple, pour présenter le contenu de l'article. En règle générale, on se limitera à un simple paragraphe... bien qu'il soit possible dans l'absolu d'en mettre plusieurs.

---

La balise HTML `<!--more-->` marque la fin du résumé et le début du corps de l'article. Elle est **nécessaire** à la bonne mise en forme du site. Donc ne l'oubliez pas !

---

Le **corps** de l'article, quant à lui, est entièrement composé de texte au format Markdown. Lorsque le contenu impose une mise en forme locale complexe que Markdown n'est pas capable de décrire, vous pouvez directement injecter du code HTML pour préciser la structure votre mise en forme.


## Le préambule en détail

Les métadonnées définies dans le préambule correspondent à la liste des propriétés suivantes :

<div class="scrollable" markdown="1">

| propriété   | description                     | valeur        | requise                      | multi-valuée                 |
|:-----------:|:--------------------------------|:--------------|:----------------------------:|:----------------------------:|
| `title`     | le titre de l'article           | libre         | <i class="fas fa-check"></i> |                              |
| `subtitle`  | un sous-titre                   | libre         |                              |                              |
| `author`    | auteur de l'article             | normalisée    | <i class="fas fa-check"></i> | <i class="fas fa-check"></i> |
| `date`      | date de publication             | normalisée    | pour les guides              |                              |
| `icon`      | icône associée à l'article      | normalisée    |                              |                              |
| `type`      | typologie de l'article          | normalisée    |                              | <i class="fas fa-check"></i> |
| `platforms` | plateformes concernées          | normalisée    |                              | <i class="fas fa-check"></i> |
| `languages` | langages concernés              | normalisée    |                              | <i class="fas fa-check"></i> |
| `tags`      | mots-clés principaux            | libre         |                              | <i class="fas fa-check"></i> |
| `styled`    | feuille de styles personnalisés | true \| false |                              |                              |
{: .nowrap }

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
title: Comparatif de la Gamebuino META, de la PyGamer et de la 32blit
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

### Les icônes

Lorsqu'une liste d'articles est construite, comme sur la page d'accueil par exemple, chaque article est automatiquement affublé d'une icône. Vous pouvez définir l'icône qui sera associée à l'article par l'intermédiaire de la propriété `icon`. Les icônes actuellement disponibles sont les suivantes :

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

### Les styles personnalisés

Comme je vous l'ai mentionné au début de ce guide, j'ai prévu un mécanisme automatisé qui vous permet d'associer votre propre feuille de styles à un article. Cette fonctionnalité est à utiliser avec parcimonie pour garantir l'homogénéité visuelle du site. Mais cela peut s'avérer très utile lorsque vous avez besoin de définir une mise en forme complexe d'éléments, qui n'est pas prévue par défaut. Pour cela, il suffit d'ajouter :

```yaml
styled: true
```

dans le préambule de votre article pour indiquer au moteur de template qu'il doit prendre en compte votre feuille de styles CSS personnalisés. Je vous rappelle que le fichier de cette feuille de styles doit nécessairement se nommer `styles.scss` et se trouver dans l'arborescence suivante :

```
article-assets
`-- slugified-title
    `-- css
        `-- styles.scss
```

où `slugified-title` doit correspondre au titre *URL compliant* de votre article.


{% comment %}
--------------------------------------------------------------------------------
--                              nouvelle section                              --
--------------------------------------------------------------------------------
{% endcomment %}


# Astuces de mise en forme

Nous allons maintenant examiner quelques règles de mise en forme concernant la plupart des composants dont vous aurez besoin au cours de la rédaction de vos articles. Je pars du principe que vous maîtrisez le langage Markdown et ses règles syntaxiques. Je ne m'attarderai donc pas sur son usage standard. Vous pouvez toujours vous référer, par exemple, [au guide suivant][markdown] si nécessaire. Notez que Jekyll utilise par défaut un dialecte enrichi de Markdown automatiquement interprété par le moteur [Kramdown][kramdown].

Kramdown vous permet, entre autre, de préciser certains attributs des éléments HTML générés par Jekyll à partir de votre texte source. Nous allons en examiner quelques exemples.

**Les éléments de type `inline`**

```md
**Bleu**{: style="color:#28d" }
```

Permettra d'enrichir la mise en forme du mot **Bleu**{: style="color:#28d" } en générant le code HTML suivant :

```html
<strong style="color:#28d">Bleu</strong>
```

**Les éléments de type `block`**

```md
Un paragraphe bleu centré
{: .center style="color:#28d" }
```

Permettra d'afficher le paragraphe sous cette forme :

Un paragraphe bleu centré
{: .center style="color:#28d" }

Vous noterez le passage à la ligne pour spécifier que vous souhaitez appliquer l'enrichissement à l'ensemble du paragraphe. Le point qui préfixe `.center` indique que la propriété préfixée doit être considée comme une **classe** CSS. Et vous voyez également que l'on peut associer plusieurs propriétés à un même élément. Autrement dit, le code HTML résultant est le suivant :

```html
<p class="center" style="color:#28d">Un paragraphe bleu centré</p>
```

Bien entendu, il faut que cette classe soit définie dans la feuille de styles de l'article. Et c'est bien le cas ici, il existe en effet une classe CSS `center` qui vous permet de centrer facilement un élément. J'ai défini quelques *helpers* comme celui-là pour vous simplifier la vie. Je vous renvoie à la fin de ce guide pour en consulter la liste.


## Les icônes *fontawesome*

Vous pouvez utiliser [les icônes gratuites fontawesome][fontawesome]. Par exemple :

```md
<i class="fab fa-5x fa-github"></i>
{: .center .discrete .inlaid }
```

<i class="fab fa-5x fa-github"></i>
{: .center .discrete .inlaid }


## Les blocs de code

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

<span style="color:#a00">Rouge</span> permet également d'afficher un bloc de code avec la numérotation des lignes. Mais pour utiliser cette fonctionnalité, Markdown n'est pas suffisant. Il faudra donc introduire votre bloc de code en utilisant des directives [Liquid][liquid], qui est le moteur de template de Jekyll.

Par exemple, pour introduire un bloc de code Python avec numérotation automatique des lignes, on écrira :

```
{{ '{% highlight py linenos' }} %}

# le code...

{{ '{% endhighlight' }} %}
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

## Les tableaux

Par défaut, le tableau Markdown suivant :

```md
| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
```

sera mis en forme comme ceci par le template :

| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |

Mais vous pouvez utiliser quelques *helpers* pour en modifier le rendu.

**Inverser l'alternance des lignes grisées :**

```md
| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .even }
```

| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .even }

**Supprimer les bordures de lignes :**

```md
| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .noline }
```

| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .noline }

**Supprimer la coloration des lignes :**

```md
| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .nostrip }
```

| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .nostrip }

**Combiner les effets :**

```md
| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .nostrip .noline }
```

| type       | taille  | valeurs        |
|-----------:|:-------:|:---------------|
| `uint8_t`  | 8 bits  | 0 à 255        |
| `int8_t`   | 8 bits  | -127 à 128     |
| `uint16_t` | 16 bits | 0 à 65535      |
| `int16_t`  | 16 bits | -32767 à 32768 |
{: .nostrip .noline }

**Rendre le tableau responsive :**{: style="color:#a00" }

Les tableaux font partie des éléments HTML les plus chiants à gérer lorsqu'on se penche sur les aspects **responsive**. Et sur un smartphone, il y a de fortes chances pour que votre tableau ne rentre pas dans le cadre de la page... Aussi, pour ne pas déstructurer la mise en page, j'ai prévu un petit *helper* `scrollable` chargé d'encapsuler les éléments qui peuvent poser problème dans un contexte responsive, comme les tableaux. Il est **vivement recommandé** (pour ne pas dire **obligatoire**) d'utiliser cette précaution. Elle permet d'éviter un débordement en plaçant le tableau à l'intérieur d'un bloc à défilement horizontal. Un autre *helper* `nowrap` peut lui être associé pour empêcher la césure automatique impliquant des passage à la ligne dans un tableau.

```md
<div class="scrollable" markdown="1">

| type       | taille  | valeurs                  |
|-----------:|:-------:|:-------------------------|
| `uint8_t`  | 8 bits  | 0 à 255                  |
| `int8_t`   | 8 bits  | -127 à 128               |
| `uint16_t` | 16 bits | 0 à 65535                |
| `int16_t`  | 16 bits | -32767 à 32768           |
| `uint32_t` | 32 bits | 0 à 4294967296           |
| `int32_t`  | 32 bits | -2147483647 à 2147483648 |
{: .nowrap }

</div>
```

<div class="scrollable" markdown="1">

| type       | taille  | valeurs                  |
|-----------:|:-------:|:-------------------------|
| `uint8_t`  | 8 bits  | 0 à 255                  |
| `int8_t`   | 8 bits  | -127 à 128               |
| `uint16_t` | 16 bits | 0 à 65535                |
| `int16_t`  | 16 bits | -32767 à 32768           |
| `uint32_t` | 32 bits | 0 à 4294967296           |
| `int32_t`  | 32 bits | -2147483647 à 2147483648 |
{: .nowrap }

</div>


## Les encarts

Pour attirer l'attention du lecteur sur un aspect important, vous pouvez utilisez l'élément HTML `blockquote`, qui se traduit simplement en Markdown par l'usage du chevron : `>`

```md
> **Remarque très importante**
> 
> Pensez à ne pas trop en abuser pour ne pas risquer d'annuler l'effet attendu...
```

> **Remarque très importante**
> 
> Pensez à ne pas trop en abuser pour ne pas risquer d'annuler l'effet attendu...

## Les images

Pour intégrer des images à vos articles, rien de plus simple... Markdown dispose d'une directive spécifique pour cela. Par exemple :

```md
![La console PyGamer](https://cdn-shop.adafruit.com/1200x900/4242-00.jpg)
```

permettra d'intégrer l'image sous cette forme :

![La console PyGamer][adafruit-pygamer]

Le template redimensionnera automatiquement l'image pour qu'elle occupe au mieux l'espace disponible dans le corps de la page. Par ailleurs, une mise en forme est appliquée par défaut à l'image pour arrondir ses coins et lui ajouter une ombre portée.

Vous pouvez également définir des **références** dans votre document Markdown pour réduire les URLs de vos images ou de vos liens hypertextes dans le corps du document. Ces références sont en général rassemblées en fin de document. Il suffit de procéder comme suit :

```md
<!-- à placer à l'endroit où vous souhaitez intégrer l'image -->
![La console PyGamer][pygamer]

<!-- référence à placer en fin de document -->
[pygamer]: https://cdn-shop.adafruit.com/1200x900/4242-00.jpg
```

### Redimensionnement des images

Vous pouvez également contraindre le redimensionnement de l'image...

**Soit en utilisant les classes *helpers* CSS que j'ai prédéfinies :**

- la classe `w-50` spécifie une occupation de 50% de l'espace disponible en largeur,
- la classe `w-75` spécifie une occupation de 75% de l'espace disponible en largeur.

Par exemple :

```md
![La console PyGamer][pygamer]{: .w-50 }
```

![La console PyGamer][adafruit-pygamer]{: .w-50 }

**Soit en spécifiant directement les dimensions de l'image :**

Vous pouvez également contraindre la largeur et/ou la hauteur en pixels. Par exemple :

```md
![La console PyGamer][pygamer]{: width="300" }
```

![La console PyGamer][adafruit-pygamer]{: width="300" }

Attention toutefois à respecter le ratio original de l'image si vous spécifiez la largeur **et** la hauteur... Sinon vous risquez de déformer l'image :

```md
![La console PyGamer][pygamer]{: width="500" height="200" }
```

![La console PyGamer][adafruit-pygamer]{: width="500" height="200" }

> **Remarque**
> 
> Les contraintes de redimensionnement ne sont (volontairement) pas prises en compte sur les smartphones.

### Un peu de cosmétique

Pour modifier l'habillage par défaut de l'image, vous pouvez utiliser les classes *helpers* CSS suivantes :

- `sharp` supprime l'effet de coins arrondis
- `noshadow` supprime l'ombre portée

Par exemple :

```md
![La console PyGamer][pygamer]{: width="300" .sharp .noshadow }
```

![La console PyGamer][adafruit-pygamer]{: width="300" .sharp .noshadow }

Vous pouvez même appliquer des transformations géométriques à l'image :

```md
![La console PyGamer][pygamer]{: width="300" style="transform: rotate(-15deg);" }
```

![La console PyGamer][adafruit-pygamer]{: width="300" style="transform: rotate(-15deg);" }

Vous voyez que dans ce cas, la transformation est appliquée *in situ* sans affecter les autres composants environnants, ce qui peut entraîner des chevauchements non souhaitables. Dans ce cas, je vous conseille d'encapsuler l'image dans un wrapper HTML pour dégager des marges suffisantes autour de l'image :

```md
<!-- l'attribut markdown="1" permet d'indiquer que ce qui      -->
<!-- se trouve à l'intérieur du bloc HTML doit être interprété -->
<!-- normalement par le moteur Kramdown                        -->
<div markdown="1" style="margin:50px auto">
![La console PyGamer][pygamer]{: width="300" style="transform: rotate(-15deg);" }
</div>
```

<div markdown="1" style="margin:50px auto">
![La console PyGamer][adafruit-pygamer]{: width="300" style="transform: rotate(-15deg);" }
</div>

### Intégrer des images locales

Les exemples décrits jusqu'ici s'appuyaient sur une image empruntée sur un domaine externe, mais vous pouvez bien évidemment intégrer vos propres images dans vos articles ! Pour cela, souvenez-vous de la variable prédéfinie `myassets` dont je vous ai parlé au début de ce guide à la section **Structuration des contenus du site**. Vous devez avant tout placer vos images dans le répertoire adéquat. Par exemple, j'ai placé l'image `32blit.jpg` dans l'arborescence des ressources propres à ce guide :

```
article-assets
`-- authoring-guide
    `-- images
        `-- 32blit.jpg
```

Pour pouvoir accéder facilement à mon image, je dois préalablement charger la définition de la variable `myassets` dans le scope de mon article en plaçant la directive Liquid suivante au début de l'article, juste après le préambule :

```liquid
{{ '{% include myassets.html' }} %}
```

Après quoi je peux facilement intégrer mon image de cette façon :

```
![La console 32blit]({{ '{{ myassets'}} }}/images/32blit.jpg){: .w-50 }
```

![La console 32blit]({{ myassets }}/images/32blit.jpg){: .w-50 }


## Le lecteur vidéo HTML

*Pas encore intégré, mais ça va viendre...*
{: .discrete }

## Le lecteur vidéo de YouTube

Il n'existe pas de directive Markdown pour intégrer facilement des vidéos comme elles peuvent exister pour les images. J'ai donc prévu une petite macro dans le template, chargée d'intégrer pour vous les élements HTML nécessaires à l'affichage du lecteur vidéo de YouTube. Cette macro attend les propriétés suivantes :

- `id`, dont la valeur correspond à l'identifiant YouTube de la vidéo,
- `w`, dont la valeur peut être **50** ou **75** et permet d'appliquer la classe CSS `w-50` ou `w-75` sur le lecteur.

Si la propriété `w` n'est pas spécifiée, le lecteur vidéo occupera 100% de la largeur disponible.

```liquid
{{ '{% include youtube.html id="QfsUnN-C3vI" w=75' }} %}
```

{% include youtube.html id="QfsUnN-C3vI" w=75 %}

Vous pouvez également spécifier l'instant à partir duquel doit démarrer la vidéo en utilisant :

- la propriété `h` pour indiquer l'heure
- la propriété `m` pour indiquer la minute
- la propriété `s` pour indiquer la seconde

```liquid
{{ '{% include youtube.html id="AIL4qi5UIQE" w=75 m=4 s=59' }} %}
```

{% include youtube.html id="AIL4qi5UIQE" w=75 m=4 s=59 %}

Les mêmes règles d'habillage que pour les images peuvent s'appliquer également au lecteur vidéo de YouTube.


## Les consoles

Lorsque vous aurez besoin d'intégrer une démo qui tourne sur console dans vos articles, vous pourrez vous appuyer sur la macro `demo.html`, qu'il suffira d'inclure à l'emplacement où vous souhaitez intégrer la démo, en y injectant les paramètres adéquats.

### La Gamebuino META

Supposons que l'on souhaite afficher la démo du jeu de la vie qui est visible en page d'accueil. Voilà comment appliquer la macro `demo.html` :

```liquid
{{ '{% assign asset = site.baseurl | append: "/assets/images/demo-gamebuino-320x256.gif"' }} %}
{{ '{% include demo.html console="gamebuino" screen=asset' }} %}
```

Ici on est obligé de précalculer une variable `asset` qui va permettre de désigner le chemin d'accès à l'image que l'on souhaite afficher à l'écran, car Jekyll ne permet pas de passer une expression comme paramètre lors d'un `include`.

{% assign asset = site.baseurl | append: "/assets/images/demo-gamebuino-320x256.gif" %}
{% include demo.html console="gamebuino" screen=asset %}

Dans cet exemple on est allé chercher une image dans le répertoire des ressources globales de construction du site :

```
assets
`-- images
    `-- demo-gamebuino-320x256.gif
```

Mais vous pouvez tout à fait faire la même chose avec une ressource propre à votre article. Par exemple, si je souhaite afficher l'image suivante, qui est située dans le répertoire des ressources de mon article :

```
article-assets
`-- authoring-guide
    `-- css
        `-- images
            `-- sweet-valentine-320x256.gif
```

Il me suffit d'invoquer la macro `demo.html` de cette façon :

```liquid
{{ '{% assign asset = myassets | append: "/images/sweet-valentine-320x256.gif"' }} %}
{{ '{% include demo.html console="gamebuino" screen=asset' }} %}
```

{% assign asset = myassets | append: "/images/sweet-valentine-320x256.gif" %}
{% include demo.html console="gamebuino" screen=asset %}

### La PyGamer

Pour la PyGamer, c'est pareil, à la différence près qu'il faut spécifier `console="pygamer"` :

```liquid
{{ '{% assign asset = site.baseurl | append: "/assets/images/demo-pygamer-320x256.gif"' }} %}
{{ '{% include demo.html console="pygamer" screen=asset' }} %}
```

{% assign asset = site.baseurl | append: "/assets/images/demo-pygamer-320x256.gif" %}
{% include demo.html console="pygamer" screen=asset %}

> **Remarque**
> 
> Les images de démo pour la Gamebuino et la PyGamer doivent respecter le ratio des dimensions de leur écran, qui mesure **160x128** px. Les images que j'utilise ici mesurent **320x256** px. Elles respectent donc le ratio imposé, et j'ai volontairement intégré des images à une échelle **2:1** de manière à augmenter la densité de points et obtenir un meilleur rendu, avec plus de finesse, dans le navigateur. Aussi, je vous encourage à appliquer la même règle dans vos articles  <i class="far fa-smile-wink"></i>

## Les helper-classes

`.discrete`

Vous permet de diminuer le contraste d'un texte pour le rendre plus discret.
{: .discrete}

`.inlaid`

Vous permet de donner un effet très léger d'incrustation à un élément HTML.
{: .inlaid }

`.center`

Vous permet de centrer l'élément HTML.
{: .center }

`.w-50`

Vous permet de contraindre l'élément HTML à n'occuper que 50% de la largeur disponible.

`.w-75`

Vous permet de contraindre l'élément HTML à n'occuper que 75% de la largeur disponible.

`.sharp`

Vous permet de supprimer l'effet de coins arrondis sur les éléments multimedia.

`.noshadow`

Vous permet de supprimer l'effet d'ombre portée sur les éléments multimedia.

`.nowrap`

Vous permet de forcer un tableau à ne pas appliquer de césure automatique de passage à la ligne.

`.scrollable`

Vous permet de prévenir un risque de débordement et d'encapsuler l'élément HTML qui pose problème à l'intérieur d'un bloc à défilement horizontal. Très utile dans un contexte **responsive**.

> N'hésitez pas à me solliciter pour intégrer de nouveaux *helpers*  
> concernant des mises en forme fréquemment utilisées
{: .center }

{% comment %}
--------------------------------------------------------------------------------
--                            liste des références                            --
--------------------------------------------------------------------------------
{% endcomment %}

[adafruit-pygamer]: https://cdn-shop.adafruit.com/1200x900/4242-00.jpg
[fontawesome]:      https://fontawesome.com/icons
[kramdown]:         https://kramdown.gettalong.org/quickref.html
[liquid]:           https://shopify.github.io/liquid/
[markdown]:         https://www.markdownguide.org/
[sass]:             https://sass-lang.com/