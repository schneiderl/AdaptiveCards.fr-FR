---
title: Style natif - Kit de développement logiciel .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ee5bec1a11f39ad69d40e57410c105b50ba45981
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552721"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="6e23f-102">Style natif - .NET WPF</span><span class="sxs-lookup"><span data-stu-id="6e23f-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="6e23f-103">Tandis que la configuration de l’hôte vous aidera à la plupart de la façon dont il sur chaque plateforme, il est probable que vous devrez faire certains styles natif sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="6e23f-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="6e23f-104">WPF facilite cette procédure en vous permettant de passer un ResourceDictionary pour style affiné, comportement, animations, etc.</span><span class="sxs-lookup"><span data-stu-id="6e23f-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="6e23f-105">Élément</span><span class="sxs-lookup"><span data-stu-id="6e23f-105">Element</span></span> | <span data-ttu-id="6e23f-106">Noms de style</span><span class="sxs-lookup"><span data-stu-id="6e23f-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="6e23f-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="6e23f-107">AdaptiveCard</span></span> | <span data-ttu-id="6e23f-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="6e23f-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="6e23f-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="6e23f-109">Action.OpenUrl</span></span>  | <span data-ttu-id="6e23f-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="6e23f-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="6e23f-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="6e23f-111">Action.ShowCard</span></span> | <span data-ttu-id="6e23f-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="6e23f-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="6e23f-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="6e23f-113">Action.Submit</span></span>  | <span data-ttu-id="6e23f-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="6e23f-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="6e23f-115">colonne</span><span class="sxs-lookup"><span data-stu-id="6e23f-115">Column</span></span> | <span data-ttu-id="6e23f-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="6e23f-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="6e23f-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="6e23f-117">ColumnSet</span></span> | <span data-ttu-id="6e23f-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="6e23f-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="6e23f-119">Conteneur</span><span class="sxs-lookup"><span data-stu-id="6e23f-119">Container</span></span> | <span data-ttu-id="6e23f-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="6e23f-120">Adaptive.Container</span></span>|
| <span data-ttu-id="6e23f-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="6e23f-121">Input.ChoiceSet</span></span> | <span data-ttu-id="6e23f-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="6e23f-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="6e23f-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="6e23f-123">Input.Date</span></span> | <span data-ttu-id="6e23f-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="6e23f-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="6e23f-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="6e23f-125">Input.Number</span></span> | <span data-ttu-id="6e23f-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="6e23f-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="6e23f-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="6e23f-127">Input.Text</span></span> | <span data-ttu-id="6e23f-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="6e23f-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="6e23f-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="6e23f-129">Input.Time</span></span> | <span data-ttu-id="6e23f-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="6e23f-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="6e23f-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="6e23f-131">Input.Toggle</span></span>| <span data-ttu-id="6e23f-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="6e23f-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="6e23f-133">Image</span><span class="sxs-lookup"><span data-stu-id="6e23f-133">Image</span></span>  | <span data-ttu-id="6e23f-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="6e23f-134">Adaptive.Image</span></span> |
| <span data-ttu-id="6e23f-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="6e23f-135">ImageSet</span></span>  | <span data-ttu-id="6e23f-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="6e23f-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="6e23f-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="6e23f-137">FactSet</span></span> | <span data-ttu-id="6e23f-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="6e23f-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="6e23f-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="6e23f-139">TextBlock</span></span>  | <span data-ttu-id="6e23f-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="6e23f-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="6e23f-141">Cet exemple de dictionnaire de ressource de XAML qui définit l’arrière-plan de toutes les TextBlocks sur « cyan ».</span><span class="sxs-lookup"><span data-stu-id="6e23f-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="6e23f-142">Vous souhaiterez probablement que quelque chose plus avancé que cela 😁</span><span class="sxs-lookup"><span data-stu-id="6e23f-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> <span data-ttu-id="6e23f-143">**Une remarque sur la génération d’image côté serveur** WPF le convertisseur fournit une `RenderCardToImageAsync` méthode qui peut être utilisé pour la génération d’images du côté serveur.</span><span class="sxs-lookup"><span data-stu-id="6e23f-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="6e23f-144">Vous devez utiliser uniquement le `ResourcesPath` propriété si utilisés dans cet environnement.</span><span class="sxs-lookup"><span data-stu-id="6e23f-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="6e23f-145">Consultez le [rendu de l’Image](../net-image/getting-started.md) docs pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="6e23f-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>