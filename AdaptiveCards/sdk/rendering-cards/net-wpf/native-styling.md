---
title: Styles natifs-SDK .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f9243fc6880c926c04f80f74713e91d1e37cf3d5
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417595"
---
# <a name="native-styling---net-wpf"></a><span data-ttu-id="3b8a2-102">Styles natifs-WPF .NET</span><span class="sxs-lookup"><span data-stu-id="3b8a2-102">Native styling - .NET WPF</span></span>

<span data-ttu-id="3b8a2-103">Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="3b8a2-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="3b8a2-104">WPF facilite cette opération en vous permettant de transmettre un ResourceDictionary pour un style, un comportement, des animations, etc. précis.</span><span class="sxs-lookup"><span data-stu-id="3b8a2-104">WPF makes this easy by allowing you to pass a ResourceDictionary for fine-grained styling, behavior, animations, etc.</span></span>

| <span data-ttu-id="3b8a2-105">Élément</span><span class="sxs-lookup"><span data-stu-id="3b8a2-105">Element</span></span> | <span data-ttu-id="3b8a2-106">Noms de style</span><span class="sxs-lookup"><span data-stu-id="3b8a2-106">Style names</span></span> |
|---|---|
| <span data-ttu-id="3b8a2-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="3b8a2-107">AdaptiveCard</span></span> | <span data-ttu-id="3b8a2-108">Carte adaptative.</span><span class="sxs-lookup"><span data-stu-id="3b8a2-108">Adaptive.Card</span></span>| 
| <span data-ttu-id="3b8a2-109">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="3b8a2-109">Action.OpenUrl</span></span>  | <span data-ttu-id="3b8a2-110">Adaptative. action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="3b8a2-110">Adaptive.Action.OpenUrl</span></span>  |
| <span data-ttu-id="3b8a2-111">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="3b8a2-111">Action.ShowCard</span></span> | <span data-ttu-id="3b8a2-112">Adaptive. action. ShowCard</span><span class="sxs-lookup"><span data-stu-id="3b8a2-112">Adaptive.Action.ShowCard</span></span> |
| <span data-ttu-id="3b8a2-113">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="3b8a2-113">Action.Submit</span></span>  | <span data-ttu-id="3b8a2-114">Adaptative. action. Submit</span><span class="sxs-lookup"><span data-stu-id="3b8a2-114">Adaptive.Action.Submit</span></span>  |
| <span data-ttu-id="3b8a2-115">Colonne</span><span class="sxs-lookup"><span data-stu-id="3b8a2-115">Column</span></span> | <span data-ttu-id="3b8a2-116">Adaptative. Column, adaptative. action. TAP</span><span class="sxs-lookup"><span data-stu-id="3b8a2-116">Adaptive.Column, Adaptive.Action.Tap</span></span> |
| <span data-ttu-id="3b8a2-117">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="3b8a2-117">ColumnSet</span></span> | <span data-ttu-id="3b8a2-118">Adaptive. ColumnSet, adaptatif. VerticalSeparator</span><span class="sxs-lookup"><span data-stu-id="3b8a2-118">Adaptive.ColumnSet, Adaptive.VerticalSeparator</span></span> |
| <span data-ttu-id="3b8a2-119">Conteneur</span><span class="sxs-lookup"><span data-stu-id="3b8a2-119">Container</span></span> | <span data-ttu-id="3b8a2-120">Adaptative. Container</span><span class="sxs-lookup"><span data-stu-id="3b8a2-120">Adaptive.Container</span></span>|
| <span data-ttu-id="3b8a2-121">Entrée. ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="3b8a2-121">Input.ChoiceSet</span></span> | <span data-ttu-id="3b8a2-122">Adaptative. Input. ChoiceSet, adaptative. Input. ChoiceSet. ComboBox, adaptative. Input. ChoiceSet. CheckBox, adaptative. Input. ChoiceSet. radio, adaptative. Input. ChoiceSet. ComboBoxItem</span><span class="sxs-lookup"><span data-stu-id="3b8a2-122">Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem</span></span> |
| <span data-ttu-id="3b8a2-123">Entrée. date</span><span class="sxs-lookup"><span data-stu-id="3b8a2-123">Input.Date</span></span> | <span data-ttu-id="3b8a2-124">Adaptative. Input. Text. date</span><span class="sxs-lookup"><span data-stu-id="3b8a2-124">Adaptive.Input.Text.Date</span></span>
| <span data-ttu-id="3b8a2-125">Entrée. nombre</span><span class="sxs-lookup"><span data-stu-id="3b8a2-125">Input.Number</span></span> | <span data-ttu-id="3b8a2-126">Adaptative. Input. Text. Number</span><span class="sxs-lookup"><span data-stu-id="3b8a2-126">Adaptive.Input.Text.Number</span></span> |
| <span data-ttu-id="3b8a2-127">Input. Text</span><span class="sxs-lookup"><span data-stu-id="3b8a2-127">Input.Text</span></span> | <span data-ttu-id="3b8a2-128">Adaptative. Input. Text</span><span class="sxs-lookup"><span data-stu-id="3b8a2-128">Adaptive.Input.Text</span></span> |
| <span data-ttu-id="3b8a2-129">Input. Time</span><span class="sxs-lookup"><span data-stu-id="3b8a2-129">Input.Time</span></span> | <span data-ttu-id="3b8a2-130">Adaptative. Input. Text. Time</span><span class="sxs-lookup"><span data-stu-id="3b8a2-130">Adaptive.Input.Text.Time</span></span> |
| <span data-ttu-id="3b8a2-131">Entrée. Toggle</span><span class="sxs-lookup"><span data-stu-id="3b8a2-131">Input.Toggle</span></span>| <span data-ttu-id="3b8a2-132">Adaptative. Input. Toggle</span><span class="sxs-lookup"><span data-stu-id="3b8a2-132">Adaptive.Input.Toggle</span></span>|
| <span data-ttu-id="3b8a2-133">Image</span><span class="sxs-lookup"><span data-stu-id="3b8a2-133">Image</span></span>  | <span data-ttu-id="3b8a2-134">Adaptive. image</span><span class="sxs-lookup"><span data-stu-id="3b8a2-134">Adaptive.Image</span></span> |
| <span data-ttu-id="3b8a2-135">ImageSet</span><span class="sxs-lookup"><span data-stu-id="3b8a2-135">ImageSet</span></span>  | <span data-ttu-id="3b8a2-136">Adaptive. ImageSet</span><span class="sxs-lookup"><span data-stu-id="3b8a2-136">Adaptive.ImageSet</span></span> |
| <span data-ttu-id="3b8a2-137">FactSet</span><span class="sxs-lookup"><span data-stu-id="3b8a2-137">FactSet</span></span> | <span data-ttu-id="3b8a2-138">Adaptive. FactSet, adaptative. fact. title, adaptatif. fact. Value</span><span class="sxs-lookup"><span data-stu-id="3b8a2-138">Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value</span></span> |
| <span data-ttu-id="3b8a2-139">TextBlock</span><span class="sxs-lookup"><span data-stu-id="3b8a2-139">TextBlock</span></span>  | <span data-ttu-id="3b8a2-140">Adaptive. TextBlock</span><span class="sxs-lookup"><span data-stu-id="3b8a2-140">Adaptive.TextBlock</span></span> |

<span data-ttu-id="3b8a2-141">Cet exemple de dictionnaire de ressources XAML définit l’arrière-plan de tous les TextBlocks sur Aqua.</span><span class="sxs-lookup"><span data-stu-id="3b8a2-141">This sample XAML Resource dictionary that sets the background of all TextBlocks to Aqua.</span></span> <span data-ttu-id="3b8a2-142">Vous souhaiterez probablement une plus grande avancée que celle-ci😁</span><span class="sxs-lookup"><span data-stu-id="3b8a2-142">You will probably want something more advanced than this 😁</span></span>

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

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> <span data-ttu-id="3b8a2-143">**Remarque sur la génération d’images côté serveur** Le convertisseur WPF fournit une `RenderCardToImageAsync` méthode qui peut être utilisée pour la génération d’images côté serveur.</span><span class="sxs-lookup"><span data-stu-id="3b8a2-143">**A note about server-side image generation** The WPF renderer provides a `RenderCardToImageAsync` method that can be used for server-side image generation.</span></span> <span data-ttu-id="3b8a2-144">Vous devez uniquement utiliser la `ResourcesPath` propriété si elle est utilisée dans cet environnement.</span><span class="sxs-lookup"><span data-stu-id="3b8a2-144">You must only use the `ResourcesPath` property if used in this environment.</span></span> <span data-ttu-id="3b8a2-145">Consultez les documents de [rendu d’image](../net-image/getting-started.md) pour plus d’informations</span><span class="sxs-lookup"><span data-stu-id="3b8a2-145">See the [Image Rendering](../net-image/getting-started.md) docs for more</span></span>