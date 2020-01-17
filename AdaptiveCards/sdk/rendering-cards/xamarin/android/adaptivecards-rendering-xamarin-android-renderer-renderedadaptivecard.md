---
title: RenderedAdaptiveCard, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 608b28638ce6ed0a218cfc8dbbe73f22de1ab8cb
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145993"
---
# <a name="renderedadaptivecard"></a>RenderedAdaptiveCard

```csharp
public class RenderedAdaptiveCard : Java.Lang.Object
```

**Namespace**

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a>Récapitulatif

| Attributes | |
| ---- | --- |
| AdaptiveCard | Représentation logique de la carte adaptative rendue. |
| Entrées | Dictionnaire de l’élément d’entrée et des informations ajoutées par l’utilisateur. |
| Affichage | Résultat visuel du processus de rendu. |
| Avertissements | Liste des avertissements générés à partir du processus de rendu. |

&nbsp;

| Méthodes publiques | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](#addwarning) |

## <a name="public-methods"></a>Méthodes publiques

---

### <a id="addwarning"></a>AddWarning
<p style='text-align:right'>Ajouté dans la version 0,1</p>

```csharp
public void AddWarning (AdaptiveWarning warning)

```

Ajoute un avertissement à la liste d’avertissements.

| Paramètres | |
| --- | --- |
| avertissement | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning``` |
