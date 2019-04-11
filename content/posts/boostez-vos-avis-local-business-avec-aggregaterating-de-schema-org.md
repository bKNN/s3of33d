+++
categories = []
date = "2019-04-10T22:00:00+00:00"
description = ""
location = "Bordeaux, FR"
slug = "bypass-search-console"
tags = []
title = "Bypass la Search Cosole avec des URLs externes"
type = "post"

+++
La nouvelle version de la Search Console et l'outils d'inspection d'URL est très utile pour diagnostiquer des problèmes lié au rendu de GoogleBot (coucou les blocages robots.txt) :

![](/uploads/inspectionURL.PNG)

Une autre point cool est qu'il inclut le résultat après l'exécution du JS.

Malheureusement, si pas d'accès à la Search Console... pas d'inspection d'URL possible :

![](/uploads/nope.PNG)

Mais il existe une astuce...

> Les redirections entre domaines !

![](/uploads/god.jpeg)

Par exemple, pourquoi pas analyser la homepage de la Corée du Nord, afin de les aider à quelques reco SEO : 

![](/uploads/north-korea.PNG)

Nous sommes sur le compte Search Console _test.pierrick.dev_ , accédant volontairement au compte de la Search Console de : [http://www.korea-dpr.com/](http://www.korea-dpr.com/ "http://www.korea-dpr.com/")

## Méthode

C'est simple :

* Avoir un compte Search Console pour un site web que vous contrôlez.
* Configurez une redirection vers l'URL souhaitée sur une propriété que vous ne contrôlez pas.
* Inspectez l'URL redirigée dans la Search Console.
* Tester l'URL en direct.

That's it.

A savoir, l'inspecteur d'URL utilise l'agent qui indexe votre site web... dans la plupart des cas il s'agit aujourd'hui de Googlebot Mobile: Smartphone.

## Comment voir plus qu'un aperçu

Le code source fournie peut être copiée et collée (contrairement à certains autres outils de Google). Ainsi, même si l'aperçu ne fournit qu'une image limitée au-dessus de la copie, vous pouvez toujours l'utiliser. Pour faire ça :

* Copiez le code HTML de la page testée.
* Inspectez l'élément dans Chrome.
* Modifiez en tant que HTML.
* Ecrasez en collant le rendu GoogleBot.
* Appuyez sur Entrée pour afficher la page web rendue complète.

![](/uploads/Inspecteur.PNG)

Pour aller plus loin, je suggère d'utiliser Chrome 41 afin d'avoir le rendu visuel le plus proche de ce qu'un robot est capable d'afficher actuellement.

Voici un lien pour télécharger gratuitement la version de chrome41 : [https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win/310958/](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win/310958/ "https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win/310958/")

## Limites

Si la destination est bloquée dans le fichier robots.txt, cela ne fonctionnera pas. Il y a potentiellement d'autres restrictions mais je n'ai pas encore eu de cas concret.

Point positif, il n'y a actuellement aucune limite de fréquence sur les interrogations d'URL... concrètement, cela peut donc être automatisé.

Plus rigolo encore.... **Nous pouvons l'utiliser pour soumettre du contenu d'autres personnes à l'indexation.**

![](/uploads/Indexation.PNG)

> La boite de Pandore

![](/uploads/fight.PNG)

## Autres idées d'utilisation...

Cette technique est potentiellement utiles pour les devis avant audit, car elle peut vous donner des informations auxquelles vous ne devriez pas encore avoir accès (par exemple en regardant l'agent Google, on peut voir si le site est passé ou pas encore en indexation Mobile First).

C'est un excellent moyen de voir rapidement si des problèmes de ressources sont bloqués et de commencer à auditer en attendant d'avoir les accès complet à la Search Console.

Et d'autres détournement sont encore possible grâce à cette technique... Rappelez vous que vous utilisez par conséquent l'adresse IP authentique Google, donc vous aurez accès au même contenu que les robots Google, sans filtrage, quelques idées : 

* Contournement des paywalls (hello les sites d'actu)
* Vérifier sur un concurrent fait du cloacking
* Vérifier si notre cloack fonctionne correctement

Et je suis persuadé que vous trouverez d'autres idées sur la façon de l'utiliser... profitez tant que rien n'est bloqué !

Stay Safe.