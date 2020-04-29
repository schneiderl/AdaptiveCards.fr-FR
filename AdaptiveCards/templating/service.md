---
title: Service de modèles de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: db211fc3bac27dc980ae87983a918a35730f8e5e
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82136185"
---
# <a name="adaptive-cards-template-service"></a><span data-ttu-id="86b7c-102">Service de modèles de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="86b7c-102">Adaptive Cards Template Service</span></span>

<span data-ttu-id="86b7c-103">Le service de modèles de cartes adaptatives est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.</span><span class="sxs-lookup"><span data-stu-id="86b7c-103">The Adaptive Cards Template Service is a proof-of-concept service that allows anyone to find, contribute to, and share a set of well-known templates.</span></span>

<span data-ttu-id="86b7c-104">Il est utile si vous voulez afficher des données sans avoir à écrire une carte adaptative personnalisée pour celles-ci.</span><span class="sxs-lookup"><span data-stu-id="86b7c-104">It's useful if you want to display some data but don't want to bother writing a custom adaptive card for it.</span></span>

> <span data-ttu-id="86b7c-105">Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).</span><span class="sxs-lookup"><span data-stu-id="86b7c-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="86b7c-106">*Termes et contrat*</span><span class="sxs-lookup"><span data-stu-id="86b7c-106">*Terms and agreement*</span></span> 
> 
> <span data-ttu-id="86b7c-107">Ce service de **niveau alpha** est fourni « en l’état », avec tous ses défauts et sans aucun support.</span><span class="sxs-lookup"><span data-stu-id="86b7c-107">This **alpha-level** service is provided "as-is", with all faults and is not supported in any way.</span></span> <span data-ttu-id="86b7c-108">Toute collecte de données à partir du service est soumise à la [déclaration de confidentialité de Microsoft](https://go.microsoft.com/fwlink/?LinkID=824704).</span><span class="sxs-lookup"><span data-stu-id="86b7c-108">Any data collection from the service is subject to the [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkID=824704).</span></span>
> 
> <span data-ttu-id="86b7c-109">Ces fonctionnalités sont **en préversion et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="86b7c-109">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="86b7c-110">Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="86b7c-110">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

## <a name="how-does-the-service-help-me"></a><span data-ttu-id="86b7c-111">En quoi le service peut-il m’aider ?</span><span class="sxs-lookup"><span data-stu-id="86b7c-111">How does the service help me?</span></span>

<span data-ttu-id="86b7c-112">Prenons un exemple : je viens de recevoir des données. Il peut s’agir de données financières, de données Microsoft Graph, de données schema.org ou de données personnalisées provenant de mon organisation.</span><span class="sxs-lookup"><span data-stu-id="86b7c-112">Let's say I just got a piece of data, maybe it's financial data, Microsoft Graph data, schema.org data, or custom data from within my organization.</span></span> 

<span data-ttu-id="86b7c-113">Je souhaite les présenter à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="86b7c-113">Now I want to display the data to a user.</span></span> 

<span data-ttu-id="86b7c-114">Pour cela, je dois normalement écrire un code d’interface utilisateur personnalisé dans toutes les piles front-end que je livre aux utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="86b7c-114">Traditionally that means writing custom UI code in all of the front-end stacks that I deliver to end-users.</span></span>

<span data-ttu-id="86b7c-115">Imaginons maintenant un monde dans lequel mon application pourrait « apprendre » de nouveaux modèles d’interface utilisateur en fonction du type de données.</span><span class="sxs-lookup"><span data-stu-id="86b7c-115">But what if there were a world where my app could "learn" new UI templates based on the type of data?</span></span> <span data-ttu-id="86b7c-116">Un monde où quiconque pourrait participer à l’élaboration de modèles d’interface utilisateur communs, les améliorer et les partager au sein de leurs propres projets, au sein d’une organisation voire à l’échelle de l’Internet.</span><span class="sxs-lookup"><span data-stu-id="86b7c-116">A world where anyone could contribute, enhance, and share common UI templates, within their own projects, within an organization, or for the entire internet.</span></span>

## <a name="what-is-the-card-template-service"></a><span data-ttu-id="86b7c-117">Qu’est-ce que le service de modèles de cartes ?</span><span class="sxs-lookup"><span data-stu-id="86b7c-117">What is the card template service?</span></span>

<span data-ttu-id="86b7c-118">Le service de modèles de cartes est un point de terminaison REST simple qui vous aide à effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="86b7c-118">The card template service is a simple REST endpoint that helps:</span></span>

* <span data-ttu-id="86b7c-119">**Rechercher** un modèle en analysant la structure de vos données</span><span class="sxs-lookup"><span data-stu-id="86b7c-119">**Find** a template by analyzing the structure of your data</span></span>
* <span data-ttu-id="86b7c-120">**Obtenir** un modèle pour pouvoir le lier directement sur le client *sans envoyer vos données au serveur ni quitter l’appareil*</span><span class="sxs-lookup"><span data-stu-id="86b7c-120">**Get** a template so you can bind it directly on the client, *without sending your data to the server or ever leaving the device*</span></span>
* <span data-ttu-id="86b7c-121">**Remplir** un modèle sur le serveur quand la liaison de données côté client n’est pas appropriée ou possible</span><span class="sxs-lookup"><span data-stu-id="86b7c-121">**Populate** a template on the server, when client-side data binding isn't appropriate or possible</span></span>

<span data-ttu-id="86b7c-122">Derrière tout cela :</span><span class="sxs-lookup"><span data-stu-id="86b7c-122">Behind it all, is:</span></span>

* <span data-ttu-id="86b7c-123">Un dépôt de modèles open source et partagés, basé sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="86b7c-123">A shared, open-source template repository backed by GitHub.</span></span> <span data-ttu-id="86b7c-124">*(Le dépôt est actuellement privé, mais il sera rendu public dès que nous aurons réglé quelques détails.)*</span><span class="sxs-lookup"><span data-stu-id="86b7c-124">*(The repo is currently private but will be made public as soon as we tie up some loose ends)*</span></span>
* <span data-ttu-id="86b7c-125">Tous les modèles étant des fichiers JSON plats dans le dépôt, les opérations de modification, de contribution et de partage s’inscrivent naturellement dans un workflow de développeur.</span><span class="sxs-lookup"><span data-stu-id="86b7c-125">All the templates are flat JSON files in the repo, which makes editing, contributing, and sharing a natural part of a developer workflow.</span></span>
* <span data-ttu-id="86b7c-126">Vous aurez également accès au code du service pour pouvoir l’héberger là où vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="86b7c-126">The code for the service will be made available so you can host wherever makes the most sense to you.</span></span> 

## <a name="using-the-service"></a><span data-ttu-id="86b7c-127">Utilisation du service</span><span class="sxs-lookup"><span data-stu-id="86b7c-127">Using the service</span></span>

### <a name="get-all-templates"></a><span data-ttu-id="86b7c-128">Obtenir tous les modèles</span><span class="sxs-lookup"><span data-stu-id="86b7c-128">Get all templates</span></span> 

<span data-ttu-id="86b7c-129">Ce point de terminaison retourne une liste de tous les modèles connus.</span><span class="sxs-lookup"><span data-stu-id="86b7c-129">This endpoint returns a list of all known templates.</span></span>

> `HTTP GET https://templates.adaptivecards.io/list`

<span data-ttu-id="86b7c-130">**Extrait de la réponse**</span><span class="sxs-lookup"><span data-stu-id="86b7c-130">**Response excerpt**</span></span>

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

### <a name="find-a-template"></a><span data-ttu-id="86b7c-131">Trouver un modèle</span><span class="sxs-lookup"><span data-stu-id="86b7c-131">Find a template</span></span>

<span data-ttu-id="86b7c-132">Ce point de terminaison tente de trouver un modèle en analysant la structure de vos données.</span><span class="sxs-lookup"><span data-stu-id="86b7c-132">This endpoint tries to find a template by analyzing the structure of your data.</span></span>

> `HTTP POST https://templates.adaptivecards.io/find`

#### <a name="example"></a><span data-ttu-id="86b7c-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="86b7c-133">Example</span></span>

<span data-ttu-id="86b7c-134">Prenons un exemple : je viens d’accéder à un point de terminaison [Microsoft Graph](https://graph.microsoft.com) pour obtenir des données organisationnelles me concernant.</span><span class="sxs-lookup"><span data-stu-id="86b7c-134">Let's say I access a [Microsoft Graph](https://graph.microsoft.com) endpoint to get organizational data about me.</span></span>

> `HTTP GET https://graph.microsoft.com/v1.0/me/`

![Capture d’écran de l’Afficheur Graph](content/2019-08-01-12-08-13.png)

<span data-ttu-id="86b7c-136">Cette API retourne des **données JSON**, mais comment puis-je **les présenter** aux utilisateurs au moyen de cartes adaptatives ?</span><span class="sxs-lookup"><span data-stu-id="86b7c-136">That API returned **JSON data**, but how do I **display it** to users using Adaptive Cards?</span></span> 

<span data-ttu-id="86b7c-137">Tout d’abord, je souhaite voir s’il existe un modèle pour ce type de données. J’envoie donc une requête HTTP au point de terminaison `/find` avec mes données dans `POST body`.</span><span class="sxs-lookup"><span data-stu-id="86b7c-137">First I want to see if a template exists for this type of data, so I make an HTTP request to the `/find` endpoint with my data in the `POST body`.</span></span>

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

<span data-ttu-id="86b7c-138">**Réponse :**</span><span class="sxs-lookup"><span data-stu-id="86b7c-138">**Response:**</span></span>

```json
[
  {
    "templateUrl": "graph.microsoft.com/Profile.json",
    "confidence": 1
  }
]
```

<span data-ttu-id="86b7c-139">Le service retourne une liste de tous les modèles correspondants, ainsi qu’une valeur `confidence` indiquant le degré de correspondance.</span><span class="sxs-lookup"><span data-stu-id="86b7c-139">The service returns a list of any matching templates, along with a `confidence` indicating how close the match is.</span></span> <span data-ttu-id="86b7c-140">Je peux à présent utiliser l’URL de ce modèle pour **obtenir** le modèle ou le **remplir** côté serveur.</span><span class="sxs-lookup"><span data-stu-id="86b7c-140">Now I can use that template URL to **get** the template, or **populate** it server-side.</span></span>

### <a name="get-a-template"></a><span data-ttu-id="86b7c-141">Obtenir un modèle</span><span class="sxs-lookup"><span data-stu-id="86b7c-141">Get a template</span></span>

<span data-ttu-id="86b7c-142">Un modèle récupéré à partir de ce point de terminaison peut être rempli avec des données au moment de l’exécution [à l’aide des kits SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="86b7c-142">A template retrieved from this endpoint can be populated with data at runtime [using the templatng SDKs](sdk.md).</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]`

<span data-ttu-id="86b7c-143">Vous pouvez également inclure un « exemple de données » avec le modèle, ce qui rend la modification dans le concepteur plus conviviale :</span><span class="sxs-lookup"><span data-stu-id="86b7c-143">You can also include "sample data" with the template, which makes editing in the designer more friendly:</span></span>

> `HTTP GET https://templates.adaptivecards.io/[TEMPLATE-PATH]?sampleData=true`

#### <a name="example"></a><span data-ttu-id="86b7c-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="86b7c-144">Example</span></span>

<span data-ttu-id="86b7c-145">Nous obtenons le modèle de profil Microsoft Graph retourné par `/find` ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="86b7c-145">Let's get the Microsoft Graph profile template that was returned from `/find` above.</span></span>

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

<span data-ttu-id="86b7c-146">**Extrait de la réponse**</span><span class="sxs-lookup"><span data-stu-id="86b7c-146">**Response excerpt**</span></span>

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

<span data-ttu-id="86b7c-147">Utilisez maintenant ce modèle avec les [kits SDK de création de modèles](sdk.md) pour créer une carte adaptative prête pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="86b7c-147">Now use this template with the [templating SDKs](sdk.md) to create a ready-to-render Adaptive Card.</span></span>

### <a name="populate-a-template-server-side"></a><span data-ttu-id="86b7c-148">Remplir un modèle côté serveur</span><span class="sxs-lookup"><span data-stu-id="86b7c-148">Populate a template server-side</span></span>

<span data-ttu-id="86b7c-149">Dans certains cas, il est inutile de remplir un modèle sur le client.</span><span class="sxs-lookup"><span data-stu-id="86b7c-149">In some cases it may not make sense to populate a template on the client.</span></span>  <span data-ttu-id="86b7c-150">Vous pouvez alors faire en sorte que le service retourne une carte adaptative entièrement remplie, prête à être passée à n’importe quel renderer de carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="86b7c-150">For these use cases, you can have the service return a fully-populated Adaptive Card, ready to be passed to any Adaptive Card Renderer.</span></span>

> `HTTP POST https://templates.adaptivecards.io/[TEMPLATE-PATH]`

#### <a name="example"></a><span data-ttu-id="86b7c-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="86b7c-151">Example</span></span>

<span data-ttu-id="86b7c-152">Remplissons le modèle de profil Microsoft Graph retourné par `/find` à l’aide des données ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="86b7c-152">Let's populate the Microsoft Graph profile template that was returned from `/find` using the data above.</span></span>

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

<span data-ttu-id="86b7c-153">**Extrait de la réponse**</span><span class="sxs-lookup"><span data-stu-id="86b7c-153">**Response excerpt**</span></span>

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

<span data-ttu-id="86b7c-154">Notez que la réponse remplace le texte `"{name}"` du premier `TextBlock` par `"Megan Bowen"`, comme dans la requête `GET`.</span><span class="sxs-lookup"><span data-stu-id="86b7c-154">Notice how the response replaced the text of the first `TextBlock` with `"Megan Bowen"` instead of `"{name}"`, as in the `GET` request.</span></span> <span data-ttu-id="86b7c-155">Cette carte adaptative peut désormais être passée à n’importe quel renderer de carte adaptative sans passer par la création de modèles côté client.</span><span class="sxs-lookup"><span data-stu-id="86b7c-155">This AdaptiveCard can now be passed to any Adaptive Card renderer without going through client-side templating.</span></span>

## <a name="contributing-templates"></a><span data-ttu-id="86b7c-156">Contribution aux modèles</span><span class="sxs-lookup"><span data-stu-id="86b7c-156">Contributing templates</span></span>

<span data-ttu-id="86b7c-157">Les modèles sont hébergés sur GitHub dans le dépôt [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates).</span><span class="sxs-lookup"><span data-stu-id="86b7c-157">The templates are hosted on GitHub in the [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates) repo.</span></span>

<span data-ttu-id="86b7c-158">Nous espérons que l’utilisation de GitHub comme magasin de stockage pour les modèles nous permettra de « démocratiser » le processus de création, d’amélioration et de partage de modèles.</span><span class="sxs-lookup"><span data-stu-id="86b7c-158">Our hope is that by using GitHub as a backing store for the templates, we can "democratize" the process of authoring, enhancing, and sharing templates.</span></span> <span data-ttu-id="86b7c-159">N’importe qui peut envoyer une demande de tirage (pull request) incluant un modèle entièrement nouveau ou améliorer des modèles existants... le tout dans l’expérience de développement conviviale de GitHub.</span><span class="sxs-lookup"><span data-stu-id="86b7c-159">Anyone can submit a Pull Request that includes an entirely new template, or make enhancements to existing ones... all within the developer-friendly experience of GitHub.</span></span>

## <a name="self-hosting-the-service"></a><span data-ttu-id="86b7c-160">Auto-hébergement du service</span><span class="sxs-lookup"><span data-stu-id="86b7c-160">Self-hosting the service</span></span>

<span data-ttu-id="86b7c-161">Tous les types de données ne sont pas appropriés pour le service de modèles de cartes adaptatives « central » hébergé sur `https://templates.adaptivecards.io`.</span><span class="sxs-lookup"><span data-stu-id="86b7c-161">Not all types of data are appropriate for the "central" Adaptive Cards template service hosted at `https://templates.adaptivecards.io`.</span></span> 

<span data-ttu-id="86b7c-162">Nous voulons nous assurer que tout le monde peut héberger le service de modèles au sein de votre organisation, c’est pourquoi le code source est disponible sur GitHub et peut être facilement déployé sur votre propre fonction Azure.</span><span class="sxs-lookup"><span data-stu-id="86b7c-162">We want to make sure anyone can host the template service within your organization, so the source code is available on GitHub and can be easily deployed to your own Azure Function.</span></span> 

<span data-ttu-id="86b7c-163">Commencez ici ➡ [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates)</span><span class="sxs-lookup"><span data-stu-id="86b7c-163">Get started here ➡ [adaptivecards-templates](https://github.com/microsoft/adaptivecards-templates)</span></span>
