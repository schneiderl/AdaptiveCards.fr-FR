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
# <a name="adaptive-card-templating-sdks"></a><span data-ttu-id="30aef-102">Kits SDK de création de modèles de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="30aef-102">Adaptive Card Templating SDKs</span></span>

<span data-ttu-id="30aef-103">Les kits SDK de création de modèles de cartes adaptatives facilitent le remplissage d’un [modèle de carte](language.md) avec des données réelles sur n’importe quelle plateforme prise en charge.</span><span class="sxs-lookup"><span data-stu-id="30aef-103">The Adaptive Card Templating SDKs make it easy to populate a [card template](language.md) with real data on any supported platform.</span></span>

> <span data-ttu-id="30aef-104">Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).</span><span class="sxs-lookup"><span data-stu-id="30aef-104">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="30aef-105">**Changements cassants** dans la version **RC (Release Candidate) de mai 2020**</span><span class="sxs-lookup"><span data-stu-id="30aef-105">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="30aef-106">Nous avons travaillé dur à la publication des modèles et nous sommes dans la dernière ligne droite !</span><span class="sxs-lookup"><span data-stu-id="30aef-106">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="30aef-107">Nous avons dû apporter des modifications mineures avant de finaliser la version.</span><span class="sxs-lookup"><span data-stu-id="30aef-107">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="30aef-108">Changements cassants de mai 2020</span><span class="sxs-lookup"><span data-stu-id="30aef-108">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="30aef-109">La syntaxe de liaison a changé et passe de `{...}` à `${...}`.</span><span class="sxs-lookup"><span data-stu-id="30aef-109">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="30aef-110">Par exemple : `"text": "Hello {name}"` devient `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="30aef-110">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="30aef-111">L’API JavaScript ne contient plus d’objet `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="30aef-111">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="30aef-112">Passez simplement vos données à la fonction `expand`.</span><span class="sxs-lookup"><span data-stu-id="30aef-112">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="30aef-113">Consultez la [page du SDK](sdk.md) pour obtenir les détails complets.</span><span class="sxs-lookup"><span data-stu-id="30aef-113">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="30aef-114">L’API .NET a été reconçue pour correspondre davantage à l’API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="30aef-114">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="30aef-115">Vous trouverez des informations détaillées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="30aef-115">Please below for full details.</span></span>

## <a name="javascript"></a><span data-ttu-id="30aef-116">JavaScript</span><span class="sxs-lookup"><span data-stu-id="30aef-116">JavaScript</span></span>

<span data-ttu-id="30aef-117">La bibliothèque [adaptivecards-Templating](https://www.npmjs.com/package/adaptivecards-templating) est disponible sur npm et par le biais de CDN.</span><span class="sxs-lookup"><span data-stu-id="30aef-117">The [adaptivecards-templating](https://www.npmjs.com/package/adaptivecards-templating) library is available on npm and via CDN.</span></span> <span data-ttu-id="30aef-118">Suivez le lien du package pour obtenir une documentation complète.</span><span class="sxs-lookup"><span data-stu-id="30aef-118">See the package link for full documentation.</span></span>

### <a name="npm"></a><span data-ttu-id="30aef-119">npm</span><span class="sxs-lookup"><span data-stu-id="30aef-119">npm</span></span>

<span data-ttu-id="30aef-120">[![Installation npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="30aef-120">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span>

```console
npm install adaptivecards-templating
```

### <a name="cdn"></a><span data-ttu-id="30aef-121">CDN</span><span class="sxs-lookup"><span data-stu-id="30aef-121">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards-templating/dist/adaptivecards-templating.min.js"></script>
``` 


### <a name="usage"></a><span data-ttu-id="30aef-122">Utilisation</span><span class="sxs-lookup"><span data-stu-id="30aef-122">Usage</span></span>

<span data-ttu-id="30aef-123">L’exemple ci-dessous part du principe que vous avez également installé la bibliothèque [adaptivecards](https://www.npmjs.com/package/adaptivecards) pour afficher la carte.</span><span class="sxs-lookup"><span data-stu-id="30aef-123">The sample below assumes you've also installed the [adaptivecards](https://www.npmjs.com/package/adaptivecards) library in order to render the card.</span></span> 

<span data-ttu-id="30aef-124">Si vous n’envisagez pas d’afficher la carte, vous pouvez supprimer le code `parse` et `render`.</span><span class="sxs-lookup"><span data-stu-id="30aef-124">If you don't plan on rendering the card then you can remove the `parse` and `render` code.</span></span> 

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

## <a name="net"></a><span data-ttu-id="30aef-125">.NET</span><span class="sxs-lookup"><span data-stu-id="30aef-125">.NET</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="30aef-126">La version Release Candidate de .NET sera disponible vers le 23 mai.</span><span class="sxs-lookup"><span data-stu-id="30aef-126">The .NET Release Candidate will be available around 05/23.</span></span> <span data-ttu-id="30aef-127">Recherchez la version `1.0.0-RC1`.</span><span class="sxs-lookup"><span data-stu-id="30aef-127">Look for version `1.0.0-RC1`</span></span>
>

<span data-ttu-id="30aef-128">[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="30aef-128">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span>

```console
dotnet add package AdaptiveCards.Templating
```

### <a name="usage"></a><span data-ttu-id="30aef-129">Utilisation</span><span class="sxs-lookup"><span data-stu-id="30aef-129">Usage</span></span>

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

### <a name="custom-functions"></a><span data-ttu-id="30aef-130">Fonctions personnalisées</span><span class="sxs-lookup"><span data-stu-id="30aef-130">Custom Functions</span></span>

<span data-ttu-id="30aef-131">Les fonctions personnalisées peuvent être ajoutées à la bibliothèque d’expressions adaptatives, en plus des fonctions prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="30aef-131">Custom functions can be added to Adaptive Expression Library in addition to the prebuilt functions.</span></span>

<span data-ttu-id="30aef-132">Dans l’exemple ci-dessous, la fonction personnalisée stringFormat est ajoutée, et elle est utilisée pour la mise en forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="30aef-132">In the below example, stringFormat custom function is added, and the funtion is used to format a string.</span></span>
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

## <a name="troubleshooting"></a><span data-ttu-id="30aef-133">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="30aef-133">Troubleshooting</span></span>
<span data-ttu-id="30aef-134">Q.</span><span class="sxs-lookup"><span data-stu-id="30aef-134">Q.</span></span> <span data-ttu-id="30aef-135">Pourquoi une exception AdaptiveTemplateException est-elle levée lorsque j’appelle ```expand()``` ?</span><span class="sxs-lookup"><span data-stu-id="30aef-135">Why am I running into an AdaptiveTemplateException calling ```expand()```?</span></span>   
<span data-ttu-id="30aef-136">A.</span><span class="sxs-lookup"><span data-stu-id="30aef-136">A.</span></span> <span data-ttu-id="30aef-137">Si votre message d’erreur ressemble à « '\<offending item>' à la ligne '\<line number>' est **mal formé pour '$data : ' pair** ».</span><span class="sxs-lookup"><span data-stu-id="30aef-137">If your error message looks like '\<offending item>' at line, '\<line number>' is **malformed for '$data : ' pair**".</span></span>   
<span data-ttu-id="30aef-138">Vérifiez que la valeur fournie pour « $data » correspond à du code JSON valide, tel qu’un nombre, une valeur booléenne, un objet ou un tableau, que la syntaxe est correcte pour le langage AEL, et que l’entrée existe dans le contexte de données au numéro de ligne indiqué.</span><span class="sxs-lookup"><span data-stu-id="30aef-138">Please ensure that value provided for "$data" is valid json such as number, boolean, object, and array, or follows correct syntax for Adaptive Template language,  and the entry exists in the data context at the line number.</span></span>

<span data-ttu-id="30aef-139">Q.</span><span class="sxs-lookup"><span data-stu-id="30aef-139">Q.</span></span> <span data-ttu-id="30aef-140">Pourquoi une exception ArgumentNullException est-elle levée lorsque j’appelle ```expand()``` ?</span><span class="sxs-lookup"><span data-stu-id="30aef-140">Why am I running into an ArgumentNullException calling ```expand()```?</span></span>   
<span data-ttu-id="30aef-141">A.</span><span class="sxs-lookup"><span data-stu-id="30aef-141">A.</span></span> <span data-ttu-id="30aef-142">Si votre message d’erreur ressemble à « **Vérifiez si le contexte de données parent est défini ou entrez une valeur non nulle pour** '\<offending item>' à la ligne '\<line number>' ».</span><span class="sxs-lookup"><span data-stu-id="30aef-142">If your error message looks like" **Check if parent data context is set, or please enter a non-null value for** '\<offending item>' at line, '\<line number>'".</span></span>   
<span data-ttu-id="30aef-143">Celui-ci indique qu’il n’existe aucun contexte de données pour la liaison de données demandée.</span><span class="sxs-lookup"><span data-stu-id="30aef-143">It indicates that there doesn't exist data context for the requested data binding.</span></span> <span data-ttu-id="30aef-144">Vérifiez que le contexte de données racine est défini, le cas échéant, et vérifiez qu’un contexte de données est disponible pour la liaison actuelle, comme indiqué par le numéro de ligne.</span><span class="sxs-lookup"><span data-stu-id="30aef-144">Please ensure that root data context is set, if exists, ensure that any data context is available for current binding as indicated by the line number.</span></span>

<span data-ttu-id="30aef-145">Q.</span><span class="sxs-lookup"><span data-stu-id="30aef-145">Q.</span></span> <span data-ttu-id="30aef-146">Pourquoi le format de date/heure dans la RFC 3389, par ex. « 2017-02-14T06:08:00Z », ne fonctionne pas avec les fonctions TIME/DATE quand il est utilisé avec le modèle ?</span><span class="sxs-lookup"><span data-stu-id="30aef-146">Why date/time in RFC 3389 format e.g "2017-02-14T06:08:00Z" when used with template doesn't works with TIME/DATE functions?</span></span>   
<span data-ttu-id="30aef-147">A.</span><span class="sxs-lookup"><span data-stu-id="30aef-147">A.</span></span> <span data-ttu-id="30aef-148">Le SDK .NET nuget version 1.0.0-rc.0 expose ce comportement.</span><span class="sxs-lookup"><span data-stu-id="30aef-148">.NET sdk nuget version 1.0.0-rc.0 exhibits this behavior.</span></span> <span data-ttu-id="30aef-149">Ce comportement est corrigé dans les prochaines mises en production.</span><span class="sxs-lookup"><span data-stu-id="30aef-149">this behavior is corrected in the subsequent releases.</span></span> <span data-ttu-id="30aef-150">Le comportement par défaut du désérialiseur json.Net change la chaîne au format date/heure et est désactivé dans les prochaines mises en production.</span><span class="sxs-lookup"><span data-stu-id="30aef-150">json.Net deserilizer's default behavior changes date/time format string, and it's disabled for the subsequent releases.</span></span> <span data-ttu-id="30aef-151">Utilisez la fonction formatDateTime() pour mettre en forme la chaîne date/heure dans la RFC 3389, comme montré dans [cet exemple](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28), ou vous pouvez contourner les fonctions TIME/DATE et utiliser juste formatDateTime().</span><span class="sxs-lookup"><span data-stu-id="30aef-151">Please use formatDateTime() function to format the date/time string to RFC 3389 as seen in [this example](https://github.com/microsoft/AdaptiveCards/blob/db99ee07dadf317fe45e114a508e3de6e4325d0f/samples/Templates/Elements/Template.Functions.DateFunctions.json#L28), or you can bypass TIME/DATE functions, and just use formatDateTime().</span></span> <span data-ttu-id="30aef-152">Pour plus d’informations sur formatDateTime(), rendez-vous [ici](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).</span><span class="sxs-lookup"><span data-stu-id="30aef-152">For more information on formatDateTime(), please go [here](https://docs.microsoft.com/azure/bot-service/adaptive-expressions/adaptive-expressions-prebuilt-functions?view=azure-bot-service-4.0#date-and-time-functions).</span></span>
