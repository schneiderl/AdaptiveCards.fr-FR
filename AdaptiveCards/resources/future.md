---
title: Feuille de route des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138002"
---
# <a name="future-work"></a>Travaux futurs

Nous avons fait des progrès considérables définissant des cartes adaptatives, mais il existe toujours un grand nombre de tâches à effectuer. Notre espoir est que via les Communautés de développeurs active comme botness et des partenaires comme Slack et Kik, nous pouvons créer un écosystème exceptionnel de cartes d’inter-plateformes.

## <a name="roadmap"></a>Feuille de route

Vous pouvez voir notre [actuel (non finale) feuille de route ici](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog). Notez que quoi que ce soit ici est susceptible de changer et n’est pas une garantie de livraison.

## <a name="future-ideas"></a>Idées futures

Voici quelques idées futures, que nous avons, qui sont simplement dans la scène réfléchi. Si vous êtes intéressé par un de ces, faites-le nous savoir dans un commentaire.

### <a name="great-looking-cards-from-data"></a>Excellents cartes qui recherchent des données

Nous savons de nombreux auteurs de carte disposez déjà de données bien définies derrière leurs cartes. Notre objectif est d’Explorer un modèle de création de modèles qui permettrait de cartes à générer (côté serveur ou côté client) basé sur les données et un référentiel de modèles bien définis et personnalisables.

### <a name="make-cards-responsive"></a>Rendre des cartes réactive

Dispositions de la carte doivent être réactives à l’espace disponible. Des cartes adaptatives sont adaptables aux différents appareils, les styles de l’expérience utilisateur et et infrastructures d’interface utilisateur, mais ils ne sont pas réactives encore. Propriétés supplémentaires doivent être définies sur les éléments qui permettent les producteurs de carte fournir les indications nécessaires pour les bibliothèques de rendu afin qu’ils peuvent modifier intelligemment la disposition d’une façon qui conserve l’intention de la carte.

### <a name="responsive-exploration"></a>Exploration réactive

* Ajouter un **importance** propriété qui annote l’importance du contenu. Contenu moins importante peut être supprimé pour s’ajuster à la quantité d’espace disponible
* Ajouter **contraintes** et **stratégie** propriétés décrivant comment réagir lorsque les contraintes ne peuvent pas être satisfaites. 
  * Masquer le contenu ou réduire le contenu à la plus petite taille.
  * Ajoutez un seuil qui, lorsque dépassée, change `columnSet` à carrousel de colonnes.

### <a name="new-element-types"></a>Nouveaux types d’élément

* Mappages ? -intégrer une carte dans une carte avec la stratégie de secours en bitmap ou l’interactivité
* *Quels éléments souhaitez-vous ou devez*?

### <a name="new-rendering-libraries"></a>Nouvelles bibliothèques de rendu

* Réagir ?
* Xamarin ?
* *Quelles infrastructures voulez-vous ?*
