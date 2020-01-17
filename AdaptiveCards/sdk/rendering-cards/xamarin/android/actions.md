---
title: Actions-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 6175bd4dc0709cc808a92e42f1b87d9a5f74ba0c
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146073"
---
# <a name="actions---xamarinandroid"></a><span data-ttu-id="aec90-102">Actions-Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="aec90-102">Actions - Xamarin.Android</span></span>

<span data-ttu-id="aec90-103">Lorsqu’une action de cartes est exécutée, la classe qui a été passée à l’appel de rendu qui implémente l’interface [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) est appelée.</span><span class="sxs-lookup"><span data-stu-id="aec90-103">When a cards action is executed, the class that was passed to the render call that implements the [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) interface gets invoked.</span></span> <span data-ttu-id="aec90-104">Voici comment définir votre gestionnaire d’actions :</span><span class="sxs-lookup"><span data-stu-id="aec90-104">Here is how to define your action handler:</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;

// ...

public class CardActionHandlerImpl : ICardActionHandler
{

    public void OnAction(BaseActionElement element, RenderedAdaptiveCard renderedCard)
    {
        ActionType actionType = element.ElementType;
        if (actionType == ActionType.Submit)
        {
            var submitAction = SubmitAction.Dynamic_cast(element);
            var data = submitAction.DataJson;
            Toast.MakeText(this, data + "\n" + inputValues, ToastLength.Short).Show();
        }
        else if (actionType == ActionType.ShowCard)
        {           
            showCard(card);
        }
        else if (actionType == ActionType.OpenUrl)
        {
            openUrl(url);
        }
    }

    public void OnMediaPlay(BaseCardElement element, RenderedAdaptiveCard renderedCard) { }

    public void OnMediaStop(BaseCardElement element, RenderedAdaptiveCard renderedCard) { }
}
```
