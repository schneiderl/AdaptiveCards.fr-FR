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
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="78771-102">Kit de développement logiciel .NET pour la création de cartes</span><span class="sxs-lookup"><span data-stu-id="78771-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="78771-103">Comme décrit dans la [mise en route](../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle d’objet JSON.</span><span class="sxs-lookup"><span data-stu-id="78771-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="78771-104">La bibliothèque .NET facilite beaucoup l’utilisation avec ce code JSON.</span><span class="sxs-lookup"><span data-stu-id="78771-104">The .NET library makes working with that JSON much easier.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78771-105">**Dernières modifications issues des v0.5**</span><span class="sxs-lookup"><span data-stu-id="78771-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="78771-106">Package renommé à partir de `Microsoft.AdaptiveCards` à `AdaptiveCards`</span><span class="sxs-lookup"><span data-stu-id="78771-106">Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`</span></span>
> 1. <span data-ttu-id="78771-107">En raison de collisions de nom fréquentes de types de framework, toutes les classes de modèle ont le préfixe « Adaptive ».</span><span class="sxs-lookup"><span data-stu-id="78771-107">Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive".</span></span> <span data-ttu-id="78771-108">Par exemple, `TextBlock` est maintenant `AdaptiveTextBlock`</span><span class="sxs-lookup"><span data-stu-id="78771-108">E.g., `TextBlock` is now `AdaptiveTextBlock`</span></span>
> 1. <span data-ttu-id="78771-109">Toutes les propriétés « uri » ont été modifiées à partir du type `string` à `Uri`</span><span class="sxs-lookup"><span data-stu-id="78771-109">All "uri" properties were changed from type `string` to `Uri`</span></span>
> 1. <span data-ttu-id="78771-110">Ont également été certaines modifications du schéma à partir de la version préliminaire v0.5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="78771-110">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>


## <a name="nuget-install"></a><span data-ttu-id="78771-111">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="78771-111">NuGet Install</span></span>
<span data-ttu-id="78771-112">Le `AdaptiveCards` package NuGet fournit des types pour travailler avec des cartes adaptatives dans .NET</span><span class="sxs-lookup"><span data-stu-id="78771-112">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="78771-113">[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="78771-113">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="78771-114">Exemple : Créer un AdaptiveCard et sérialiser au format JSON</span><span class="sxs-lookup"><span data-stu-id="78771-114">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="78771-115">Cet exemple montre comment créer une carte adaptative à l’aide de la norme C# objets et puis les sérialise au format JSON pour le transport sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="78771-115">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

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

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="78771-116">Exemple : Analyser un AdaptiveCard à partir de JSON</span><span class="sxs-lookup"><span data-stu-id="78771-116">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="78771-117">Cet exemple montre comment analyser une charge utile JSON dans une carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="78771-117">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="78771-118">Cela rend plus facile à manipuler le modèle objet ou même de rendre des cartes adaptatives à l’intérieur de votre application à l’aide de notre [convertisseur kits de développement logiciel](../../rendering-cards/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="78771-118">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

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
