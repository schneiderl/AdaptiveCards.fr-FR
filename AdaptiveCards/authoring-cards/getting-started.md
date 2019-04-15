---
title: Prise en main
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9d363da0c10b242e23d2594984292fcc1f31382f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552681"
---
# <a name="getting-started"></a>Prise en main 

Une carte adaptative est un modèle d’objet de carte sérialisé en JSON.

## <a name="adaptive-card-structure"></a>Structure de carte adaptative

La structure de base d’une carte est comme suit :

* `AdaptiveCard` -L’objet racine décrit le AdaptiveCard lui-même, y compris sa composition de l’élément, ses actions, comment il doit être prononcé et la version de schéma requise pour l’afficher.
* `body` : Le corps de la carte est constitué des blocs de construction appelé `elements`. Éléments peuvent être composées dans des dispositions presque illimitées pour créer de nombreux types de cartes. 
* `actions` -Nombre de cartes ont un ensemble d’actions qu'utilisateur peut prendre le dessus. Cette propriété décrit ces actions généralement obtient restituée dans une barre d’action « » en bas.

### <a name="example-card"></a>Carte de l’exemple

Cette carte exemple qui inclut une seule ligne de texte suivie d’une image.

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

Chaque élément a un `type` est la propriété qui identifie quel type d’objet. En examinant la carte ci-dessus, vous pouvez voir nous avons deux éléments, un `TextBlock` et un `Image`.

Tous les éléments de carte adaptative **empilent verticalement** et **développez à la largeur de leur parent** (pensez `display: block` au format HTML). Toutefois, vous pouvez utiliser un `ColumnSet` pour créer des colonnes côte à côte de conteneurs.

## <a name="adaptive-elements"></a>Éléments ADAPTATIF

Les éléments principaux sont :

* **TextBlock** -ajoute un bloc de texte avec des propriétés pour contrôler l’aspect du texte
* **Image** -ajoute une image avec les propriétés qui contrôlent l’aspect de l’image

## <a name="container-elements"></a>Éléments conteneurs

Les cartes peuvent également avoir des conteneurs, qui organisent une collection d’éléments enfants.

* **Conteneur** -définit une collection d’éléments
* **Jeu de colonnes/colonne** -définit une collection de colonnes, chaque colonne est un conteneur
* **FactSet** -conteneur de faits
* **ImageSet** -expérience de galerie pour une collection d’images de photos d’Images de conteneur afin que l’interface utilisateur peut afficher appropriée.

## <a name="input-elements"></a>Éléments d’entrée

Éléments d’entrée vous autorise à demander de l’interface utilisateur native créer des formulaires simples :

* **Input.Text** -obtenir le contenu de texte à partir de l’utilisateur
* **Input.Date** -obtenir une Date de l’utilisateur
* **Input.Time** -obtenir un temps de l’utilisateur
* **Input.Number** -obtenir un nombre à partir de l’utilisateur
* **Input.ChoiceSet** : donner à l’utilisateur un ensemble de choix et demandez-lui de prélèvement
* **Input.Toggle** : donner à l’utilisateur un choix unique entre deux éléments et les sélectionner

## <a name="actions"></a>Actions

Actions ajoutent des boutons à la carte. Il peuvent effectuer diverses actions, telles que l’ouverture d’une URL ou l’envoi des données.

* **Action.OpenUrl** -le bouton ouvre une URL externe pour l’affichage
* **Action.ShowCard** -demande une carte secondaires à afficher à l’utilisateur.
* **Action.Submit** -poser pour tous les éléments d’entrée à collecter dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte pour vous.

> **Exemple Action.Submit**: Avec Skype, un Action.Submit renverra un robot de Bot Framework activité au robot avec le **valeur** propriété contenant un objet avec toutes les données d’entrée sur ce dernier.

## <a name="learn-more"></a>En savoir plus

* [Parcourir les cartes d’exemple](http://adaptivecards.io/samples/) d’inspiration
* Utilisez le [Explorateur de schémas](http://adaptivecards.io/explorer) pour parcourir les éléments disponibles
* Générer une carte à l’aide de la [visualiseur Interactive](http://adaptivecards.io/visualizer/)
* [Nous contacter](http://adaptivecards.io/connect) avec vos commentaires
