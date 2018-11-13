+++
categories = ["", "V"]
date = "2011-03-23"
description = "dfadsfasdf"
location = "Santa Fe, NM"
slug = "dfa,mdn,fnmansd,"
tags = ["xxx", "yyy", "ssss", "vvvvv"]
title = "Doublez vos performances... Grâce à la rotation des Gifs !"
type = "post"

+++
### **Introduction**

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