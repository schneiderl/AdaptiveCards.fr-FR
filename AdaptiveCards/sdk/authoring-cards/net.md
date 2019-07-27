---
title: Kit de développement logiciel (SDK) .NET pour cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: fb1a79da288cbce77c4f684b384982feb96e7a8c
ms.sourcegitcommit: f8de9c02b92cd8927a18e59e5650c92b2b78db06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523848"
---
# <a name="net-sdk-for-authoring-cards"></a>Kit de développement logiciel (SDK) .NET pour la création de cartes

Comme nous l’avons décrit dans la page [prise en main](../../authoring-cards/getting-started.md) , une carte adaptative est un modèle d’objet JSON. La bibliothèque .NET facilite grandement l’utilisation de ce JSON.


## <a name="nuget-install"></a>Installation de NuGet
Le `AdaptiveCards` package NuGet fournit des types pour l’utilisation des cartes adaptatives dans .net

[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)

```console
Install-Package AdaptiveCards
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a>Exemple : Créer un AdaptiveCard et le sérialiser en JSON

Cet exemple montre comment créer une carte adaptative à l’aide d' C# objets standard, puis la sérialiser au format JSON pour le transport sur le réseau.

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

Cet exemple montre comment analyser une charge utile JSON dans une carte adaptative. Cela facilite la manipulation du modèle d’objet, voire le rendu des cartes adaptatives dans votre application à l’aide de nos [Kits de développement](../../rendering-cards/getting-started.md)logiciel (SDK) de convertisseur.

```csharp
try
{
    // Get a JSON-serialized payload
    // Your app will probably get cards from somewhere else :)
    var client = new HttpClient();
    var response = await client.GetAsync("http://adaptivecards.io/payloads/ActivityUpdate.json");
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
