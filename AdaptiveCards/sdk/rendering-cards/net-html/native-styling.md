---
title: Style natif - Kit de développement logiciel .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 620940dee873742898d58979c61827320bc3c202
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552561"
---
# <a name="native-styling---net-html"></a><span data-ttu-id="2e427-102">Style natif - .NET HTML</span><span class="sxs-lookup"><span data-stu-id="2e427-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="2e427-103">Tandis que la configuration de l’hôte vous aidera à la plupart de la façon dont il sur chaque plateforme, il est probable que vous devrez faire certains styles natif sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="2e427-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="2e427-104">HTML facilite cette procédure en ajoutant les classes CSS à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="2e427-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="2e427-105">Élément</span><span class="sxs-lookup"><span data-stu-id="2e427-105">Element</span></span> | <span data-ttu-id="2e427-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="2e427-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="2e427-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="2e427-107">AdaptiveCard</span></span> | <span data-ttu-id="2e427-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="2e427-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="2e427-109">Toutes les Actions</span><span class="sxs-lookup"><span data-stu-id="2e427-109">All Actions</span></span> | <span data-ttu-id="2e427-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="2e427-110">ac-pushButton</span></span> | 
| <span data-ttu-id="2e427-111">Sélectionnez les Actions</span><span class="sxs-lookup"><span data-stu-id="2e427-111">Select Actions</span></span> | <span data-ttu-id="2e427-112">AC-sélectionnables</span><span class="sxs-lookup"><span data-stu-id="2e427-112">ac-selectable</span></span> |
| <span data-ttu-id="2e427-113">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="2e427-113">Action.OpenUrl</span></span>  | <span data-ttu-id="2e427-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="2e427-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="2e427-115">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="2e427-115">Action.ShowCard</span></span> | <span data-ttu-id="2e427-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="2e427-116">ac-action-showCard</span></span> |
| <span data-ttu-id="2e427-117">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="2e427-117">Action.Submit</span></span>  | <span data-ttu-id="2e427-118">ac-action-submit</span><span class="sxs-lookup"><span data-stu-id="2e427-118">ac-action-submit</span></span>  |
| <span data-ttu-id="2e427-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="2e427-119">ActionSet</span></span> | <span data-ttu-id="2e427-120">ac-actionset</span><span class="sxs-lookup"><span data-stu-id="2e427-120">ac-actionset</span></span> |
| <span data-ttu-id="2e427-121">colonne</span><span class="sxs-lookup"><span data-stu-id="2e427-121">Column</span></span> | <span data-ttu-id="2e427-122">AC-colonne</span><span class="sxs-lookup"><span data-stu-id="2e427-122">ac-column</span></span> |
| <span data-ttu-id="2e427-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="2e427-123">ColumnSet</span></span> | <span data-ttu-id="2e427-124">AC-jeu de colonnes</span><span class="sxs-lookup"><span data-stu-id="2e427-124">ac-columnset</span></span> |
| <span data-ttu-id="2e427-125">Conteneur</span><span class="sxs-lookup"><span data-stu-id="2e427-125">Container</span></span> | <span data-ttu-id="2e427-126">AC-container</span><span class="sxs-lookup"><span data-stu-id="2e427-126">ac-container</span></span> |
| <span data-ttu-id="2e427-127">Toutes les entrées</span><span class="sxs-lookup"><span data-stu-id="2e427-127">All Inputs</span></span> | <span data-ttu-id="2e427-128">alimentation en courant alternatif</span><span class="sxs-lookup"><span data-stu-id="2e427-128">ac-input</span></span> |
| <span data-ttu-id="2e427-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="2e427-129">Input.ChoiceSet</span></span> | <span data-ttu-id="2e427-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="2e427-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="2e427-131">Input.Date</span><span class="sxs-lookup"><span data-stu-id="2e427-131">Input.Date</span></span> | <span data-ttu-id="2e427-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="2e427-132">ac-dateInput</span></span> |
| <span data-ttu-id="2e427-133">Input.Number</span><span class="sxs-lookup"><span data-stu-id="2e427-133">Input.Number</span></span> | <span data-ttu-id="2e427-134">ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="2e427-134">ac-numberInput</span></span> |
| <span data-ttu-id="2e427-135">Input.Text</span><span class="sxs-lookup"><span data-stu-id="2e427-135">Input.Text</span></span> | <span data-ttu-id="2e427-136">ac-textInput</span><span class="sxs-lookup"><span data-stu-id="2e427-136">ac-textInput</span></span> |
| <span data-ttu-id="2e427-137">Input.Time</span><span class="sxs-lookup"><span data-stu-id="2e427-137">Input.Time</span></span> | <span data-ttu-id="2e427-138">ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="2e427-138">ac-timeInput</span></span> |
| <span data-ttu-id="2e427-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="2e427-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="2e427-140">Image</span><span class="sxs-lookup"><span data-stu-id="2e427-140">Image</span></span>  | <span data-ttu-id="2e427-141">ac-image</span><span class="sxs-lookup"><span data-stu-id="2e427-141">ac-image</span></span> |
| <span data-ttu-id="2e427-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="2e427-142">ImageSet</span></span>  | <span data-ttu-id="2e427-143">ac-imageset</span><span class="sxs-lookup"><span data-stu-id="2e427-143">ac-imageset</span></span> |
| <span data-ttu-id="2e427-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="2e427-144">FactSet</span></span> | <span data-ttu-id="2e427-145">AC-factset</span><span class="sxs-lookup"><span data-stu-id="2e427-145">ac-factset</span></span> |
| <span data-ttu-id="2e427-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="2e427-146">TextBlock</span></span>  | <span data-ttu-id="2e427-147">ac-textblock</span><span class="sxs-lookup"><span data-stu-id="2e427-147">ac-textblock</span></span> |