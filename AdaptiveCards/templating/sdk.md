---
title: SDK de création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 5f60a458af99f1b88e8ee428a8f29f1849be9b62
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878876"
---
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="2cb46-102">SDK de création de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="2cb46-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="2cb46-103">Les kits de développement logiciel (SDK) de création de cartes adaptatives facilitent la remplissage d’un [modèle de carte](language.md) avec des données réelles sur n’importe quelle plateforme prise en charge.</span><span class="sxs-lookup"><span data-stu-id="2cb46-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="2cb46-104">Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.</span><span class="sxs-lookup"><span data-stu-id="2cb46-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="2cb46-105">Ces fonctionnalités sont **en version préliminaire et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="2cb46-105">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="2cb46-106">Vos commentaires sont non seulement des bienvenues, mais essentiels pour garantir que nous fournissons les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="2cb46-106">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>
> 
> <span data-ttu-id="2cb46-107">Au cours de la première version préliminaire, seul le SDK JavaScript est disponible, mais un kit de développement logiciel (SDK) .NET devrait bientôt arriver.</span><span class="sxs-lookup"><span data-stu-id="2cb46-107">During the initial preview only the JavaScript SDK is available, but a .NET SDK should arrive shortly.</span></span>

## <a name="javascript"></a><span data-ttu-id="2cb46-108">JavaScript</span><span class="sxs-lookup"><span data-stu-id="2cb46-108">JavaScript</span></span>

<span data-ttu-id="2cb46-109">La bibliothèque [adaptivecards-Templating](https://www.npmjs.com/package/adaptivecards-templating) est disponible sur NPM et via CDN.</span><span class="sxs-lookup"><span data-stu-id="2cb46-109">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="2cb46-110">Consultez le lien du package pour obtenir une documentation complète.</span><span class="sxs-lookup"><span data-stu-id="2cb46-110">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="2cb46-111">NPM</span><span class="sxs-lookup"><span data-stu-id="2cb46-111">npm</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="2cb46-112">CDN</span><span class="sxs-lookup"><span data-stu-id="2cb46-112">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a><span data-ttu-id="2cb46-113">Utilisation</span><span class="sxs-lookup"><span data-stu-id="2cb46-113">Usage</span></span>

<span data-ttu-id="2cb46-114">L’exemple ci-dessous suppose que vous avez également installé la bibliothèque [adaptivecards](https://www.npmjs.com/package/adaptivecards) pour afficher la carte.</span><span class="sxs-lookup"><span data-stu-id="2cb46-114">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="2cb46-115">Si vous n’envisagez pas de restituer la carte, `parse` vous `render` pouvez supprimer le code et.</span><span class="sxs-lookup"><span data-stu-id="2cb46-115">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net-coming-soon"></a><span data-ttu-id="2cb46-116">.NET (bientôt*disponible*)</span><span class="sxs-lookup"><span data-stu-id="2cb46-116">.NET (*coming soon*)</span></span>

<span data-ttu-id="2cb46-117">PAS ENCORE OPÉRATIONNEL:</span><span class="sxs-lookup"><span data-stu-id="2cb46-117">NOT WORKING YET:</span></span> 

```console
nuget install AdaptiveCards.Templating
```
