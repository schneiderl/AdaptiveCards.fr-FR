---
title: Actions - SDK UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: d1d3410b19071f601b31e14882f2cccb4d1e6ccb
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552971"
---
# <a name="actions---uwp"></a><span data-ttu-id="36ca1-102">Actions - UWP</span><span class="sxs-lookup"><span data-stu-id="36ca1-102">Actions - UWP</span></span>

<span data-ttu-id="36ca1-103">N’importe quel **actions** au sein de la carte s’affiche en tant que UWP **bouton**de, mais c’est à votre application à gérer que se passe-t-il quand un utilisateur appuie dessus (à l’exception des actions ShowCard... Voir extrait de code pour plus d’informations).</span><span class="sxs-lookup"><span data-stu-id="36ca1-103">Any **actions** within the card will render as UWP **Button**'s, but it's up to your app to handle what happens when a user presses them (except for ShowCard actions... see code snippet for more info).</span></span>

<span data-ttu-id="36ca1-104">Le `RenderedAdaptiveCard` objet fournit une `Action` événement à cet effet.</span><span class="sxs-lookup"><span data-stu-id="36ca1-104">The `RenderedAdaptiveCard` object provides an `Action` event for this purpose.</span></span>

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
