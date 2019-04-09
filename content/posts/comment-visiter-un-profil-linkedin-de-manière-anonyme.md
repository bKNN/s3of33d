+++
categories = []
date = "2019-04-05T22:00:00+00:00"
description = ""
draft = true
location = "Bordeaux, FR"
slug = ""
tags = []
title = "Boostez vos avis Local Businesses avec aggregateRating de schema.org"
type = "post"

+++
Les rich snippets sont toujours complexe à mettre en place. En particulier pour les entreprises locales, où les informations manque encore de clarté.

On se retrouve vite perdu sur... qu'elles règles utiliser, comment les déclencher et comment les mettre en oeuvre.

![](/uploads/Capture.PNG)

Schema.org, et l'interprétation par Google de ces microdonnées ne cessent d'évoluer continuellement, et complexifie la tâche pour nous SEO.

Au début, il était bien entendu possible de mettre sur tous nos sites 5 étoiles en ajoutant simplement le balisage aggregateRating et d'en abuser à outrance. 

Google c'est depuis réveillé, et cette approche se retrouve de moins en moins recommandé car très proche du contenu spammy que Google peut potentiellement pénaliser du jour au lendemain.

## Des règles à suivre :

* Ne jamais mettre de aggregateRating sur la page d'accueil (risque d'envoyer un fort signal de spam auprès de Google).
* aggregateRating doit représenter des avis réels, visible depuis le site.
* Si la page n'affiche pas d'avis, alors n'y intégrez pas le schema aggregateRating. Dans tous les cas, la page doit avoir une notation ainsi que les avis clairement identifiable ou un lien vers la page où les avis sont visible.
* Les avis doivent provenir de votre site (on ne prends pas les avis Google, Yelp, Tripadvisor...)

Dernier point, valable pour toutes les pages, pour qu'une page déclenche des étoiles dans les SERP, elle doit avoir une certaine autorité

Ces règles sont basé et interprété depuis les Google [Guidelines for review snippets](https://developers.google.com/search/docs/data-types/review-snippet#review-snippet-guidelines)

## Comment maximiser les chances ?

En gardant à l'esprit les paramètres ci-dessus, il existe plusieurs façons d'appliquer des avis sur votre site tout en maximisant les chances d'obtenir les étoiles dans les SERPs

# Comment afficher les profils LinkedIn sans compte ?

1. Recherchez l'URL du profil de la personne à l'aide de Google, et Copiez la.

![](/uploads/joeveix.PNG)

_Si vous connaissez pas encore Joe Veix..._ [_Cliquez ICI_](https://theoutline.com/post/5495/how-to-beat-linked-in-the-game)

1. Ouvrir le [test d'optimisation mobile de Google](https://search.google.com/test/mobile-friendly "test d'optimisation mobile de Google") - c'est toujours notre meilleur pote ! Puis collez l'URL

![](/uploads/test_opti_mobile.PNG)

1. Ouvrez l'onglet HTML et copiez le code.

![](/uploads/copy.png)

1. Collez le code dans une visionneuse HTML en ligne tel que [codepen.io](https://codepen.io/pen/ "codepen.io")

![](/uploads/linkedin_profile.PNG)

**TADAAAAAAAAAAAAAM !**

Vous n'êtes maintenant plus limité pour la consultation des profils en anonyme.

Cette méthode est bien entendu adaptable à d'autres sites proposant le même système de blocage de contenu que Linkedin.

Google prêtent que le rendu affiché par le mobile test est crawler par le Googlebot utilisé pour le ranking. Ainsi tout contenu qui se doit d'être accessible aux robots pour l'indexation nous est dorénavant potentiellement accessible aussi.

_624b4e_