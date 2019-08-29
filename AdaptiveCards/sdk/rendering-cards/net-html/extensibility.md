---
title: Extensibilité-Kit de développement logiciel (SDK) HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5aedc2b0bb19cb7a26caa16c8490d0d2f3c93282
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552531"
---
# <a name="extensibility---net-html"></a>Extensibilité-.NET HTML

## <a name="custom-element-rendering"></a>Rendu d’élément personnalisé

Pour un contrôle total du convertisseur, vous pouvez utiliser la propriété `ElementRenderers` pour **ajouter**, **supprimer** ou **remplacer** les convertisseurs par défaut.

L’exemple suivant montre comment définir un élément `"type": "Rating"` personnalisé et en effectuer le rendu.

```csharp
// Register the new type with the JSON parser
AdaptiveTypedElementConverter.RegisterTypedElement<MyCustomRating>();

// Add the new type to the element renderer registry
renderer.ElementRenderers.Set<MyCustomRating>(MyCustomRating.Render);

// Define a custom Rating element type
public class MyCustomRating : AdaptiveElement
{
    public override string Type => "Rating";

    public double Rating { get; set; }

    public AdaptiveTextSize Size { get; set; }

    public AdaptiveTextColor Color { get; set; }

    public static FrameworkElement Render(MyCustomRating rating, AdaptiveRenderContext context)
    {
        var textBlock = new AdaptiveTextBlock
        {
            Size = rating.Size,
            Color = rating.Color
        };
        for (int i = 0; i < rating.Rating; i++)
        {
            textBlock.Text += "\u2605";
        }
        textBlock.Text += $" ({rating.Rating})";
        return context.Render(textBlock);
    }
}
```
