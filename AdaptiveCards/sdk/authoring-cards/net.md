---
title: SDK .NET pour des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 37dec7651a574194eb00d46014431dfb5764f9b7
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553741"
---
# <a name="net-sdk-for-authoring-cards"></a>Kit de développement logiciel .NET pour la création de cartes

Comme décrit dans la [mise en route](../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle d’objet JSON. La bibliothèque .NET facilite beaucoup l’utilisation avec ce code JSON.

> [!IMPORTANT]
> **Dernières modifications issues des v0.5**
> 
> 1. Package renommé à partir de `Microsoft.AdaptiveCards` à `AdaptiveCards`
> 1. En raison de collisions de nom fréquentes de types de framework, toutes les classes de modèle ont le préfixe « Adaptive ». Par exemple, `TextBlock` est maintenant `AdaptiveTextBlock`
> 1. Toutes les propriétés « uri » ont été modifiées à partir du type `string` à `Uri`
> 1. Ont également été certaines modifications du schéma à partir de la version préliminaire v0.5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)


## <a name="nuget-install"></a>Installation de NuGet
Le `AdaptiveCards` package NuGet fournit des types pour travailler avec des cartes adaptatives dans .NET

[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a>Exemple : Créer un AdaptiveCard et sérialiser au format JSON

Cet exemple montre comment créer une carte adaptative à l’aide de la norme C# objets et puis les sérialise au format JSON pour le transport sur le réseau.

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard();

card.Body.Add(new AdaptiveTextBlock() 
{
    Text = "Hello",
    Size = AdaptiveTextSize.ExtraLarge
});

card.Body.Add(new AdaptiveImage() 
{
    Url = new Uri("http://adaptivecards.io/content/cats/1.png")
});

// serialize the card to JSON
string json = card.ToJson();
```

## <a name="example-parse-an-adaptivecard-from-json"></a>Exemple : Analyser un AdaptiveCard à partir de JSON

Cet exemple montre comment analyser une charge utile JSON dans une carte adaptative. Cela rend plus facile à manipuler le modèle objet ou même de rendre des cartes adaptatives à l’intérieur de votre application à l’aide de notre [convertisseur kits de développement logiciel](../../rendering-cards/getting-started.md).

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient("http://adaptivecards.io/payloads/ActivityUpdate.json");
    var response = await client.GetAsync(cardUrl);
    var json = await response.Content.ReadAsStringAsync();

    // Parse the JSON 
    AdaptiveCardParseResult result = AdaptiveCard.FromJson(json);

    // Get card from result
    AdaptiveCard card = result.Card;

    // Optional: check for any parse warnings
    // This includes things like unknown element "type"
    // or unknown properties on element
    IList<AdaptiveWarning> warnings = result.Warnings;
}
catch(AdaptiveSerializationException ex)
{
    // Failed to deserialize card 
    // This occurs from malformed JSON
    // or schema violations like required properties missing 
}
```
