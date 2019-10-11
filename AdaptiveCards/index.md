---
title: Vue d’ensemble du format Cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 27c7d5ac7da3ae182667cbf8efa90d29f110d1d3
ms.sourcegitcommit: ef03c0eff3272a36cfa88daf99c4d57e4bae9599
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72042533"
---
# <a name="adaptive-cards-overview"></a>Vue d’ensemble du format Cartes adaptatives 

Le format Cartes adaptatives est un format d’échange de cartes ouvert qui permet aux développeurs d’échanger du contenu d’interface utilisateur de manière commune et cohérente.

<video controls width="100%" poster="./content/videoposter.png">
    <source src="https://adaptivecardsblob.blob.core.windows.net/assets/AdaptiveCardsOverviewVideo.mp4" type="video/mp4">
</video>

## <a name="how-they-work"></a>Fonctionnement

Les [**créateurs de cartes**](authoring-cards/getting-started.md) décrivent leur contenu sous la forme d’un simple objet JSON. Ce contenu peut ensuite être restitué en mode natif à l’intérieur d’une [**application hôte**](rendering-cards/getting-started.md), en s’adaptant automatiquement à l’apparence de l’hôte.

Par exemple, Contoso Bot peut créer par le biais de Bot Framework une carte adaptative qui, une fois remise à Skype, adopte l’apparence d’une carte Skype. Quand ce même contenu est envoyé à Microsoft Teams, il en adopte l’apparence. Comme de plus en plus d’applications hôtes commencent à prendre en charge le format Cartes adaptatives, ce même contenu apparaît automatiquement dans ces applications, dont il épouse l’apparence.

Les utilisateurs sont gagnants, car tout semble familier. Les applications hôtes sont gagnantes, car elles contrôlent l’expérience utilisateur. Les créateurs de cartes sont également gagnants, car la portée de leur contenu s’élargit sans travail supplémentaire.

## <a name="goals"></a>Objectifs 

Les objectifs des cartes adaptatives sont les suivants :

* **Portables** : Sur toute application, tout appareil et toute infrastructure d’interface utilisateur
* **Ouvertes** : Les bibliothèques et le schéma sont open source et partagés
* **Économiques** : Faciles à définir, faciles à utiliser
* **Expressives** : Ciblées sur le flux de contenu que les développeurs souhaitent produire
* **Purement déclaratives** : Aucun code n’est nécessaire ou autorisé
* **Automatiquement mises en forme** : En fonction des instructions de la marque et de l’expérience utilisateur de l’application hôte

## <a name="for-card-authors"></a>Pour les créateurs de cartes
Le format Cartes adaptatives est idéal pour les créateurs de cartes :

* **Un seul schéma** : Vous avez un format unique, ce qui réduit le coût de création d’une carte et optimise le nombre d’endroits où elle peut être utilisée.
* **Expression plus riche** : Votre contenu peut refléter plus fidèlement ce que vous voulez exprimer, car vous disposez d’une palette plus riche.
* **Champ large** : Votre contenu fonctionne sur un plus grand ensemble d’applications sans que vous deviez apprendre de nouveaux schémas.
* **Contrôles d’entrée** : Votre carte peut inclure des contrôles d’entrée pour collecter des informations auprès de l’utilisateur qui voit la carte.
* **Meilleurs outils** : Un écosystème de cartes ouvert signifie que de meilleurs outils sont partagés par le plus grand nombre.

## <a name="for-experience-owners"></a>Pour les propriétaires d’expérience utilisateur
En tant que développeur d’applications, si vous souhaitez exploiter un écosystème de contenu tiers, vous aimerez le format Cartes adaptatives pour les raisons suivantes :

* **Expérience utilisateur cohérente** : Vous garantissez une expérience cohérente pour vos utilisateurs, car vous avez la main sur le style de la carte rendue.
* **Performances natives** : Vous bénéficiez de performances natives grâce au ciblage direct de votre infrastructure d’interface utilisateur.
* **Sécurité** : La distribution du contenu étant sécurisée, vous n’êtes pas obligé d’ouvrir votre infrastructure d’interface utilisateur à des scripts ou du balisage bruts.
* **Implémentation facile** : Vous profitez de bibliothèques prêtes à l’emploi qui facilitent l’intégration à toute plateforme prise en charge 
* **Documentation gratuite** : Vous gagnez du temps, car vous n’avez pas à inventer, implémenter et documenter un schéma propriétaire.
* **Outils partagés** : Vous gagnez du temps, car vous n’êtes pas obligé de créer des outils personnalisés.

## <a name="core-design-principles"></a>Principes de conception de base 

Le format Cartes adaptatives repose sur un ensemble de [principes directeurs](resources/principles.md) qui sont utiles pour préserver la conception. 

### <a name="semantic-instead-of-pixel-perfect"></a>Privilégier la sémantique à une disposition de type « pixel parfait »
Nous nous sommes efforcés autant que possible de privilégier des concepts et valeurs sémantiques au détriment d’une disposition pure de type « pixel parfait ». Des exemples d’expression sémantique sont montrés avec des couleurs, des tailles et des éléments comme FactSet et ImageSet. L’application hôte peut ainsi prendre de meilleures décisions concernant l’apparence réelle.

### <a name="card-authors-own-the-content-host-app-owns-the-look-and-feel"></a>Les créateurs de cartes ont la main sur le contenu, tandis que l’application hôte contrôle l’apparence
Le créateur d’une carte est maître de ce qu’il veut exprimer, mais l’application qui affiche la carte contrôle son apparence dans le contexte de son application.

### <a name="keep-it-simple-but-expressive"></a>Rester simple, mais expressif
Nous voulons que les cartes adaptatives soient expressives et universelles, mais nous ne souhaitons pas créer une infrastructure d’interface utilisateur.  L’objectif consiste à créer une couche intermédiaire qui est « suffisamment expressive », à l’image de Markdown dans le cas des documents.

En misant sur la simplicité et l’expressivité, Markdown a créé une description simple et cohérente du contenu des documents.  De la même façon, nous pensons que le format Cartes adaptatives peut créer un moyen simple et expressif de décrire le contenu d’une carte.

### <a name="when-in-doubt-keep-it-out"></a>En cas de doute, ignorer
Il est plus facile d’effectuer un ajout plus tard que de rester dans l’erreur. Si nous avons été amenés à débattre de l’opportunité d’ajouter ou non quelque chose, nous avons choisi de l’ignorer.  Il est toujours plus facile d’ajouter une propriété que de conserver quelque chose que nous aurions aimé ne pas avoir à prendre en charge.


## <a name="build-2019-session"></a>Session Build 2019

La session suivante de la conférence Microsoft Build présente les cartes adaptatives dans des cas d’utilisation très divers. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/wT1yFr_j6IM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
