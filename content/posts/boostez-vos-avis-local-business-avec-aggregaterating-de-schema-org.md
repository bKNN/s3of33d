+++
categories = []
date = "2019-04-05T22:00:00+00:00"
description = ""
draft = true
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