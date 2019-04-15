---
title: État de convertisseur
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 303d5675f58bd2c870dcdf5718d508d2e3c78fca
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553351"
---
# <a name="renderer-status"></a>État de convertisseur
Les tableaux suivants indiquent l’état actuel de chaque convertisseur, en fonction de leurs versions publiées publiques.

### <a name="parsing"></a>L’analyse

|Fonctionnalité | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Retournent des erreurs de validation | ✅ | ✅ | ✅ | ✅ | ✅ |
|Analyser les propriétés inconnues | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Rendu de la carte

|Fonctionnalité | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Recherchez la version prise en charge | ✅ | ✅ | ✅ | ✅ | ✅  |
|Afficher le schéma complet | ✅ | ✅ | ✅ | ✅ | ✅ |
|Afficher la barre d’actions | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ignorer des éléments inconnus | ✅ | ✅ | ✅ | ✅ | ✅ |
|Prise en charge de la configuration hôte | ✅ | ✅ | ✅ | ✅ | ✅ |
|Style de la plateforme native | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="element-rendering"></a>Rendu de l’élément

|Fonctionnalité | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|L’espacement et le séparateur | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Format DATE/heure TextBlock](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Prise en charge Markdown de TextBlock](../authoring-cards/text-features.md#markdown) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Prise en charge de l’ensemble de l’entrée | ✅ | ✅ | ✅ | ✅ | ✅ |

\* Prise en charge intégrée de Markdown n’inclut pas le convertisseur HTML afin de réduire la taille de la bibliothèque et pour permettre à applications consommatrices d’utiliser leur processeur Markdown par défaut. Le convertisseur HTML toutefois utiliseront automatiquement Markdown-informatique s’il est chargé.

### <a name="extensbility"></a>Extensbility

|Fonctionnalité | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Remplacer le convertisseur d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ajouter nouveau convertisseur d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|Supprimer l’élément convertisseur | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Convertisseur d’Action de remplacement/ajouter/supprimer](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ❌ | ✅ | ✅ |

### <a name="actions"></a>Actions

| Fonctionnalité | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Prise en charge Action.OpenUrl | ✅ | ✅ | ✅ | ✅ | ✅  |
| Prise en charge Action.ShowCard  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Prise en charge Action.Submit  | ✅ | ✅ | ✅ | ✅ | ✅  |
| prise en charge selectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Événements

|       Fonctionnalité        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Visibilité de l’élément modifiée |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

