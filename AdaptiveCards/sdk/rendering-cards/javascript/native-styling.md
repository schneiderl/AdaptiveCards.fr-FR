---
title: Style natif - SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 6f086d268abcaeb7fa159b74708597e89aafaf53
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552891"
---
# <a name="native-styling---javascript"></a><span data-ttu-id="4abca-102">Style natif - JavaScript</span><span class="sxs-lookup"><span data-stu-id="4abca-102">Native styling - JavaScript</span></span>

<span data-ttu-id="4abca-103">Utiliser CSS pour le style précis de la carte HTML.</span><span class="sxs-lookup"><span data-stu-id="4abca-103">Use CSS for fine-grained styling of the card HTML.</span></span>

<span data-ttu-id="4abca-104">Les classes CSS suivants seront ajoutés aux différents éléments.</span><span class="sxs-lookup"><span data-stu-id="4abca-104">The following CSS classes will be added to various elements.</span></span>

| <span data-ttu-id="4abca-105">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="4abca-105">CSS class</span></span> | <span data-ttu-id="4abca-106">Utilisation</span><span class="sxs-lookup"><span data-stu-id="4abca-106">Usage</span></span> |
|---|---|
| <span data-ttu-id="4abca-107">.AC-container</span><span class="sxs-lookup"><span data-stu-id="4abca-107">.ac-container</span></span> | <span data-ttu-id="4abca-108">Conteneurs</span><span class="sxs-lookup"><span data-stu-id="4abca-108">containers</span></span> |
| <span data-ttu-id="4abca-109">.AC sélectionnable</span><span class="sxs-lookup"><span data-stu-id="4abca-109">.ac-selectable</span></span>  | <span data-ttu-id="4abca-110">éléments avec `selectAction`</span><span class="sxs-lookup"><span data-stu-id="4abca-110">elements with `selectAction`</span></span> |
| <span data-ttu-id="4abca-111">.AC-image</span><span class="sxs-lookup"><span data-stu-id="4abca-111">.ac-image</span></span> | <span data-ttu-id="4abca-112">image</span><span class="sxs-lookup"><span data-stu-id="4abca-112">image</span></span> |
| <span data-ttu-id="4abca-113">.ac-pushButton</span><span class="sxs-lookup"><span data-stu-id="4abca-113">.ac-pushButton</span></span> | <span data-ttu-id="4abca-114">actions rendues comme des boutons</span><span class="sxs-lookup"><span data-stu-id="4abca-114">actions rendered like buttons</span></span> |
| <span data-ttu-id="4abca-115">.ac-linkButton</span><span class="sxs-lookup"><span data-stu-id="4abca-115">.ac-linkButton</span></span>  | <span data-ttu-id="4abca-116">actions restituées comme liens</span><span class="sxs-lookup"><span data-stu-id="4abca-116">actions rendered like links</span></span> |
| <span data-ttu-id="4abca-117">entrée de .ac</span><span class="sxs-lookup"><span data-stu-id="4abca-117">.ac-input</span></span> | <span data-ttu-id="4abca-118">Contrôles d’entrée</span><span class="sxs-lookup"><span data-stu-id="4abca-118">input controls</span></span>|
| <span data-ttu-id="4abca-119">.AC-textInput</span><span class="sxs-lookup"><span data-stu-id="4abca-119">.ac-textInput</span></span>| <span data-ttu-id="4abca-120">Entrée de texte</span><span class="sxs-lookup"><span data-stu-id="4abca-120">text input</span></span> |
| <span data-ttu-id="4abca-121">.ac-multiline</span><span class="sxs-lookup"><span data-stu-id="4abca-121">.ac-multiline</span></span> | <span data-ttu-id="4abca-122">entrée de texte multiligne</span><span class="sxs-lookup"><span data-stu-id="4abca-122">multiline text input</span></span> |
| <span data-ttu-id="4abca-123">.ac-numberInput</span><span class="sxs-lookup"><span data-stu-id="4abca-123">.ac-numberInput</span></span> | <span data-ttu-id="4abca-124">Saisie d’un nombre</span><span class="sxs-lookup"><span data-stu-id="4abca-124">number input</span></span>|
| <span data-ttu-id="4abca-125">.ac-dateInput</span><span class="sxs-lookup"><span data-stu-id="4abca-125">.ac-dateInput</span></span> | <span data-ttu-id="4abca-126">entrée de date</span><span class="sxs-lookup"><span data-stu-id="4abca-126">date input</span></span>|
| <span data-ttu-id="4abca-127">.ac-timeInput</span><span class="sxs-lookup"><span data-stu-id="4abca-127">.ac-timeInput</span></span> | <span data-ttu-id="4abca-128">entrées du temps</span><span class="sxs-lookup"><span data-stu-id="4abca-128">time input</span></span> |
| <span data-ttu-id="4abca-129">.ac-multichoiceInput</span><span class="sxs-lookup"><span data-stu-id="4abca-129">.ac-multichoiceInput</span></span> | <span data-ttu-id="4abca-130">entrée de choix</span><span class="sxs-lookup"><span data-stu-id="4abca-130">multichoice input</span></span>|