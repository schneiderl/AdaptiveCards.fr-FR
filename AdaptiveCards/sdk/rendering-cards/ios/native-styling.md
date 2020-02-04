---
title: Stylisation Native-Kit de développement logiciel (SDK) iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f9ed839a19ac778381fa36361ad37e95b7ab5e08
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727471"
---
# <a name="native-styling---ios"></a><span data-ttu-id="f1a6c-102">Stylisation Native-iOS</span><span class="sxs-lookup"><span data-stu-id="f1a6c-102">Native styling - iOS</span></span>

<span data-ttu-id="f1a6c-103">Utilisez XIB pour un style affiné.</span><span class="sxs-lookup"><span data-stu-id="f1a6c-103">Use XIB for fine-grained styling.</span></span>

<span data-ttu-id="f1a6c-104">Les XIB suivants existent</span><span class="sxs-lookup"><span data-stu-id="f1a6c-104">The following XIBs exist</span></span>

| <span data-ttu-id="f1a6c-105">XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-105">XIB</span></span> | <span data-ttu-id="f1a6c-106">Utilisation</span><span class="sxs-lookup"><span data-stu-id="f1a6c-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="f1a6c-107">ACRButton. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-107">ACRButton.xib</span></span> | <span data-ttu-id="f1a6c-108">boutons</span><span class="sxs-lookup"><span data-stu-id="f1a6c-108">buttons</span></span> |
| <span data-ttu-id="f1a6c-109">ACRCellForCompactMode. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-109">ACRCellForCompactMode.xib</span></span>   | <span data-ttu-id="f1a6c-110">Mode compact ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="f1a6c-110">ChoiceSet compact mode</span></span>|
| <span data-ttu-id="f1a6c-111">ACRDatePicker. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-111">ACRDatePicker.xib</span></span> | <span data-ttu-id="f1a6c-112">DatePicker pour Input. date</span><span class="sxs-lookup"><span data-stu-id="f1a6c-112">DatePicker for Input.Date</span></span> |
| <span data-ttu-id="f1a6c-113">ACRDateTextField. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-113">ACRDateTextField.xib</span></span>  | <span data-ttu-id="f1a6c-114">TextField pour Input. date</span><span class="sxs-lookup"><span data-stu-id="f1a6c-114">TextField for Input.Date</span></span> |
| <span data-ttu-id="f1a6c-115">ACRInputTableView. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-115">ACRInputTableView.xib</span></span>   | <span data-ttu-id="f1a6c-116">Conteneur pour les entrées</span><span class="sxs-lookup"><span data-stu-id="f1a6c-116">Container for Inputs</span></span> |
| <span data-ttu-id="f1a6c-117">ACRLabelView. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-117">ACRLabelView.xib</span></span>  | <span data-ttu-id="f1a6c-118">TextBlock</span><span class="sxs-lookup"><span data-stu-id="f1a6c-118">TextBlock</span></span> |
| <span data-ttu-id="f1a6c-119">ACRPickerView. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-119">ACRPickerView.xib</span></span> | <span data-ttu-id="f1a6c-120">ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="f1a6c-120">ChoiceSet</span></span> |
| <span data-ttu-id="f1a6c-121">ACRQuickActionMultilineView. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-121">ACRQuickActionMultilineView.xib</span></span>  | <span data-ttu-id="f1a6c-122">Actions rapides avec des lignes multilignes</span><span class="sxs-lookup"><span data-stu-id="f1a6c-122">Quick Actions with multilines</span></span> |
| <span data-ttu-id="f1a6c-123">ACRQuickActionView. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-123">ACRQuickActionView.xib</span></span> | <span data-ttu-id="f1a6c-124">Actions rapides</span><span class="sxs-lookup"><span data-stu-id="f1a6c-124">Quick Actions</span></span> |
| <span data-ttu-id="f1a6c-125">ACRTextField. XIB</span><span class="sxs-lookup"><span data-stu-id="f1a6c-125">ACRTextField.xib</span></span> | <span data-ttu-id="f1a6c-126">Entrée</span><span class="sxs-lookup"><span data-stu-id="f1a6c-126">Input</span></span> |

<span data-ttu-id="f1a6c-127">XIB peut être modifié à l’aide de XCode IB.</span><span class="sxs-lookup"><span data-stu-id="f1a6c-127">XIB can be edited through XCode IB.</span></span>
<span data-ttu-id="f1a6c-128">Une fois les XIB modifiés dans la spécification.</span><span class="sxs-lookup"><span data-stu-id="f1a6c-128">Once XIBs are edited to the specification.</span></span>
<span data-ttu-id="f1a6c-129">À partir d’un terminal</span><span class="sxs-lookup"><span data-stu-id="f1a6c-129">From a terminal</span></span>
```
ibtool --compile name.nib name.xib 
```

<span data-ttu-id="f1a6c-130">Par exemple, pour le style d’un bouton</span><span class="sxs-lookup"><span data-stu-id="f1a6c-130">For example, to style a button</span></span>
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

<span data-ttu-id="f1a6c-131">Les fichiers de plume générés peuvent être ensuite remplacés à AdaptiveCards. Framework</span><span class="sxs-lookup"><span data-stu-id="f1a6c-131">The generated nib files can be then replaced at AdaptiveCards.framework</span></span>
