---
title: Styles natifs-SDK HTML .NET
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
# <a name="native-styling---net-html"></a><span data-ttu-id="9ca33-102">Styles natifs-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="9ca33-102">Native styling - .NET HTML</span></span>

<span data-ttu-id="9ca33-103">Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="9ca33-103">While Host Config will get you most of the way there on each platform, it's likely that you will have to do some native styling on each platform.</span></span> 

<span data-ttu-id="9ca33-104">Le langage HTML facilite cette tâche en ajoutant des classes CSS à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="9ca33-104">HTML makes this easy by adding CSS classes to every element.</span></span>

| <span data-ttu-id="9ca33-105">Élément</span><span class="sxs-lookup"><span data-stu-id="9ca33-105">Element</span></span> | <span data-ttu-id="9ca33-106">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="9ca33-106">CSS class</span></span> |
|---|---|
| <span data-ttu-id="9ca33-107">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="9ca33-107">AdaptiveCard</span></span> | <span data-ttu-id="9ca33-108">ac-adaptivecard</span><span class="sxs-lookup"><span data-stu-id="9ca33-108">ac-adaptivecard</span></span> |
| <span data-ttu-id="9ca33-109">Toutes les actions</span><span class="sxs-lookup"><span data-stu-id="9ca33-109">All Actions</span></span> | <span data-ttu-id="9ca33-110">ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="9ca33-110">ac-pushButton</span></span> | 
| <span data-ttu-id="9ca33-111">Sélectionner des actions</span><span class="sxs-lookup"><span data-stu-id="9ca33-111">Select Actions</span></span> | <span data-ttu-id="9ca33-112">AC-sélectionnable</span><span class="sxs-lookup"><span data-stu-id="9ca33-112">ac-selectable</span></span> |
| <span data-ttu-id="9ca33-113">Action. OpenUrl</span><span class="sxs-lookup"><span data-stu-id="9ca33-113">Action.OpenUrl</span></span>  | <span data-ttu-id="9ca33-114">ac-action-openUrl</span><span class="sxs-lookup"><span data-stu-id="9ca33-114">ac-action-openUrl</span></span> |
| <span data-ttu-id="9ca33-115">Action. ShowCard</span><span class="sxs-lookup"><span data-stu-id="9ca33-115">Action.ShowCard</span></span> | <span data-ttu-id="9ca33-116">ac-action-showCard</span><span class="sxs-lookup"><span data-stu-id="9ca33-116">ac-action-showCard</span></span> |
| <span data-ttu-id="9ca33-117">Action. Submit</span><span class="sxs-lookup"><span data-stu-id="9ca33-117">Action.Submit</span></span>  | <span data-ttu-id="9ca33-118">AC-action-envoyer</span><span class="sxs-lookup"><span data-stu-id="9ca33-118">ac-action-submit</span></span>  |
| <span data-ttu-id="9ca33-119">ActionSet</span><span class="sxs-lookup"><span data-stu-id="9ca33-119">ActionSet</span></span> | <span data-ttu-id="9ca33-120">AC-actionset</span><span class="sxs-lookup"><span data-stu-id="9ca33-120">ac-actionset</span></span> |
| <span data-ttu-id="9ca33-121">colonne</span><span class="sxs-lookup"><span data-stu-id="9ca33-121">Column</span></span> | <span data-ttu-id="9ca33-122">AC-Column</span><span class="sxs-lookup"><span data-stu-id="9ca33-122">ac-column</span></span> |
| <span data-ttu-id="9ca33-123">ColumnSet</span><span class="sxs-lookup"><span data-stu-id="9ca33-123">ColumnSet</span></span> | <span data-ttu-id="9ca33-124">AC-columnset</span><span class="sxs-lookup"><span data-stu-id="9ca33-124">ac-columnset</span></span> |
| <span data-ttu-id="9ca33-125">Conteneur</span><span class="sxs-lookup"><span data-stu-id="9ca33-125">Container</span></span> | <span data-ttu-id="9ca33-126">AC-Container</span><span class="sxs-lookup"><span data-stu-id="9ca33-126">ac-container</span></span> |
| <span data-ttu-id="9ca33-127">Toutes les entrées</span><span class="sxs-lookup"><span data-stu-id="9ca33-127">All Inputs</span></span> | <span data-ttu-id="9ca33-128">entrée c.a.</span><span class="sxs-lookup"><span data-stu-id="9ca33-128">ac-input</span></span> |
| <span data-ttu-id="9ca33-129">Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="9ca33-129">Input.ChoiceSet</span></span> | <span data-ttu-id="9ca33-130">ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="9ca33-130">ac-multichoiceInput</span></span>  |
| <span data-ttu-id="9ca33-131">Entrée. date</span><span class="sxs-lookup"><span data-stu-id="9ca33-131">Input.Date</span></span> | <span data-ttu-id="9ca33-132">ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="9ca33-132">ac-dateInput</span></span> |
| <span data-ttu-id="9ca33-133">Entrée. nombre</span><span class="sxs-lookup"><span data-stu-id="9ca33-133">Input.Number</span></span> | <span data-ttu-id="9ca33-134">AC-numberInput</span><span class="sxs-lookup"><span data-stu-id="9ca33-134">ac-numberInput</span></span> |
| <span data-ttu-id="9ca33-135">Input. Text</span><span class="sxs-lookup"><span data-stu-id="9ca33-135">Input.Text</span></span> | <span data-ttu-id="9ca33-136">AC-textInput</span><span class="sxs-lookup"><span data-stu-id="9ca33-136">ac-textInput</span></span> |
| <span data-ttu-id="9ca33-137">Input. Time</span><span class="sxs-lookup"><span data-stu-id="9ca33-137">Input.Time</span></span> | <span data-ttu-id="9ca33-138">AC-timeInput</span><span class="sxs-lookup"><span data-stu-id="9ca33-138">ac-timeInput</span></span> |
| <span data-ttu-id="9ca33-139">Input.Toggle</span><span class="sxs-lookup"><span data-stu-id="9ca33-139">Input.Toggle</span></span>| - |
| <span data-ttu-id="9ca33-140">Image</span><span class="sxs-lookup"><span data-stu-id="9ca33-140">Image</span></span>  | <span data-ttu-id="9ca33-141">image AC</span><span class="sxs-lookup"><span data-stu-id="9ca33-141">ac-image</span></span> |
| <span data-ttu-id="9ca33-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="9ca33-142">ImageSet</span></span>  | <span data-ttu-id="9ca33-143">ac-imageset</span><span class="sxs-lookup"><span data-stu-id="9ca33-143">ac-imageset</span></span> |
| <span data-ttu-id="9ca33-144">FactSet</span><span class="sxs-lookup"><span data-stu-id="9ca33-144">FactSet</span></span> | <span data-ttu-id="9ca33-145">AC-FactSet</span><span class="sxs-lookup"><span data-stu-id="9ca33-145">ac-factset</span></span> |
| <span data-ttu-id="9ca33-146">TextBlock</span><span class="sxs-lookup"><span data-stu-id="9ca33-146">TextBlock</span></span>  | <span data-ttu-id="9ca33-147">AC-TextBlock</span><span class="sxs-lookup"><span data-stu-id="9ca33-147">ac-textblock</span></span> |