---
title: Prise en main
author: matthidinger
ms.author: mahiding
ms.date: 11/9/2017
ms.topic: article
ms.openlocfilehash: 9cc7344ac357dcb95c7e47e377dbb12fbcd66957
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417487"
---
# <a name="getting-started"></a><span data-ttu-id="11f6a-102">Prise en main</span><span class="sxs-lookup"><span data-stu-id="11f6a-102">Getting Started</span></span> 

<span data-ttu-id="11f6a-103">Une carte adaptative est un modèle d'objet de carte sérialisé au format JSON.</span><span class="sxs-lookup"><span data-stu-id="11f6a-103">An Adaptive Card is a JSON-serialized card object model.</span></span>

## <a name="adaptive-card-structure"></a><span data-ttu-id="11f6a-104">Structure d'une carte adaptative</span><span class="sxs-lookup"><span data-stu-id="11f6a-104">Adaptive Card structure</span></span>

<span data-ttu-id="11f6a-105">La structure de base d'une carte est la suivante :</span><span class="sxs-lookup"><span data-stu-id="11f6a-105">The basic structure of a card is as follows:</span></span>

* <span data-ttu-id="11f6a-106">`AdaptiveCard` : l'objet racine décrit la carte adaptative proprement dite, avec sa composition en termes d'éléments, ses actions, la façon dont elle doit être lue et la version du schéma requise pour la restituer.</span><span class="sxs-lookup"><span data-stu-id="11f6a-106">`AdaptiveCard` - The root object describes the AdaptiveCard itself, including its element makeup, its actions, how it should be spoken, and the schema version required to render it.</span></span>
* <span data-ttu-id="11f6a-107">`body` -le corps de la carte est constitué de modules appelés `elements`.</span><span class="sxs-lookup"><span data-stu-id="11f6a-107">`body` - The body of the card is made up of building-blocks known as `elements`.</span></span> <span data-ttu-id="11f6a-108">Les éléments peuvent être composés selon des combinaisons quasiment infinies pour créer de nombreux types de cartes.</span><span class="sxs-lookup"><span data-stu-id="11f6a-108">Elements can be composed in nearly infinite arrangements to create many types of cards.</span></span> 
* <span data-ttu-id="11f6a-109">`actions` : beaucoup de cartes disposent d'un ensemble d'actions applicables par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-109">`actions` - Many cards have a set of actions a user may take on it.</span></span> <span data-ttu-id="11f6a-110">Cette propriété décrit les actions qui sont généralement présentées sur une « barre d'action », en bas.</span><span class="sxs-lookup"><span data-stu-id="11f6a-110">This property describes those actions which typically get rendered in an "action bar" at the bottom.</span></span>

### <a name="example-card"></a><span data-ttu-id="11f6a-111">Exemple de carte</span><span class="sxs-lookup"><span data-stu-id="11f6a-111">Example Card</span></span>

<span data-ttu-id="11f6a-112">Cet exemple de carte comprend une ligne de texte suivie d'une image.</span><span class="sxs-lookup"><span data-stu-id="11f6a-112">This sample card which includes a single line of text followed by an image.</span></span>

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

## <a name="type-property"></a><span data-ttu-id="11f6a-113">Propriété `Type`</span><span class="sxs-lookup"><span data-stu-id="11f6a-113">`Type` property</span></span>

<span data-ttu-id="11f6a-114">Chaque élément possède une propriété `type` qui identifie le type d'objet dont il s'agit.</span><span class="sxs-lookup"><span data-stu-id="11f6a-114">Every element has a `type` property which identifies what kind of object it is.</span></span> <span data-ttu-id="11f6a-115">En examinant la carte ci-dessus, vous pouvez constater que nous disposons de deux éléments : `TextBlock` et `Image`.</span><span class="sxs-lookup"><span data-stu-id="11f6a-115">Looking at the above card, you can see we have two elements, a `TextBlock` and an `Image`.</span></span>

<span data-ttu-id="11f6a-116">Tous les éléments de la carte adaptative **sont empilés verticalement** et **s'étendent sur la largeur de leur parent** (pensez à `display: block` en HTML).</span><span class="sxs-lookup"><span data-stu-id="11f6a-116">All Adaptive Card elements **stack vertically** and **expand to the width of their parent** (think `display: block` in HTML).</span></span> <span data-ttu-id="11f6a-117">Vous pouvez toutefois utiliser `ColumnSet` pour créer des colonnes de conteneurs côte à côte.</span><span class="sxs-lookup"><span data-stu-id="11f6a-117">However, you can use a `ColumnSet` to create side-by-side columns of containers.</span></span>

## <a name="adaptive-elements"></a><span data-ttu-id="11f6a-118">Éléments adaptatifs</span><span class="sxs-lookup"><span data-stu-id="11f6a-118">Adaptive Elements</span></span>

<span data-ttu-id="11f6a-119">Les principaux éléments sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="11f6a-119">The most fundamental elements are:</span></span>

* <span data-ttu-id="11f6a-120">**TextBlock** : ajoute un bloc de texte avec des propriétés permettant de contrôler l'aspect du texte.</span><span class="sxs-lookup"><span data-stu-id="11f6a-120">**TextBlock** - adds a block of text with properties to control what the text looks like</span></span>
* <span data-ttu-id="11f6a-121">**Image** : ajoute une image avec des propriétés permettant de contrôler l'aspect de l'image.</span><span class="sxs-lookup"><span data-stu-id="11f6a-121">**Image** - adds an image with properties to control what the image looks like</span></span>

## <a name="container-elements"></a><span data-ttu-id="11f6a-122">Éléments conteneurs</span><span class="sxs-lookup"><span data-stu-id="11f6a-122">Container elements</span></span>

<span data-ttu-id="11f6a-123">Les cartes peuvent également comporter des conteneurs, qui permettent d'organiser une collection d'éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="11f6a-123">Cards can also have containers, which arrange a collection of child elements.</span></span>

* <span data-ttu-id="11f6a-124">**Container** : définit une collection d'éléments.</span><span class="sxs-lookup"><span data-stu-id="11f6a-124">**Container** - Defines a a collection of elements</span></span>
* <span data-ttu-id="11f6a-125">**ColumnSet/Column** : définit une collection de colonnes ; chaque colonne est un conteneur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-125">**ColumnSet/Column** - Defines a collection of columns, each column is a container</span></span>
* <span data-ttu-id="11f6a-126">**FactSet** : conteneur de faits.</span><span class="sxs-lookup"><span data-stu-id="11f6a-126">**FactSet** - Container of Facts</span></span>
* <span data-ttu-id="11f6a-127">**ImageSet** : conteneur d'images permettant à l'interface utilisateur d'afficher l'expérience de galerie photo appropriée pour une collection d'images.</span><span class="sxs-lookup"><span data-stu-id="11f6a-127">**ImageSet** - Container of Images so that UI can show appropriate photo gallery experience for a collection of images.</span></span>

## <a name="input-elements"></a><span data-ttu-id="11f6a-128">Éléments d'entrée</span><span class="sxs-lookup"><span data-stu-id="11f6a-128">Input elements</span></span>

<span data-ttu-id="11f6a-129">Les éléments d'entrée vous permettent de demander une interface utilisateur native pour créer des formulaires simples :</span><span class="sxs-lookup"><span data-stu-id="11f6a-129">Input elements allow you to ask for native UI to build simple forms:</span></span>

* <span data-ttu-id="11f6a-130">**Input.Text** : obtenir du contenu textuel auprès de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-130">**Input.Text** - get text content from the user</span></span>
* <span data-ttu-id="11f6a-131">**Input.Date** : obtenir une date auprès de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-131">**Input.Date** - get a Date from the user</span></span>
* <span data-ttu-id="11f6a-132">**Input.Time** : obtenir une heure auprès de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-132">**Input.Time** - get a Time from the user</span></span>
* <span data-ttu-id="11f6a-133">**Input.Number** : obtenir un nombre auprès de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-133">**Input.Number** - get a Number from the user</span></span>
* <span data-ttu-id="11f6a-134">**Input.ChoiceSet** : donner à l'utilisateur un ensemble de possibilités et lui demander de choisir.</span><span class="sxs-lookup"><span data-stu-id="11f6a-134">**Input.ChoiceSet** - Give the user a set of choices and have them pick</span></span>
* <span data-ttu-id="11f6a-135">**Input.Toggle** : donner à l'utilisateur de faire un choix entre deux éléments.</span><span class="sxs-lookup"><span data-stu-id="11f6a-135">**Input.Toggle** - Give the user a single choice between two items and have them pick</span></span>

## <a name="actions"></a><span data-ttu-id="11f6a-136">Actions</span><span class="sxs-lookup"><span data-stu-id="11f6a-136">Actions</span></span>

<span data-ttu-id="11f6a-137">Les actions ajoutent des boutons à la carte.</span><span class="sxs-lookup"><span data-stu-id="11f6a-137">Actions add buttons to the card.</span></span> <span data-ttu-id="11f6a-138">Ceux-ci permettent d'effectuer différents types d'actions, comme l'ouverture d'une URL ou l'envoi de certaines données.</span><span class="sxs-lookup"><span data-stu-id="11f6a-138">These can perform a variety of actions, like opening a URL or submitting some data.</span></span>

* <span data-ttu-id="11f6a-139">**Action.OpenUrl** : le bouton ouvre une URL externe à des fins d'affichage.</span><span class="sxs-lookup"><span data-stu-id="11f6a-139">**Action.OpenUrl** - the button opens an external URL for viewing</span></span>
* <span data-ttu-id="11f6a-140">**Action.ShowCard** : permet de demander de présenter une sous-carte à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f6a-140">**Action.ShowCard** - Requests a sub-card to be shown to the user.</span></span>
* <span data-ttu-id="11f6a-141">**Action.Submit** : permet de demander de regrouper tous les éléments d'entrée au sein d'un même objet, qui vous est ensuite envoyé via une méthode définie par l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="11f6a-141">**Action.Submit** - Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

> <span data-ttu-id="11f6a-142">**Example Action.Submit** : avec Skype, Action.Submit renvoie une activité Bot Framework au bot. La propriété **Value** comporte un objet contenant toutes les données d'entrée.</span><span class="sxs-lookup"><span data-stu-id="11f6a-142">**Example Action.Submit**: With Skype, an Action.Submit will send a Bot Framework bot activity back to the bot with the **Value** property containing an object with all of the input data on it.</span></span>

## <a name="learn-more"></a><span data-ttu-id="11f6a-143">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="11f6a-143">Learn More</span></span>

* <span data-ttu-id="11f6a-144">[Parcourir des exemples de cartes](https://adaptivecards.io/samples/) pour trouver l'inspiration</span><span class="sxs-lookup"><span data-stu-id="11f6a-144">[Browse Sample cards](https://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="11f6a-145">Utiliser l'[Explorateur de schémas](https://adaptivecards.io/explorer) pour parcourir les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="11f6a-145">Use the [Schema Explorer](https://adaptivecards.io/explorer) to browse the available elements</span></span>
* <span data-ttu-id="11f6a-146">Générer une carte à l'aide du [Visualiseur interactif](https://adaptivecards.io/visualizer/)</span><span class="sxs-lookup"><span data-stu-id="11f6a-146">Build a card using the [Interactive Visualizer](https://adaptivecards.io/visualizer/)</span></span>
* <span data-ttu-id="11f6a-147">[Nous contacter](https://adaptivecards.io/connect) pour nous faire part de vos commentaires</span><span class="sxs-lookup"><span data-stu-id="11f6a-147">[Get in touch](https://adaptivecards.io/connect) with any feedback you have</span></span>
