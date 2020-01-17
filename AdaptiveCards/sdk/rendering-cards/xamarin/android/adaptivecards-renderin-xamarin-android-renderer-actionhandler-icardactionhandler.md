---
title: ICardActionHandler, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 8b526ccb66be3a261384d6c4f68a850558e2549e
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146153"
---
# <a name="icardactionhandler"></a><span data-ttu-id="e69eb-102">ICardActionHandler</span><span class="sxs-lookup"><span data-stu-id="e69eb-102">ICardActionHandler</span></span>

```csharp
public interface ICardActionHandler : IJavaObject 
```

<span data-ttu-id="e69eb-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="e69eb-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler
```

### <a name="summary"></a><span data-ttu-id="e69eb-104">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="e69eb-104">Summary</span></span>

| <span data-ttu-id="e69eb-105">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="e69eb-105">Public methods</span></span> | |
| --- | ---- |
| ```abstract void``` | [```OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)```](#onaction) |
| ```abstract void``` | [```OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)```](#onmediaplay) |
| ```abstract void``` | [```OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)```](#onmediastop) |

## <a name="public-methods"></a><span data-ttu-id="e69eb-106">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="e69eb-106">Public Methods</span></span>
--- 
### <a id="onaction"></a><span data-ttu-id="e69eb-107">OnAction</span><span class="sxs-lookup"><span data-stu-id="e69eb-107">OnAction</span></span>
<p style='text-align:right'><span data-ttu-id="e69eb-108">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="e69eb-108">Added in version 0.1.0</span></span></p>

```csharp
void OnAction (BaseActionElement p0, RenderedAdaptiveCard p1)
```

<span data-ttu-id="e69eb-109">Écouteur appelé lorsqu’un clic est effectué sur un OpenUrlAction, SubmitAction ou ShowCardAction (s’il n’est pas Inline).</span><span class="sxs-lookup"><span data-stu-id="e69eb-109">Listener called when a OpenUrlAction, SubmitAction or ShowCardAction (if not inline) are clicked.</span></span>

| <span data-ttu-id="e69eb-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e69eb-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="e69eb-111">P0</span><span class="sxs-lookup"><span data-stu-id="e69eb-111">p0</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElement``` |
| <span data-ttu-id="e69eb-112">p1</span><span class="sxs-lookup"><span data-stu-id="e69eb-112">p1</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) |

#### <a name="sample"></a><span data-ttu-id="e69eb-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="e69eb-113">Sample</span></span>

```csharp
public class MyCardActionHandler : ICardActionHandler
{

    public void OnAction(BaseActionElement element, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = element.ElementType;
        if (actionType == ActionType.Submit)
        {
            var inputs = renderedCard.Inputs;
            string inputValues = string.Empty;
            foreach (var inputString in inputs)
            {
                inputValues += $"{{{inputString.Key} : {inputString.Value}}}\n";
            }
            submitData(inputValues);
        }
        else if (actionType == ActionType.ShowCard)
        {
            var showcardAction = ShowCardAction.Dynamic_cast(element);
            showCard(showcardAction.Card)
        }
        else if (actionType == ActionType.OpenUrl)
        {
            var openUrlAction = OpenUrlAction.Dynamic_cast(element);
            openUrl(openUrlAction.Url);
        }
    }
}
```

---
### <a id="onmediaplay"></a><span data-ttu-id="e69eb-114">OnMediaPlay</span><span class="sxs-lookup"><span data-stu-id="e69eb-114">OnMediaPlay</span></span>
<p style='text-align:right'><span data-ttu-id="e69eb-115">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="e69eb-115">Added in version 0.1</span></span></p>

```csharp
void OnMediaPlay (BaseCardElement p0, RenderedAdaptiveCard p1)
```

<span data-ttu-id="e69eb-116">Écouteur appelé lorsque l’élément multimédia commence à être lu.</span><span class="sxs-lookup"><span data-stu-id="e69eb-116">Listener called when the media element starts playing.</span></span>

| <span data-ttu-id="e69eb-117">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e69eb-117">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="e69eb-118">P0</span><span class="sxs-lookup"><span data-stu-id="e69eb-118">p0</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement``` |
| <span data-ttu-id="e69eb-119">p1</span><span class="sxs-lookup"><span data-stu-id="e69eb-119">p1</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) |

#### <a name="sample"></a><span data-ttu-id="e69eb-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="e69eb-120">Sample</span></span>

```csharp
public class MyCardActionHandler : ICardActionHandler
{
    public void OnMediaPlay(BaseCardElement element, RenderedAdaptiveCard renderedCard)
    {
    }
}
```

--- 

### <a id="onmediastop"></a><span data-ttu-id="e69eb-121">OnMediaStop</span><span class="sxs-lookup"><span data-stu-id="e69eb-121">OnMediaStop</span></span>
<p style='text-align:right'><span data-ttu-id="e69eb-122">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="e69eb-122">Added in version 0.1</span></span></p>

```csharp
void OnMediaStop (BaseCardElement p0, RenderedAdaptiveCard p1)
```

<span data-ttu-id="e69eb-123">Écouteur appelé lorsque l’élément multimédia cesse de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="e69eb-123">Listener called when the media element stops playing.</span></span>

| <span data-ttu-id="e69eb-124">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e69eb-124">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="e69eb-125">P0</span><span class="sxs-lookup"><span data-stu-id="e69eb-125">p0</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElement``` |
| <span data-ttu-id="e69eb-126">p1</span><span class="sxs-lookup"><span data-stu-id="e69eb-126">p1</span></span> | [```AdaptiveCards.Rendering.Xamarin.Android.Renderer.RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md) |

#### <a name="sample"></a><span data-ttu-id="e69eb-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="e69eb-127">Sample</span></span>

```csharp
public class MyCardActionHandler : ICardActionHandler
{
    public void OnMediaStop(BaseCardElement element, RenderedAdaptiveCard renderedCard)
    {
    }
}
```