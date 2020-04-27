---
title: Feuille de route des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: b11edbedca83bb26d2990d029a220165f68bc1ca
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454892"
---
# <a name="future-work"></a>Travail à venir

Même si nous avançons à grands pas dans la définition des cartes adaptatives, il reste encore beaucoup de travail à faire. Nous espérons qu’avec des communautés de développeurs actives comme botness et d’excellents partenaires comme Slack et Kik, nous pourrons créer un excellent écosystème de cartes multiplateformes.

## <a name="roadmap"></a>Feuille de route

Vous pouvez consulter notre [feuille de route actuelle (non finale) ici](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog). Notez que tout ce qui se trouve ici peut faire l’objet de modifications, et qu’il ne s’agit pas d’une garantie d’expédition.

## <a name="future-ideas"></a>Idées pour l’avenir

Voici quelques idées pour l’avenir, qui n’en sont encore qu’à l’étape du brainstorming. Si elles vous intéressent, faites-le nous savoir dans un commentaire.

### <a name="great-looking-cards-from-data"></a>Jolies cartes à partir des données

Nous savons que de nombreux auteurs de cartes ont déjà des données bien définies sous-jacentes à leurs cartes. Notre plan consiste à explorer un modèle de création de modèles qui permettrait la génération de cartes (côté serveur ou côté client) en fonction des données et un référentiel de modèles bien définis et personnalisables.

### <a name="make-cards-responsive"></a>Rendre les cartes réactives

Les dispositions de cartes doivent être réactives à l’espace disponible. Les cartes adaptatives sont adaptables à différents appareils, styles d’expérience utilisateur et frameworks d’interface utilisateur, mais elles ne sont pas encore réactives. Des propriétés supplémentaires doivent être définies sur les éléments afin de permettre aux producteurs de cartes de fournir aux bibliothèques de rendu les indications nécessaires leur permettant de changer intelligemment la disposition d’une manière qui conserve l’intention de la carte.

### <a name="responsive-exploration"></a>Exploration réactive

* Ajouter une propriété d’**importance** qui annote l’importance du contenu. Le contenu moins important peut être supprimé afin que le contenu restant tienne dans l’espace disponible.
* Ajouter des **contraintes** et des propriétés de **stratégie** décrivant comment réagir quand les contraintes ne peuvent pas être satisfaites. 
  * Masquer le contenu ou réduire le contenu à une taille plus petite.
  * Ajouter un seuil qui, en cas de dépassement, change `columnSet` en carrousel de colonnes.

### <a name="new-element-types"></a>Nouveaux types d’éléments

* Cartes ? - Incorporer une carte géographique dans une carte adaptative avec interactivité ou retour à la bitmap.
* *Quels éléments souhaitez-vous ou vous faut-il* ?

### <a name="new-rendering-libraries"></a>Nouvelles bibliothèques de rendu

* React ?
* Xamarin ?
* *Quels frameworks souhaitez-vous ?*
