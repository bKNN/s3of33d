+++
categories = []
date = "2018-11-12T23:00:00+00:00"
description = ""
location = "Bordeaux, FR"
slug = ""
tags = []
title = "Doublez vos performances... Grâce à la rotation des Gifs !"
type = "post"

+++
Nous sommes tous fans des gifs (et si ce n'est pas le cas, [CLIQUE ICI](https://www.baidu.com/)).

Les GIFs c'est toujours drôle, même quand on commence à les analyser...

Jetez un coups d’œil à ces deux beaux gradient au format GIF :

![](/uploads/gradient-hor.gif)

![](/uploads/gradient-hor.gif)

Ces deux images sont à 100% identiques, une simple rotation à 90° à été effectué... et pourtant :

* Le gradient vertical pèse **281 Ko**
* Le gradient horizontal pèse **28 Ko**

![](/uploads/jamy.jpg "MAIS DIS JAMY")

**MAIS DIS JAMY, POURQUOI EST-CE LE CAS ?**

    > Les fichiers GIF suivent un algorithme de compression qui supprime la redondance horizontale.

[Designing for Performance](http://designingforperformance.com/optimizing-images/#gif)

Ainsi, chaque GIF à une taille radicalement différentes, car son format offre une compression nettement meilleure dans un sens.

Après cette fabuleuse découverte, pourquoi ne pas s'amuser à penser performance web avec un pro-tips sorti tout droit du futur. 

**MERCI LE CSS <3**

    <img src = "horizontal.gif" style = "transformation: rotate (90deg);" />

Et hop, il est possible de réduire la taille de la page en enregistrant une copie d'un fichier GIF pivoté à 90° puis le refaire pivoter grâce au CSS à son état d'origine.

**GAIN INCROYABLE DE PLUS DE 90% D’ÉCONOMIE !**

![](/uploads/magic.gif)

## Mais qu'en est-il réellement ?

Un PUG qui bronze à l'endroit pèse **4,82 Mo** :

![](/uploads/pug_hor.gif)

Avec une rotation à 90 degrès, ce même GIF pèse : **4,84 Mo** :**![](/uploads/pug-ver.gif)**

Cette fois-ci, le gain est bien moins frappant que lors du premier test. 

**MAIS.... gain toutefois il y a !**

Malheureusement, cette technique du fond des tiroirs est à double tranchants. Après des années de recherche (wallah, je le jure) et de test de divers GIFs. Elle possède une faiblesse...

C'est une épée à double tranchant... 

Par conséquent, comme au réveil, il ne faut jamais se précipiter pour tout faire pivoter.

![](/uploads/ocean_hor.gif)

![](/uploads/ocean_ver.gif)

La rotation de ce fabuleux océan passe de **860 Ko** à **950 Ko**.

La rotation n'est pas donc toujours une bonne idée.

Pour approfondir cette découverte, nous allons récupérer tous les GIFS présent [d'une page](https://www.tumblr.com/search/l%27amour%20est%20dans%20le%20pr%C3%A9%20gif "d'une page") choisi au plus grand des hasards, et faire pivoter chaque GIF.

à suivre...