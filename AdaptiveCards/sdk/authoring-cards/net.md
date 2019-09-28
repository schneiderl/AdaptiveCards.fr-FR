---
title: Kit de développement logiciel (SDK) .NET pour cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: 10400d5db3aac8ea60e5f03f5ab5d9b013211954
ms.sourcegitcommit: 4dd40521cd39313657f1dab642f49ff04098ba35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71343736"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="6c9fa-102">Kit de développement logiciel (SDK) .NET pour la création de cartes</span><span class="sxs-lookup"><span data-stu-id="6c9fa-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="6c9fa-103">Comme nous l’avons décrit dans la page [prise en main](../../authoring-cards/getting-started.md) , une carte adaptative est un modèle d’objet JSON.</span><span class="sxs-lookup"><span data-stu-id="6c9fa-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="6c9fa-104">La bibliothèque .NET facilite grandement l’utilisation de ce JSON.</span><span class="sxs-lookup"><span data-stu-id="6c9fa-104">The .NET library makes working with that JSON much easier.</span></span>


## <a name="nuget-install"></a><span data-ttu-id="6c9fa-105">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="6c9fa-105">NuGet Install</span></span>
<span data-ttu-id="6c9fa-106">Le `AdaptiveCards` package NuGet fournit des types pour l’utilisation des cartes adaptatives dans .net</span><span class="sxs-lookup"><span data-stu-id="6c9fa-106">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="6c9fa-107">[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="6c9fa-107">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="6c9fa-108">Exemple : Créer un AdaptiveCard et le sérialiser en JSON</span><span class="sxs-lookup"><span data-stu-id="6c9fa-108">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="6c9fa-109">Cet exemple montre comment créer une carte adaptative à l’aide d' C# objets standard, puis la sérialiser au format JSON pour le transport sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="6c9fa-109">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

```csharp
using AdaptiveCards;
// ...

AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion(1, 0));

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

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="6c9fa-110">Exemple : Analyser un AdaptiveCard à partir de JSON</span><span class="sxs-lookup"><span data-stu-id="6c9fa-110">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="6c9fa-111">Cet exemple montre comment analyser une charge utile JSON dans une carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="6c9fa-111">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="6c9fa-112">Cela facilite la manipulation du modèle d’objet, voire le rendu des cartes adaptatives dans votre application à l’aide de nos [Kits de développement](../../rendering-cards/getting-started.md)logiciel (SDK) de convertisseur.</span><span class="sxs-lookup"><span data-stu-id="6c9fa-112">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

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
