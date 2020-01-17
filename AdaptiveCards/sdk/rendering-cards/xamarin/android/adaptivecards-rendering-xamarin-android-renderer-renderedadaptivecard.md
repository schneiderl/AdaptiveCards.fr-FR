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
# <a name="renderedadaptivecard"></a><span data-ttu-id="7ce1e-102">RenderedAdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="7ce1e-102">RenderedAdaptiveCard</span></span>

```csharp
public class RenderedAdaptiveCard : Java.Lang.Object
```

<span data-ttu-id="7ce1e-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="7ce1e-103">**Namespace**</span></span>

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a><span data-ttu-id="7ce1e-104">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="7ce1e-104">Summary</span></span>

| <span data-ttu-id="7ce1e-105">Attributes</span><span class="sxs-lookup"><span data-stu-id="7ce1e-105">Attributes</span></span> | |
| ---- | --- |
| <span data-ttu-id="7ce1e-106">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="7ce1e-106">AdaptiveCard</span></span> | <span data-ttu-id="7ce1e-107">Représentation logique de la carte adaptative rendue.</span><span class="sxs-lookup"><span data-stu-id="7ce1e-107">Logical representation of the rendered adaptive card.</span></span> |
| <span data-ttu-id="7ce1e-108">Entrées</span><span class="sxs-lookup"><span data-stu-id="7ce1e-108">Inputs</span></span> | <span data-ttu-id="7ce1e-109">Dictionnaire de l’élément d’entrée et des informations ajoutées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7ce1e-109">Dictionary of input element and information added by the user.</span></span> |
| <span data-ttu-id="7ce1e-110">Affichage</span><span class="sxs-lookup"><span data-stu-id="7ce1e-110">View</span></span> | <span data-ttu-id="7ce1e-111">Résultat visuel du processus de rendu.</span><span class="sxs-lookup"><span data-stu-id="7ce1e-111">Visual result from the rendering process.</span></span> |
| <span data-ttu-id="7ce1e-112">Avertissements</span><span class="sxs-lookup"><span data-stu-id="7ce1e-112">Warnings</span></span> | <span data-ttu-id="7ce1e-113">Liste des avertissements générés à partir du processus de rendu.</span><span class="sxs-lookup"><span data-stu-id="7ce1e-113">List of warnings produced from the rendering process.</span></span> |

&nbsp;

| <span data-ttu-id="7ce1e-114">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="7ce1e-114">Public methods</span></span> | |
| --- | ---- |
| ```void``` | [```AddWarning AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning warning)```](#addwarning) |

## <a name="public-methods"></a><span data-ttu-id="7ce1e-115">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="7ce1e-115">Public Methods</span></span>

---

### <a id="addwarning"></a><span data-ttu-id="7ce1e-116">AddWarning</span><span class="sxs-lookup"><span data-stu-id="7ce1e-116">AddWarning</span></span>
<p style='text-align:right'><span data-ttu-id="7ce1e-117">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="7ce1e-117">Added in version 0.1</span></span></p>

```csharp
public void AddWarning (AdaptiveWarning warning)

```

<span data-ttu-id="7ce1e-118">Ajoute un avertissement à la liste d’avertissements.</span><span class="sxs-lookup"><span data-stu-id="7ce1e-118">Adds a warning to the warning list.</span></span>

| <span data-ttu-id="7ce1e-119">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ce1e-119">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="7ce1e-120">avertissement</span><span class="sxs-lookup"><span data-stu-id="7ce1e-120">warning</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.Renderer.AdaptiveWarning``` |
