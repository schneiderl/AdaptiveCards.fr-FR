---
title: Prise en main
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: c9a0ad07ba5fefbcdc35239591c02fe0720b5b66
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454842"
---
# <a name="getting-started"></a>Prise en main 

Une carte adaptative est un modèle d'objet de carte sérialisé au format JSON.

## <a name="adaptive-card-structure"></a>Structure d'une carte adaptative

La structure de base d'une carte est la suivante :

* `AdaptiveCard` : l'objet racine décrit la carte adaptative proprement dite, avec sa composition en termes d'éléments, ses actions, la façon dont elle doit être lue et la version du schéma requise pour la restituer.
* `body` -le corps de la carte est constitué de modules appelés `elements`. Les éléments peuvent être composés selon des combinaisons quasiment infinies pour créer de nombreux types de cartes. 
* `actions` : beaucoup de cartes disposent d'un ensemble d'actions applicables par l'utilisateur. Cette propriété décrit les actions qui sont généralement présentées sur une « barre d'action », en bas.

### <a name="example-card"></a>Exemple de carte

Cet exemple de carte comprend une ligne de texte suivie d'une image.

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a>Propriété `Type`

Chaque élément possède une propriété `type` qui identifie le type d'objet dont il s'agit. En examinant la carte ci-dessus, vous pouvez constater que nous disposons de deux éléments : `TextBlock` et `Image`.

Tous les éléments de la carte adaptative **sont empilés verticalement** et **s'étendent sur la largeur de leur parent** (pensez à `display: block` en HTML). Vous pouvez toutefois utiliser `ColumnSet` pour créer des colonnes de conteneurs côte à côte.

## <a name="adaptive-elements"></a>Éléments adaptatifs

Les principaux éléments sont les suivants :

* **TextBlock** : ajoute un bloc de texte avec des propriétés permettant de contrôler l'aspect du texte.
* **Image** : ajoute une image avec des propriétés permettant de contrôler l'aspect de l'image.

## <a name="container-elements"></a>Éléments conteneurs

Les cartes peuvent également comporter des conteneurs, qui permettent d'organiser une collection d'éléments enfants.

* **Container** : définit une collection d'éléments.
* **ColumnSet/Column** : définit une collection de colonnes ; chaque colonne est un conteneur.
* **FactSet** : conteneur de faits.
* **ImageSet** : conteneur d'images permettant à l'interface utilisateur d'afficher l'expérience de galerie photo appropriée pour une collection d'images.

## <a name="input-elements"></a>Éléments d'entrée

Les éléments d'entrée vous permettent de demander une interface utilisateur native pour créer des formulaires simples :

* **Input.Text** : obtenir du contenu textuel auprès de l'utilisateur.
* **Input.Date** : obtenir une date auprès de l'utilisateur.
* **Input.Time** : obtenir une heure auprès de l'utilisateur.
* **Input.Number** : obtenir un nombre auprès de l'utilisateur.
* **Input.ChoiceSet** : donner à l'utilisateur un ensemble de possibilités et lui demander de choisir.
* **Input.Toggle** : donner à l'utilisateur de faire un choix entre deux éléments.

## <a name="actions"></a>Actions

Les actions ajoutent des boutons à la carte. Ceux-ci permettent d'effectuer différents types d'actions, comme l'ouverture d'une URL ou l'envoi de certaines données.

* **Action.OpenUrl** : le bouton ouvre une URL externe à des fins d'affichage.
* **Action.ShowCard** : permet de demander de présenter une sous-carte à l'utilisateur.
* **Action.Submit** : permet de demander de regrouper tous les éléments d'entrée au sein d'un même objet, qui vous est ensuite envoyé via une méthode définie par l'application hôte.

> **Example Action.Submit** : avec Skype, Action.Submit renvoie une activité Bot Framework au bot. La propriété **Value** comporte un objet contenant toutes les données d'entrée.

## <a name="learn-more"></a>En savoir plus

* [Parcourir des exemples de cartes](http://adaptivecards.io/samples/) pour trouver l'inspiration
* Utiliser l'[Explorateur de schémas](http://adaptivecards.io/explorer) pour parcourir les éléments disponibles
* Générer une carte à l'aide du [Visualiseur interactif](http://adaptivecards.io/visualizer/)
* [Nous contacter](http://adaptivecards.io/connect) pour nous faire part de vos commentaires
