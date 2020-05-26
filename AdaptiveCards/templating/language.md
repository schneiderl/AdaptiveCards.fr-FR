---
title: Langage de modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 1b5a7df25eedb96ec6edfe02912d328ab59d2801
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631343"
---
# <a name="adaptive-cards-template-language"></a><span data-ttu-id="1e44f-102">Langage de modèle de cartes adaptatives</span><span class="sxs-lookup"><span data-stu-id="1e44f-102">Adaptive Cards Template Language</span></span>

<span data-ttu-id="1e44f-103">La création de modèles permet de séparer les **données** de la **disposition** dans votre carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="1e44f-103">Templating enables the separation of **data** from **layout** in your Adaptive Card.</span></span> <span data-ttu-id="1e44f-104">Le langage de modèle est la syntaxe utilisée pour créer un modèle.</span><span class="sxs-lookup"><span data-stu-id="1e44f-104">The template langauge is the syntax used to author a template.</span></span> 

> <span data-ttu-id="1e44f-105">Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).</span><span class="sxs-lookup"><span data-stu-id="1e44f-105">Please read this for an [overview of Adaptive Card Templating](index.md)</span></span>

> [!IMPORTANT] 
> 
> <span data-ttu-id="1e44f-106">**Changements cassants** dans la version **RC (Release Candidate) de mai 2020**</span><span class="sxs-lookup"><span data-stu-id="1e44f-106">**Breaking changes** in the **May 2020 Release Candidate**</span></span>
>
> <span data-ttu-id="1e44f-107">Nous avons travaillé dur à la publication des modèles et nous sommes dans la dernière ligne droite !</span><span class="sxs-lookup"><span data-stu-id="1e44f-107">We've been hard at work getting templating released, and we're finally in the home stretch!</span></span> <span data-ttu-id="1e44f-108">Nous avons dû apporter des modifications mineures avant de finaliser la version.</span><span class="sxs-lookup"><span data-stu-id="1e44f-108">We had to make some minor breaking changes as we close on the release.</span></span>

## <a name="breaking-changes-as-of-may-2020"></a><span data-ttu-id="1e44f-109">Changements cassants de mai 2020</span><span class="sxs-lookup"><span data-stu-id="1e44f-109">Breaking changes as of May 2020</span></span>

1. <span data-ttu-id="1e44f-110">La syntaxe de liaison a changé et passe de `{...}` à `${...}`.</span><span class="sxs-lookup"><span data-stu-id="1e44f-110">The binding syntax changed from `{...}` to `${...}`</span></span>
    * <span data-ttu-id="1e44f-111">Par exemple : `"text": "Hello {name}"` devient `"text": "Hello ${name}"`</span><span class="sxs-lookup"><span data-stu-id="1e44f-111">For Example: `"text": "Hello {name}"` becomes `"text": "Hello ${name}"`</span></span>
    
## <a name="binding-to-data"></a><span data-ttu-id="1e44f-112">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="1e44f-112">Binding to data</span></span>

<span data-ttu-id="1e44f-113">L’écriture d’un modèle est aussi simple que de remplacer le contenu « non statique » de votre carte par des « expressions de liaison ».</span><span class="sxs-lookup"><span data-stu-id="1e44f-113">Writing a template is as simple as replacing the "non-static" content of your card with "binding expressions".</span></span>

### <a name="static-card-payload"></a><span data-ttu-id="1e44f-114">Charge utile de carte statique</span><span class="sxs-lookup"><span data-stu-id="1e44f-114">Static card payload</span></span>

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### <a name="template-payload"></a><span data-ttu-id="1e44f-115">Charge utile de modèle</span><span class="sxs-lookup"><span data-stu-id="1e44f-115">Template payload</span></span>

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* <span data-ttu-id="1e44f-116">Les expressions de liaison peuvent être placées à n’importe quel endroit où le contenu statique peut se trouver.</span><span class="sxs-lookup"><span data-stu-id="1e44f-116">Binding expressions can be placed just about anywhere that static content can be</span></span>
* <span data-ttu-id="1e44f-117">La syntaxe de liaison commence par `${` et se termine par `}`.</span><span class="sxs-lookup"><span data-stu-id="1e44f-117">The binding syntax starts with `${` and ends with `}`.</span></span> <span data-ttu-id="1e44f-118">Par exemple : `${myProperty}`</span><span class="sxs-lookup"><span data-stu-id="1e44f-118">E.g., `${myProperty}`</span></span>
* <span data-ttu-id="1e44f-119">Utilisez la *notation par points* pour accéder aux sous-objets d’une hiérarchie d’objets.</span><span class="sxs-lookup"><span data-stu-id="1e44f-119">Use *Dot-notation* to access sub-objects of an object hierarchy.</span></span> <span data-ttu-id="1e44f-120">Par exemple : `${myParent.myChild}`</span><span class="sxs-lookup"><span data-stu-id="1e44f-120">E.g., `${myParent.myChild}`</span></span>
* <span data-ttu-id="1e44f-121">Grâce à une gestion appropriée des valeurs Null, vous n’obtiendrez pas d’exceptions si vous accédez à une propriété Null dans un graphique d’objet.</span><span class="sxs-lookup"><span data-stu-id="1e44f-121">Graceful null handling ensures you won't get exceptions if you access a null property in an object graph</span></span>
* <span data-ttu-id="1e44f-122">Utilisez la *syntaxe d’indexeur* pour récupérer des propriétés par clé ou les éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="1e44f-122">Use *Indexer syntax* to retrieve properties by key or items in an array.</span></span> <span data-ttu-id="1e44f-123">Par exemple : `${myArray[0]}`</span><span class="sxs-lookup"><span data-stu-id="1e44f-123">E.g., `${myArray[0]}`</span></span>

## <a name="providing-the-data"></a><span data-ttu-id="1e44f-124">Ajout des données</span><span class="sxs-lookup"><span data-stu-id="1e44f-124">Providing the data</span></span>

<span data-ttu-id="1e44f-125">Maintenant que vous disposez d’un modèle, vous devez lui ajouter des données pour le finaliser.</span><span class="sxs-lookup"><span data-stu-id="1e44f-125">Now that you have a template, you'll want to provide the data that makes it complete.</span></span> <span data-ttu-id="1e44f-126">Pour ce faire, vous avez deux options :</span><span class="sxs-lookup"><span data-stu-id="1e44f-126">You have two options to do this:</span></span>

1. <span data-ttu-id="1e44f-127">**Option A : Inline dans la charge utile du modèle**.</span><span class="sxs-lookup"><span data-stu-id="1e44f-127">**Option A: Inline within the template payload**.</span></span> <span data-ttu-id="1e44f-128">Vous pouvez fournir les données inline dans la charge utile du modèle `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="1e44f-128">You can provide the data inline within the `AdaptiveCard` template payload.</span></span> <span data-ttu-id="1e44f-129">Pour ce faire, il vous suffit d’ajouter un attribut `$data` à l’objet racine `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="1e44f-129">To do so, simply add a `$data` attribute to the root `AdaptiveCard` object.</span></span>
2. <span data-ttu-id="1e44f-130">**Option B : En tant qu’objet de données distinct**.</span><span class="sxs-lookup"><span data-stu-id="1e44f-130">**Option B: As a separate data object**.</span></span> <span data-ttu-id="1e44f-131">Avec cette option, vous fournissez deux objets distincts au [SDK de création de modèles](sdk.md) au moment de l’exécution : `template` et `data`.</span><span class="sxs-lookup"><span data-stu-id="1e44f-131">With this option you provide two separate objects to the [Templating SDK](sdk.md) at runtime: the `template` and the `data`.</span></span> <span data-ttu-id="1e44f-132">Il s’agit de l’approche la plus courante, car en général, vous créez un modèle, puis vous y ajoutez des données dynamiques ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="1e44f-132">This will be the more common approach, since typically you will create a template and want to provide dynamic data later.</span></span>

### <a name="option-a-inline-data"></a><span data-ttu-id="1e44f-133">Option A : Données inline</span><span class="sxs-lookup"><span data-stu-id="1e44f-133">Option A: Inline data</span></span>

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
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

### <a name="option-b-separating-the-template-from-the-data"></a><span data-ttu-id="1e44f-134">Option B : Séparation du modèle des données</span><span class="sxs-lookup"><span data-stu-id="1e44f-134">Option B: Separating the template from the data</span></span>

<span data-ttu-id="1e44f-135">Une autre approche, d’ailleurs plus vraisemblable, consiste à créer un modèle de carte réutilisable sans y inclure de données.</span><span class="sxs-lookup"><span data-stu-id="1e44f-135">Alternatively (and more likely), you'll create a re-usable card template without including the data.</span></span> <span data-ttu-id="1e44f-136">Vous pouvez stocker ce modèle en tant que fichier et l’ajouter au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="1e44f-136">This template could be stored as a file and added to source control.</span></span>

<span data-ttu-id="1e44f-137">**EmployeeCardTemplate.json**</span><span class="sxs-lookup"><span data-stu-id="1e44f-137">**EmployeeCardTemplate.json**</span></span>

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

<span data-ttu-id="1e44f-138">Ensuite, chargez-le et fournissez les données au moment de l’exécution à l’aide des [kits SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="1e44f-138">Then load it up and provide the data at runtime using the [Templating SDKs](sdk.md).</span></span>

<span data-ttu-id="1e44f-139">**Exemple JavaScript**</span><span class="sxs-lookup"><span data-stu-id="1e44f-139">**JavaScript example**</span></span>

<span data-ttu-id="1e44f-140">Cet exemple utilise le package [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).</span><span class="sxs-lookup"><span data-stu-id="1e44f-140">Using the [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating) package.</span></span>

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var card = template.expand({
    $root: {
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
    }
});

// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a><span data-ttu-id="1e44f-141">Prise en charge du concepteur</span><span class="sxs-lookup"><span data-stu-id="1e44f-141">Designer Support</span></span>

<span data-ttu-id="1e44f-142">Le concepteur de cartes adaptatives a été mis à jour pour prendre en charge la création de modèles.</span><span class="sxs-lookup"><span data-stu-id="1e44f-142">The Adaptive Card Designer has been updated to support templating.</span></span> 

> <span data-ttu-id="1e44f-143">Faites un essai sur : **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span><span class="sxs-lookup"><span data-stu-id="1e44f-143">Try it out at: **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**</span></span>

<span data-ttu-id="1e44f-144">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="1e44f-144">[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)</span></span>

* <span data-ttu-id="1e44f-145">**Éditeur d’exemple de données** : spécifiez un exemple de données ici pour voir la carte liée aux données en « Mode Aperçu ».</span><span class="sxs-lookup"><span data-stu-id="1e44f-145">**Sample Data Editor** - Specify sample data here to view the data-bound card when in "Preview Mode."</span></span> <span data-ttu-id="1e44f-146">Ce volet contient un petit bouton permettant de remplir la structure de données avec un exemple de données existant.</span><span class="sxs-lookup"><span data-stu-id="1e44f-146">There is a small button in this pane to populate the Data Structure from the existing sample data.</span></span>
* <span data-ttu-id="1e44f-147">**Mode Aperçu** : appuyez sur le bouton de la barre d’outils pour basculer entre l’expérience de modification et l’expérience d’aperçu de l’exemple de données.</span><span class="sxs-lookup"><span data-stu-id="1e44f-147">**Preview Mode** - Press the toolbar button to toggle between the edit-experience and the sample-data-preview experience</span></span>
* <span data-ttu-id="1e44f-148">**Ouvrir l’exemple** : cliquez sur ce bouton pour ouvrir divers exemples de charge utile.</span><span class="sxs-lookup"><span data-stu-id="1e44f-148">**Open Sample** - click this button to open various sample payloads</span></span>

## <a name="advanced-binding"></a><span data-ttu-id="1e44f-149">Liaison avancée</span><span class="sxs-lookup"><span data-stu-id="1e44f-149">Advanced binding</span></span>

### <a name="binding-scopes"></a><span data-ttu-id="1e44f-150">Étendues de liaison</span><span class="sxs-lookup"><span data-stu-id="1e44f-150">Binding scopes</span></span>

<span data-ttu-id="1e44f-151">Des mots clés réservés vous donnent accès à différentes étendues de liaison.</span><span class="sxs-lookup"><span data-stu-id="1e44f-151">There are a few reserved keywords to access various binding scopes.</span></span> 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### <a name="assigning-a-data-context-to-elements"></a><span data-ttu-id="1e44f-152">Affectation d’un contexte de données à des éléments</span><span class="sxs-lookup"><span data-stu-id="1e44f-152">Assigning a data context to elements</span></span>

<span data-ttu-id="1e44f-153">Pour affecter un « contexte de données » à un élément, ajoutez un attribut `$data` à l’élément.</span><span class="sxs-lookup"><span data-stu-id="1e44f-153">To assign a "data context" to any element add a `$data` attribute to the element.</span></span>

```json
{
    "type": "Container",
    "$data": "${mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': ${mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: ${$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a><span data-ttu-id="1e44f-154">Répétition d’éléments dans un tableau</span><span class="sxs-lookup"><span data-stu-id="1e44f-154">Repeating items in an array</span></span>

* <span data-ttu-id="1e44f-155">Si la propriété `$data` d’un élément de carte adaptative est liée à un **tableau**, **cet élément est répété pour chaque élément du tableau**.</span><span class="sxs-lookup"><span data-stu-id="1e44f-155">If an Adaptive Card element's `$data` property is bound to an **array**, then the **element itself will be repeated for each item in the array.**</span></span> 
* <span data-ttu-id="1e44f-156">Toute expression de liaison (`${myProperty}`) utilisée dans les valeurs de propriété a pour étendue l’**élément individuel** dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="1e44f-156">Any binding expressions (`${myProperty}`) used in property values will be scoped to the **individual item** within the array.</span></span>
* <span data-ttu-id="1e44f-157">En cas de liaison à un tableau de chaînes, utilisez `${$data}` pour accéder à l’élément de chaîne individuel.</span><span class="sxs-lookup"><span data-stu-id="1e44f-157">If binding to an array of strings, use `${$data}` to access the individual string element.</span></span> <span data-ttu-id="1e44f-158">Par exemple : `"text": "${$data}"`</span><span class="sxs-lookup"><span data-stu-id="1e44f-158">E.g., `"text": "${$data}"`</span></span>

<span data-ttu-id="1e44f-159">Par exemple, le `TextBlock` ci-dessous est répété 3 fois car `$data` est un tableau.</span><span class="sxs-lookup"><span data-stu-id="1e44f-159">For example, the `TextBlock` below will be repeated 3 times since it's `$data` is an array.</span></span> <span data-ttu-id="1e44f-160">Notez que la propriété `text` est liée à la propriété `name` d’un objet individuel dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="1e44f-160">Notice how the `text` property is bound to the `name` property of an individual object within the array.</span></span> 

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
            "text": "${name}"
        }
    ]
}
```

<span data-ttu-id="1e44f-161">**Ce qui donne :**</span><span class="sxs-lookup"><span data-stu-id="1e44f-161">**Resulting in:**</span></span>

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

## <a name="built-in-functions"></a><span data-ttu-id="1e44f-162">Fonctions intégrées</span><span class="sxs-lookup"><span data-stu-id="1e44f-162">Built-in functions</span></span>

<span data-ttu-id="1e44f-163">Aucun langage de création de modèles ne serait complet sans une suite de fonctions d’assistance.</span><span class="sxs-lookup"><span data-stu-id="1e44f-163">No templating language is complete without a rich suite of helper functions.</span></span> <span data-ttu-id="1e44f-164">La création de modèles de cartes adaptatives s’appuie sur le [langage AEL](https://aka.ms/adaptive-expressions), qui est un standard ouvert permettant de déclarer des expressions pouvant être évaluées sur un grand nombre de plateformes différentes.</span><span class="sxs-lookup"><span data-stu-id="1e44f-164">Adaptive Card Templating is built on top of the [Adaptive Expression Language](https://aka.ms/adaptive-expressions) (AEL), which is an open standard for declaring expressions that can be evaluated on many different platforms.</span></span> <span data-ttu-id="1e44f-165">Comme il s’agit d’un vrai sur-ensemble de « Logic Apps », vous pouvez utiliser une syntaxe similaire à celle de Power Automate, etc.</span><span class="sxs-lookup"><span data-stu-id="1e44f-165">And it's a proper superset of "Logic Apps", so you can use similar syntax as Power Automate, etc.</span></span>

<span data-ttu-id="1e44f-166">**Il ne s’agit là que d’un petit échantillon des fonctions intégrées.**</span><span class="sxs-lookup"><span data-stu-id="1e44f-166">**This is just a small sampling of the built-in functions.**</span></span>

<span data-ttu-id="1e44f-167">Consultez la liste complète des [fonctions prédéfinies du langage AEL](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="1e44f-167">Check out the full list of [Adaptive Expression Language Pre-built functions](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).</span></span>

### <a name="conditional-evaluation"></a><span data-ttu-id="1e44f-168">Évaluation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="1e44f-168">Conditional evaluation</span></span>

* <span data-ttu-id="1e44f-169">if(*expression*, *valeur_true*, *valeur_false*)</span><span class="sxs-lookup"><span data-stu-id="1e44f-169">if(*expression*, *trueValue*, *falseValue*)</span></span>

<span data-ttu-id="1e44f-170">**Exemple `if`**</span><span class="sxs-lookup"><span data-stu-id="1e44f-170">**`if` example**</span></span>

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="parsing-json"></a><span data-ttu-id="1e44f-171">Analyse du JSON</span><span class="sxs-lookup"><span data-stu-id="1e44f-171">Parsing JSON</span></span>

* <span data-ttu-id="1e44f-172">JSON (*jsonString*) - Analyser une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="1e44f-172">json(*jsonString*) - Parse a JSON string</span></span>

<span data-ttu-id="1e44f-173">**Exemple `json`**</span><span class="sxs-lookup"><span data-stu-id="1e44f-173">**`json` example**</span></span>

<span data-ttu-id="1e44f-174">Il s’agit d’une réponse Azure DevOps où la propriété `message` est une chaîne sérialisée au format JSON.</span><span class="sxs-lookup"><span data-stu-id="1e44f-174">This is an Azure DevOps response where the `message` property is a JSON-serialized string.</span></span> <span data-ttu-id="1e44f-175">Pour pouvoir accéder aux valeurs de la chaîne, nous devons utiliser la fonction `json` dans notre modèle.</span><span class="sxs-lookup"><span data-stu-id="1e44f-175">In order to access values within the string, we need to use the `json` function in our template.</span></span>

<span data-ttu-id="1e44f-176">**Données**</span><span class="sxs-lookup"><span data-stu-id="1e44f-176">**Data**</span></span> 

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

<span data-ttu-id="1e44f-177">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="1e44f-177">**Usage**</span></span>

```json
{
    "type": "TextBlock",
    "text": "${json(message).releaseName}"
}
```

<span data-ttu-id="1e44f-178">**Ce qui donne**</span><span class="sxs-lookup"><span data-stu-id="1e44f-178">**Resulting In**</span></span>

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a><span data-ttu-id="1e44f-179">Fonctions personnalisées</span><span class="sxs-lookup"><span data-stu-id="1e44f-179">Custom functions</span></span>

<span data-ttu-id="1e44f-180">Les fonctions personnalisées sont prises en charge via les API des [SDK de création de modèles](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="1e44f-180">Custom functions are supported via APIs in the [Templating SDKs](sdk.md).</span></span> 

## <a name="conditional-layout-with-when"></a><span data-ttu-id="1e44f-181">Disposition conditionnelle avec `$when`</span><span class="sxs-lookup"><span data-stu-id="1e44f-181">Conditional layout with `$when`</span></span>

<span data-ttu-id="1e44f-182">Pour supprimer un élément entier si une condition est remplie, utilisez la propriété `$when`.</span><span class="sxs-lookup"><span data-stu-id="1e44f-182">To drop an entire element if a condition is met, use the `$when` property.</span></span> <span data-ttu-id="1e44f-183">Si `$when` prend la valeur `false`, l’utilisateur ne voit pas l’élément.</span><span class="sxs-lookup"><span data-stu-id="1e44f-183">If `$when` evaluates to `false` the element will not appear to the user.</span></span>

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "${price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "${price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a><span data-ttu-id="1e44f-184">Composition de modèles</span><span class="sxs-lookup"><span data-stu-id="1e44f-184">Composing templates</span></span>

<span data-ttu-id="1e44f-185">À l’heure actuelle, il n’est pas possible de composer ensemble les « parties » d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="1e44f-185">Currently there is no support for composing template "parts" together.</span></span> <span data-ttu-id="1e44f-186">Toutefois, nous explorons différentes pistes et espérons vous en dire plus très bientôt.</span><span class="sxs-lookup"><span data-stu-id="1e44f-186">But we are exploring options and hope to share more soon.</span></span> <span data-ttu-id="1e44f-187">Vos idées sont les bienvenues !</span><span class="sxs-lookup"><span data-stu-id="1e44f-187">Any thoughts here welcome!</span></span>

## <a name="examples"></a><span data-ttu-id="1e44f-188">Exemples</span><span class="sxs-lookup"><span data-stu-id="1e44f-188">Examples</span></span>

<span data-ttu-id="1e44f-189">Parcourez la [page d’exemples](https://adaptivecards.io/samples) mise à jour pour explorer toutes sortes de nouvelles cartes basées sur des modèles.</span><span class="sxs-lookup"><span data-stu-id="1e44f-189">Browse the updated [Samples page](https://adaptivecards.io/samples) to explore all sorts of new templated cards.</span></span>
