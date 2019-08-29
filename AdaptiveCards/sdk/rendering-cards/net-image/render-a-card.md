---
title: Rendu d’une carte-SDK de rendu d’image .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ae32007d75abe4fb452ee48e32dd4e9bea8dfa4f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552491"
---
# <a name="render-a-card---net-image"></a>Rendre une carte-image .NET

Voici comment afficher une carte à l’aide du kit de développement logiciel (SDK) d’image .NET.

```csharp
try
{
    // A URL that returns an Adaptive Card JSON payload
    var cardUrl = "http://adaptivecards.io/payloads/ActivityUpdate.json";

    // Timeout after 30 seconds
    var cts = new CancellationTokenSource(TimeSpan.FromSeconds(30));

    // Get the JSON from the card URL
    var client = new HttpClient();
    var response = await client.GetAsync(cardUrl, cts.Token);
    var json = await response.Content.ReadAsStringAsync();

    // Parse the Adaptive Card JSON
    AdaptiveCardParseResult parseResult = AdaptiveCard.FromJson(json);
    AdaptiveCard card = parseResult.Card;

    // Create a host config with no interactivity 
    // (buttons in images would be deceiving)
    AdaptiveHostConfig hostConfig = new AdaptiveHostConfig()
    {
        SupportsInteractivity = false
    };

    // Create a renderer
    AdaptiveCardRenderer renderer = new AdaptiveCardRenderer(hostConfig);

    // Set any XAML resource Dictionary if you have one
    //renderer.ResourcesPath = <path-to-your-resourcedictionary.xaml>;

    // Render the card to png
    // Set createStaThread to true if running from a server
    RenderedAdaptiveCardImage renderedCard =
        await renderer.RenderCardToImageAsync(card, createStaThread: true, cancellationToken: cts.Token);
}
catch (OperationCanceledException)
{
    // Timed out
}
catch (Exception ex)
{
    // Log failure
}
```