---
title: Actions-Kit de développement logiciel (SDK) UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 98b4374ce6a31d6d7ec2416d3b4e451ef1c59d1b
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454102"
---
# <a name="actions---uwp"></a><span data-ttu-id="8ca5b-102">Actions-UWP</span><span class="sxs-lookup"><span data-stu-id="8ca5b-102">Actions - UWP</span></span>

<span data-ttu-id="8ca5b-103">Toutes les **actions** de la carte s’affichent en tant que **bouton**UWP, mais c’est à votre application de gérer ce qui se passe quand un utilisateur clique dessus (à l’exception des actions ShowCard... Pour plus d’informations, consultez l’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="8ca5b-103">Any **actions** within the card will render as UWP **Button**'s, but it's up to your app to handle what happens when a user presses them (except for ShowCard actions... see code snippet for more info).</span></span>

<span data-ttu-id="8ca5b-104">L’objet `RenderedAdaptiveCard` fournit un événement `Action` à cette fin.</span><span class="sxs-lookup"><span data-stu-id="8ca5b-104">The `RenderedAdaptiveCard` object provides an `Action` event for this purpose.</span></span>

```csharp
// Render a card (as previously shown)
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// ...

// Attach the event handler for action click events
renderedAdaptiveCard.Action += RenderedAdaptiveCard_Action;

private async void RenderedAdaptiveCard_Action(RenderedAdaptiveCard sender, AdaptiveActionEventArgs args)
{
    if (args.Action is AdaptiveOpenUrlAction openUrlAction)
    {
        await Launcher.LaunchUriAsync(openUrlAction.Url);
    }

    else if (args.Action is AdaptiveShowCardAction showCardAction)
    {
        // This is only fired if, in HostConfig, you set the ShowCard ActionMode to Popup.
        // Otherwise, the renderer will automatically display the card inline without firing this event.
    }

    else if (args.Action is AdaptiveSubmitAction submitAction)
    {
        // Get the data and inputs
        string data = submitAction.DataJson.Stringify();
        string inputs = args.Inputs.AsJson().Stringify();

        // Process them as desired
    }
}
```
