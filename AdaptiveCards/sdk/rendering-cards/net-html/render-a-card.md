---
title: Afficher une carte - Kit de développement logiciel .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 8dc1baffb91f0755f1955ee02b8a3e820b0d34e4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553101"
---
# <a name="render-a-card---net-html"></a>Afficher une carte - HTML de .NET

Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel .NET HTML.

## <a name="instantiate-a-renderer"></a>Instancier un convertisseur

L’étape suivante consiste à créer une instance du convertisseur. 

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

## <a name="render-a-card-to-html"></a>Afficher une carte au format HTML

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

    // Get the output HTML 
    HtmlTag html = renderedCard.Html;

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
