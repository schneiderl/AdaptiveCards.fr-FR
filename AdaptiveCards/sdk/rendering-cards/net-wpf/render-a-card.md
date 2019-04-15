---
title: Afficher une carte - Kit de développement logiciel .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 6bc476c79c6d06c7ecb770fb1c3e89eb55e81b9a
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553471"
---
# <a name="render-a-card---net-wpf"></a>Afficher une carte - .NET WPF

Voici comment effectuer le rendu d’une carte à l’aide du SDK de WPF .NET.

> [!NOTE]
> **`Media` avec l’URL HTTPS, ne fonctionneront pas dans WPF**
> 
> Suite à un [bogue dans le contrôle MediaElement de WPF](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) nous ne sommes pas capables de restituer de média pris en charge par le biais de HTTPS. Vous devez utiliser des URL HTTP dans le `Media` élément jusqu'à ce que ce problème soit résolu.  

## <a name="instantiate-a-renderer"></a>Instancier un convertisseur

Créez une instance de la bibliothèque de convertisseur. 

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

## <a name="render-a-card-to-xaml"></a>Afficher une carte pour XAML

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard()
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
    // Or the card exceeded the maxmimum number of supported actions, etc
    IList<AdaptiveWarning> warnings = renderedCard.Warnings;
}
catch(AdaptiveException ex)
{
    // Failed rendering
}
```

