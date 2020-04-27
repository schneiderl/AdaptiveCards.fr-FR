---
title: Motivations et principes
author: matthidinger
ms.author: mahiding
ms.date: 5/14/2018
ms.topic: article
ms.openlocfilehash: 243ad63fc585c5afc3fa396b86ff6261e8a7ee93
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454812"
---
# <a name="motivations-and-principles"></a>Motivations et principes

Vous trouverez ci-dessous les motivations et les principes régissant l’évolution du format de carte adaptative.

## <a name="motivations-behind-the-format"></a>Motivations du format

Début 2016, plusieurs équipes de Microsoft (notamment Outlook, Windows et Bot Framework) se sont rendu compte qu’elles souhaitaient toutes quelque chose d’extrêmement similaires (« cartes ») et que chacune d’elles concevait indépendamment ses propres solutions :

- Windows avait son propre format de vignettes et de notifications dynamiques.
-  Bot Framework utilisait un ensemble de modèles de cartes prédéfinis parmi lesquels les développeurs pouvaient choisir lors de l’envoi de messages de bot.
- Outlook utilisait son propre format MessageCard pour sa fonctionnalité de messages actionnables.

En même temps, d’autres plateformes telles que LINE, FaceBook Messenger, Slack, et ainsi de suite, définissaient leur propre format de « carte » propriétaire. Quelques employés de Microsoft se sont donc réunis et ont commencé à tenter de définir un format de carte unique et ouvert, ainsi qu’un ensemble de kits SDK qui :

- Faciliteraient l’échange de cartes entre les hôtes.
- Permettraient à chaque hôte de conserver le contrôle du style des cartes afin de garantir la cohérence visuelle.
- Permettraient à une application hôte d’afficher facilement des cartes avec un minimum d’effort par le biais de kits SDK prêts à l’emploi.
- Fourniraient également de la valeur à des tiers et finiraient par être largement adoptés par le secteur.

## <a name="principles-governing-adaptive-cards"></a>Principes régissant les cartes adaptatives

1.  **La carte adaptative est un format de carte _simple_ et _déclaratif_**

    1.  Elle n’est pas censée être un remplacement ou une alternative à HTML ou XAML.
    2.  Il n’y a **pas de « code-behind »** avec les cartes adaptatives.
        1. Les auteurs de cartes ne peuvent pas incorporer de code personnalisé/arbitraire avec leurs charges utiles. Ainsi, un hôte de carte adaptative n’a jamais besoin d’exécuter de code tiers.
        2. Le dynamisme et l’interactivité sont obtenus uniquement par le biais de balisage déclaratif.
    3.  Cela garantit que l’effort nécessaire pour créer un SDK de carte adaptative pour une nouvelle plateforme demeure raisonnable.

2.  **Le format carte adaptative ne peut pas imposer l’utilisation d’une technologie sous-jacente particulière.**

    1.  Le format de carte adaptative ne repose pas sur JavaScript, C#, Python ou tout autre langage.
    2.  De même, il ne repose pas sur HTML ou XAML, ni sur tout autre framework graphique/d’interface utilisateur.
    3.  Ainsi, les cartes adaptatives peuvent être rendues de manière native sur n’importe quelle plateforme tant qu’il existe un renderer.

3.  **Le format de carte adaptative est une _propriété partagée_** .

    1.  Le format et ses kits SDK doivent être open source, et c’est la communauté qui doit être à l’origine de son évolution.
    2.  Le format n’est donc pas détenu ni piloté par une équipe spécifique.

4.  **Le format de carte adaptative n’est pas conçu « uniquement pour une utilisation par Microsoft »** .

    1.  Au lieu de cela, il est conçu pour répondre aux besoins d’un large éventail d’applications et de cas d’usage.

5.  **Le _groupe de travail de carte adaptative_ régit l’évolution du format**.

    1.  Ce groupe de travail se compose d’un ensemble d’employés de Microsoft qui sont tous impliqués dans la réussite du format.
    2.  Les membres du groupe de travail participent à des réunions hebdomadaires (actuellement le lundi) au cours desquelles ils examinent les propositions de fonctionnalités, discutent des problèmes ouverts et suivent l’avancement global des éléments de travail vNext.
    3.  Le groupe de travail utilise les commentaires fournis par la communauté globale, notamment les équipes Microsoft internes, pour décider de l’évolution du format.
        1. Tout le monde peut participer au groupe de travail en ouvrant des problèmes dans GitHub (voir ci-dessous).
        2. Ce sont les problèmes/demandes de fonctionnalités enracinés dans l’utilisation réelle du framework des cartes adaptatives (en tant qu’hôte ou en tant qu’auteur de carte) qui ont le plus d’impact sur l’avenir du format.
    4.  Pour être approuvées par le groupe de travail, les nouvelles fonctionnalités proposées :
        1. Doivent être justifiées par des cas d’usage de la vie réelle.
        2. Doivent avoir une spécification fonctionnelle.
    5.  Les nouvelles fonctionnalités approuvées sont ajoutées au backlog et prises en compte pour vNext.
        1. Les critères utilisés pour hiérarchiser les nouvelles fonctionnalités incluent l’ampleur des scénarios couverts par la fonctionnalité, sa complexité/facilité de maintenance, et bien plus encore.
        2. En cas de doute, elles sont ignorées. Il est beaucoup plus facile d’introduire ultérieurement une fonctionnalité bien conçue que de vivre indéfiniment avec une erreur.
    6.  Toutes les nouvelles fonctionnalités sont implémentées dans tous les kits SDK pris en charge.
    7.  Toutes les nouvelles fonctionnalités sont documentées et associées à une carte de test publiée dans le dossier d’exemples.
    8.  Les nouvelles versions du format et des kits SDK passent par une phase bêta.
    9.  Le planning de publication du schéma de carte adaptative et des versions de SDK est motivé par la qualité, pas par la date.

6.  **Interopérabilité**
    1.  Les cartes créées conformément au format documenté (par exemple celles n’utilisant aucune extension propre à l’hôte) s’afficheront correctement dans n’importe quel hôte qui prend en charge les cartes adaptatives.
    2.  Les seules exceptions à ces principes sont les suivantes :
        1.  Certains hôtes sont susceptibles de ne pas autoriser l’interactivité et n’afficheront donc pas les entrées et les actions.
        2.  L’exécution des actions Action.Submit est à la discrétion de l’hôte, et tous les hôtes ne gèreront pas nécessairement toutes les charges utiles Action.Submit. De plus, certains hôtes sont susceptibles de ne pas prendre en charge Action.Submit.

7.  **Le format doit être extensible.**

    1.  Les hôtes doivent avoir la liberté d’ajouter la prise en charge d’éléments personnalisés ou d’actions personnalisées qui vont au-delà des capacités du format.
    2.  C’est particulièrement important pour les actions, car différents hôtes ne prennent pas nécessairement en charge le même ensemble d’actions.
    3.  Ces ajouts sont à la discrétion de l’hôte.
        1. Il ne s’agit pas d’ajouts *de facto* à la spécification de carte adaptative.
        2. Par conséquent, une charge utile qui les utilise devient incompatible avec le format de carte adaptative standard.
        3. Ils peuvent toutefois être présentés au groupe de travail et proposés en tant que nouvelles fonctionnalités pour une version ultérieure du format, comme décrit au point n°5.

8.  **Les créateurs de cartes ont la main sur le contenu, tandis que l’application hôte contrôle l’apparence**.

    1.  Les applications hôtes imposent leur style. Ainsi, les cartes semblent être des extensions natives de l’expérience de l’application.
    2.  Les auteurs de cartes peuvent toujours spécifier le style, mais uniquement par le biais d’expressions sémantiques de couleurs, de tailles, et ainsi de suite.

9.  **Des kits SDK seront fournis pour les plateformes de développement les plus connues.**

    1.  Les kits SDK facilitent le rendu des charges utiles de cartes adaptatives dans n’importe quel hôte.
    2.  Cela garantit que la barrière à l’entrée est la plus basse possible à la fois pour les développeurs tiers et pour les équipes Microsoft.
