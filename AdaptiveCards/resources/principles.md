---
title: Les principes et les motivations
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 78fe44463c4ddb832ba0cc72d456b6d21518bac4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553151"
---
# <a name="motivations-and-principles"></a>Les principes et les motivations

Voici les motivations et principes régissant l’évolution du format de carte adaptative.

## <a name="motivations-behind-the-format"></a>Motivations derrière le format

Dans les premières 2016, plusieurs équipes chez Microsoft (y compris Outlook, Windows et l’infrastructure de robot) sont rendu compte que tous les souhaitait quelque chose de très similaires (« cartes ») et que chacun d’eux ont été conception indépendamment de leurs propres solutions :

- Windows avait son propre format de vignettes dynamiques et Notifications
-  Le Bot framework utilisait un ensemble de modèles de carte prédéfinie aux développeurs pouvait choisir parmi lors de l’envoi de messages de robot
- Outlook a été à l’aide de son propre format MessageCard pour sa fonctionnalité Messages actionnables

En même temps, les autres plateformes telles que la ligne, FaceBook Messenger, Slack et bien plus encore ont été définissant leur propres, format propriétaire « carte ». Afin que quelques employés de Microsoft collectées et démarrer un effort pour définir un format de carte unique, ouvrez et un ensemble de kits de développement logiciel qui :

- Faciliterait l’échange de cartes entre les hôtes
- Permettrait à chaque hôte pour contrôler le style des cartes de façon à garantir la cohérence visuelle
- Permettrait de facilement pour une application hôte afficher les cartes avec un minimum d’effort via les kits de développement logiciel prêt à l’emploi
- Et qui serait également fournir de valeur à des tiers et finalement obtenir adopté à grande échelle par le secteur d’activité

## <a name="principles-governing-adaptive-cards"></a>Principes relatifs à des cartes adaptatives

1.  **Carte adaptative est un _simple_ et _déclarative_ format de carte**

    1.  Il n’est pas destiné en tant que HTML ou XAML remplacement/alternative
    2.  Il est **aucune « code-behind »** avec des cartes adaptatives
        1. Auteurs de carte ne peut pas incorporer le code personnalisé/arbitraire avec leurs charges utiles, et par conséquent un hôte de la carte adaptative n’a jamais besoin d’exécuter du code de tiers
        2. Dynamisme et l’interactivité sont EFFECTUES uniquement par le biais de balisage déclaratif
    3.  Cela garantit que les efforts nécessaires à la génération d’un SDK carte adaptative pour une nouvelle plateforme restent raisonnable

2.  **Le format de carte adaptative ne peut pas imposer l’utilisation d’une technologie sous-jacente particulier**

    1.  Le format de carte adaptative ne repose pas sur JavaScript, C#, Python ou tout autre langage
    2.  De même qu’il ne repose pas sur le HTML ou XAML ou une autre infrastructure / d’interface graphique utilisateur
    3.  De cette façon, des cartes adaptatives peut être rendus en mode natif sur n’importe quelle plateforme pour tant qu’il existe un convertisseur

3.  **Le format de carte adaptative est un _propriété partagée_**

    1.  Ainsi que ses kits de développement logiciel, le format doit être son évolution proposés par la Communauté et open source
    2.  Le format n’est par conséquent pas détenu ni dues à toute une équipe

4.  **Le format de carte adaptative n’est pas conçu « simplement pour l’utilisation de Microsoft »**

    1.  Au lieu de cela, il est conçu pour répondre aux besoins d’un large éventail d’applications et de cas d’usage

5.  **Le _groupe de travail de carte adaptative_ régit l’évolution du format**

    1.  Ce groupe de travail est composé d’un ensemble d’employés de Microsoft qui sont tous profondément impliquées dans la réussite du format
    2.  Les groupe de travail effectue réunions hebdomadaires (actuellement lundi) pendant quelle fonctionnalité propositions sont révisées, ouvrez problèmes sont abordées et triées et suivie de la progression globale sur les éléments de travail vNext
    3.  Le groupe de travail utilise des commentaires à partir de la Communauté dans son ensemble, y compris les équipes internes de Microsoft, pour déterminer la façon dont le format évolue
        1. Tout le monde peut participer à signaler des problèmes dans GitHub (voir ci-dessous), le groupe de travail
        2. Problèmes/demandes émanant de l’utilisation réelle de l’infrastructure des cartes adaptatives (en tant qu’hôte ou en tant qu’un auteur de la carte) ont le plus d’impact sur l’avenir du format
    4.  Doit être approuvé par le groupe de travail proposé de nouvelles fonctionnalités :
        1. Doit être justifiée par cas d’utilisation réelle
        2. Doit avoir une spécification fonctionnelle
    5.  Nouvelle fonctionnalité approuvée sont étudiées vNext et ajouté à la file d’attente
        1. Les critères utilisés pour hiérarchiser les nouvelles fonctionnalités incluent la largeur de la fonctionnalité permet des scénarios, sa complexité/la facilité de maintenance et bien plus encore
        2. En cas de doute, conservez-la ! Il est beaucoup plus facile d’introduire une fonctionnalité bien conçue plus tard de vie avec une erreur indéfiniment.
    6.  Toutes les nouvelles fonctionnalités sont implémentées dans tous les kits de développement logiciel pris en charge
    7.  Toutes les nouvelles fonctionnalités sont documentées et associées à une carte de test publiée dans le dossier samples
    8.  Nouvelles versions de format et des kits de développement logiciel passer par une phase bêta
    9.  La planification de la version de schéma de la carte adaptative et les versions SDK est pilotée par qualité, pas de date

6.  **Interopérabilité**
    1.  Cartes créés selon le format documenté (par exemple, ne pas à l’aide des extensions spécifiques à l’hôte) seront afficheront correctement dans n’importe quel hôte ADAPTATIF carte prenant en charge
    2.  Les seules exceptions à cette principes sont :
        1.  Certains hôtes ne permettent pas d’interactivité et par conséquent n’affichera entrées ni des actions
        2.  Exécution des actions de Action.Submit est à la discrétion de l’hôte, et pas tous les ordinateurs hôtes nécessairement correctement gérera toutes les charges utiles de Action.Submit. En outre, certains hôtes ne peuvent pas en charge Action.Submit tout

7.  **Le format doit être extensible**

    1.  Hôtes doivent avoir la possibilité d’ajouter la prise en charge des éléments personnalisés ou des actions personnalisées qui vont au-delà de ce que le format est capable de
    2.  Cela est particulièrement important pour les actions, comme les différents hôtes ne met pas en charge le même ensemble d’actions
    3.  Ces ajouts sont à la discrétion de l’hôte
        1. Ils ne sont pas un *facto* ajout à la spécification de la carte adaptative
        2. Par conséquent, ils rendent une charge utile qui les utilise incompatible avec le format standard de la carte adaptative
        3. Ils peuvent toutefois être présentés pour le groupe de travail et proposée en tant que de nouvelles fonctionnalités pour une future version du format, comme décrit au point #5

8.  **Les auteurs de carte propriétaire du contenu, héberger des applications de possèdent l’apparence**

    1.  Héberger des applications imposent leur appliquer un style afin de rechercher des cartes et l’apparence, comme ils sont des extensions natives de l’expérience de l’application
    2.  Les auteurs de carte peuvent spécifier des styles, mais uniquement via des expressions sémantiques de couleurs, tailles, etc.

9.  **Kits de développement logiciel seront fournies pour les plateformes de développeur plus populaires**

    1.  Kits de développement logiciel facilitent le rendu des charges utiles de carte adaptative dans n’importe quel hôte
    2.  Cela garantit que l’obstacle à l’entrée est faible peut être à la fois pour les développeurs tiers et Microsoft teams
