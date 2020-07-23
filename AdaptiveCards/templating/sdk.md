---
title: Kits SDK de création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 05/15/2020
ms.topic: article
ms.openlocfilehash: a8db2f5ef84203187ed1b9d0fc8dd3ce63ee3569
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417576"
---
# <a name="adaptive-card-templating-sdks"></a>Kits SDK de création de modèles de cartes adaptatives

Les kits SDK de création de modèles de cartes adaptatives facilitent le remplissage d’un [modèle de carte](language.md) avec des données réelles sur n’importe quelle plateforme prise en charge.

> Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).

> [!IMPORTANT] 
> 
> **Changements cassants** dans la version **RC (Release Candidate) de mai 2020**
>
> Nous avons travaillé dur à la publication des modèles et nous sommes dans la dernière ligne droite ! Nous avons dû apporter des modifications mineures avant de finaliser la version.

## <a name="breaking-changes-as-of-may-2020"></a>Changements cassants de mai 2020

1. La syntaxe de liaison a changé et passe de `{...}` à `${...}`. 
    * Par exemple : `"text": "Hello {name}"` devient `"text": "Hello ${name}"`
2. L’API JavaScript ne contient plus d’objet `EvaluationContext`. Passez simplement vos données à la fonction `expand`. Consultez la [page du SDK](sdk.md) pour obtenir les détails complets.
3. L’API .NET a été reconçue pour correspondre davantage à l’API JavaScript. Vous trouverez des informations détaillées ci-dessous.

## <a name="javascript"></a>JavaScript

La bibliothèque [adaptivecards-Templating](https://www.npmjs.com/package/adaptivecards-templating) est disponible sur npm et par le biais de CDN. Suivez le lien du package pour obtenir une documentation complète.

### <a name="npm"></a>npm

[![Installation npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)

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
            "text": "Hello ${name}!"
        }
    ]
};
 
// Create a Template instance from the template payload
var template = new ACData.Template(templatePayload);
 
// Expand the template with your `$root` data object.
// This binds it to the data and produces the final Adaptive Card payload
var cardPayload = template.expand({
   $root: {
      name: "Matt Hidinger"
   }
});
 
// OPTIONAL: Render the card (requires that the adaptivecards library be loaded)
var adaptiveCard = new AdaptiveCards.AdaptiveCard();
adaptiveCard.parse(cardPayload);
document.getElementById('exampleDiv').appendChild(adaptiveCard.render());
```

## <a name="net"></a>.NET 

> [!IMPORTANT] 
> 
> La version Release Candidate de .NET sera disponible vers le 23 mai. Recherchez la version `1.0.0-RC1`.
>

[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a>Utilisation

```cs
// Import the library 
using AdaptiveCards.Templating;
```

```cs
var templateJson = @"
{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.2"",
    ""body"": [
        {
            ""type"": ""TextBlock"",
            ""text"": ""Hello ${name}!""
        }
    ]
}";

// Create a Template instance from the template payload
AdaptiveCardTemplate template = new AdaptiveCardTemplate(templateJson);

// You can use any serializable object as your data
var myData = new
{
    Name = "Matt Hidinger"
};

// "Expand" the template - this generates the final Adaptive Card payload
string cardJson = template.Expand(myData);
```

### <a name="custom-functions"></a>Fonctions personnalisées

Les fonctions personnalisées peuvent être ajoutées à la bibliothèque d’expressions adaptatives, en plus des fonctions prédéfinies.

Dans l’exemple ci-dessous, la fonction personnalisée stringFormat est ajoutée, et elle est utilisée pour la mise en forme d’une chaîne.
```cs
string jsonTemplate = @"{
    ""type"": ""AdaptiveCard"",
    ""version"": ""1.0"",
    ""body"": [{
        ""type"": ""TextBlock"",
        ""text"": ""${stringFormat(strings.myName, person.firstName, person.lastName)}""
    }]
}";

string jsonData = @"{
    ""strings"": {
        ""myName"": ""My name is {0} {1}""
    },
    ""person"": {
        ""firstName"": ""Andrew"",
        ""lastName"": ""Leader""
    }
}";

AdaptiveCardTemplate template = new AdaptiveCardTemplate(jsonTemplate);

var context = new EvaluationContext
{
    Root = jsonData
};

// a custom function is added
AdaptiveExpressions.Expression.Functions.Add("stringFormat", (args) =>
{
    string formattedString = "";

    // argument is packed in sequential order as defined in the template
    // For example, suppose we have "${stringFormat(strings.myName, person.firstName, person.lastName)}"
    // args will have following entries
    // args[0]: strings.myName
    // args[1]: person.firstName
    // args[2]: strings.lastName
    if (args[0] != null && args[1] != null && args[2] != null) 
    {
        string formatString = args[0];
        string[] stringArguments = {args[1], args[2] };
        formattedString = string.Format(formatString, stringArguments);
    }
    return formattedString;
});

string cardJson = template.Expand(context);
```

## <a name="troubleshooting"></a>Résolution des problèmes
Q. Pourquoi une exception AdaptiveTemplateException est-elle levée lorsque j’appelle ```expand()``` ?   
A. Si votre message d’erreur ressemble à « '\<offending item>' à la ligne '\<line number>' est **mal formé pour '$data : ' pair** ».   
Vérifiez que la valeur fournie pour « $data » correspond à du code JSON valide, tel qu’un nombre, une valeur booléenne, un objet ou un tableau, que la syntaxe est correcte pour le langage AEL, et que l’entrée existe dans le contexte de données au numéro de ligne indiqué.

Q. Pourquoi une exception ArgumentNullException est-elle levée lorsque j’appelle ```expand()``` ?   
A. Si votre message d’erreur ressemble à « **Vérifiez si le contexte de données parent est défini ou entrez une valeur non nulle pour** '\<offending item>' à la ligne '\<line number>' ».   
Celui-ci indique qu’il n’existe aucun contexte de données pour la liaison de données demandée. Vérifiez que le contexte de données racine est défini, le cas échéant, et vérifiez qu’un contexte de données est disponible pour la liaison actuelle, comme indiqué par le numéro de ligne.

Q. Pourquoi le format de date/heure dans la RFC 3389, par ex. « 2017-02-14T06:08:00Z », ne fonctionne pas avec les fonctions TIME/DATE quand il est utilisé avec le modèle ?   
A. Le SDK .NET nuget version 1.0.0-rc.0 expose ce comportement. Ce comportement est corrigé dans les prochaines mises en production. Le comportement par défaut du désérialiseur json.Net change la chaîne au format date/heure et est désactivé dans les prochaines mises en production. Utilisez la fonction formatDateTime() pour mettre en forme la chaîne date/heure dans la RFC 3389, comme montré dans [cet exemple](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28), ou vous pouvez contourner les fonctions TIME/DATE et utiliser juste formatDateTime(). Pour plus d’informations sur formatDateTime(), rendez-vous [ici](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).
