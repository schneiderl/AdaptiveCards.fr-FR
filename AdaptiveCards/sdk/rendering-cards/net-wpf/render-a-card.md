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
# <a name="render-a-card---net-wpf"></a><span data-ttu-id="7b783-102">Afficher une carte - .NET WPF</span><span class="sxs-lookup"><span data-stu-id="7b783-102">Render a card - .NET WPF</span></span>

<span data-ttu-id="7b783-103">Voici comment effectuer le rendu d’une carte à l’aide du SDK de WPF .NET.</span><span class="sxs-lookup"><span data-stu-id="7b783-103">Here's how to render a card using the .NET WPF SDK.</span></span>

> [!NOTE]
> <span data-ttu-id="7b783-104">**`Media` avec l’URL HTTPS, ne fonctionneront pas dans WPF**</span><span class="sxs-lookup"><span data-stu-id="7b783-104">**`Media` with HTTPS URLs will not work in WPF**</span></span>
> 
> <span data-ttu-id="7b783-105">Suite à un [bogue dans le contrôle MediaElement de WPF](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) nous ne sommes pas capables de restituer de média pris en charge par le biais de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7b783-105">Due to a [bug in the WPF MediaElement control](https://stackoverflow.com/questions/30702505/playing-media-from-https-site-in-media-element-throwing-null-reference-exception) we aren't able to render media that is served via HTTPS.</span></span> <span data-ttu-id="7b783-106">Vous devez utiliser des URL HTTP dans le `Media` élément jusqu'à ce que ce problème soit résolu.</span><span class="sxs-lookup"><span data-stu-id="7b783-106">You should use HTTP URLs in the `Media` element until this is addressed.</span></span>  

## <a name="instantiate-a-renderer"></a><span data-ttu-id="7b783-107">Instancier un convertisseur</span><span class="sxs-lookup"><span data-stu-id="7b783-107">Instantiate a renderer</span></span>

<span data-ttu-id="7b783-108">Créez une instance de la bibliothèque de convertisseur.</span><span class="sxs-lookup"><span data-stu-id="7b783-108">Create an instance of the renderer library.</span></span> 

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

## <a name="render-a-card-to-xaml"></a><span data-ttu-id="7b783-109">Afficher une carte pour XAML</span><span class="sxs-lookup"><span data-stu-id="7b783-109">Render a card to XAML</span></span>

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

