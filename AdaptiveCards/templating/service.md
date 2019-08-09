---
title: Service de modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 81d1e598b6157b6ba1fedbf458a7c624705afcd5
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878886"
---
# <a name="adaptive-cards-template-service"></a><span data-ttu-id="7ac3f-102">Service de modèle de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="7ac3f-102">Adaptive Cards Template Service</span></span>

<span data-ttu-id="7ac3f-103">Le service de modèle de cartes adaptatives est un service de preuve de concept qui permet à quiconque de rechercher, de contribuer et de partager un ensemble de modèles connus.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-103">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="7ac3f-104">Elle est utile si vous souhaitez afficher des données, mais ne souhaitez pas avoir à écrire une carte adaptative personnalisée pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-104">It's useful if you want to display some data but don't want to bother writing a custom adaptive card for it.</span></span>

> <span data-ttu-id="7ac3f-105">Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="7ac3f-106">*Termes et contrats*</span><span class="sxs-lookup"><span data-stu-id="7ac3f-106">*Terms and agreement*</span></span> 
> 
> <span data-ttu-id="7ac3f-107">Ce service de **niveau alpha** est fourni «en l’État», avec toutes les erreurs et n’est en aucun cas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-107">This **alpha-level** service is provided "as-is", with all faults and is not supported in any way.</span></span> <span data-ttu-id="7ac3f-108">Toute collecte de données à partir du service est soumise à la [déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).</span><span class="sxs-lookup"><span data-stu-id="7ac3f-108">Any data collection from the service is subject to the [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkID=824704).</span></span>
> 
> <span data-ttu-id="7ac3f-109">Ces fonctionnalités sont **en version préliminaire et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-109">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="7ac3f-110">Vos commentaires sont non seulement des bienvenues, mais essentiels pour garantir que nous fournissons les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-110">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-does-the-service-help-me"></a><span data-ttu-id="7ac3f-111">Comment le service m’aide-t-il?</span><span class="sxs-lookup"><span data-stu-id="7ac3f-111">How does the service help me?</span></span>

<span data-ttu-id="7ac3f-112">Supposons que vous disposiez d’un élément de données, peut-être des données financières, des données Microsoft Graph, des données schema.org ou des données personnalisées à partir de mon organisation.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-112">Let's say I just got a piece of data, maybe it's financial data, Microsoft Graph data, schema.org data, or custom data from within my organization.</span></span> 

<span data-ttu-id="7ac3f-113">Je souhaite à présent afficher les données à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-113">Now I want to display the data to a user.</span></span> 

<span data-ttu-id="7ac3f-114">Traditionnellement, cela signifie écrire du code d’interface utilisateur personnalisé dans toutes les piles frontales que je livre aux utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-114">Traditionally that means writing custom UI code in all of the front-end stacks that I deliver to end-users.</span></span>

<span data-ttu-id="7ac3f-115">Mais que se passe-t-il si mon application pouvait «apprendre» de nouveaux modèles d’interface utilisateur en fonction du type de données?</span><span class="sxs-lookup"><span data-stu-id="7ac3f-115">But what if there were a world where my app could "learn" new UI templates based on the type of data?</span></span> <span data-ttu-id="7ac3f-116">Un monde où tout le monde peut contribuer, améliorer et partager des modèles d’interface utilisateur communs, au sein de leurs propres projets, au sein d’une organisation ou pour l’ensemble de l’Internet.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-116">A world where anyone could contribute, enhance, and share common UI templates, within their own projects, within an organization, or for the entire internet.</span></span>

## <a name="what-is-the-card-template-service"></a><span data-ttu-id="7ac3f-117">Qu’est-ce que le service de modèle de carte?</span><span class="sxs-lookup"><span data-stu-id="7ac3f-117">What is the card template service?</span></span>

<span data-ttu-id="7ac3f-118">Le service de modèle de carte est un point de terminaison REST simple qui permet d’obtenir les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="7ac3f-118">The card template service is a simple REST endpoint that helps:</span></span>

* <span data-ttu-id="7ac3f-119">**Rechercher** un modèle en analysant la structure de vos données</span><span class="sxs-lookup"><span data-stu-id="7ac3f-119">**Find** a template by analyzing the structure of your data</span></span>
* <span data-ttu-id="7ac3f-120">**Obtenir** un modèle pour pouvoir le lier directement sur le client, *sans envoyer vos données au serveur ou sans jamais quitter l’appareil*</span><span class="sxs-lookup"><span data-stu-id="7ac3f-120">**Get** a template so you can bind it directly on the client, *without sending your data to the server or ever leaving the device*</span></span>
* <span data-ttu-id="7ac3f-121">**Remplissage** d’un modèle sur le serveur, lorsque la liaison de données côté client n’est pas appropriée ou possible</span><span class="sxs-lookup"><span data-stu-id="7ac3f-121">**Populate** a template on the server, when client-side data binding isn't appropriate or possible</span></span>

<span data-ttu-id="7ac3f-122">En arrière-plan, est:</span><span class="sxs-lookup"><span data-stu-id="7ac3f-122">Behind it all, is:</span></span>

* <span data-ttu-id="7ac3f-123">Un référentiel de modèles Open source partagé, sauvegardé par GitHub.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-123">A shared, open-source template repository backed by GitHub.</span></span> <span data-ttu-id="7ac3f-124">*(Le référentiel est actuellement privé, mais sera rendu public dès que nous mettrons des points faibles.)*</span><span class="sxs-lookup"><span data-stu-id="7ac3f-124">*(The repo is currently private but will be made public as soon as we tie up some loose ends)*</span></span>
* <span data-ttu-id="7ac3f-125">Tous les modèles sont des fichiers JSON plats dans le référentiel, ce qui permet de modifier, de contribuer et de partager une partie naturelle d’un flux de travail de développement.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-125">All the templates are flat JSON files in the repo, which makes editing, contributing, and sharing a natural part of a developer workflow.</span></span>
* <span data-ttu-id="7ac3f-126">Le code du service sera mis à disposition pour que vous puissiez l’héberger là où vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-126">The code for the service will be made available so you can host wherever makes the most sense to you.</span></span> 

## <a name="using-the-service"></a><span data-ttu-id="7ac3f-127">Utilisation du service</span><span class="sxs-lookup"><span data-stu-id="7ac3f-127">Using the service</span></span>

### <a name="get-all-templates"></a><span data-ttu-id="7ac3f-128">Récupération de tous les modèles</span><span class="sxs-lookup"><span data-stu-id="7ac3f-128">Get all templates</span></span> 

<span data-ttu-id="7ac3f-129">Ce point de terminaison retourne une liste de tous les modèles connus.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-129">This endpoint returns a list of all known templates.</span></span>

> `HTTP GET https://templates.adaptivecards.io/list`

<span data-ttu-id="7ac3f-130">**Extrait de réponse**</span><span class="sxs-lookup"><span data-stu-id="7ac3f-130">**Response excerpt**</span></span>

```json
{
  "graph.microsoft.com": {
    "templates": [
      {
        "file": "Files.json",
        "fullPath": "graph.microsoft.com/Files.json"
      },
      {
        "file": "Profile.json",
        "fullPath": "graph.microsoft.com/Profile.json"
      }
   ]
}
```

### <a name="find-a-template"></a><span data-ttu-id="7ac3f-131">Rechercher un modèle</span><span class="sxs-lookup"><span data-stu-id="7ac3f-131">Find a template</span></span>

<span data-ttu-id="7ac3f-132">Ce point de terminaison tente de trouver un modèle en analysant la structure de vos données.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-132">This endpoint tries to find a template by analyzing the structure of your data.</span></span>

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a><span data-ttu-id="7ac3f-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ac3f-133">Example</span></span>

<span data-ttu-id="7ac3f-134">Supposons que je clique juste sur un point de terminaison [Microsoft Graph](https://graph.microsoft.com) pour obtenir des données organisationnelles à mon sujet.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-134">Let's say I just hit a [Microsoft Graph](https://graph.microsoft.com) endpoint to get organizational data about me.</span></span>

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Capture d’écran de l’Explorateur graphique](content/2019-08-01-12-08-13.png)

<span data-ttu-id="7ac3f-136">Cette API a renvoyé des **données JSON**, mais comment l' **Afficher** aux utilisateurs à l’aide de cartes adaptatives?</span><span class="sxs-lookup"><span data-stu-id="7ac3f-136">That API returned **JSON data**, but how do I **display it** to users using Adaptive Cards?</span></span> 

<span data-ttu-id="7ac3f-137">Tout d’abord, je souhaite voir s’il existe un modèle pour ce type de données. je fais donc une requête `/find` http au point de terminaison avec `POST body`mes données dans le.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-137">First I want to see if a template exists for this type of data, so I make an HTTP request to the `/find` endpoint with my data in the `POST body`.</span></span>

```
HTTP POST https://templates.adaptivecards.io/find

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

<span data-ttu-id="7ac3f-138">**Lutte**</span><span class="sxs-lookup"><span data-stu-id="7ac3f-138">**Response:**</span></span>

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

<span data-ttu-id="7ac3f-139">Le service retourne une liste de tous les modèles correspondants, ainsi qu' `confidence` une indication de la fermeture de la correspondance.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-139">The service returns a list of any matching templates, along with a `confidence` indicating how close the match is.</span></span> <span data-ttu-id="7ac3f-140">Je peux maintenant utiliser cette URL de modèle pour **récupérer** le modèle ou le **remplir** côté serveur.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-140">Now I can use that template URL to **get** the template, or **populate** it server-side.</span></span>

### <a name="get-a-template"></a><span data-ttu-id="7ac3f-141">Obtenir un modèle</span><span class="sxs-lookup"><span data-stu-id="7ac3f-141">Get a template</span></span>

<span data-ttu-id="7ac3f-142">Un modèle récupéré à partir de ce point de terminaison peut être rempli avec les données au moment de l’exécution [à l’aide des Kits SDK templatng](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="7ac3f-142">A template retrieved from this endpoint can be populated with data at runtime [using the templatng SDKs](sdk.md).</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

<span data-ttu-id="7ac3f-143">Vous pouvez également inclure des «exemples de données» avec le modèle, ce qui rend la modification dans le concepteur plus conviviale:</span><span class="sxs-lookup"><span data-stu-id="7ac3f-143">You can also include "sample data" with the template, which makes editing in the designer more friendly:</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a><span data-ttu-id="7ac3f-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ac3f-144">Example</span></span>

<span data-ttu-id="7ac3f-145">Nous obtenons le modèle de `/find` profil Microsoft Graph qui a été retourné ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-145">Let's get the Microsoft Graph profile template that was returned from `/find` above.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="7ac3f-146">**Extrait de réponse**</span><span class="sxs-lookup"><span data-stu-id="7ac3f-146">**Response excerpt**</span></span>

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "{name}"
    },
    {
        // ...snip
    }
  ]
}
```

<span data-ttu-id="7ac3f-147">Utilisez maintenant ce modèle avec les [Kits de développement](sdk.md) logiciel (SDK) de création de modèles pour créer une carte adaptative prête à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-147">Now use this template with the [templating SDKs](sdk.md) to create a ready-to-render Adaptive Card.</span></span>

### <a name="populate-a-template-server-side"></a><span data-ttu-id="7ac3f-148">Remplir un modèle côté serveur</span><span class="sxs-lookup"><span data-stu-id="7ac3f-148">Populate a template server-side</span></span>

<span data-ttu-id="7ac3f-149">Dans certains cas, il peut s’avérer inutile de remplir un modèle sur le client.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-149">In some cases it may not make sense to populate a template on the client.</span></span>  <span data-ttu-id="7ac3f-150">Pour ces cas d’utilisation, vous pouvez faire en sorte que le service retourne une carte adaptative entièrement remplie, prête à être transmise à n’importe quel convertisseur de carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-150">For these use cases, you can have the service return a fully-populated Adaptive Card, ready to be passed to any Adaptive Card Renderer.</span></span>

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a><span data-ttu-id="7ac3f-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ac3f-151">Example</span></span>

<span data-ttu-id="7ac3f-152">Nous allons remplir le modèle de profil Microsoft Graph qui a été `/find` retourné à l’aide des données ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-152">Let's populate the Microsoft Graph profile template that was returned from `/find` using the data above.</span></span>

```
HTTP POST https://templates.adaptivecards.io/graph.microsoft.com/Profile.json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users/$entity",
    "businessPhones": [
        "+1 412 555 0109"
    ],
    "displayName": "Megan Bowen",
    "givenName": "Megan",
    "jobTitle": "Auditor",
    "mail": "MeganB@M365x214355.onmicrosoft.com",
    "mobilePhone": null,
    "officeLocation": "12/1110",
    "preferredLanguage": "en-US",
    "surname": "Bowen",
    "userPrincipalName": "MeganB@M365x214355.onmicrosoft.com",
    "id": "48d31887-5fad-4d73-a9f5-3c356e68a038"
}
```

<span data-ttu-id="7ac3f-153">**Extrait de réponse**</span><span class="sxs-lookup"><span data-stu-id="7ac3f-153">**Response excerpt**</span></span>

```json
{
  "type": "AdaptiveCard",
  "version": "1.0",
  "body": [
    {
      "type": "TextBlock",
      "size": "Medium",
      "weight": "Bolder",
      "text": "Megan Bowen"
    },
    {
        // ...snip
    }
  ]
}
```

<span data-ttu-id="7ac3f-154">Notez que la réponse a remplacé le texte de la `TextBlock` première `"Megan Bowen"` par au `"{name}"`lieu de, comme `GET` dans la demande.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-154">Notice how the response replaced the text of the first `TextBlock` with `"Megan Bowen"` instead of `"{name}"`, as in the `GET` request.</span></span> <span data-ttu-id="7ac3f-155">Ce AdaptiveCard peut désormais être passé à n’importe quel convertisseur de carte adaptative sans passer par la création de modèles côté client.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-155">This AdaptiveCard can now be passed to any Adaptive Card renderer without going through client-side templating.</span></span>

## <a name="contributing-templates"></a><span data-ttu-id="7ac3f-156">Modèles contributeurs</span><span class="sxs-lookup"><span data-stu-id="7ac3f-156">Contributing templates</span></span>

<span data-ttu-id="7ac3f-157">Le service de modèle est associé à un GitHub référentiel (qui est actuellement **privé**), mais nous allons ouvrir la source une fois que nous aurons des terminaisons libres.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-157">The template service is backed by a GitHub repo (which is currently **private**), but we will open source once we tie up some loose ends.</span></span>

<span data-ttu-id="7ac3f-158">Nous espérons qu’en utilisant GitHub comme magasin de stockage pour les modèles, nous pouvons «démocratiser» le processus de création, d’amélioration et de partage de modèles.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-158">Our hope is that by using GitHub as a backing store for the templates, we can "democratize" the process of authoring, enhancing, and sharing templates.</span></span> <span data-ttu-id="7ac3f-159">Tout le monde peut soumettre une demande de tirage incluant un modèle entièrement nouveau ou apporter des améliorations à celles qui existent déjà... tout cela dans l’expérience conviviale du développeur de GitHub.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-159">Anyone can submit a Pull Request that includes an entirely new template, or make enhancements to existing ones... all within the developer-friendly experience of GitHub.</span></span>

## <a name="self-hosting-the-service"></a><span data-ttu-id="7ac3f-160">Hébergement automatique du service</span><span class="sxs-lookup"><span data-stu-id="7ac3f-160">Self-hosting the service</span></span>

<span data-ttu-id="7ac3f-161">Tous les types de données ne sont pas adaptés au service de modèle de cartes adaptatives «central `https://templates.adaptivecards.io`» hébergé à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-161">Not all types of data are appropriate for the "central" Adaptive Cards template service hosted at `https://templates.adaptivecards.io`.</span></span> 

<span data-ttu-id="7ac3f-162">Nous voulons nous assurer que tout le monde peut héberger le service de modèle au sein de votre organisation. le code source sera donc mis à disposition et nous faciliterons le déploiement sur Azure ou votre propre serveur principal.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-162">We want to make sure anyone can host the template service within your organization, so the source code will be made available and we'll make it very simple to deploy to Azure or your own back-end.</span></span>

<span data-ttu-id="7ac3f-163">En savoir plus à ce jour ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="7ac3f-163">More on this at a later date.</span></span>