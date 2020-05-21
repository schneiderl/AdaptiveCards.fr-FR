---
title: Effectuer le rendu d’une carte – Kit de développement logiciel (SDK) HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 3ecc0e3bc30c8750cbe40dbf94946ab604b492ce
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631330"
---
# <a name="render-a-card---net-html"></a><span data-ttu-id="bcb19-102">Effectuer le rendu d’une carte – HTML .NET</span><span class="sxs-lookup"><span data-stu-id="bcb19-102">Render a card - .NET HTML</span></span>

<span data-ttu-id="bcb19-103">Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel (SDK) HTML .NET.</span><span class="sxs-lookup"><span data-stu-id="bcb19-103">Here's how to render a card using the .NET HTML SDK.</span></span>

## <a name="instantiate-a-renderer"></a><span data-ttu-id="bcb19-104">Instancier un convertisseur</span><span class="sxs-lookup"><span data-stu-id="bcb19-104">Instantiate a renderer</span></span>

<span data-ttu-id="bcb19-105">L’étape suivante consiste à créer une instance du convertisseur.</span><span class="sxs-lookup"><span data-stu-id="bcb19-105">The next step is to create an instance of the renderer.</span></span> 

```csharp
using AdaptiveCards;
using AdaptiveCards.Rendering;
using AdaptiveCards.Rendering.Html;
// ... 

// Create a card renderer
AdaptiveCardRenderer renderer = new AdaptiveCardRenderer();

// For fun, check the schema version this renderer supports
AdaptiveSchemaVersion schemaVersion = renderer.SupportedSchemaVersion; // 1.0
```

## <a name="render-a-card-to-html"></a><span data-ttu-id="bcb19-106">Effectuer le rendu d’une carte au format HTML</span><span class="sxs-lookup"><span data-stu-id="bcb19-106">Render a card to HTML</span></span>

```csharp
// Build a simple card
// In the real world this would probably be provided as JSON
AdaptiveCard card = new AdaptiveCard(renderer.SupportedSchemaVersion)
{
    Body = { new AdaptiveTextBlock() { Text = "Hello World" } }
};

try
{
    // Render the card
    RenderedAdaptiveCard renderedCard = renderer.RenderCard(card);

    // Get the output HTML 
    HtmlTag html = renderedCard.Html;

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
