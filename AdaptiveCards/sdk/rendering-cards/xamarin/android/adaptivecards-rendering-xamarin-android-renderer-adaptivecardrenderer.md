---
title: AdaptiveCardRenderer, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: c90fb22f60fa75a37b6372c2660f8599535fd961
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146063"
---
# <a name="adaptivecardrenderer"></a><span data-ttu-id="fc3a3-102">AdaptiveCardRenderer</span><span class="sxs-lookup"><span data-stu-id="fc3a3-102">AdaptiveCardRenderer</span></span>

```csharp
public class AdaptiveCardRenderer : global::Java.Lang.Object
```

<span data-ttu-id="fc3a3-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="fc3a3-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer
```

### <a name="summary"></a><span data-ttu-id="fc3a3-104">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="fc3a3-104">Summary</span></span>

| <span data-ttu-id="fc3a3-105">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="fc3a3-105">Public methods</span></span> | |
| --- | ---- |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler)```](#render0) |
| ```RenderedAdaptiveCard``` | [```Render (Context context, FragmentManager fragmentManager, AdaptiveCard adaptiveCard, ICardActionHandler cardActionHandler, HostConfig hostConfig)```](#render1) |

## <a name="public-methods"></a><span data-ttu-id="fc3a3-106">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="fc3a3-106">Public Methods</span></span>

---

### <a id="render0"></a><span data-ttu-id="fc3a3-107">Crée</span><span class="sxs-lookup"><span data-stu-id="fc3a3-107">Render</span></span>
<p style='text-align:right'><span data-ttu-id="fc3a3-108">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="fc3a3-108">Added in version 0.1.0</span></span></p>

```csharp
public RenderedAdaptiveCard Render (Context context, 
                                    FragmentManager fragmentManager, 
                                    AdaptiveCard adaptiveCard,
                                    ICardActionHandler cardActionHandler)
```

<span data-ttu-id="fc3a3-109">Génère le rendu de la carte adaptative spécifiée avec les valeurs par défaut pour la configuration de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-109">Renders the specified adaptive card with default values for the host config.</span></span>

| <span data-ttu-id="fc3a3-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc3a3-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="fc3a3-111">context</span><span class="sxs-lookup"><span data-stu-id="fc3a3-111">context</span></span> | ```Android.Content.Context``` |
| <span data-ttu-id="fc3a3-112">fragmentManager</span><span class="sxs-lookup"><span data-stu-id="fc3a3-112">fragmentManager</span></span> | ```Android.Support.V4.App.FragmentManager``` |
| <span data-ttu-id="fc3a3-113">adaptiveCard</span><span class="sxs-lookup"><span data-stu-id="fc3a3-113">adaptiveCard</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md) |
| <span data-ttu-id="fc3a3-114">cardActionHandler</span><span class="sxs-lookup"><span data-stu-id="fc3a3-114">cardActionHandler</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) |

| <span data-ttu-id="fc3a3-115">Returns</span><span class="sxs-lookup"><span data-stu-id="fc3a3-115">Returns</span></span> |
| --- | --- |
| [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) | |

#### <a name="sample"></a><span data-ttu-id="fc3a3-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="fc3a3-116">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler);
```

---

### <a id="render1"></a><span data-ttu-id="fc3a3-117">Crée</span><span class="sxs-lookup"><span data-stu-id="fc3a3-117">Render</span></span>
<p style='text-align:right'><span data-ttu-id="fc3a3-118">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="fc3a3-118">Added in version 0.1.0</span></span></p>

```csharp
RenderedAdaptiveCard Render (Context context, 
                            FragmentManager fragmentManager, 
                            AdaptiveCard adaptiveCard, 
                            ICardActionHandler cardActionHandler, 
                            HostConfig hostConfig)
```

<span data-ttu-id="fc3a3-119">Génère le rendu de la carte adaptative spécifiée à l’aide de la configuration d’hôte donnée.</span><span class="sxs-lookup"><span data-stu-id="fc3a3-119">Renders the specified adaptive card with using the given host config.</span></span>

| <span data-ttu-id="fc3a3-120">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc3a3-120">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="fc3a3-121">context</span><span class="sxs-lookup"><span data-stu-id="fc3a3-121">context</span></span> | ```Android.Content.Context``` |
| <span data-ttu-id="fc3a3-122">fragmentManager</span><span class="sxs-lookup"><span data-stu-id="fc3a3-122">fragmentManager</span></span> | ```Android.Support.V4.App.FragmentManager``` |
| <span data-ttu-id="fc3a3-123">adaptiveCard</span><span class="sxs-lookup"><span data-stu-id="fc3a3-123">adaptiveCard</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md) |
| <span data-ttu-id="fc3a3-124">cardActionHandler</span><span class="sxs-lookup"><span data-stu-id="fc3a3-124">cardActionHandler</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler.ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) |
| <span data-ttu-id="fc3a3-125">hostConfig</span><span class="sxs-lookup"><span data-stu-id="fc3a3-125">hostConfig</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HostConfig``` |

| <span data-ttu-id="fc3a3-126">Returns</span><span class="sxs-lookup"><span data-stu-id="fc3a3-126">Returns</span></span> | |
| --- | --- |
| [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) | |

#### <a name="sample"></a><span data-ttu-id="fc3a3-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="fc3a3-127">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.Instance.Render(context, SupportFragmentManager, parseResult.AdaptiveCard, cardActionHandler, hostConfig);
```