+++
categories = []
date = "2019-04-16T22:00:00+00:00"
description = ""
location = "Bordeaux, FR"
slug = "blackhat-seo-google-evenements"
tags = []
title = "100% Blackhat SEO - Spammons les événements Google"
type = "post"

+++
Dans cet article nous allons parler d'une technique permettant de faire apparaître sans aucune autorité une page web sur un terme de recherche.

La faille consiste à détourner les microdata LocalBusiness. Et on peut s'amuser qu'importe la marque et son volume de recherche !

Un petit exemple réalisé pour la publication de ce post (désolé ECV Digital Bordeaux 😟) :

![](/uploads/Capture-4.PNG)

Petit zoom ?

![](/uploads/Capture2.PNG)

Et si on clique sur l’événement ?

![](/uploads/Capture3.PNG)

_On rank 1er sur : "google, t'es quand même plutôt sympa !, 14 juillet", dinguerie !_

Et bien sur, si on clique de nouveau sur le lien, on arrive vers un site merveilleux... 

La technique est vraiment toute simple... Seulement, il est difficile pour Google aujourd'hui d'éviter cette forme de spam puisque des sites éthiques s'en servent pour de vrais événements.

## Comment faire ?

Il suffit de créer une page orpheline. On se fou totalement de la qualité, une seule condition : la page doit contenir un balisage schema.org d’événement valide et l'évènement doit bien sur avoir lieu chez la marque que nous visons.

Voici un exemple :

![](/uploads/microdata.PNG)

On soumet ensuite l'URL à Google depuis la Search Console, et il nous reste plus qu'à attendre le passage du robot.

It's done!

_624b4e_