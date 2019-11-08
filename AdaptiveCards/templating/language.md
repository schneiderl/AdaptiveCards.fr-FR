---
title: Langue du modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 42a1f43fbcfe1416820637af750acc960b9effde
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750400"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="b4f3c-102">Langue du modèle de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="b4f3c-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="b4f3c-103">La création de modèles permet de séparer les **données** de la **disposition** dans votre carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="b4f3c-104">La langue du modèle est la syntaxe utilisée pour créer un modèle.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="b4f3c-105">Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="b4f3c-106">Ces fonctionnalités sont **en préversion et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="b4f3c-107">Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="b4f3c-108">Lors de la création d’un modèle, vous pouvez spécifier les données Inline avec la charge utile `AdaptiveCard`, ou au moment de l’exécution à l’aide des [Kits SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b4f3c-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="b4f3c-109">Spécifier les données dans la carte</span><span class="sxs-lookup"><span data-stu-id="b4f3c-109">Specify data within the card</span></span>

<span data-ttu-id="b4f3c-110">Pour fournir des données directement dans la charge utile de la carte, ajoutez simplement un attribut `$data` à votre `AdaptiveCard` (voir ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="b4f3c-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="b4f3c-111">Liaison aux données</span><span class="sxs-lookup"><span data-stu-id="b4f3c-111">Binding to the data</span></span>

<span data-ttu-id="b4f3c-112">Vous pouvez lier les données au sein de la `body` ou `actions` de la carte.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="b4f3c-113">La syntaxe de liaison commence par `{` et se termine par `}`.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="b4f3c-114">Par exemple, `{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="b4f3c-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="b4f3c-115">Notation de points pour accéder aux sous-objets</span><span class="sxs-lookup"><span data-stu-id="b4f3c-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="b4f3c-116">Syntaxe de l’indexeur pour récupérer des propriétés par clé ou éléments dans un tableau</span><span class="sxs-lookup"><span data-stu-id="b4f3c-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="b4f3c-117">Gestion des valeurs NULL gracieuses pour les hiérarchies profondes</span><span class="sxs-lookup"><span data-stu-id="b4f3c-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="b4f3c-118">*Documentation de la syntaxe d’échappement bientôt disponible*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-118">*Escape syntax documentation to come soon*</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    },
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="b4f3c-119">Séparation du modèle des données</span><span class="sxs-lookup"><span data-stu-id="b4f3c-119">Separating the template from the data</span></span>

<span data-ttu-id="b4f3c-120">En guise d’alternative (et plus probable), vous allez créer un « modèle » de carte réutilisable sans inclure les données.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="b4f3c-121">Ce modèle peut être stocké en tant que fichier et ajouté au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="b4f3c-122">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-122">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptivCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

<span data-ttu-id="b4f3c-123">Ensuite, chargez-la et fournissez les données au moment de l’exécution à l’aide des [Kits SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b4f3c-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="b4f3c-124">**Exemple JavaScript**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-124">**JavaScript example**</span></span>

<span data-ttu-id="b4f3c-125">Utilisation du package [adaptivecards-Templating](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="b4f3c-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    "employee": {
        "name": "Matt",
        "manager": { "name": "Thomas" },
        "peers": [{
            "name": "Andrew" 
        }, { 
            "name": "Lei"
        }, { 
            "name": "Mary Anne"
        }, { 
            "name": "Adam"
        }]
    }
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a><span data-ttu-id="b4f3c-126">Prise en charge du concepteur</span><span class="sxs-lookup"><span data-stu-id="b4f3c-126">Designer Support</span></span>

<span data-ttu-id="b4f3c-127">Le concepteur de cartes adaptatives a été mis à jour pour prendre en charge la création de modèles.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="b4f3c-128">Essayez-le à l’adresse suivante :  **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-128">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="b4f3c-129">[image ![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="b4f3c-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="b4f3c-130">**Exemple d’éditeur de données** : spécifiez des exemples de données ici pour afficher la carte liée aux données en mode aperçu.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-130">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="b4f3c-131">Ce volet contient un petit bouton qui permet de remplir la structure de données à partir des données d’exemple existantes.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-131">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="b4f3c-132">**Structure de données** : il s’agit de la structure de vos exemples de données.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-132">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="b4f3c-133">Les champs peuvent être glissés sur l’aire de conception pour créer une liaison avec eux</span><span class="sxs-lookup"><span data-stu-id="b4f3c-133">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="b4f3c-134">**Mode aperçu** -Appuyez sur le bouton de barre d’outils pour basculer entre l’expérience de modification et l’exemple d’expérience de l’aperçu des données</span><span class="sxs-lookup"><span data-stu-id="b4f3c-134">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="b4f3c-135">**Ouvrir l’exemple** : cliquez sur ce bouton pour ouvrir divers exemples de charge utile.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-135">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="b4f3c-136">Liaison avancée</span><span class="sxs-lookup"><span data-stu-id="b4f3c-136">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="b4f3c-137">Portées de liaison</span><span class="sxs-lookup"><span data-stu-id="b4f3c-137">Binding scopes</span></span>

<span data-ttu-id="b4f3c-138">Il existe quelques mots clés réservés pour accéder à différentes étendues de liaison.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-138">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="b4f3c-139">*Remarque :* tous ces éléments ne sont pas implémentés dans la version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-139">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="b4f3c-140">Assignation d’un contexte de données à des éléments</span><span class="sxs-lookup"><span data-stu-id="b4f3c-140">Assigning a data context to elements</span></span>

<span data-ttu-id="b4f3c-141">Pour assigner un « contexte de données » à un élément, ajoutez un attribut `$data` à l’élément.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-141">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

```json
{
    "type": "Container",
    "$data": "{mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': {mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: {$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="b4f3c-142">Répétition d’éléments dans un tableau</span><span class="sxs-lookup"><span data-stu-id="b4f3c-142">Repeating items in an array</span></span>

<span data-ttu-id="b4f3c-143">Cette partie est un peu « Dark Magic ».</span><span class="sxs-lookup"><span data-stu-id="b4f3c-143">This part is a bit of "dark magic".</span></span> <span data-ttu-id="b4f3c-144">Commentaires de bienvenue.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-144">Feedback welcome.</span></span>

* <span data-ttu-id="b4f3c-145">Si la propriété `$data` d’objets est définie sur un **tableau**, l' **objet lui-même est répété pour chaque élément du tableau.**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-145">If the objects' `$data` property is set to an **array**, then the **object itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="b4f3c-146">À mesure qu’il est répété, les `$data` utilisées dans les liaisons de propriété sont limitées à l' **élément individuel** dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-146">As it is being repeated, `$data` used in property bindings are scoped to the **individual item** within the array.</span></span>

<span data-ttu-id="b4f3c-147">Par exemple, le `TextBlock` ci-dessous est répété 3 fois, car il est `$data` est un tableau.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-147">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="b4f3c-148">Notez que la propriété `text` est liée à la propriété `name` d’un objet individuel dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-148">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

```json
{
    "type": "Container",
    "items": [
        {
            "type": "TextBlock",
            "$data": [
                { "name": "Matt" }, 
                { "name": "David" }, 
                { "name": "Thomas" }
            ],
            "text": "{name}"
        }
    ]
}
```

<span data-ttu-id="b4f3c-149">**Ce qui donne :**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-149">**Resulting in:**</span></span>

```json
{
    "type": "Container",
    "items": [ 
        {
            "type": "TextBlock",
            "text": "Matt"
        },
        {
            "type": "TextBlock",
            "text": "David"
        }
        {
            "type": "TextBlock",
            "text": "Thomas"
        }
    ]
}
```

## <a name="functions"></a><span data-ttu-id="b4f3c-150">Fonctions</span><span class="sxs-lookup"><span data-stu-id="b4f3c-150">Functions</span></span>

<span data-ttu-id="b4f3c-151">Aucun langage de création de modèles n’est terminé sans aucune fonction d’assistance.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-151">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="b4f3c-152">Nous allons fournir un ensemble standard de fonctions qui fonctionnent sur chaque kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="b4f3c-152">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="b4f3c-153">La syntaxe ici est toujours active dans l’air. Veuillez recommencer, mais voici ce que nous avons planifié :</span><span class="sxs-lookup"><span data-stu-id="b4f3c-153">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="b4f3c-154">Fonctions de chaîne</span><span class="sxs-lookup"><span data-stu-id="b4f3c-154">String functions</span></span>

* <span data-ttu-id="b4f3c-155">substr</span><span class="sxs-lookup"><span data-stu-id="b4f3c-155">substr</span></span>
* <span data-ttu-id="b4f3c-156">indexOf *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-156">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="b4f3c-157">toUpper *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-157">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="b4f3c-158">toLower *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-158">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="b4f3c-159">Fonctions numériques</span><span class="sxs-lookup"><span data-stu-id="b4f3c-159">Number functions</span></span>

* <span data-ttu-id="b4f3c-160">Mise en forme (devise, décimal, etc.) *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-160">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="b4f3c-161">Fonctions de date</span><span class="sxs-lookup"><span data-stu-id="b4f3c-161">Date functions</span></span>

* <span data-ttu-id="b4f3c-162">Analyse des formats de chaîne de date bien connus *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-162">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="b4f3c-163">Mise en forme des représentations de date/heure connues *(ne fonctionnant pas encore)*</span><span class="sxs-lookup"><span data-stu-id="b4f3c-163">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="b4f3c-164">Fonctions conditionnelles</span><span class="sxs-lookup"><span data-stu-id="b4f3c-164">Conditional functions</span></span>

* <span data-ttu-id="b4f3c-165">if (*expression*, *TrueValue*, *FalseValue*)</span><span class="sxs-lookup"><span data-stu-id="b4f3c-165">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="b4f3c-166">**exemple de`if`**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-166">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="b4f3c-167">Manipulation de données</span><span class="sxs-lookup"><span data-stu-id="b4f3c-167">Data manipulation</span></span>

* <span data-ttu-id="b4f3c-168">JSON. Parse-capacité à analyser une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="b4f3c-168">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="b4f3c-169">**exemple de`JSON.parse`**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-169">**`JSON.parse` example**</span></span>

<span data-ttu-id="b4f3c-170">Il s’agit d’une réponse Azure DevOps où la propriété `message` est une chaîne sérialisée au format JSON.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-170">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="b4f3c-171">Pour accéder aux valeurs de la chaîne, nous devons utiliser la fonction `JSON.parse` dans notre modèle.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-171">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="b4f3c-172">**Données**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-172">**Data**</span></span> 

```json
{
    "id": "1291525457129548",
    "status": 4,
    "author": "Matt Hidinger",
    "message": "{\"type\":\"Deployment\",\"buildId\":\"9542982\",\"releaseId\":\"129\",\"buildNumber\":\"20180504.3\",\"releaseName\":\"Release-104\",\"repoProvider\":\"GitHub\"}",
    "start_time": "2018-05-04T18:05:33.3087147Z",
    "end_time": "2018-05-04T18:05:33.3087147Z"
}
```

<span data-ttu-id="b4f3c-173">**Syntaxe**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-173">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="b4f3c-174">**Ce qui se traduit par**</span><span class="sxs-lookup"><span data-stu-id="b4f3c-174">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="b4f3c-175">Fonctions personnalisées</span><span class="sxs-lookup"><span data-stu-id="b4f3c-175">Custom functions</span></span>

<span data-ttu-id="b4f3c-176">Nous voulons nous assurer que les hôtes peuvent ajouter des fonctions personnalisées, ce qui signifie que nous avons besoin d’une prise en charge fiable de la prise en charge de secours si une fonction n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="b4f3c-176">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="b4f3c-177">Nous sommes toujours en cours d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-177">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="b4f3c-178">Disposition conditionnelle</span><span class="sxs-lookup"><span data-stu-id="b4f3c-178">Conditional layout</span></span>

<span data-ttu-id="b4f3c-179">Pour supprimer l’intégralité d’un élément si une condition est remplie, utilisez la propriété `$when`.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-179">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="b4f3c-180">Si `$when` prend la valeur `false` l’élément ne s’affiche pas à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-180">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "{price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "{price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a><span data-ttu-id="b4f3c-181">Composition de modèles</span><span class="sxs-lookup"><span data-stu-id="b4f3c-181">Composing templates</span></span>

<span data-ttu-id="b4f3c-182">Il n’existe actuellement aucune prise en charge pour composer les « parties » du modèle.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-182">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="b4f3c-183">Toutefois, nous explorons les options et espérons partager plus tôt.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-183">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="b4f3c-184">Toutes les pensées ici Bienvenue !</span><span class="sxs-lookup"><span data-stu-id="b4f3c-184">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="b4f3c-185">Exemples</span><span class="sxs-lookup"><span data-stu-id="b4f3c-185">Examples</span></span>

<span data-ttu-id="b4f3c-186">Parcourez la [page d’exemples](https://adaptivecards.io/samples) mise à jour pour explorer toutes sortes de cartes basées sur un modèle.</span><span class="sxs-lookup"><span data-stu-id="b4f3c-186">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
