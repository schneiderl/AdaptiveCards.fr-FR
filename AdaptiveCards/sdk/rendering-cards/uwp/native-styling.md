---
title: Style natif-Kit de développement logiciel (SDK) UWP
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3c7616ce4fe307eda3073f7037842e3e3df81b
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417518"
---
# <a name="native-styling---uwp"></a><span data-ttu-id="9c571-102">Style natif-UWP</span><span class="sxs-lookup"><span data-stu-id="9c571-102">Native styling - UWP</span></span>

<span data-ttu-id="9c571-103">Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="9c571-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="9c571-104">UWP facilite cette tâche en vous permettant de transmettre un ResourceDictionary pour un style, un comportement, des animations, etc. précis.</span><span class="sxs-lookup"><span data-stu-id="9c571-104">UWP makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="9c571-105">Élément</span><span class="sxs-lookup"><span data-stu-id="9c571-105">Element</span></span> | <span data-ttu-id="9c571-106">Noms de style</span><span class="sxs-lookup"><span data-stu-id="9c571-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="9c571-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="9c571-107">AdaptiveCard</span></span> | <span data-ttu-id="9c571-108">Carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="9c571-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="9c571-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="9c571-109">Action.OpenUrl</span></span>  | <span data-ttu-id="9c571-110">Adaptative. action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="9c571-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="9c571-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="9c571-111">Action.ShowCard</span></span> | <span data-ttu-id="9c571-112">Adaptive. action. ShowCard</span><span class="sxs-lookup"><span data-stu-id="9c571-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="9c571-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="9c571-113">Action.Submit</span></span>  | <span data-ttu-id="9c571-114">Adaptative. action. Submit</span><span class="sxs-lookup"><span data-stu-id="9c571-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="9c571-115">Colonne</span><span class="sxs-lookup"><span data-stu-id="9c571-115">Column</span></span> | <span data-ttu-id="9c571-116">Adaptative. Column, adaptative. action. TAP</span><span class="sxs-lookup"><span data-stu-id="9c571-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="9c571-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="9c571-117">ColumnSet</span></span> | <span data-ttu-id="9c571-118">Adaptive. ColumnSet, adaptatif. VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="9c571-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="9c571-119">Conteneur</span><span class="sxs-lookup"><span data-stu-id="9c571-119">Container</span></span> | <span data-ttu-id="9c571-120">Adaptative. Container</span><span class="sxs-lookup"><span data-stu-id="9c571-120">Adaptive.Container</span></span>|
| <span data-ttu-id="9c571-121">Entrée. ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="9c571-121">Input.ChoiceSet</span></span> | <span data-ttu-id="9c571-122">Adaptative. Input. ChoiceSet, adaptative. Input. ChoiceSet. ComboBox, adaptative. Input. ChoiceSet. CheckBox, adaptative. Input. ChoiceSet. radio, adaptative. Input. ChoiceSet. ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="9c571-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="9c571-123">Entrée. date</span><span class="sxs-lookup"><span data-stu-id="9c571-123">Input.Date</span></span> | <span data-ttu-id="9c571-124">Adaptative. Input. Text. date</span><span class="sxs-lookup"><span data-stu-id="9c571-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="9c571-125">Entrée. nombre</span><span class="sxs-lookup"><span data-stu-id="9c571-125">Input.Number</span></span> | <span data-ttu-id="9c571-126">Adaptative. Input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="9c571-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="9c571-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="9c571-127">Input.Text</span></span> | <span data-ttu-id="9c571-128">Adaptative. Input. Text</span><span class="sxs-lookup"><span data-stu-id="9c571-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="9c571-129">Input. Time</span><span class="sxs-lookup"><span data-stu-id="9c571-129">Input.Time</span></span> | <span data-ttu-id="9c571-130">Adaptative. Input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="9c571-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="9c571-131">Entrée. Toggle</span><span class="sxs-lookup"><span data-stu-id="9c571-131">Input.Toggle</span></span>| <span data-ttu-id="9c571-132">Adaptative. Input. Toggle</span><span class="sxs-lookup"><span data-stu-id="9c571-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="9c571-133">Image</span><span class="sxs-lookup"><span data-stu-id="9c571-133">Image</span></span>  | <span data-ttu-id="9c571-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="9c571-134">Adaptive.Image</span></span> |
| <span data-ttu-id="9c571-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="9c571-135">ImageSet</span></span>  | <span data-ttu-id="9c571-136">Adaptive. ImageSet</span><span class="sxs-lookup"><span data-stu-id="9c571-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="9c571-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="9c571-137">FactSet</span></span> | <span data-ttu-id="9c571-138">Adaptive. FactSet, adaptative. fact. title, adaptatif. fact. Value</span><span class="sxs-lookup"><span data-stu-id="9c571-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="9c571-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="9c571-139">TextBlock</span></span>  | <span data-ttu-id="9c571-140">Adaptive. TextBlock</span><span class="sxs-lookup"><span data-stu-id="9c571-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="9c571-141">Cet exemple de dictionnaire de ressources XAML définit l’arrière-plan de tous les TextBlocks sur Aqua.</span><span class="sxs-lookup"><span data-stu-id="9c571-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="9c571-142">Vous souhaiterez probablement une plus grande avancée que celle-ci😁</span><span class="sxs-lookup"><span data-stu-id="9c571-142">You will probably want something more advanced than this 😁</span></span>

```xml
<ResourceDictionary
    xmlns="https://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="https://schemas.microsoft.com/winfx/2006/xaml">
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
