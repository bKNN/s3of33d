+++
categories = []
date = "2018-11-13T23:00:00+00:00"
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

## MAIS DIS JAMY, POURQUOI EST-CE LE CAS ?

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

![](/uploads/comparatif-gif.jpg)

Le dossier original pèse **12,7 Mo** et une fois toutes les images renversées à 90°, la taille totale à augmenté à **13,1 Mo**.

Sur du volume, le gain est finalement discutable, Buzzfeed ou Giphy n'y verrais aucune économie.... et pas forcément de gain d'argent.

MAIS, les GIFs c'est rigolo, nous allons donc pousser le vice jusqu'au bout !

![](/uploads/super-webperf.gif)

## Yaaaaaalllaaaaaaah!

Voici une méthodo que nous pourrions appliquer dès qu'on parle de gros volume :

1. Conversion en lots des GIFs (rotation à 90°)
2. Vérifier la taille
3. Télécharger le plus petit de chaque paire
4. Manipuler le CSS

Pour pivoter des GIFs à la volée, rien de mieux que les bonnes vieilles lignes de commandes [imagemagick](https://www.imagemagick.org/script/index.php "imagemagick") ou [gifsicle](http://www.lcdf.org/gifsicle/ "gifsicle") peuvent être de très bon alliés.

Exemple de ligne de commande avec imagemagick :

    convert exemple.gif  -rotate  90  exemple_90deg.gif

Le but étant de travailler avec le fichier le plus petit des deux...

Puis d'intégrer dans le CSS un règle spécifique.

Dans notre cas, si l'attribut src d'une balise <img> se termine par **_90deg.gif**, alors dans ce cas nous voudrons le faire revenir dans le sens normal via le CSS grâce à la règle suivante :

    [src $ = "_ 90deg.gif"] { 
    }
        -webkit-transform: rotate(270deg);
        -moz-transform: rotate(270deg);
        -o-transform: rotate(270deg);
        -ms-transform: rotate(270deg);
        transform: rotate(270deg);

Reste plus qu'à s'assurer que le code HTML pointe correctement vers les versions pivotées... **ET C'EST GAGNÉ !**

![](/uploads/win.gif)

## Sérieusement?

C'est toujours cool d'économiser des octets sur le téléchargement, mais pensez aussi que chaque action CSS applique un temps de chargement supplémentaire sur le rendu.

En soit, chaque site est différent, et cette méthode reste trop fastidieuse pour qu'elle devienne W3C Friendly :'(

La suite s'agirait donc de tester si la transformations 2D via CSS utilisent beaucoup (ou non) de ressource côté serveur. Je ne le pense pas, et dans ce cas, le compromis est donc probablement viable.

Si votre site Web possède donc de beau gradient en GIF (ce qui je suppose n'est pas le cas.... triste vie), alors je vous recommande fortement d'adopter cette fabuleuse méthode pour changer le web de demain !

![](/uploads/donald-Make-Web-Development-Great-Again-crowd.png)

Si l'article vous à plus ou vous à fait sourire, n'hésitez pas à le partager (même à ta grand-mère) et gardons espoir mes frères, **un jour la rotation de GIFS sera reconnue comme Qualité web chez OPQUAST !**

_624b4e_