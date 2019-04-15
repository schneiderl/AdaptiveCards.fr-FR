---
title: Prise en main
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9d363da0c10b242e23d2594984292fcc1f31382f
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552681"
---
# <a name="getting-started"></a><span data-ttu-id="2238c-102">Prise en main</span><span class="sxs-lookup"><span data-stu-id="2238c-102">Getting Started</span></span> 

<span data-ttu-id="2238c-103">Une carte adaptative est un modèle d’objet de carte sérialisé en JSON.</span><span class="sxs-lookup"><span data-stu-id="2238c-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="2238c-104">Structure de carte adaptative</span><span class="sxs-lookup"><span data-stu-id="2238c-104">Adaptive Card structure</span></span>

<span data-ttu-id="2238c-105">La structure de base d’une carte est comme suit :</span><span class="sxs-lookup"><span data-stu-id="2238c-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="2238c-106">`AdaptiveCard` -L’objet racine décrit le AdaptiveCard lui-même, y compris sa composition de l’élément, ses actions, comment il doit être prononcé et la version de schéma requise pour l’afficher.</span><span class="sxs-lookup"><span data-stu-id="2238c-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="2238c-107">`body` : Le corps de la carte est constitué des blocs de construction appelé `elements`.</span><span class="sxs-lookup"><span data-stu-id="2238c-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="2238c-108">Éléments peuvent être composées dans des dispositions presque illimitées pour créer de nombreux types de cartes.</span><span class="sxs-lookup"><span data-stu-id="2238c-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="2238c-109">`actions` -Nombre de cartes ont un ensemble d’actions qu'utilisateur peut prendre le dessus.</span><span class="sxs-lookup"><span data-stu-id="2238c-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="2238c-110">Cette propriété décrit ces actions généralement obtient restituée dans une barre d’action « » en bas.</span><span class="sxs-lookup"><span data-stu-id="2238c-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="2238c-111">Carte de l’exemple</span><span class="sxs-lookup"><span data-stu-id="2238c-111">Example Card</span></span>

<span data-ttu-id="2238c-112">Cette carte exemple qui inclut une seule ligne de texte suivie d’une image.</span><span class="sxs-lookup"><span data-stu-id="2238c-112">This sample card which includes a single line of text followed by an image.</span></span>

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Here is a ninja cat"
        },
        {
            "type": "Image",
            "url": "http://adaptivecards.io/content/cats/1.png"
        }
    ]
}
```

## <a name="type-property"></a><span data-ttu-id="2238c-113">Propriété `Type`</span><span class="sxs-lookup"><span data-stu-id="2238c-113">`Type` property</span></span>

<span data-ttu-id="2238c-114">Chaque élément a un `type` est la propriété qui identifie quel type d’objet.</span><span class="sxs-lookup"><span data-stu-id="2238c-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="2238c-115">En examinant la carte ci-dessus, vous pouvez voir nous avons deux éléments, un `TextBlock` et un `Image`.</span><span class="sxs-lookup"><span data-stu-id="2238c-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="2238c-116">Tous les éléments de carte adaptative **empilent verticalement** et **développez à la largeur de leur parent** (pensez `display: block` au format HTML).</span><span class="sxs-lookup"><span data-stu-id="2238c-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="2238c-117">Toutefois, vous pouvez utiliser un `ColumnSet` pour créer des colonnes côte à côte de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="2238c-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="2238c-118">Éléments ADAPTATIF</span><span class="sxs-lookup"><span data-stu-id="2238c-118">Adaptive Elements</span></span>

<span data-ttu-id="2238c-119">Les éléments principaux sont :</span><span class="sxs-lookup"><span data-stu-id="2238c-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="2238c-120">**TextBlock** -ajoute un bloc de texte avec des propriétés pour contrôler l’aspect du texte</span><span class="sxs-lookup"><span data-stu-id="2238c-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="2238c-121">**Image** -ajoute une image avec les propriétés qui contrôlent l’aspect de l’image</span><span class="sxs-lookup"><span data-stu-id="2238c-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="2238c-122">Éléments conteneurs</span><span class="sxs-lookup"><span data-stu-id="2238c-122">Container elements</span></span>

<span data-ttu-id="2238c-123">Les cartes peuvent également avoir des conteneurs, qui organisent une collection d’éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="2238c-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="2238c-124">**Conteneur** -définit une collection d’éléments</span><span class="sxs-lookup"><span data-stu-id="2238c-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="2238c-125">**Jeu de colonnes/colonne** -définit une collection de colonnes, chaque colonne est un conteneur</span><span class="sxs-lookup"><span data-stu-id="2238c-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="2238c-126">**FactSet** -conteneur de faits</span><span class="sxs-lookup"><span data-stu-id="2238c-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="2238c-127">**ImageSet** -expérience de galerie pour une collection d’images de photos d’Images de conteneur afin que l’interface utilisateur peut afficher appropriée.</span><span class="sxs-lookup"><span data-stu-id="2238c-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="2238c-128">Éléments d’entrée</span><span class="sxs-lookup"><span data-stu-id="2238c-128">Input elements</span></span>

<span data-ttu-id="2238c-129">Éléments d’entrée vous autorise à demander de l’interface utilisateur native créer des formulaires simples :</span><span class="sxs-lookup"><span data-stu-id="2238c-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="2238c-130">**Input.Text** -obtenir le contenu de texte à partir de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="2238c-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="2238c-131">**Input.Date** -obtenir une Date de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="2238c-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="2238c-132">**Input.Time** -obtenir un temps de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="2238c-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="2238c-133">**Input.Number** -obtenir un nombre à partir de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="2238c-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="2238c-134">**Input.ChoiceSet** : donner à l’utilisateur un ensemble de choix et demandez-lui de prélèvement</span><span class="sxs-lookup"><span data-stu-id="2238c-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="2238c-135">**Input.Toggle** : donner à l’utilisateur un choix unique entre deux éléments et les sélectionner</span><span class="sxs-lookup"><span data-stu-id="2238c-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="2238c-136">Actions</span><span class="sxs-lookup"><span data-stu-id="2238c-136">Actions</span></span>

<span data-ttu-id="2238c-137">Actions ajoutent des boutons à la carte.</span><span class="sxs-lookup"><span data-stu-id="2238c-137">Actions add buttons to the card.</span></span> <span data-ttu-id="2238c-138">Il peuvent effectuer diverses actions, telles que l’ouverture d’une URL ou l’envoi des données.</span><span class="sxs-lookup"><span data-stu-id="2238c-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="2238c-139">**Action.OpenUrl** -le bouton ouvre une URL externe pour l’affichage</span><span class="sxs-lookup"><span data-stu-id="2238c-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="2238c-140">**Action.ShowCard** -demande une carte secondaires à afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2238c-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="2238c-141">**Action.Submit** -poser pour tous les éléments d’entrée à collecter dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte pour vous.</span><span class="sxs-lookup"><span data-stu-id="2238c-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="2238c-142">**Exemple Action.Submit**: Avec Skype, un Action.Submit renverra un robot de Bot Framework activité au robot avec le **valeur** propriété contenant un objet avec toutes les données d’entrée sur ce dernier.</span><span class="sxs-lookup"><span data-stu-id="2238c-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="2238c-143">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="2238c-143">Learn More</span></span>

* <span data-ttu-id="2238c-144">[Parcourir les cartes d’exemple](http://adaptivecards.io/samples/) d’inspiration</span><span class="sxs-lookup"><span data-stu-id="2238c-144">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="2238c-145">Utilisez le [Explorateur de schémas](http://adaptivecards.io/explorer) pour parcourir les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="2238c-145">Use the [Schema Explorer](http://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="2238c-146">Générer une carte à l’aide de la [visualiseur Interactive](http://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="2238c-146">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="2238c-147">[Nous contacter](http://adaptivecards.io/connect) avec vos commentaires</span><span class="sxs-lookup"><span data-stu-id="2238c-147">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
