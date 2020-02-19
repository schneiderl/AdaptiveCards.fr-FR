---
title: Styles natifs-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 5b829d9eefe933f133c8532030856849802c5eb5
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454492"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="a5e14-102">Styles natifs-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="a5e14-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="a5e14-103">Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="a5e14-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="a5e14-104">Le langage HTML facilite cette tâche en ajoutant des classes CSS à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="a5e14-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="a5e14-105">Élément</span><span class="sxs-lookup"><span data-stu-id="a5e14-105">Element</span></span> | <span data-ttu-id="a5e14-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="a5e14-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="a5e14-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="a5e14-107">AdaptiveCard</span></span> | <span data-ttu-id="a5e14-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="a5e14-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="a5e14-109">Toutes les actions</span><span class="sxs-lookup"><span data-stu-id="a5e14-109">All Actions</span></span> | <span data-ttu-id="a5e14-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="a5e14-110">ac-pushButton</span></span> | 
| <span data-ttu-id="a5e14-111">Sélectionner des actions</span><span class="sxs-lookup"><span data-stu-id="a5e14-111">Select Actions</span></span> | <span data-ttu-id="a5e14-112">AC-sélectionnable</span><span class="sxs-lookup"><span data-stu-id="a5e14-112">ac-selectable</span></span> |
| <span data-ttu-id="a5e14-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="a5e14-113">Action.OpenUrl</span></span>  | <span data-ttu-id="a5e14-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="a5e14-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="a5e14-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="a5e14-115">Action.ShowCard</span></span> | <span data-ttu-id="a5e14-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="a5e14-116">ac-action-showCard</span></span> |
| <span data-ttu-id="a5e14-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="a5e14-117">Action.Submit</span></span>  | <span data-ttu-id="a5e14-118">AC-action-envoyer</span><span class="sxs-lookup"><span data-stu-id="a5e14-118">ac-action-submit</span></span>  |
| <span data-ttu-id="a5e14-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="a5e14-119">ActionSet</span></span> | <span data-ttu-id="a5e14-120">AC-actionset</span><span class="sxs-lookup"><span data-stu-id="a5e14-120">ac-actionset</span></span> |
| <span data-ttu-id="a5e14-121">Column</span><span class="sxs-lookup"><span data-stu-id="a5e14-121">Column</span></span> | <span data-ttu-id="a5e14-122">AC-Column</span><span class="sxs-lookup"><span data-stu-id="a5e14-122">ac-column</span></span> |
| <span data-ttu-id="a5e14-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="a5e14-123">ColumnSet</span></span> | <span data-ttu-id="a5e14-124">AC-columnset</span><span class="sxs-lookup"><span data-stu-id="a5e14-124">ac-columnset</span></span> |
| <span data-ttu-id="a5e14-125">Conteneur</span><span class="sxs-lookup"><span data-stu-id="a5e14-125">Container</span></span> | <span data-ttu-id="a5e14-126">AC-Container</span><span class="sxs-lookup"><span data-stu-id="a5e14-126">ac-container</span></span> |
| <span data-ttu-id="a5e14-127">Toutes les entrées</span><span class="sxs-lookup"><span data-stu-id="a5e14-127">All Inputs</span></span> | <span data-ttu-id="a5e14-128">entrée c.a.</span><span class="sxs-lookup"><span data-stu-id="a5e14-128">ac-input</span></span> |
| <span data-ttu-id="a5e14-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="a5e14-129">Input.ChoiceSet</span></span> | <span data-ttu-id="a5e14-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="a5e14-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="a5e14-131">Entrée. date</span><span class="sxs-lookup"><span data-stu-id="a5e14-131">Input.Date</span></span> | <span data-ttu-id="a5e14-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="a5e14-132">ac-dateInput</span></span> |
| <span data-ttu-id="a5e14-133">Entrée. nombre</span><span class="sxs-lookup"><span data-stu-id="a5e14-133">Input.Number</span></span> | <span data-ttu-id="a5e14-134">AC-numberInput</span><span class="sxs-lookup"><span data-stu-id="a5e14-134">ac-numberInput</span></span> |
| <span data-ttu-id="a5e14-135">Input. Text</span><span class="sxs-lookup"><span data-stu-id="a5e14-135">Input.Text</span></span> | <span data-ttu-id="a5e14-136">AC-textInput</span><span class="sxs-lookup"><span data-stu-id="a5e14-136">ac-textInput</span></span> |
| <span data-ttu-id="a5e14-137">Input. Time</span><span class="sxs-lookup"><span data-stu-id="a5e14-137">Input.Time</span></span> | <span data-ttu-id="a5e14-138">AC-timeInput</span><span class="sxs-lookup"><span data-stu-id="a5e14-138">ac-timeInput</span></span> |
| <span data-ttu-id="a5e14-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="a5e14-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="a5e14-140">Image</span><span class="sxs-lookup"><span data-stu-id="a5e14-140">Image</span></span>  | <span data-ttu-id="a5e14-141">image AC</span><span class="sxs-lookup"><span data-stu-id="a5e14-141">ac-image</span></span> |
| <span data-ttu-id="a5e14-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="a5e14-142">ImageSet</span></span>  | <span data-ttu-id="a5e14-143">ac-imageset</span><span class="sxs-lookup"><span data-stu-id="a5e14-143">ac-imageset</span></span> |
| <span data-ttu-id="a5e14-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="a5e14-144">FactSet</span></span> | <span data-ttu-id="a5e14-145">AC-FactSet</span><span class="sxs-lookup"><span data-stu-id="a5e14-145">ac-factset</span></span> |
| <span data-ttu-id="a5e14-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="a5e14-146">TextBlock</span></span>  | <span data-ttu-id="a5e14-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="a5e14-147">ac-textblock</span></span> |