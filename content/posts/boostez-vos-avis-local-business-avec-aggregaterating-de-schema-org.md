+++
categories = []
date = "2019-04-05T22:00:00+00:00"
description = ""
draft = true
location = "Bordeaux, FR"
slug = "localbusiness-et-agregaterating-microdata"
tags = []
title = "Boostez vos avis Local Business avec aggregateRating de schema.org"
type = "post"

+++
Les rich snippets sont toujours complexe à mettre en place. En particulier pour les entreprises locales, où les informations manque encore de clarté.

On se retrouve vite perdu sur... qu'elles règles utiliser, comment les déclencher et comment les mettre en oeuvre.

![](/uploads/Capture.PNG)

Schema.org, et l'interprétation par Google de ces microdonnées ne cessent d'évoluer continuellement, et complexifie la tâche pour nous SEO.

Au début, il était bien entendu possible de mettre sur tous nos sites 5 étoiles en ajoutant simplement le balisage aggregateRating et d'en abuser à outrance.

![](/uploads/838dfaa1646cf245524e81363282385da77df40da1a0f503ac26687be6662047.jpg)

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

### Option 1 : Utiliser un site de notation

Il existent aujourd'hui des sites qui permettent de gérer l'intégralité des avis pour vous, nous pouvons citer par exemple TrustPilot.

Ces systèmes facilitent la mise en oeuvre en permettant d'ajouter simplement un widget ou un extrait de code à votre site web.

Toutefois, ils ne sont pas gratuit et nécessitent de l'engagement pour la mise en oeuvre et l'utilisation. Ce qui dans notre cas n'est pas forcément nécessaire lorsque l'on souhaite uniquement obtenir des étoiles dans les SERP pour notre local businesses.

### Option 2 : On se construit son propre système de notation

Avec de la motivation, on se rends compte qu'il est assez simple de construire un système de notation de base pour son site web en respectant l'essentiel des directives de Google.

Dans notre cas, nous allons illustrer une mise en en place sur le CMS Wordpress, mais bien entendu cette mise en oeuvre peut être adapté à d'autres cas, l'idée générale s'applique à n'importe quel CMS, avec un moyen simplet et gratuit de le faire.

#### Etape 1

Créer une page témoignages, avis sur votre site web et complétez là par des commentaires de clients.

Ces commentaires peuvent être fictif, en statique, aucun soucis là dessus.

Pour intégrer rapidement des étoiles depuis Wordpress voici un plugin vraiment pratique : [Universal Star Rating](https://en-ca.wordpress.org/plugins/universal-star-rating/).

Faites bien attention lors du choix d'autres plugins. Beaucoup d'entre eux injectent directement leurs propre schéma dans le site de manière rarement optimisées.

#### Etape 2

Attribuez une notation à partir du [review schema.org](http://schema.org/Review). Tout comme Google, je recommande d'utiliser le JSON LD, et c'est donc ce que nous allons utiliser :

    {
      " @type " :  " Review " ,
      " auteur " :  " [X] " ,
      " datePublished " :  " [X] " ,
      " reviewBody " :  " [X] " ,
      " reviewRating " : {
        " @type " :  " Rating " ,
        " bestRating " :  " [X] " ,
        " ratingValue " :  " [X] " ,
        " pire évaluation " :  " [X] "
      }
    }

On peut envelopper les Review avec le schéma LocalBusiness (ou une option plus spécifique si vous préférez), et ajoutez le aggregateRating avec la moyenne de toutes les notations de la page.

    < script type = " application / ld + json " >
    {
      " @context " :  " http://schema.org " ,
      " @type " :  " LocalBusiness " ,    
      " nom " :  " [X] " ,
      " adresse " : {
        " @type " :  " PostalAddress " ,
        " streetAddress " :  " [X] " ,
        " addressLocality " :  " [X] " ,
        " addressRegion " :  " [X] " ,
        " code postal " :  " [X] "
      },
      " telePhone " :  " [X] " ,
      " openingHours " :  " [X] " ,
      " geo " : {
        " @type " :  " GeoCoordinates " ,
        " latitude " :  " [X] " ,
        " longitude " :  " [X] "
      },
      " url " :  " [X] " ,
      " logo " :  " [X] " ,
      " image " :  " [X] " ,
      " priceRange " : " [X] " ,
      " aggregRating " : {
        " @type " :  " AggregateRating " ,
        " ratingValue " :  " [X] " ,
        " ratingCount " :  " [X] "
      }
    }
    < / script >

Voici le lien [schema.org pour plus de précision sur toutes les propriétés](https://schema.org/LocalBusiness).

#### Tout rassembler

Voici un exemple pour un vendeur de voiture, on retrouve uniquement 2 commentaires dans cet exemple, mais l'extrait de code reste identique, quelque soit le nombre d'avis que vous avez sur la page :

    < script type = " application / ld + json " >
    {
      " @context " :  " http://schema.org " ,
      " @type " :  " AutoDealer " ,    
      " name " :  " Voiture Discount " ,
      " adresse " : {
        " @type " :  " PostalAddress " ,
    		" streetAddress " :  " 120-126 Quai de Bacalan " ,
    		" addressLocality " :  " Bordeaux " ,
    		" addressRegion " :  " Aquitaine " ,
    		" PostalCode " :  " 33300 "
    	},
    	" telePhone " :  " 0565656565 " ,
    	" openingHours " :  " Mo, Tu, Nous, Mardi, Vendredi , Sa 21: 00-07: 00 " ,
    	" geo " : {
    		" @type " :  " GeoCoordinates " ,
    		" latitude " :  " 29.665375 " ,
    		" longitude " :  " -95.192466 "
    	},
      " url " :  " https://www.voiturediscount.com/ " ,
      " logo " :  " https://www.voiturediscount.com/wp-content/uploads/2017/09/site-logo.png " ,
      " image " :  " https://www.voiturediscount.com/wp-content/uploads/2017/09/voiture-discount.jpg " ,
      " priceRange " : " $$ " ,
      " aggregRating " : {
        " @type " :  " AggregateRating " ,
        " ratingValue " :  " 4.75 " ,
        " ratingCount " :  " 2 "
     	 },
      " review " : [
        {
        " @type " :  " Review " ,
        " auteur " :  " Jean Valjean " ,
        " datePublished " :  " 2019-03-05 " ,
        " reviewBody " :  " Le personnel est sympathique et a été en mesure de répondre à mes questions sans interruption. Je suis très heureux de la transaction et je ferais de nouveau affaire avec eux et je les recommanderais à mes amis et à ma famille. À la recherche d’une voiture, cela devrait être votre premier et unique arrêt. Arron a fait un excellent travail en aidant dans l’expérience d’achat. Il était un excellent vendeur et serait le type avec qui je parlerais. " ,
        " reviewRating " : {
          " @type " :  " Rating " ,
          " meilleure évaluation " :  " 5 " ,
          " ratingValue " :  " 5 " ,
          " pire évaluation " :  " 1 "
        }
        },
        {
        " @type " :  " Review " ,
        " auteur " :  " Spike Lee " ,
        " datePublished " :  " 2019-10-17 " ,
        " reviewBody " :  " Avec le personnel, la propreté et la qualité des véhicules vendus par VoitureDiscount. Je le recommande vivement à un ami. Nous avons eu un petit problème d'équipement au cours de mon processus, mais cela a été rectifié. Merci Pedro Herrera pour votre professionnalisme et de l' assistance. J'attendons avec impatience les futurs achats de king of Cars. J'ai acheté une Fiat Multipla. " ,
        " reviewRating " : {
          " @type " :  " Rating " ,
          " meilleure évaluation " :  " 5 " ,
          " ratingValue " :  " 4 " ,
          " pire évaluation " :  " 1 "
        }
        }
      ]
    }
    < / script >

Ajoutez le balisage dans l'en-tête <head> du site.

Depuis Wordpress il est possible d'utiliser un plugin [Per page add to head](https://wordpress.org/plugins/per-page-add-to/). Cela permet d'ajouter facilement le JSON-LD sur n'importe qu'elle page, mais il existe d’innombrables autres moyens pour y parvenir.

Dans tous les cas !

**Pensez bien à utiliser l'**[**outil de test de données structurées**]() **proposé par Google pour vérifier les implémentations.**  
N'ignorez jamais les avertissements, et corrigez absolument les erreurs éventuelles !

#### Etape 3

Ajoutez un formulaire du type : "Laissez un commentaire" quelque part sur la page Témoignages.

Vous pouvez éventuellement créer un système complet qui modère les soumissions puis les publie sur la page, mais rien ne vous y oblige. En soit... personne le saura... ¯ \\ _ (ツ) _ / ¯

#### Etape 4

Ajoutez votre schéma LocalBusiness et aggregRatingRating à d'autres pages pertinentes de votre site. Des exemples courants sont :

* les pages de services,
* les pages à propos de nous,
* qui sommes-nous,...

Évitez par contre les choses comme les billets de blogs, les pages ressources et tout autre élément pour lequel les avis ne sont pas applicables. Et on évite par conséquent de le mettre sur trop de page du site !

Exemple :

    < script type = " application / ld + json " >
    {
      " @context " :  " http://schema.org " ,
      " @type " :  " AutoDealer " ,    
      " name " :  " Voiture Discount " ,
      " adresse " : {
        " @type " :  " PostalAddress " ,
        " streetAddress " :  " 120-126 Quai de Bacalan " ,
        " addressLocality " :  " Bordeaux " ,
        " addressRegion " :  " Aquitaine " ,
        " PostalCode " :  " 33300 "
      },
      " telePhone " :  " 0565656565 " ,
      " openingHours " :  " Mo, Tu, Nous, Mardi, Vendredi , Sa 21: 00-07: 00 " ,
      " geo " : {
        " @type " :  " GeoCoordinates " ,
        " latitude " :  " 29.665375 " ,
        " longitude " :  " -95.192466 "
      },
      " url " :  " https://www.voiturediscount.com/ " ,
      " logo " :  " https://www.voiturediscount.com/wp-content/uploads/2017/09/site-logo.png " ,
      " image " :  " https://www.voiturediscount.com/wp-content/uploads/2017/09/voiture-discount.jpg " ,
      " priceRange " : " $$ " ,
      " aggregRating " : {
        " @type " :  " AggregateRating " ,
        " ratingValue " :  " 4.75 " ,
        " ratingCount " :  " 2 "
     	}
    }
    < / script >

**Encore une fois, ne pas mettre de notation sur la page d'Accueil !**

Vous pouvez cependant mettre le LocalBusiness, il suffit juste de supprimer la valeur AggregateRating :

    < script type = " application / ld + json " >
    {
      " @context " :  " http://schema.org " ,
      " @type " :  " AutoDealer " ,    
      " name " :  " Voiture Discount " ,
      " adresse " : {
        " @type " :  " PostalAddress " ,
        " streetAddress " :  " 120-126 Quai de Bacalan " ,
        " addressLocality " :  " Bordeaux " ,
        " addressRegion " :  " Aquitaine " ,
        " PostalCode " :  " 33300 "
      },
      " telePhone " :  " 0565656565 " ,
      " openingHours " :  " Mo, Tu, Nous, Mardi, Vendredi , Sa 21: 00-07: 00 " ,
      " geo " : {
        " @type " :  " GeoCoordinates " ,
        " latitude " :  " 29.665375 " ,
        " longitude " :  " -95.192466 "
      },
      " url " :  " https://www.voiturediscount.com/ " ,
      " logo " :  " https://www.voiturediscount.com/wp-content/uploads/2017/09/site-logo.png " ,
      " image " :  " https://www.voiturediscount.com/wp-content/uploads/2017/09/voiture-discount.jpg " ,
      " priceRange " : " $$ " ,
    }
    < / script >

**Remarque :** chaque page comportant un aggregateRating doit afficher toutes les notations qu'elle référence OU afficher une notation globale et créer un lien vers la page contenant les avis.

Vous pouvez le faire comme bon vous semble. Pour voiture discount on pourrait par exemple ajouter un bloc comme celui ci à toutes les pages sur lesquelles j'ai mis le schéma aggregateRating (on juge pas le design svp!) :

![](/uploads/Capture-1.PNG)

Et c'est fini !