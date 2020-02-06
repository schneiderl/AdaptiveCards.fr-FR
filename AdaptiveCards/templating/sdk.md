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
# <a name="adaptive-card-templating-sdks"></a>Kits SDK de création de modèles de cartes adaptatives

Les kits SDK de création de modèles de cartes adaptatives facilitent le remplissage d’un [modèle de carte](language.md) avec des données réelles sur n’importe quelle plateforme prise en charge.

> Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).

> [!IMPORTANT] 
> 
> Ces fonctionnalités sont **en préversion et sujettes à modification**. Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.
> 
> Seul le SDK JavaScript est disponible durant la préversion initiale, mais un SDK .NET devrait bientôt sortir.

## <a name="javascript"></a>JavaScript

La bibliothèque [adaptivecards-Templating](https://www.npmjs.com/package/adaptivecards-templating) est disponible sur npm et par le biais de CDN. Suivez le lien du package pour obtenir une documentation complète.

### <a name="npm"></a>npm

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a>Utilisation

L’exemple ci-dessous part du principe que vous avez également installé la bibliothèque [adaptivecards](https://www.npmjs.com/package/adaptivecards) pour afficher la carte. 

Si vous n’envisagez pas d’afficher la carte, vous pouvez supprimer le code `parse` et `render`. 

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

## <a name="net"></a>.NET 

```console
dotnet add package AdaptiveCards.Templating --version 0.1.0-alpha1
```

> [!NOTE]
>
> Envisagez de remplacer la version ci-dessus par la dernière version publiée.

Importer la bibliothèque 

```cs
using AdaptiveCards.Templating
```

Utilisez le moteur de création de modèles en passant votre modèle et vos données au format JSON.

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
