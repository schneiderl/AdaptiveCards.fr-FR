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
# <a name="adaptive-card-templating-sdks"></a>SDK de création de cartes adaptatives

Les kits de développement logiciel (SDK) de création de cartes adaptatives facilitent la remplissage d’un [modèle de carte](language.md) avec des données réelles sur n’importe quelle plateforme prise en charge.

> Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.

> [!IMPORTANT] 
> 
> Ces fonctionnalités sont **en version préliminaire et sujettes à modification**. Vos commentaires sont non seulement des bienvenues, mais essentiels pour garantir que nous fournissons les fonctionnalités dont **vous** avez besoin.
> 
> Au cours de la première version préliminaire, seul le SDK JavaScript est disponible, mais un kit de développement logiciel (SDK) .NET devrait bientôt arriver.

## <a name="javascript"></a>JavaScript

La bibliothèque [adaptivecards-Templating](https://www.npmjs.com/package/adaptivecards-templating) est disponible sur NPM et via CDN. Consultez le lien du package pour obtenir une documentation complète.

### <a name="npm"></a>NPM

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 

### <a name="usage"></a>Utilisation

L’exemple ci-dessous suppose que vous avez également installé la bibliothèque [adaptivecards](https://www.npmjs.com/package/adaptivecards) pour afficher la carte. 

Si vous n’envisagez pas de restituer la carte, `parse` vous `render` pouvez supprimer le code et. 

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

## <a name="net-coming-soon"></a>.NET (bientôt*disponible*)

PAS ENCORE OPÉRATIONNEL: 

```console
nuget install AdaptiveCards.Templating
```
