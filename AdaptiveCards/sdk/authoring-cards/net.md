---
title: Kit de développement logiciel (SDK) .NET pour cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 10/01/2017
ms.topic: article
ms.openlocfilehash: fa86d83a8f20490ec286b69653099ac8cd81b8ef
ms.sourcegitcommit: 4d80c553ab574befa8c84706fd85d22077915745
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387350"
---
# <a name="net-sdk-for-authoring-cards"></a><span data-ttu-id="9d3f1-102">Kit de développement logiciel (SDK) .NET pour la création de cartes</span><span class="sxs-lookup"><span data-stu-id="9d3f1-102">.NET SDK for Authoring Cards</span></span>

<span data-ttu-id="9d3f1-103">Comme nous l’avons décrit dans la page [prise en main](../../authoring-cards/getting-started.md) , une carte adaptative est un modèle d’objet JSON.</span><span class="sxs-lookup"><span data-stu-id="9d3f1-103">As we described in the [Getting Started](../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON object model.</span></span> <span data-ttu-id="9d3f1-104">La bibliothèque .NET facilite grandement l’utilisation de ce JSON.</span><span class="sxs-lookup"><span data-stu-id="9d3f1-104">The .NET library makes working with that JSON much easier.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d3f1-105">**Dernières modifications de v 0.5**</span><span class="sxs-lookup"><span data-stu-id="9d3f1-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="9d3f1-106">Package renommé `Microsoft.AdaptiveCards` en`AdaptiveCards`</span><span class="sxs-lookup"><span data-stu-id="9d3f1-106">Package renamed from `Microsoft.AdaptiveCards` to `AdaptiveCards`</span></span>
> 1. <span data-ttu-id="9d3f1-107">En raison des collisions de noms fréquentes avec les types de Framework, toutes les classes de modèle ont été précédées de «Adaptive».</span><span class="sxs-lookup"><span data-stu-id="9d3f1-107">Due to frequent name collisions with framework types, all model classes have been prefixed with "Adaptive".</span></span> <span data-ttu-id="9d3f1-108">Par exemple, `TextBlock` est maintenant`AdaptiveTextBlock`</span><span class="sxs-lookup"><span data-stu-id="9d3f1-108">E.g., `TextBlock` is now `AdaptiveTextBlock`</span></span>
> 1. <span data-ttu-id="9d3f1-109">Toutes les propriétés «URI» ont été modifiées `string` du type à`Uri`</span><span class="sxs-lookup"><span data-stu-id="9d3f1-109">All "uri" properties were changed from type `string` to `Uri`</span></span>
> 1. <span data-ttu-id="9d3f1-110">Certaines modifications de schéma ont également été apportées à la version préliminaire v 0,5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="9d3f1-110">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>


## <a name="nuget-install"></a><span data-ttu-id="9d3f1-111">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="9d3f1-111">NuGet Install</span></span>
<span data-ttu-id="9d3f1-112">Le `AdaptiveCards` package NuGet fournit des types pour l’utilisation des cartes adaptatives dans .net</span><span class="sxs-lookup"><span data-stu-id="9d3f1-112">The `AdaptiveCards` NuGet package provides types for working with adaptive cards in .NET</span></span>

<span data-ttu-id="9d3f1-113">[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span><span class="sxs-lookup"><span data-stu-id="9d3f1-113">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.svg)](https://www.nuget.org/packages/AdaptiveCards)</span></span>

```console
Install-Package AdaptiveCards -IncludePrerelease
```

## <a name="example-create-an-adaptivecard-and-serialize-to-json"></a><span data-ttu-id="9d3f1-114">Exemple : Créer un AdaptiveCard et le sérialiser en JSON</span><span class="sxs-lookup"><span data-stu-id="9d3f1-114">Example: Create an AdaptiveCard and serialize to JSON</span></span>

<span data-ttu-id="9d3f1-115">Cet exemple montre comment créer une carte adaptative à l’aide d' C# objets standard, puis la sérialiser au format JSON pour le transport sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="9d3f1-115">This example demonstrates how to build an Adaptive Card using standard C# objects and then serialize it to JSON for transport over the wire.</span></span>

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

## <a name="example-parse-an-adaptivecard-from-json"></a><span data-ttu-id="9d3f1-116">Exemple : Analyser un AdaptiveCard à partir de JSON</span><span class="sxs-lookup"><span data-stu-id="9d3f1-116">Example: Parse an AdaptiveCard from JSON</span></span>

<span data-ttu-id="9d3f1-117">Cet exemple montre comment analyser une charge utile JSON dans une carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="9d3f1-117">This example demonstrates how to parse a JSON payload into an Adaptive Card.</span></span> <span data-ttu-id="9d3f1-118">Cela facilite la manipulation du modèle d’objet, voire le rendu des cartes adaptatives dans votre application à l’aide de nos [Kits de développement](../../rendering-cards/getting-started.md)logiciel (SDK) de convertisseur.</span><span class="sxs-lookup"><span data-stu-id="9d3f1-118">This makes it easy to manipulate the object model or even render Adaptive Cards inside your app by using our [renderer SDKs](../../rendering-cards/getting-started.md).</span></span>

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
