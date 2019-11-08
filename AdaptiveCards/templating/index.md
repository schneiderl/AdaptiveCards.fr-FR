---
title: Vue d’ensemble de la création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 07/29/2019
ms.topic: article
ms.openlocfilehash: 11ade4c2a41111f372873ea9a0677fe823c5b0ab
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750427"
---
# <a name="adaptive-cards-templating-preview"></a><span data-ttu-id="bdbf5-102">Création de modèles de cartes adaptatives (préversion)</span><span class="sxs-lookup"><span data-stu-id="bdbf5-102">Adaptive Cards Templating (Preview)</span></span>

<span data-ttu-id="bdbf5-103">Nous sommes heureux de partager une préversion de nouveaux outils qui vous aideront à **créer**, **réutiliser** et **partager** des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-103">We're excited to share a preview of new tools that will help you **create**, **reuse**, and **share** Adaptive Cards.</span></span> 

> [!IMPORTANT] 
> 
> <span data-ttu-id="bdbf5-104">Ces fonctionnalités sont **en préversion et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-104">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="bdbf5-105">Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-105">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-can-templating-help-you"></a><span data-ttu-id="bdbf5-106">Comment la création de modèles peut-elle vous aider ?</span><span class="sxs-lookup"><span data-stu-id="bdbf5-106">How can templating help you?</span></span>

<span data-ttu-id="bdbf5-107">La création de modèles permet de séparer des **données** d’une **disposition** dans une carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-107">Templating enables the separation of **data** from the **layout** in an Adaptive Card.</span></span> 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a><span data-ttu-id="bdbf5-108">Elle permet de concevoir une carte une seule fois, puis de peupler celles-ci de données réelles</span><span class="sxs-lookup"><span data-stu-id="bdbf5-108">It helps design a card once, and then populate it with real data</span></span>

<span data-ttu-id="bdbf5-109">Aujourd’hui, il est impossible de créer une carte à l’aide du [concepteur de carte adaptative](https://adaptivecards.io/designer) et d’utiliser ce JSON pour alimenter la charge utile avec du **contenu dynamique**.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-109">Today it's impossible to create a card using the [Adaptive Card Designer](https://adaptivecards.io/designer) and use that JSON to populate the payload with **dynamic content**.</span></span> <span data-ttu-id="bdbf5-110">Pour ce faire, vous devez écrire du code personnalisé pour générer une chaîne JSON, ou utiliser les kits de développement logiciel (SDK) Modèle objet pour créer un modèle objet représentant votre carte et le sérialiser dans JSON.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-110">In order to achieve this you must write custom code to build a JSON string, or use the Object Model SDKs to build an OM representing your card and serialize it to JSON.</span></span> <span data-ttu-id="bdbf5-111">Dans les deux cas, le concepteur effectue une opération unidirectionnelle ponctuelle et facilite l’ajustement du modèle de carte une fois celle-ci convertie en code.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-111">In either case the Designer is a one-time one-way operation and doesn't make it easy to tweak the card design later once you've converted it to code.</span></span>

### <a name="it-makes-tranmissions-over-the-wire-smaller"></a><span data-ttu-id="bdbf5-112">Il réduit le volume des transmissions par câble</span><span class="sxs-lookup"><span data-stu-id="bdbf5-112">It makes tranmissions over the wire smaller</span></span>

<span data-ttu-id="bdbf5-113">Imaginez un monde où un modèle et des données peuvent être combinés **directement sur le client**.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-113">Imagine a world where a template and data can be combined **directly on the client**.</span></span> <span data-ttu-id="bdbf5-114">Cela signifie que, si vous utilisez le même modèle plusieurs fois, ou souhaitez le mettre à jour avec de nouvelles données, vous devez simplement envoyer de nouvelles données à l’appareil qui réutilise le même modèle indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-114">This means if you use the same template multiple times, or want to update it with new data, you just need to send new data to the device and it can re-use the same template over and over.</span></span>

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a><span data-ttu-id="bdbf5-115">Il vous aide à créer une carte de bel aspect simplement à partir des données que vous fournissez</span><span class="sxs-lookup"><span data-stu-id="bdbf5-115">It helps you create a great looking card from just the data you provide</span></span>

<span data-ttu-id="bdbf5-116">Nous pensons que les cartes adaptatives sont remarquables, mais que se passerait-il si vous n’aviez pas à écrire de carte adaptative pour tout ce que vous voulez afficher à un utilisateur ?</span><span class="sxs-lookup"><span data-stu-id="bdbf5-116">We think Adaptive Cards are great, but what if you didn't have to write an Adaptive Card for everything you want to display to a user?</span></span> <span data-ttu-id="bdbf5-117">Un service de modèles (décrit ci-dessous) nous permet de créer un monde où chacun peut contribuer, découvrir et partager des modèles sur tout type de données.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-117">With a template service (described below) we can create a world where everyone can contribute, discover, and share templates over any type of data.</span></span> 

<span data-ttu-id="bdbf5-118">Partagez au sein de vos propres projets, de votre organisation ou avec l’Internet entier.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-118">Share within your own projects, your organization, or with the entire internet.</span></span>

### <a name="ai-and-other-services-could-improve-user-experiences"></a><span data-ttu-id="bdbf5-119">L’intelligence artificielle et d’autres services peuvent améliorer l’expérience utilisateur</span><span class="sxs-lookup"><span data-stu-id="bdbf5-119">AI and other services could improve user experiences</span></span>

<span data-ttu-id="bdbf5-120">En séparant les données du contenu, la solution ouvre la porte à l’intelligence artificielle et à d’autres services pour analyser les données des cartes que nous voyons et améliorer la productivité des utilisateurs ou nous aider à trouver des informations.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-120">By separating data from content it opens a door for AI and other services to  "reason" over the data in the cards we see and enhance user productivity or help us find things.</span></span>

## <a name="what-is-adaptive-cards-templating"></a><span data-ttu-id="bdbf5-121">Qu’est-ce que la création de modèles de cartes adaptatives ?</span><span class="sxs-lookup"><span data-stu-id="bdbf5-121">What is Adaptive Cards Templating?</span></span>

<span data-ttu-id="bdbf5-122">Il est composé de 3 composants principaux :</span><span class="sxs-lookup"><span data-stu-id="bdbf5-122">It's comprised of 3 major components:</span></span>

1. <span data-ttu-id="bdbf5-123">Le **[langage de gabarit](language.md)** est la syntaxe utilisée pour le créer un modèle.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-123">The **[Template Language](language.md)** is the syntax used for authoring a template.</span></span> <span data-ttu-id="bdbf5-124">Le concepteur vous permet même d’afficher un aperçu de vos modèles au moment de la conception en incluant des « exemples de données ».</span><span class="sxs-lookup"><span data-stu-id="bdbf5-124">The Designer even lets you preview your templates at design time by including "sample data".</span></span>
2. <span data-ttu-id="bdbf5-125">Des **[kits de développement (SDK) de modèles](sdk.md)** existent sur toutes les plateformes de carte adaptative prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-125">The **[Templating SDK's](sdk.md)** will exist on all supported Adaptive Card platforms.</span></span> <span data-ttu-id="bdbf5-126">Ces kits de développement logiciel (SDK) permettent de peupler un modèle de données réelles, sur le serveur principal ou directement sur le client.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-126">These SDKs allow you to populate a template with real data, on the back-end or directly on the client.</span></span> 
3. <span data-ttu-id="bdbf5-127">Le **[service de modèles](service.md)** est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-127">The **[Template Service](service.md)** is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

## <a name="template-language"></a><span data-ttu-id="bdbf5-128">Langage de modèle</span><span class="sxs-lookup"><span data-stu-id="bdbf5-128">Template Language</span></span>

<span data-ttu-id="bdbf5-129">Le langue de modèle est la syntaxe utilisée pour créer un modèle de carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-129">The template langauge is the syntax used to author an Adaptive Card template.</span></span> 

> [!NOTE]
> 
> <span data-ttu-id="bdbf5-130">Suivez avec l’exemple ci-dessous en ouvrant un nouvel onglet pour</span><span class="sxs-lookup"><span data-stu-id="bdbf5-130">Follow along with the example below by opening up a new tab to</span></span>
>
> **https://adaptivecards.io/designer**
> 
> <span data-ttu-id="bdbf5-131">Cliquez sur le bouton **Mode Aperçu** pour basculer entre le mode création et le mode aperçu.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-131">Click the **Preview Mode** button to toggle between design-mode and preview-mode.</span></span>

![Capture d’écran du concepteur](content/2019-08-01-13-58-27.png)

<span data-ttu-id="bdbf5-133">Le concepteur vient d’être mis à jour et prend maintenant en charge la création de modèles et fournit des **exemples de données** pour voir un aperçu de la carte en cours de conception.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-133">The newly updated Designer adds support for authoring templates and providing **Sample Data** to preview the card at design-time.</span></span>

<span data-ttu-id="bdbf5-134">Collez l’exemple ci-dessous dans le volet de l’**éditeur de charge utile de carte** :</span><span class="sxs-lookup"><span data-stu-id="bdbf5-134">Paste the example below into the **Card Payload Editor** pane:</span></span> 

<span data-ttu-id="bdbf5-135">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="bdbf5-135">**EmployeeCardTemplate.json**</span></span>

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
                            "url": "{photo}",
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
                            "text": "Hi {name}!",
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
            "text": "Your manager is: **{manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "{peers}",
                    "title": "{name}",
                    "value": "{title}"
                }
            ]
        }
    ]
}
```

<span data-ttu-id="bdbf5-136">Collez ensuite les données JSON ci-dessous dans l’**éditeur d’exemple de données**.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-136">Then paste the JSON data below into the **Sample Data Editor**.</span></span> 

<span data-ttu-id="bdbf5-137">L’**exemple de données** vous permet de voir exactement comment votre carte apparaîtra au moment de l’exécution, quand elle recevra des données réelles.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-137">**Sample Data** helps you see exactly how your card will appear at runtime when passed actual data.</span></span>

<span data-ttu-id="bdbf5-138">**EmployeeData**</span><span class="sxs-lookup"><span data-stu-id="bdbf5-138">**EmployeeData**</span></span>

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

<span data-ttu-id="bdbf5-139">Cliquez sur le bouton **Mode Aperçu**.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-139">Click the **Preview Mode** button.</span></span> <span data-ttu-id="bdbf5-140">Le rendu de la carte doit être conforme à l’exemple de données fourni ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-140">You should see the card render according to the sample data provided above.</span></span> <span data-ttu-id="bdbf5-141">N’hésitez pas à apporter des ajustements à l’exemple de données et observez en temps réel la mise à jour de la carte.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-141">Feel free to make tweaks to the sample data and watch the card update in realtime.</span></span>

<span data-ttu-id="bdbf5-142">**Félicitations**, vous venez de créer votre premier modèle de carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-142">**Congratulations**, you just authored your first Adaptive Card Template!</span></span> <span data-ttu-id="bdbf5-143">Voyons à présent comment peupler le modèle de données réelles.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-143">Next let's learn how to populate the template with real data.</span></span>

> <span data-ttu-id="bdbf5-144">En savoir plus sur le [langage de modèle](language.md)</span><span class="sxs-lookup"><span data-stu-id="bdbf5-144">Learn more about the [template language](language.md)</span></span>

## <a name="sdk-support"></a><span data-ttu-id="bdbf5-145">Prise en charge du Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="bdbf5-145">SDK support</span></span>

<span data-ttu-id="bdbf5-146">Les kits de développement logiciel (SDK) de création de modèles permettent de remplir un modèle de données réelles.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-146">The Templating SDKs make it possible to populate a template with real-data.</span></span>

> [!NOTE]
>
> <span data-ttu-id="bdbf5-147">Au cours de la période de préversion initiale, nous ne disposons que d’un ensemble limité de kits de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="bdbf5-147">During the initial preview we only have a limited set of SDKs available.</span></span> <span data-ttu-id="bdbf5-148">Lors de la mise en production, des bibliothèques de création de modèles seront disponibles pour chaque plateforme de cartes adaptatives prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-148">When we release there will be templating libraries for every supported Adaptive Cards platform.</span></span>

<span data-ttu-id="bdbf5-149">Plateforme</span><span class="sxs-lookup"><span data-stu-id="bdbf5-149">Platform</span></span> | <span data-ttu-id="bdbf5-150">Installer</span><span class="sxs-lookup"><span data-stu-id="bdbf5-150">Install</span></span> | <span data-ttu-id="bdbf5-151">Documentation</span><span class="sxs-lookup"><span data-stu-id="bdbf5-151">Documentation</span></span>
--- | --- | ---
<span data-ttu-id="bdbf5-152">JavaScript</span><span class="sxs-lookup"><span data-stu-id="bdbf5-152">JavaScript</span></span> | `npm install adaptivecards-templating` | [<span data-ttu-id="bdbf5-153">Documentation</span><span class="sxs-lookup"><span data-stu-id="bdbf5-153">Documentation</span></span>](https://www.npmjs.com/package/adaptivecards-templating)
<span data-ttu-id="bdbf5-154">.NET</span><span class="sxs-lookup"><span data-stu-id="bdbf5-154">.NET</span></span> | `nuget install AdaptiveCards.Templating` | [<span data-ttu-id="bdbf5-155">Documentation</span><span class="sxs-lookup"><span data-stu-id="bdbf5-155">Documentation</span></span>](https://docs.microsoft.com/en-us/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a><span data-ttu-id="bdbf5-156">Exemple JavaScript</span><span class="sxs-lookup"><span data-stu-id="bdbf5-156">JavaScript Example</span></span>

<span data-ttu-id="bdbf5-157">Le code JavaScript ci-dessous montre le modèle général qui sera utilisé pour peupler un modèle de données.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-157">The JavaScript below shows the general pattern that will be used to populate a template with data.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    // Data goes here
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

> <span data-ttu-id="bdbf5-158">En savoir plus sur les [Kits de développement logiciel (SDK) de création de modèles](sdk.md)</span><span class="sxs-lookup"><span data-stu-id="bdbf5-158">Learn more about the [templating SDKs](sdk.md)</span></span>

## <a name="template-service"></a><span data-ttu-id="bdbf5-159">Service de modèles</span><span class="sxs-lookup"><span data-stu-id="bdbf5-159">Template Service</span></span>

<span data-ttu-id="bdbf5-160">Le service de modèles de cartes adaptatives est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-160">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="bdbf5-161">Il est utile si vous voulez afficher des données sans vous ennuyer à écrire une carte adaptative personnalisée pour celles-ci.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-161">It's useful if you want to display some data but don't want to bother writing a custom Adaptive Card for it.</span></span>

<span data-ttu-id="bdbf5-162">L’API permettant d’obtenir un modèle est assez simple, mais le service offre en fait bien plus, notamment la possibilité d’analyser vos données et de trouver un modèle susceptible de vous convenir.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-162">The API to get a template is straight-forward enough, but the service actually offers much more, including the ability to analyze your data and find a template that might work for you.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="bdbf5-163">Tous les modèles sont des fichiers JSON plats stockés dans un référentiel GitHub afin que tout le monde puisse y contribuer, comme à tout autre code open source.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-163">All templates are flat JSON files stored in a GitHub repo so anyone can contribute to them like any other open source code.</span></span>

> <span data-ttu-id="bdbf5-164">En savoir plus sur [le service de modèles de carte](service.md)</span><span class="sxs-lookup"><span data-stu-id="bdbf5-164">Learn more about the [card template Service](service.md)</span></span>

## <a name="whats-next-and-sending-feedback"></a><span data-ttu-id="bdbf5-165">Étapes suivantes et envoi de commentaires</span><span class="sxs-lookup"><span data-stu-id="bdbf5-165">What's next and sending feedback</span></span>

<span data-ttu-id="bdbf5-166">La création de modèles et la séparation de la présentation et des données nous rapprochent de l’objectif de notre mission : « un écosystème pour l’échange de contenu de carte de manière commune et cohérente ».</span><span class="sxs-lookup"><span data-stu-id="bdbf5-166">Templating and the separation of presentation from data takes us a whole lot closer toward our mission: "an ecosystem for exchanging card content in a common and consistent way".</span></span>

<span data-ttu-id="bdbf5-167">Nous sommes impatients de pouvoir partager des informations supplémentaires dès que possible.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-167">We're eager to share more as soon as we can.</span></span> <span data-ttu-id="bdbf5-168">En attendant, veuillez nous faire part de vos commentaires ici, sur [GitHub](https://github.com/microsoft/AdaptiveCards) ou sur Twitter **[@MattHidinger](https://twitter.com/matthidinger)** / **#AdaptiveCards**.</span><span class="sxs-lookup"><span data-stu-id="bdbf5-168">In the meantime please give feedback here, [GitHub](https://github.com/microsoft/AdaptiveCards), or Twitter **[@MattHidinger](https://twitter.com/matthidinger)**/**#AdaptiveCards**.</span></span> 
