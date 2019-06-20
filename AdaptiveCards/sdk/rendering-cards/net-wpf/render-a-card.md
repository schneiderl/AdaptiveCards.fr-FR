---
title: Effectuer le rendu d’une carte – Kit de développement logiciel (SDK) WPF .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f847b83a17456dbf80f869ef8ef0df699e57f50e
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134299"
---
# <a name="render-a-card---net-wpf"></a>Effectuer le rendu d’une carte – WPF .NET

Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel (SDK) WPF .NET.

> [!NOTE]
> **`Media` avec des URL HTTPS ne fonctionne pas en WPF**
> 
> Suite à un [bogue dans le contrôle WPF MediaElement](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception), nous ne pouvons pas effectuer le rendu d’éléments multimédias servis via HTTPS. En attendant ce que ce problème soit résolu, vous devez utiliser des URL HTTP dans l’élément `Media`.  

## <a name="instantiate-a-renderer"></a>Instancier un convertisseur

Créez une instance de la bibliothèque du convertisseur. 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Wpf;
// ...

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// If using the Xceed package, enable the enhanced input
renderer.UseXceedElementRenderers();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion;
```

## <a name="render-a-card-to-xaml"></a>Effectuer le rendu d’une carte au format XAML

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard("1.0")
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the FrameworkElement
    // Add this to your app's UI somewhere
    FrameworkElement fe = renderedCard.FrameworkElement;

    // (Optional) Check for any renderer warnings
    // This includes things like an unknown element type found in the card
    // Or the card exceeded the maximum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```

