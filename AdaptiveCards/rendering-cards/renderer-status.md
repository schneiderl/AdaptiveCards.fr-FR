---
title: État du rendu
author: matthidinger
ms.author: mahiding
ms.date: 10/12/2018
ms.topic: article
ms.openlocfilehash: 2b4f9d9ab376839a309a312e9846c45b0fc6cdff
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001796"
---
# <a name="renderer-status"></a>État du rendu
Les tableaux ci-dessous indiquent l’état actuel de chaque renderer, en fonction de leurs versions publiées publiques.

### <a name="parsing"></a>Analyse

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Retourner les échecs de validation | ✅ | ✅ | ✅ | ✅ | ✅ |
|Analyser les propriétés inconnues | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="card-rendering"></a>Rendu de la carte

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Vérifier la version prise en charge | ✅ | ✅ | ✅ | ✅ | ✅  |
|Afficher le schéma complet | ✅ | ✅ | ✅ | ✅ | ✅ |
|Afficher la barre d’actions | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ignorer les éléments inconnus | ✅ | ✅ | ✅ | ✅ | ✅ |
|Prise en charge de la configuration de l’hôte | ✅ | ✅ | ✅ | ✅ | ✅ |
|Style de plateforme native | ✅ | ✅ | ✅ | ✅ | ❌ |

### <a name="element-rendering"></a>Rendu d’élément

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Espacement et séparateur | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Format de DATE/HEURE TextBlock](../authoring-cards/text-features.md#datetime-formatting-and-localization) | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Prise en charge du Markdown TextBlock](../authoring-cards/text-features.md#markdown-commonmark-subset) | ✅* | ✅ | ✅ | ✅ | ✅ |
|Validation et étiquettes d’entrées | ❌ | ✅ | ✅ | ✅ | ✅ |

\* Le renderer HTML n’inclut pas la prise en charge intégrée du Markdown, afin de réduire la taille de la bibliothèque et de permettre aux applications consommatrices d’utiliser leur processeur Markdown par défaut. En revanche, le renderer HTML utilise automatiquement Markdown-It s’il est chargé.

### <a name="extensibility"></a>Extensibilité

|Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
|Remplacer le renderer d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|Ajouter un nouveau renderer d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|Supprimer le renderer d’élément | ✅ | ✅ | ✅ | ✅ | ✅ |
|[Remplacer/ajouter/supprimer le renderer d’action](https://github.com/Microsoft/AdaptiveCards/issues/1671) | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="actions"></a>Actions

| Fonctionnalités | HTML | .NET | UWP | iOS | Android |
|--- | --- | --- | --- | --- | --- | --- |
| Prise en charge d’Action.OpenUrl | ✅ | ✅ | ✅ | ✅ | ✅  |
| Prise en charge d’Action.ShowCard  | ✅ | ✅ | ✅ | ✅ | ✅ |
| Prise en charge d’Action.Submit  | ✅ | ✅ | ✅ | ✅ | ✅  |
| Prise en charge de selectAction | ✅ | ✅ | ✅ | ✅ | ✅ |

### <a name="events"></a>Événements

|       Fonctionnalités        | HTML | .NET | UWP | iOS | Android | 
|----------------------------|------|------|-----|-----|---------|
| Visibilité de l’élément modifiée |  ✅   |  ❌   |  ❌  |  ❌  | ❌ |

