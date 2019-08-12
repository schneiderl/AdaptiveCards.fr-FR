---
title: Langue du modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 993618ed94eaea1a004c7893a5a3927c0d818cd6
ms.sourcegitcommit: a16f53ba10a8607deacde5c8cc78927cac58657c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878896"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="2d011-102">Langue du modèle de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="2d011-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="2d011-103">La création de modèles permet de séparer les **données** de la **disposition** dans votre carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="2d011-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="2d011-104">La langue du modèle est la syntaxe utilisée pour créer un modèle.</span><span class="sxs-lookup"><span data-stu-id="2d011-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="2d011-105">Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.</span><span class="sxs-lookup"><span data-stu-id="2d011-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="2d011-106">Ces fonctionnalités sont **en version préliminaire et sujettes à modification**.</span><span class="sxs-lookup"><span data-stu-id="2d011-106">These features are **in preview and subject to change**.</span></span> <span data-ttu-id="2d011-107">Vos commentaires sont non seulement des bienvenues, mais essentiels pour garantir que nous fournissons les fonctionnalités dont **vous** avez besoin.</span><span class="sxs-lookup"><span data-stu-id="2d011-107">Your feedback is not only welcome, but  critical to ensure we deliver the features **you** need.</span></span>

<span data-ttu-id="2d011-108">Lors de la création d’un modèle, vous pouvez spécifier les données Inline avec la `AdaptiveCard` charge utile, ou au moment de l’exécution à l’aide des [Kits SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="2d011-108">When authoring a template you can specify the data inline with the `AdaptiveCard` payload, or at runtime using the [Templating SDKs](sdk.md).</span></span>

## <a name="specify-data-within-the-card"></a><span data-ttu-id="2d011-109">Spécifier les données dans la carte</span><span class="sxs-lookup"><span data-stu-id="2d011-109">Specify data within the card</span></span>

<span data-ttu-id="2d011-110">Pour fournir des données directement dans la charge utile de la carte `$data` , ajoutez simplement `AdaptiveCard` un attribut à votre (voir ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="2d011-110">To provide data directly within the card payload, simply add a `$data` attribute to your `AdaptiveCard` (seen below).</span></span>

## <a name="binding-to-the-data"></a><span data-ttu-id="2d011-111">Liaison aux données</span><span class="sxs-lookup"><span data-stu-id="2d011-111">Binding to the data</span></span>

<span data-ttu-id="2d011-112">Vous pouvez lier les données au sein `body` de la ou `actions` de la carte.</span><span class="sxs-lookup"><span data-stu-id="2d011-112">You can bind to the data within the `body` or `actions` of the card.</span></span>

* <span data-ttu-id="2d011-113">La syntaxe de liaison `{` commence par et `}`se termine par.</span><span class="sxs-lookup"><span data-stu-id="2d011-113">Binding syntax starts with `{` and ends with `}`.</span></span> <span data-ttu-id="2d011-114">Par exemple,`{myProperty}`</span><span class="sxs-lookup"><span data-stu-id="2d011-114">E.g., `{myProperty}`</span></span>
* <span data-ttu-id="2d011-115">Notation de points pour accéder aux sous-objets</span><span class="sxs-lookup"><span data-stu-id="2d011-115">Dot-notation to access sub-objects</span></span>
* <span data-ttu-id="2d011-116">Syntaxe de l’indexeur pour récupérer des propriétés par clé ou éléments dans un tableau</span><span class="sxs-lookup"><span data-stu-id="2d011-116">Indexer syntax to retrieve properties by key or items in an array</span></span>
* <span data-ttu-id="2d011-117">Gestion des valeurs NULL gracieuses pour les hiérarchies profondes</span><span class="sxs-lookup"><span data-stu-id="2d011-117">Graceful null handling for deep hierarchies</span></span>
* <span data-ttu-id="2d011-118">*Documentation de la syntaxe d’échappement bientôt disponible*</span><span class="sxs-lookup"><span data-stu-id="2d011-118">*Escape syntax documentation to come soon*</span></span>

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

## <a name="separating-the-template-from-the-data"></a><span data-ttu-id="2d011-119">Séparation du modèle des données</span><span class="sxs-lookup"><span data-stu-id="2d011-119">Separating the template from the data</span></span>

<span data-ttu-id="2d011-120">En guise d’alternative (et plus probable), vous allez créer un «modèle» de carte réutilisable sans inclure les données.</span><span class="sxs-lookup"><span data-stu-id="2d011-120">Alternatively (and more likely), you will create a re-usable card "template" without including the data.</span></span> <span data-ttu-id="2d011-121">Ce modèle peut être stocké en tant que fichier et ajouté au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="2d011-121">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="2d011-122">**EmployeeCardTemplate. JSON**</span><span class="sxs-lookup"><span data-stu-id="2d011-122">**EmployeeCardTemplate.json**</span></span>

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

<span data-ttu-id="2d011-123">Ensuite, chargez-la et fournissez les données au moment de l’exécution à l’aide des [Kits SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="2d011-123">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="2d011-124">**Exemple JavaScript**</span><span class="sxs-lookup"><span data-stu-id="2d011-124">**JavaScript example**</span></span>

<span data-ttu-id="2d011-125">Utilisation du package [adaptivecards-Templating](https://npmjs.com/package/adaptivecards-templating) .</span><span class="sxs-lookup"><span data-stu-id="2d011-125">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

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

## <a name="designer-support"></a><span data-ttu-id="2d011-126">Prise en charge du concepteur</span><span class="sxs-lookup"><span data-stu-id="2d011-126">Designer Support</span></span>

<span data-ttu-id="2d011-127">Le concepteur de cartes adaptatives a été mis à jour pour prendre en charge la création de modèles.</span><span class="sxs-lookup"><span data-stu-id="2d011-127">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="2d011-128">Essayez une version préliminaire «vNext» à l’adresse suivante: **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="2d011-128">Try out a "vnext" preview at: **[https://vnext.adaptivecards.io/designer](https://vnext.adaptivecards.io/designer)**</span></span>

<span data-ttu-id="2d011-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="2d011-129">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](http://vnext.adaptivecards.io/designer)</span></span>

 
<span data-ttu-id="2d011-130">Cette URL «vNext» va avoir des bogues et sera déployée fréquemment.</span><span class="sxs-lookup"><span data-stu-id="2d011-130">This "vnext" URL is going to have bugs and will deploy frequently.</span></span> <span data-ttu-id="2d011-131">**Effacez votre cache** pour vous assurer que vous disposez de la dernière version de et, si vous trouvez des bogues, faites-le nous savoir!</span><span class="sxs-lookup"><span data-stu-id="2d011-131">**Clear your cache** to make sure you have the latest, and if you find bugs please let us know!</span></span>

* <span data-ttu-id="2d011-132">**Exemple d’éditeur de données** : spécifiez des exemples de données ici pour afficher la carte liée aux données en mode aperçu.</span><span class="sxs-lookup"><span data-stu-id="2d011-132">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="2d011-133">Ce volet contient un petit bouton qui permet de remplir la structure de données à partir des données d’exemple existantes.</span><span class="sxs-lookup"><span data-stu-id="2d011-133">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="2d011-134">**Structure de données** : il s’agit de la structure de vos exemples de données.</span><span class="sxs-lookup"><span data-stu-id="2d011-134">**Data Structure** - This is the structure of your sample data.</span></span> <span data-ttu-id="2d011-135">Les champs peuvent être glissés sur l’aire de conception pour créer une liaison avec eux</span><span class="sxs-lookup"><span data-stu-id="2d011-135">Fields can be dragged onto the design surface to create a binding to them</span></span> 
* <span data-ttu-id="2d011-136">**Mode aperçu** -Appuyez sur le bouton de barre d’outils pour basculer entre l’expérience de modification et l’exemple d’expérience de l’aperçu des données</span><span class="sxs-lookup"><span data-stu-id="2d011-136">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="2d011-137">**Ouvrir l’exemple** : cliquez sur ce bouton pour ouvrir divers exemples de charge utile.</span><span class="sxs-lookup"><span data-stu-id="2d011-137">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="2d011-138">Liaison avancée</span><span class="sxs-lookup"><span data-stu-id="2d011-138">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="2d011-139">Portées de liaison</span><span class="sxs-lookup"><span data-stu-id="2d011-139">Binding scopes</span></span>

<span data-ttu-id="2d011-140">Il existe quelques mots clés réservés pour accéder à différentes étendues de liaison.</span><span class="sxs-lookup"><span data-stu-id="2d011-140">There are a few reserved keywords to access various binding scopes.</span></span> 

<span data-ttu-id="2d011-141">*Remarque:* tous ces éléments ne sont pas implémentés dans la version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="2d011-141">*Note:* not all of these are implemented in the preview.</span></span>

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="2d011-142">Assignation d’un contexte de données à des éléments</span><span class="sxs-lookup"><span data-stu-id="2d011-142">Assigning a data context to elements</span></span>

<span data-ttu-id="2d011-143">Pour assigner un «contexte de données» à un `$data` élément, ajoutez un attribut à l’élément.</span><span class="sxs-lookup"><span data-stu-id="2d011-143">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

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

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="2d011-144">Répétition d’éléments dans un tableau</span><span class="sxs-lookup"><span data-stu-id="2d011-144">Repeating items in an array</span></span>

<span data-ttu-id="2d011-145">Cette partie est un peu «Dark Magic».</span><span class="sxs-lookup"><span data-stu-id="2d011-145">This part is a bit of "dark magic".</span></span> <span data-ttu-id="2d011-146">Commentaires de bienvenue.</span><span class="sxs-lookup"><span data-stu-id="2d011-146">Feedback welcome.</span></span>

* <span data-ttu-id="2d011-147">Si la `$data` propriété des objets est définie sur un **tableau**, l' **objet lui-même est répété pour chaque élément du tableau.**</span><span class="sxs-lookup"><span data-stu-id="2d011-147">If the objects' `$data` property is set to an **array**, then the **object itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="2d011-148">À mesure qu’elle est répétée, `$data` utilisée dans les liaisons de propriété est limitée à l' **élément individuel** dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="2d011-148">As it is being repeated, `$data` used in property bindings are scoped to the **individual item** within the array.</span></span>

<span data-ttu-id="2d011-149">Par exemple, l' `TextBlock` exemple ci-dessous est répété 3 fois, `$data` car il s’agit d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="2d011-149">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="2d011-150">Notez comment la `text` propriété est liée à la `name` propriété d’un objet individuel dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="2d011-150">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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

<span data-ttu-id="2d011-151">**Ce qui donne:**</span><span class="sxs-lookup"><span data-stu-id="2d011-151">**Resulting in:**</span></span>

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

## <a name="functions"></a><span data-ttu-id="2d011-152">Fonctions</span><span class="sxs-lookup"><span data-stu-id="2d011-152">Functions</span></span>

<span data-ttu-id="2d011-153">Aucun langage de création de modèles n’est terminé sans aucune fonction d’assistance.</span><span class="sxs-lookup"><span data-stu-id="2d011-153">No templating language is complete without some helper functions.</span></span> <span data-ttu-id="2d011-154">Nous allons fournir un ensemble standard de fonctions qui fonctionnent sur chaque kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="2d011-154">We will provide a standard set of functions that work on every SDK.</span></span> 

<span data-ttu-id="2d011-155">La syntaxe ici est toujours active dans l’air. Veuillez recommencer, mais voici ce que nous avons planifié:</span><span class="sxs-lookup"><span data-stu-id="2d011-155">The syntax here is still up in the air so please check back soon, but here's a start of what we're planning:</span></span>

### <a name="string-functions"></a><span data-ttu-id="2d011-156">Fonctions de chaîne</span><span class="sxs-lookup"><span data-stu-id="2d011-156">String functions</span></span>

* <span data-ttu-id="2d011-157">substr</span><span class="sxs-lookup"><span data-stu-id="2d011-157">substr</span></span>
* <span data-ttu-id="2d011-158">indexOf *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="2d011-158">indexOf *(not working yet)*</span></span>
* <span data-ttu-id="2d011-159">toUpper *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="2d011-159">toUpper *(not working yet)*</span></span>
* <span data-ttu-id="2d011-160">toLower *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="2d011-160">toLower *(not working yet)*</span></span>

### <a name="number-functions"></a><span data-ttu-id="2d011-161">Fonctions numériques</span><span class="sxs-lookup"><span data-stu-id="2d011-161">Number functions</span></span>

* <span data-ttu-id="2d011-162">Mise en forme (devise, décimal, etc.) *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="2d011-162">Formatting (currency, decimal, etc) *(not working yet)*</span></span>

### <a name="date-functions"></a><span data-ttu-id="2d011-163">Fonctions de date</span><span class="sxs-lookup"><span data-stu-id="2d011-163">Date functions</span></span>

* <span data-ttu-id="2d011-164">Analyse des formats de chaîne de date bien connus *(ne fonctionne pas encore)*</span><span class="sxs-lookup"><span data-stu-id="2d011-164">Parsing well-known date string formats *(not working yet)*</span></span>
* <span data-ttu-id="2d011-165">Mise en forme des représentations de date/heure connues *(ne fonctionnant pas encore)*</span><span class="sxs-lookup"><span data-stu-id="2d011-165">Formatting for well-known date/time representations *(not working yet)*</span></span>

### <a name="conditional-functions"></a><span data-ttu-id="2d011-166">Fonctions conditionnelles</span><span class="sxs-lookup"><span data-stu-id="2d011-166">Conditional functions</span></span>

* <span data-ttu-id="2d011-167">if (*expression*, *TrueValue*, *FalseValue*)</span><span class="sxs-lookup"><span data-stu-id="2d011-167">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="2d011-168">**`if`tels**</span><span class="sxs-lookup"><span data-stu-id="2d011-168">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "if(priceChange >= 0, 'good', 'attention')"
}
```

### <a name="data-manipulation"></a><span data-ttu-id="2d011-169">Manipulation de données</span><span class="sxs-lookup"><span data-stu-id="2d011-169">Data manipulation</span></span>

* <span data-ttu-id="2d011-170">JSON. Parse-capacité à analyser une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="2d011-170">JSON.parse - ability to parse a JSON string</span></span> 

<span data-ttu-id="2d011-171">**`JSON.parse`tels**</span><span class="sxs-lookup"><span data-stu-id="2d011-171">**`JSON.parse` example**</span></span>

<span data-ttu-id="2d011-172">Il s’agit d’une réponse Azure DevOps `message` où la propriété est une chaîne sérialisée au format JSON.</span><span class="sxs-lookup"><span data-stu-id="2d011-172">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="2d011-173">Pour accéder aux valeurs dans la chaîne, nous devons utiliser la `JSON.parse` fonction dans notre modèle.</span><span class="sxs-lookup"><span data-stu-id="2d011-173">In order to access values within the string, we need to use the `JSON.parse` function in our template.</span></span>

<span data-ttu-id="2d011-174">**Données**</span><span class="sxs-lookup"><span data-stu-id="2d011-174">**Data**</span></span> 

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

<span data-ttu-id="2d011-175">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="2d011-175">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

<span data-ttu-id="2d011-176">**Ce qui se traduit par**</span><span class="sxs-lookup"><span data-stu-id="2d011-176">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="2d011-177">Fonctions personnalisées</span><span class="sxs-lookup"><span data-stu-id="2d011-177">Custom functions</span></span>

<span data-ttu-id="2d011-178">Nous voulons nous assurer que les hôtes peuvent ajouter des fonctions personnalisées, ce qui signifie que nous avons besoin d’une prise en charge fiable de la prise en charge de secours si une fonction n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="2d011-178">We want to make sure Hosts can add custom functions, which means we need robust support for fallback support if a function isn't supported.</span></span> <span data-ttu-id="2d011-179">Nous sommes toujours en cours d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="2d011-179">We are still evaluating this.</span></span>

## <a name="conditional-layout"></a><span data-ttu-id="2d011-180">Disposition conditionnelle</span><span class="sxs-lookup"><span data-stu-id="2d011-180">Conditional layout</span></span>

<span data-ttu-id="2d011-181">Pour supprimer un élément entier si une condition est remplie, utilisez la `$when` propriété.</span><span class="sxs-lookup"><span data-stu-id="2d011-181">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="2d011-182">Si `$when` prend `false` la valeur, l’élément ne s’affiche pas pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2d011-182">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

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

### <a name="composing-templates"></a><span data-ttu-id="2d011-183">Composition de modèles</span><span class="sxs-lookup"><span data-stu-id="2d011-183">Composing templates</span></span>

<span data-ttu-id="2d011-184">Il n’existe actuellement aucune prise en charge pour composer les «parties» du modèle.</span><span class="sxs-lookup"><span data-stu-id="2d011-184">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="2d011-185">Toutefois, nous explorons les options et espérons partager plus tôt.</span><span class="sxs-lookup"><span data-stu-id="2d011-185">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="2d011-186">Toutes les pensées ici Bienvenue!</span><span class="sxs-lookup"><span data-stu-id="2d011-186">Any thoughts here welcome!</span></span>


## <a name="examples"></a><span data-ttu-id="2d011-187">Exemples</span><span class="sxs-lookup"><span data-stu-id="2d011-187">Examples</span></span>

<span data-ttu-id="2d011-188">Nous n’avons qu’une quantité limitée d’exemples créés jusqu’à présent, mais jetez un coup d’œil ici pour commencer.</span><span class="sxs-lookup"><span data-stu-id="2d011-188">We only have a limited amount of samples created so far, but take a look here to get started.</span></span>

* <span data-ttu-id="2d011-189">Charger les exemples dans le [Concepteur](http://vnext.adaptivecards.io/designer) en cliquant sur **ouvrir l’exemple**</span><span class="sxs-lookup"><span data-stu-id="2d011-189">Load samples within the [designer](http://vnext.adaptivecards.io/designer) by clicking **Open Sample**</span></span>
* <span data-ttu-id="2d011-190">Ou simplement [Parcourir un répertoire de ces derniers](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) directement</span><span class="sxs-lookup"><span data-stu-id="2d011-190">Or just [browse a directory of them](https://github.com/Microsoft/AdaptiveCards/tree/js/template-engine/samples/v2.0/Scenarios) directly</span></span>