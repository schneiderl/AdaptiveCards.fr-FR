---
title: Vue d’ensemble de la création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: db1f44c4465db88d375dec728bcb32d5933ef702
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631371"
---
# <a name="adaptive-cards-templating"></a><span data-ttu-id="3e87b-102">Création de modèles de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="3e87b-102">Adaptive Cards Templating</span></span>

<span data-ttu-id="3e87b-103">Nous sommes heureux de partager une préversion de nouveaux outils qui vous aideront à **créer**, **réutiliser** et **partager** des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="3e87b-103">We're excited to share a preview of new tools that will help you **create**, **reuse**, and **share** Adaptive Cards.</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="3e87b-104">**Changements cassants** dans la version **RC (Release Candidate) de mai 2020**</span><span class="sxs-lookup"><span data-stu-id="3e87b-104">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="3e87b-105">La version Release Candidate de la création de modèles contient des changements cassants mineurs que vous devez connaître si vous utilisez les anciens packages.</span><span class="sxs-lookup"><span data-stu-id="3e87b-105">The templating release candidate includes some minor breaking changes that you should be aware of if you've been using the older packages.</span></span> <span data-ttu-id="3e87b-106">Voir ci-dessous pour plus de détails.</span><span class="sxs-lookup"><span data-stu-id="3e87b-106">See below for details.</span></span>


## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="3e87b-107">Changements cassants de mai 2020</span><span class="sxs-lookup"><span data-stu-id="3e87b-107">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="3e87b-108">La syntaxe de liaison a changé et passe de `{...}` à `${...}`.</span><span class="sxs-lookup"><span data-stu-id="3e87b-108">The binding syntax changed from `{...}` to `${...}`.</span></span> 
    * <span data-ttu-id="3e87b-109">Par exemple : `"text": "Hello {name}"` devient `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="3e87b-109">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
2. <span data-ttu-id="3e87b-110">L’API JavaScript ne contient plus d’objet `EvaluationContext`.</span><span class="sxs-lookup"><span data-stu-id="3e87b-110">The JavaScript API no longer contains an `EvaluationContext` object.</span></span> <span data-ttu-id="3e87b-111">Passez simplement vos données à la fonction `expand`.</span><span class="sxs-lookup"><span data-stu-id="3e87b-111">Simply pass your data to the `expand` function.</span></span> <span data-ttu-id="3e87b-112">Consultez la [page du SDK](sdk.md) pour obtenir les détails complets.</span><span class="sxs-lookup"><span data-stu-id="3e87b-112">Please see the [SDK page](sdk.md) for full details.</span></span>
3. <span data-ttu-id="3e87b-113">L’API .NET a été reconçue pour correspondre davantage à l’API JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3e87b-113">The .NET API was redesigned to more closely match the JavaScript API.</span></span> <span data-ttu-id="3e87b-114">Consultez la [page du SDK](sdk.md) pour obtenir les détails complets.</span><span class="sxs-lookup"><span data-stu-id="3e87b-114">Please see the [SDK page](sdk.md) for full details.</span></span>

## <a name="how-can-templating-help-you"></a><span data-ttu-id="3e87b-115">Comment la création de modèles peut vous aider</span><span class="sxs-lookup"><span data-stu-id="3e87b-115">How can templating help you</span></span>

<span data-ttu-id="3e87b-116">La création de modèles permet de séparer des **données** d’une **disposition** dans une carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="3e87b-116">Templating enables the separation of **data** from the **layout** in an Adaptive Card.</span></span> 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a><span data-ttu-id="3e87b-117">Elle permet de concevoir une carte une seule fois, puis de peupler celles-ci de données réelles</span><span class="sxs-lookup"><span data-stu-id="3e87b-117">It helps design a card once, and then populate it with real data</span></span>

<span data-ttu-id="3e87b-118">Aujourd’hui, il est impossible de créer une carte à l’aide du [concepteur de carte adaptative](https://adaptivecards.io/designer) et d’utiliser ce JSON pour alimenter la charge utile avec du **contenu dynamique**.</span><span class="sxs-lookup"><span data-stu-id="3e87b-118">Today it's impossible to create a card using the [Adaptive Card Designer](https://adaptivecards.io/designer) and use that JSON to populate the payload with **dynamic content**.</span></span> <span data-ttu-id="3e87b-119">Pour ce faire, vous devez écrire du code personnalisé pour générer une chaîne JSON, ou utiliser les kits de développement logiciel (SDK) Modèle objet pour créer un modèle objet représentant votre carte et le sérialiser dans JSON.</span><span class="sxs-lookup"><span data-stu-id="3e87b-119">In order to achieve this you must write custom code to build a JSON string, or use the Object Model SDKs to build an OM representing your card and serialize it to JSON.</span></span> <span data-ttu-id="3e87b-120">Dans les deux cas, le concepteur effectue une opération unidirectionnelle ponctuelle et facilite l’ajustement du modèle de carte une fois celle-ci convertie en code.</span><span class="sxs-lookup"><span data-stu-id="3e87b-120">In either case the Designer is a one-time one-way operation and doesn't make it easy to tweak the card design later once you've converted it to code.</span></span>

### <a name="it-makes-transmissions-over-the-wire-smaller"></a><span data-ttu-id="3e87b-121">Il réduit le volume des transmissions par câble</span><span class="sxs-lookup"><span data-stu-id="3e87b-121">It makes transmissions over the wire smaller</span></span>

<span data-ttu-id="3e87b-122">Imaginez un monde où un modèle et des données peuvent être combinés **directement sur le client**.</span><span class="sxs-lookup"><span data-stu-id="3e87b-122">Imagine a world where a template and data can be combined **directly on the client**.</span></span> <span data-ttu-id="3e87b-123">Cela signifie que, si vous utilisez le même modèle plusieurs fois, ou souhaitez le mettre à jour avec de nouvelles données, vous devez simplement envoyer de nouvelles données à l’appareil qui réutilise le même modèle indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="3e87b-123">This means if you use the same template multiple times, or want to update it with new data, you just need to send new data to the device and it can re-use the same template over and over.</span></span>

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a><span data-ttu-id="3e87b-124">Il vous aide à créer une carte de bel aspect simplement à partir des données que vous fournissez</span><span class="sxs-lookup"><span data-stu-id="3e87b-124">It helps you create a great looking card from just the data you provide</span></span>

<span data-ttu-id="3e87b-125">Nous pensons que les cartes adaptatives sont remarquables, mais que se passerait-il si vous n’aviez pas à écrire de carte adaptative pour tout ce que vous voulez afficher à un utilisateur ?</span><span class="sxs-lookup"><span data-stu-id="3e87b-125">We think Adaptive Cards are great, but what if you didn't have to write an Adaptive Card for everything you want to display to a user?</span></span> <span data-ttu-id="3e87b-126">Un service de modèles (décrit ci-dessous) nous permet de créer un monde où chacun peut contribuer, découvrir et partager des modèles sur tout type de données.</span><span class="sxs-lookup"><span data-stu-id="3e87b-126">With a template service (described below) we can create a world where everyone can contribute, discover, and share templates over any type of data.</span></span> 

<span data-ttu-id="3e87b-127">Partagez au sein de vos propres projets, de votre organisation ou avec l’Internet entier.</span><span class="sxs-lookup"><span data-stu-id="3e87b-127">Share within your own projects, your organization, or with the entire internet.</span></span>

### <a name="ai-and-other-services-could-improve-user-experiences"></a><span data-ttu-id="3e87b-128">L’intelligence artificielle et d’autres services peuvent améliorer l’expérience utilisateur</span><span class="sxs-lookup"><span data-stu-id="3e87b-128">AI and other services could improve user experiences</span></span>

<span data-ttu-id="3e87b-129">En séparant les données du contenu, la solution ouvre la porte à l’intelligence artificielle et à d’autres services pour analyser les données des cartes que nous voyons et améliorer la productivité des utilisateurs ou nous aider à trouver des informations.</span><span class="sxs-lookup"><span data-stu-id="3e87b-129">By separating data from content it opens a door for AI and other services to  "reason" over the data in the cards we see and enhance user productivity or help us find things.</span></span>

## <a name="what-is-adaptive-cards-templating"></a><span data-ttu-id="3e87b-130">Qu’est-ce que la création de modèles de cartes adaptatives ?</span><span class="sxs-lookup"><span data-stu-id="3e87b-130">What is Adaptive Cards Templating?</span></span>

<span data-ttu-id="3e87b-131">Il est composé de 3 composants principaux :</span><span class="sxs-lookup"><span data-stu-id="3e87b-131">It's comprised of 3 major components:</span></span>

1. <span data-ttu-id="3e87b-132">Le **[langage de gabarit](language.md)** est la syntaxe utilisée pour le créer un modèle.</span><span class="sxs-lookup"><span data-stu-id="3e87b-132">The **[Template Language](language.md)** is the syntax used for authoring a template.</span></span> <span data-ttu-id="3e87b-133">Le concepteur vous permet même d’afficher un aperçu de vos modèles au moment de la conception en incluant des « exemples de données ».</span><span class="sxs-lookup"><span data-stu-id="3e87b-133">The Designer even lets you preview your templates at design time by including "sample data".</span></span>
2. <span data-ttu-id="3e87b-134">Des **[kits de développement (SDK) de modèles](sdk.md)** existent sur toutes les plateformes de carte adaptative prises en charge.</span><span class="sxs-lookup"><span data-stu-id="3e87b-134">The **[Templating SDK's](sdk.md)** will exist on all supported Adaptive Card platforms.</span></span> <span data-ttu-id="3e87b-135">Ces kits de développement logiciel (SDK) permettent de peupler un modèle de données réelles, sur le serveur principal ou directement sur le client.</span><span class="sxs-lookup"><span data-stu-id="3e87b-135">These SDKs allow you to populate a template with real data, on the back-end or directly on the client.</span></span> 
3. <span data-ttu-id="3e87b-136">Le **[service de modèles](service.md)** est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.</span><span class="sxs-lookup"><span data-stu-id="3e87b-136">The **[Template Service](service.md)** is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

## <a name="template-language"></a><span data-ttu-id="3e87b-137">Langage de modèle</span><span class="sxs-lookup"><span data-stu-id="3e87b-137">Template Language</span></span>

<span data-ttu-id="3e87b-138">Le langage de modèle est la syntaxe utilisée pour créer un modèle de carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="3e87b-138">The template language is the syntax used to author an Adaptive Card template.</span></span> 

> [!NOTE]
> 
> <span data-ttu-id="3e87b-139">Suivez avec l’exemple ci-dessous en ouvrant un nouvel onglet pour</span><span class="sxs-lookup"><span data-stu-id="3e87b-139">Follow along with the example below by opening up a new tab to</span></span>
>
> **https://adaptivecards.io/designer**
> 
> <span data-ttu-id="3e87b-140">Cliquez sur le bouton **Mode Aperçu** pour basculer entre le mode création et le mode aperçu.</span><span class="sxs-lookup"><span data-stu-id="3e87b-140">Click the **Preview Mode** button to toggle between design-mode and preview-mode.</span></span>

![Capture d’écran du concepteur](content/2019-08-01-13-58-27.png)

<span data-ttu-id="3e87b-142">Le concepteur vient d’être mis à jour et prend maintenant en charge la création de modèles et fournit des **exemples de données** pour voir un aperçu de la carte en cours de conception.</span><span class="sxs-lookup"><span data-stu-id="3e87b-142">The newly updated Designer adds support for authoring templates and providing **Sample Data** to preview the card at design-time.</span></span>

<span data-ttu-id="3e87b-143">Collez l’exemple ci-dessous dans le volet de l’**éditeur de charge utile de carte** :</span><span class="sxs-lookup"><span data-stu-id="3e87b-143">Paste the example below into the **Card Payload Editor** pane:</span></span> 

<span data-ttu-id="3e87b-144">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="3e87b-144">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "ColumnSet",
            "style": "accent",
            "bleed": true,
            "columns": [
                {
                    "type": "Column",
                    "width": "auto",
                    "items": [
                        {
                            "type": "Image",
                            "url": "${photo}",
                            "altText": "Profile picture",
                            "size": "Small",
                            "style": "Person"
                        }
                    ]
                },
                {
                    "type": "Column",
                    "width": "stretch",
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "Hi ${name}!",
                            "size": "Medium"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Here's a bit about your org...",
                            "spacing": "None"
                        }
                    ]
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: **${manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "${peers}",
                    "title": "${name}",
                    "value": "${title}"
                }
            ]
        }
    ]
}
```

<span data-ttu-id="3e87b-145">Collez ensuite les données JSON ci-dessous dans l’**éditeur d’exemple de données**.</span><span class="sxs-lookup"><span data-stu-id="3e87b-145">Then paste the JSON data below into the **Sample Data Editor**.</span></span> 

<span data-ttu-id="3e87b-146">L’**exemple de données** vous permet de voir exactement comment votre carte apparaîtra au moment de l’exécution, quand elle recevra des données réelles.</span><span class="sxs-lookup"><span data-stu-id="3e87b-146">**Sample Data** helps you see exactly how your card will appear at runtime when passed actual data.</span></span>

<span data-ttu-id="3e87b-147">**EmployeeData**</span><span class="sxs-lookup"><span data-stu-id="3e87b-147">**EmployeeData**</span></span>

```json
{
    "name": "Matt",
    "photo": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
    "manager": {
        "name": "Thomas",
        "title": "PM Lead"
    },
    "peers": [
        {
            "name": "Lei",
            "title": "Sr Program Manager"
        },
        {
            "name": "Andrew",
            "title": "Program Manager II"
        },
        {
            "name": "Mary Anne",
            "title": "Program Manager"
        }
    ]
}
```

<span data-ttu-id="3e87b-148">Cliquez sur le bouton **Mode Aperçu**.</span><span class="sxs-lookup"><span data-stu-id="3e87b-148">Click the **Preview Mode** button.</span></span> <span data-ttu-id="3e87b-149">Le rendu de la carte doit être conforme à l’exemple de données fourni ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="3e87b-149">You should see the card render according to the sample data provided above.</span></span> <span data-ttu-id="3e87b-150">N’hésitez pas à apporter des ajustements à l’exemple de données et observez en temps réel la mise à jour de la carte.</span><span class="sxs-lookup"><span data-stu-id="3e87b-150">Feel free to make tweaks to the sample data and watch the card update in realtime.</span></span>

<span data-ttu-id="3e87b-151">**Félicitations**, vous venez de créer votre premier modèle de carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="3e87b-151">**Congratulations**, you just authored your first Adaptive Card Template!</span></span> <span data-ttu-id="3e87b-152">Voyons à présent comment peupler le modèle de données réelles.</span><span class="sxs-lookup"><span data-stu-id="3e87b-152">Next let's learn how to populate the template with real data.</span></span>

> <span data-ttu-id="3e87b-153">En savoir plus sur le [langage de modèle](language.md)</span><span class="sxs-lookup"><span data-stu-id="3e87b-153">Learn more about the [template language](language.md)</span></span>

## <a name="sdk-support"></a><span data-ttu-id="3e87b-154">Prise en charge du Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="3e87b-154">SDK support</span></span>

<span data-ttu-id="3e87b-155">Les kits de développement logiciel (SDK) de création de modèles permettent de remplir un modèle de données réelles.</span><span class="sxs-lookup"><span data-stu-id="3e87b-155">The Templating SDKs make it possible to populate a template with real-data.</span></span>

> [!NOTE]
>
> <span data-ttu-id="3e87b-156">À ce jour, les kits SDK de création de modèles sont disponibles pour .NET et NodeJS.</span><span class="sxs-lookup"><span data-stu-id="3e87b-156">At this time templating SDKs are available for .NET and NodeJS.</span></span> <span data-ttu-id="3e87b-157">Nous publierons au fur et à mesure les kits SDK pour toutes les autres plateformes de cartes adaptatives comme iOS, Android, UWP, etc.</span><span class="sxs-lookup"><span data-stu-id="3e87b-157">Over time we will release templating SDKs for all remaining Adaptive Cards platform, like iOS, Android, UWP, etc.</span></span>

<span data-ttu-id="3e87b-158">Plateforme</span><span class="sxs-lookup"><span data-stu-id="3e87b-158">Platform</span></span> | <span data-ttu-id="3e87b-159">Package</span><span class="sxs-lookup"><span data-stu-id="3e87b-159">Package</span></span> | <span data-ttu-id="3e87b-160">Installer</span><span class="sxs-lookup"><span data-stu-id="3e87b-160">Install</span></span> | <span data-ttu-id="3e87b-161">Documentation</span><span class="sxs-lookup"><span data-stu-id="3e87b-161">Documentation</span></span>
--- | --- | --- | ---
<span data-ttu-id="3e87b-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="3e87b-162">JavaScript</span></span> | <span data-ttu-id="3e87b-163">[![Installation npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span><span class="sxs-lookup"><span data-stu-id="3e87b-163">[![npm install](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating)</span></span> | `npm install adaptivecards-templating` | [<span data-ttu-id="3e87b-164">Documentation</span><span class="sxs-lookup"><span data-stu-id="3e87b-164">Documentation</span></span>](https://www.npmjs.com/package/adaptivecards-templating)
<span data-ttu-id="3e87b-165">.NET</span><span class="sxs-lookup"><span data-stu-id="3e87b-165">.NET</span></span> | <span data-ttu-id="3e87b-166">[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span><span class="sxs-lookup"><span data-stu-id="3e87b-166">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating)</span></span> | `dotnet add package AdaptiveCards.Templating` | [<span data-ttu-id="3e87b-167">Documentation</span><span class="sxs-lookup"><span data-stu-id="3e87b-167">Documentation</span></span>](https://docs.microsoft.com/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a><span data-ttu-id="3e87b-168">Exemple JavaScript</span><span class="sxs-lookup"><span data-stu-id="3e87b-168">JavaScript Example</span></span>

<span data-ttu-id="3e87b-169">Le code JavaScript ci-dessous montre le modèle général qui sera utilisé pour peupler un modèle de données.</span><span class="sxs-lookup"><span data-stu-id="3e87b-169">The JavaScript below shows the general pattern that will be used to populate a template with data.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

var card = template.expand({
    $root: {
        // Your data goes here
    }
});
// Now you have an AdaptiveCard ready to render!
```

> <span data-ttu-id="3e87b-170">En savoir plus sur les [Kits de développement logiciel (SDK) de création de modèles](sdk.md)</span><span class="sxs-lookup"><span data-stu-id="3e87b-170">Learn more about the [templating SDKs](sdk.md)</span></span>

## <a name="template-service"></a><span data-ttu-id="3e87b-171">Service de modèles</span><span class="sxs-lookup"><span data-stu-id="3e87b-171">Template Service</span></span>

<span data-ttu-id="3e87b-172">Le service de modèles de cartes adaptatives est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.</span><span class="sxs-lookup"><span data-stu-id="3e87b-172">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="3e87b-173">Il est utile si vous voulez afficher des données sans vous ennuyer à écrire une carte adaptative personnalisée pour celles-ci.</span><span class="sxs-lookup"><span data-stu-id="3e87b-173">It's useful if you want to display some data but don't want to bother writing a custom Adaptive Card for it.</span></span>

<span data-ttu-id="3e87b-174">L’API permettant d’obtenir un modèle est assez simple, mais le service offre en fait bien plus, notamment la possibilité d’analyser vos données et de trouver un modèle susceptible de vous convenir.</span><span class="sxs-lookup"><span data-stu-id="3e87b-174">The API to get a template is straight-forward enough, but the service actually offers much more, including the ability to analyze your data and find a template that might work for you.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="3e87b-175">Tous les modèles sont des fichiers JSON plats stockés dans un référentiel GitHub afin que tout le monde puisse y contribuer, comme à tout autre code open source.</span><span class="sxs-lookup"><span data-stu-id="3e87b-175">All templates are flat JSON files stored in a GitHub repo so anyone can contribute to them like any other open source code.</span></span>

> <span data-ttu-id="3e87b-176">En savoir plus sur [le service de modèles de carte](service.md)</span><span class="sxs-lookup"><span data-stu-id="3e87b-176">Learn more about the [card template Service](service.md)</span></span>

## <a name="whats-next-and-sending-feedback"></a><span data-ttu-id="3e87b-177">Étapes suivantes et envoi de commentaires</span><span class="sxs-lookup"><span data-stu-id="3e87b-177">What's next and sending feedback</span></span>

<span data-ttu-id="3e87b-178">La création de modèles et la séparation de la présentation et des données nous rapprochent de l’objectif de notre mission : « un écosystème pour un échange de contenu standardisé entre les applications et les services ».</span><span class="sxs-lookup"><span data-stu-id="3e87b-178">Templating and the separation of presentation from data takes us a whole lot closer toward our mission: "an ecosystem standardized content exchange between apps and services".</span></span> <span data-ttu-id="3e87b-179">Nous avons beaucoup à dire dans ce domaine, donc restez à l’écoute et partagez votre expérience sur [GitHub](https://github.com/Microsoft/AdaptiveCards/issues) !</span><span class="sxs-lookup"><span data-stu-id="3e87b-179">We've got plenty to deliver in this area, so stay tuned and let us know how it's working for you on [GitHub](https://github.com/Microsoft/AdaptiveCards/issues)!</span></span>
