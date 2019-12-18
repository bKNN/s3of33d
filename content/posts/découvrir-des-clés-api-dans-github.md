+++
categories = []
date = 2019-12-18T21:51:00Z
description = ""
location = "Bordeaux, FR"
slug = "seo-determination-pages-utiles-inutiles"
tags = []
title = "Déterminez vos pages utiles et inutiles au SEO à l'aide de la dataviz"
type = "post"

+++
Dans ce billet, nous allons voir ensemble comment déterminer facilement et rapidement le ratio de pages  utiles / inutiles lors d'un crawl. Nous allons en profiter pour faire une courte introduction sur la data visualisation, et son intérêt déjà évident dans le monde du SEO.

L'identification des pages utiles et inutiles peut se faire à partir de différentes sources :

* Logs
* Crawl
* Sitemaps
* Données Search Console
* Données Analytics

Et c'est en croisant ces ensemble de données que nous pouvons observer des défauts évidant ou non en fonction des sites observées.

Quelques pré-requis sont obligatoire :

* [Sitebulb](https://sitebulb.com/) ou n'importe quel crawler capable d'identifier et segmenter la source de vos URLs (trouvées dans GA ? GSC ? Au crawl ? dans le sitemap ?)
* Un accès Search Console / Analytics pour câbler le crawler
* [Anaconda](https://www.anaconda.com/distribution/#download-section) avec JupyterLab
* Le package [mattplotlib-venn](https://anaconda.org/conda-forge/matplotlib-venn) pour faire de beau diagramme de Venn

## Exporter et trier les données Sitebulb

Attention à ne pas oublier de câbler Analytics et la Search Console lors du crawl. On demande aussi l'exploration des sitemaps.

Une fois le crawl terminé, allez dans URL Explorer et ajoutez les colonnes suivantes :

![](/uploads/sitebulb-data-explorer.JPG)

Ensuite, filtrez uniquement vos URLs interne et accessible (Status code 200)

Une fois le tableau mis à jour, exportez vos données.

Avec la limite d'export d'URL de GSC en règle générale je fusionne la colonne "Found in Google Analytics" avec "Found in Google Search Analytics".

Mon tableau prêt à être travaillé, je me retrouve donc avec 3 colonnes :

![](/uploads/excel.JPG)

Place maintenant au jus de cerveau, l'objectif est maintenant de trier correctement l'ensemble des URL afin d'arriver à récupérer 7 valeurs clés :

* **URLs absentes des sitemaps et inactives** : accessible au crawl mais absente des sitemaps et non visible sur GA et GSC
* **URLs  absentes des sitemaps et actives** : accessible au crawl, présent dans GSC ou GA et absente des sitemaps
* **URLs trouvées dans les sitemaps et inactives** : absente du crawl, non visible sur GA et GSC mais trouvé dans les sitemaps
* **URLs trouvées dans les sitemaps et actives** : absente du crawl, visible sur GA ou GSC et trouvé dans les sitemaps
* **URLS inactives** : accessible au crawl et trouvé dans les sitemaps mais non visible sur GA et GSC
* **URLs totalement orphelines et inactives** : visible uniquement sur GA ou GSC
* **URLs OK** : visible GA ou GSC, accessible au crawl et présent dans les sitemaps.

A vous de trouver la technique la plus simple afin d'arriver à ce tableau final :

![](/uploads/excel-2.JPG)

## Oh Python mon beau Python !

Il vous reste plus qu'à ouvrir JupyterLab et insérer le code suivant :

    from matplotlib import pyplot as plt
    import numpy as np
    from matplotlib_venn import venn3, venn3_circles
    plt.figure(figsize=(12,12)) # modifier la taille de l'image
    plt.title("Pages Actives et Inactives") # modifier le title
    v = venn3(subsets=(251, 8, 49, 1,226,3,634), set_labels = ('URL trouvées au crawl', 'URL trouvées dans les sitemaps', 'URL trouvées dans GA + GSC')) # insérez vos données - attention de bien respecter la structure
    c=venn3_circles(subsets = (251, 8, 49, 1,226,3,634), linestyle='dashed', linewidth=1, color="grey") # petit bonus visuel
    plt.show()

Pensez bien sur à insérer vos données d'URLs en prenant soin de respecter la structure.

Puis... RUN!

![](/uploads/dataviz-seo-pages-actives.png)

Et vous voilà avec un jolie graphique tout frais.

D'autres exemples :

![](/uploads/dataviz-seo-pages-actives-2.png)

![](/uploads/dataviz-seo-pages-actives-3.png)

La librairie matplotlib permet une personnalisation relativement complète, n'hésitez pas à explorer !

Quelques autres graphiques sont disponible sur mon Gists : [https://gist.github.com/bKNN](https://gist.github.com/bKNN "https://gist.github.com/bKNN")

Toujours preneur de vos retours sur [Twitter](https://twitter.com/bKN____) !

_XOXO!_

_624b4e_