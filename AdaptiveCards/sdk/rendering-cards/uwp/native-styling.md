---
title: Style natif - SDK UWP
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3b95dc53c55c81fbbbbed6ee7605f86eb427a9
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552521"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="89ad7-102">Style natif - UWP</span><span class="sxs-lookup"><span data-stu-id="89ad7-102">Native styling - UWP</span></span>

<span data-ttu-id="89ad7-103">Tandis que la configuration de l’hôte vous aidera à la plupart de la façon dont il sur chaque plateforme, il est probable que vous devrez faire certains styles natif sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="89ad7-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="89ad7-104">UWP facilite cette procédure en vous permettant de passer un ResourceDictionary pour style affiné, comportement, animations, etc.</span><span class="sxs-lookup"><span data-stu-id="89ad7-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="89ad7-105">Élément</span><span class="sxs-lookup"><span data-stu-id="89ad7-105">Element</span></span> | <span data-ttu-id="89ad7-106">Noms de style</span><span class="sxs-lookup"><span data-stu-id="89ad7-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="89ad7-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="89ad7-107">AdaptiveCard</span></span> | <span data-ttu-id="89ad7-108">Adaptive.Card</span><span class="sxs-lookup"><span data-stu-id="89ad7-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="89ad7-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="89ad7-109">Action.OpenUrl</span></span>  | <span data-ttu-id="89ad7-110">Adaptive.Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="89ad7-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="89ad7-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="89ad7-111">Action.ShowCard</span></span> | <span data-ttu-id="89ad7-112">Adaptive.Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="89ad7-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="89ad7-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="89ad7-113">Action.Submit</span></span>  | <span data-ttu-id="89ad7-114">Adaptive.Action.Submit</span><span class="sxs-lookup"><span data-stu-id="89ad7-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="89ad7-115">colonne</span><span class="sxs-lookup"><span data-stu-id="89ad7-115">Column</span></span> | <span data-ttu-id="89ad7-116">Adaptive.Column, Adaptive.Action.Tap</span><span class="sxs-lookup"><span data-stu-id="89ad7-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="89ad7-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="89ad7-117">ColumnSet</span></span> | <span data-ttu-id="89ad7-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="89ad7-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="89ad7-119">Conteneur</span><span class="sxs-lookup"><span data-stu-id="89ad7-119">Container</span></span> | <span data-ttu-id="89ad7-120">Adaptive.Container</span><span class="sxs-lookup"><span data-stu-id="89ad7-120">Adaptive.Container</span></span>|
| <span data-ttu-id="89ad7-121">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="89ad7-121">Input.ChoiceSet</span></span> | <span data-ttu-id="89ad7-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="89ad7-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="89ad7-123">Input.Date</span><span class="sxs-lookup"><span data-stu-id="89ad7-123">Input.Date</span></span> | <span data-ttu-id="89ad7-124">Adaptive.Input.Text.Date</span><span class="sxs-lookup"><span data-stu-id="89ad7-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="89ad7-125">Input.Number</span><span class="sxs-lookup"><span data-stu-id="89ad7-125">Input.Number</span></span> | <span data-ttu-id="89ad7-126">Adaptive.Input.Text.Number</span><span class="sxs-lookup"><span data-stu-id="89ad7-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="89ad7-127">Input.Text</span><span class="sxs-lookup"><span data-stu-id="89ad7-127">Input.Text</span></span> | <span data-ttu-id="89ad7-128">Adaptive.Input.Text</span><span class="sxs-lookup"><span data-stu-id="89ad7-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="89ad7-129">Input.Time</span><span class="sxs-lookup"><span data-stu-id="89ad7-129">Input.Time</span></span> | <span data-ttu-id="89ad7-130">Adaptive.Input.Text.Time</span><span class="sxs-lookup"><span data-stu-id="89ad7-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="89ad7-131">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="89ad7-131">Input.Toggle</span></span>| <span data-ttu-id="89ad7-132">Adaptive.Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="89ad7-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="89ad7-133">Image</span><span class="sxs-lookup"><span data-stu-id="89ad7-133">Image</span></span>  | <span data-ttu-id="89ad7-134">Adaptive.Image</span><span class="sxs-lookup"><span data-stu-id="89ad7-134">Adaptive.Image</span></span> |
| <span data-ttu-id="89ad7-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="89ad7-135">ImageSet</span></span>  | <span data-ttu-id="89ad7-136">Adaptive.ImageSet</span><span class="sxs-lookup"><span data-stu-id="89ad7-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="89ad7-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="89ad7-137">FactSet</span></span> | <span data-ttu-id="89ad7-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span><span class="sxs-lookup"><span data-stu-id="89ad7-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="89ad7-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="89ad7-139">TextBlock</span></span>  | <span data-ttu-id="89ad7-140">Adaptive.TextBlock</span><span class="sxs-lookup"><span data-stu-id="89ad7-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="89ad7-141">Cet exemple de dictionnaire de ressource de XAML qui définit l’arrière-plan de toutes les TextBlocks sur « cyan ».</span><span class="sxs-lookup"><span data-stu-id="89ad7-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="89ad7-142">Vous souhaiterez probablement que quelque chose plus avancé que cela 😁</span><span class="sxs-lookup"><span data-stu-id="89ad7-142">You will probably want something more advanced than this 😁</span></span>

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
```
