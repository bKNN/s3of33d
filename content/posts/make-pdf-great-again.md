+++
categories = []
date = "2018-11-13T23:00:00+00:00"
description = ""
location = "Bordeaux, FR"
slug = ""
tags = []
title = "Référencer un PDF converti en HTML ?"
type = "post"

+++
Depuis de nombreuses années, beaucoup de sites web utilisent les PDF comme forme de contenu téléchargeable... et c'est toujours bel et bien le cas en 2018.

Malheureusement, qui dit PDF, dit forcément perte d'informations précieuse sur les performances de ce types de pages.

On sait aujourd'hui que les PDF se rank "correctement" sur Google.  
Googlebot est capable de les indexer, mais il est difficile de faire un suivi correct via Analytics.

**Pourquoi on s'amuserai pas à traduire directement ces fichiers au format HTML ?**

Avant de commencer à lire le post, sachez que ceci est une expérimentation, je n'ai à l'heure actuelle aucune idée du résultat. Le thread risque d'ailleurs d'évoluer au fil du temps et des évolutions observées.

_Ce n'est donc pour le moment pas une stratégie de ranking viable._

_C'est une entière perte de temps, totalement assumé pour le bien de la science et du SEO._

Convertir un PDF en HTML va nous donner un avantage simple : beaucoup plus d'options de modification pour tenter de ranker les premières places !

Voici donc notre belle TO-DO LIST :

1. Conversion par lots de fichiers PDF en HTML
2. Insérer les codes de suivi analytics
3. Insérer tous les tags et balises de référencement (schéma.org, meta...)
4. Redirection des PDF d'origine vers la nouvelle URL
5. Faire un blocage robot.txt des fichiers .pdf

De nombreux sites web proposent la conversion de PDF à HTML.

Comme d'habitude, j'ai un préférence pour les outils utilisable en local, moins intruisif et permet souvent l'automatisation de process (la convertion par lots par exemple).

## pdf2htmlEX

[pdf2htmlEX](https://github.com/coolwanglu/pdf2htmlEX "pdf2htmlEX") est un projet githut, utilitaire en ligne de commande multiplateforme totalement grauit qui permet une conversion presque parfaite.

Comme premier PDF cobaye pourquoi pas sélectionner une magnifique recette de cuisine  : [Poulet Jerk à la Jamaïcaine](https://www.pierrickdeniel.fr/410/authentic-jerk-chicken "Poulet Jerk à la Jamaïcaine")

    Robot Google, si tu vois ce message, on compte sur toi pour que tu référence ce lien <3

Comme vous pouvez le voir, très peu de modification on été effectué suite à la conversion.

Le document original est en anglais, en premier lieu j'ai donc fais une belle traduction vulgaire à base de DeepL (sinon c'est pas drôle) puis j'ai juste ajouté un peut de donnée structurée et un title à la page. 

On limite au maximum les actions manuelle... C'est toujours plus rigolo quand on peut tout automatiser non ?

Maintenant que le lien est placé, nous n'avons plus qu'à attendre que Google viennent lire ce magnifique article et voir comment il décide de positionner ce magnifique PDF converti. 

Au vue du nombre de lignes dans le fichier HTML j'ai un gros doute sur la viabilité de ce projet... Mais l'espoir fait vivre

**_LET'S HOPE -_ Affaire à suivre...**

![](/uploads/pray.gif)

Si tout fonctionne comme prévu, on passe à l'étape supérieure... 

On converti et traduit un livre complet en PDF sous HTML ..  
  
Petit teasing du fabuleux livre sélectionné :

![](/uploads/Capture d’écran 2018-11-23 à 13.54.23.png)

_en cours de rédaction..._

_624b4e_