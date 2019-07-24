+++
categories = []
date = "2019-07-23T22:00:00+00:00"
description = ""
location = "Bordeaux, FR"
slug = "merci-github-pour-les-cles"
tags = []
title = "Découvrir des clés API dans GitHub"
type = "post"

+++
On sait depuis quelques temps que les hackers se servent d'une multitude de combinaison afin de trouver des clés API, normalement secrètes et privés, de manière gratuite, et facile sur le web (les search tricks Google, pastebin, github...). Et ces "failles" peuvent parfois causer de [graves dommages](http://vertis.io/2013/12/16/unauthorised-litecoin-mining.html). Mais toujours en 2019, personne ne s'en inquiète réellement.

Sur Github, il est toujours possible de trouver des milliers de clés API de divers services, exposées publiquement. Les développeurs, manquant souvent de notions de cyber-sécurité et prenant rarement le temps d'auditer le code. Ils ne réalisent pas forcément à quel point il est facile de les découvrir.

Mais comment les hackers s'y prennent t-ils ?

## Les mots apparentés : une aide pour trouver les clés API

Github possède une fonction de recherche. Et le moyen le plus simplet et le plus rapide afin de trouver une clés API consiste à l'utiliser.

L'astuce consiste à penser à une chaîne qui se trouve généralement près de la chaîne de la clé API elle-même.

Afin d'éviter de risquer de compromettre tout projet récent, aucune astuce clé en main vous sera dévoiler pour des tools moderne. Place à votre réflexion...

Mais prenons un exemple outdated :

Prenons une [Class PHP](https://github.com/tpyo/amazon-s3-php-class) pour accéder à AWS S3.

On peut supposer que bon nombre de développeurs qui utilisent cette classe ne pensent pas forcément à changer le nom de la variable qui contient la clé secrète API de celle utilisé dans l'exemple du Git.

Bingo, une recherche sur "**$awsAccessKey**" nous donne plus de 50 000 résultats...

![](/uploads/awsaccesskey.JPG)

Juteux et facile n'est ce pas ?

En réalité, même une recherche simplement sur "**aws secret**", donne des résultats déjà intéressants.

Bien entendu AWS n'est pas le seul service pour lequel il est facile de rechercher une clés secrète.

En soit, n'importe quel service proposant une API est exploitable.

Il suffit d'identifier le service, et réfléchir aux mots qui peuvent accompagner la clé API.

Un autre petit exemple avec Stripe :

![](/uploads/Stripe.jpg)

Plus simplement, vous pouvez également rechercher le terme : "**api key extension:php**" pour des idées de services avec des API potentiellement exposées.

**Mais de loin, les clés les plus faciles à trouver sont celles qui contiennent un mot, ou une suite logique, particulier dans la clé**. Ce n'est pas une blague... de nombreux services très respectés commettent erreur.

Par exemple, Mailchimp à longtemps utilisé la chaîne : "usX", X étant un nombre compris entre 1 et 11.

Github reconnait USX comme un mot, ce qui permet de rechercher US1 jusqu'à US11 et obtenir toutes les clés API de Mailchimp sur Github !

Ce qui fait peur ? Ces clés API donnent un accès complet au compte Mailchimp, y compris à toutes les listes de courrier électronique, et la possibilité de leur envoyer des courriels de Mailchimp, qui proviennent du propriétaire du compte et sont du coups... payés par celui-ci.

## Les REGEX : la recherche bodybuildé si t'es énervé !

L'autre méthode de recherche de clés consiste à explorer Github et à rechercher des modèles à l'aide de RegEx.

Par exemple, pour recherche des clés AWS, vous pouvez rechercher des chaînes d'une longueur de 20 caractères, toutes majuscules et alphanumériques, et commençant par AK.

C'est beaucoup plus facile que de pirater différentes implémentations et langues d'API.

Seul hic, GitHub limite son API, la meilleure méthode consiste donc à utiliser l'API uniquement afin d'obtenir une list ede référentiels, puis téléchargez les master.zip ou analysez les fichiers à l'aide d'un simple HTTP GET.

## Petite conclusion

J'ai décidé de rédiger cet article maintenant que GitHub propose gratuitement de passer son dépôt en privé, et ce de manière illimité. Cet technique risque donc d'être de plus en plus obsolète.

Il y a un vrai problème de formation et d'incompétence pour que des développeurs soumettent toujours des clés secrètes à des référentiels publics, c'est un béaba qui devrait être un réflexe pour tous.

TOUTEFOIS, pour toutes les sociétés qui conçoit et implémente ces API, là aussi, une forte réflexion pourrait être mener afin d'éviter ce risque potientiel :

1 - Jamais, JAMAIS, une chaîne spécifique ne se répète dans toutes les clés (Coucou Mailchimp!). Et surtout, ne faites pas de cette chaîne un mot qui peut être recherché sans expression régulière.

![](/uploads/hello-mailchimp.gif)

Le mieux serait de faire varier la longueur de l'API de manière variable et d'envisager pourquoi pas l'utilisation de caractères spéciaux afin de rendre plus difficile encore la recherche par expressions rationnelles.

2 - Obligez vos utilisateurs à ne pas utiliser le moyen facile de stocker la clé secrète juste avant l'appel de l'API, ni même de la stocker dans des fichiers de projet.

Par exemple, le SDK AWS propose quelques bonnes idées:

* stocker dans des variables
* des fichiers INI sur le home directory

J'espère que cet article vous responsabilisera et vous aidera à éviter ces risques de sécurité à l'avenir.

Pour les autres... attention à l'utilisation que vous en faites ! 

_XOXO!_

_624b4e_