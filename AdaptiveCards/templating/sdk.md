---
title: Kits SDK de création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 3a9bfcd1bf8f87959a747997e04f5c5ad2a79980
ms.sourcegitcommit: 90afb3729931b0e4cae19b17ef9e49453c2d2bf6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163619"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="edff2-102">Kits SDK de création de modèles de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="edff2-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="edff2-103">Les kits SDK de création de modèles de cartes adaptatives facilitent le remplissage d’un [modèle de carte](language.md) avec des données réelles sur n’importe quelle plateforme prise en charge.</span><span class="sxs-lookup"><span data-stu-id="edff2-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="edff2-104">Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).</span><span class="sxs-lookup"><span data-stu-id="edff2-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="edff2-105">Ces fonctionnalités sont **en préversion et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="edff2-105">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="edff2-106">Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="edff2-106">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>
> 
> <span data-ttu-id="edff2-107">Seul le SDK JavaScript est disponible durant la préversion initiale, mais un SDK .NET devrait bientôt sortir.</span><span class="sxs-lookup"><span data-stu-id="edff2-107">During the initial preview only the JavaScript SDK is available, but a .NET SDK should arrive shortly.</span></span>

## <a name="javascript"></a><span data-ttu-id="edff2-108">JavaScript</span><span class="sxs-lookup"><span data-stu-id="edff2-108">JavaScript</span></span>

<span data-ttu-id="edff2-109">La bibliothèque [adaptivecards-Templating](https://www.npmjs.com/package/adaptivecards-templating) est disponible sur npm et par le biais de CDN.</span><span class="sxs-lookup"><span data-stu-id="edff2-109">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="edff2-110">Suivez le lien du package pour obtenir une documentation complète.</span><span class="sxs-lookup"><span data-stu-id="edff2-110">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="edff2-111">npm</span><span class="sxs-lookup"><span data-stu-id="edff2-111">npm</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="edff2-112">CDN</span><span class="sxs-lookup"><span data-stu-id="edff2-112">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a><span data-ttu-id="edff2-113">Utilisation</span><span class="sxs-lookup"><span data-stu-id="edff2-113">Usage</span></span>

<span data-ttu-id="edff2-114">L’exemple ci-dessous part du principe que vous avez également installé la bibliothèque [adaptivecards](https://www.npmjs.com/package/adaptivecards) pour afficher la carte.</span><span class="sxs-lookup"><span data-stu-id="edff2-114">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="edff2-115">Si vous n’envisagez pas d’afficher la carte, vous pouvez supprimer le code `parse` et `render`.</span><span class="sxs-lookup"><span data-stu-id="edff2-115">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

```js
import * as ACData from "adaptivecards-templating";
import * as AdaptiveCards from "adaptivecards";
 
// Define a template payload
var templatePayload = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hello {name}!"
        }
    ]
};
 
// Create a Template instamce from the template payload
var template = new ACData.Template(templatePayload);
 
// Create a data binding context, and set its $root property to the
// data object to bind the template to
var context = new ACData.EvaluationContext();
context.$root = {
    "name": "Mickey Mouse"
};
 
// "Expand" the template - this generates the final Adaptive Card,
// ready to render
var card = template.expand(context);
 
// Render the card
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(card);
 
var htmlElement = adaptiveCard.render();
```

## <a name="net"></a><span data-ttu-id="edff2-116">.NET</span><span class="sxs-lookup"><span data-stu-id="edff2-116">.NET</span></span> 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> <span data-ttu-id="edff2-117">Envisagez de remplacer la version ci-dessus par la dernière version publiée.</span><span class="sxs-lookup"><span data-stu-id="edff2-117">Consider changing the version above to the latest published version</span></span>

<span data-ttu-id="edff2-118">Importer la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="edff2-118">Import the library</span></span> 

```cs
using AdaptiveCards.Templating
```

<span data-ttu-id="edff2-119">Utilisez le moteur de création de modèles en passant votre modèle et vos données au format JSON.</span><span class="sxs-lookup"><span data-stu-id="edff2-119">Use the templating engine by passing in your template JSON and data JSON.</span></span>

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello {name}""
        }
    ]
}";

var dataJson = @"
{
    ""name"": ""Mickey Mouse""
}";

var transformer = new AdaptiveTransformer();
var cardJson = transformer.Transform(templateJson, dataJson);
```
