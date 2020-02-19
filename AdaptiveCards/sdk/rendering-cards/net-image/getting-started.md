---
title: SDK de rendu d’image .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: bf97d851b954b861b01b1f7ff8ce79dc9ec6413b
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454392"
---
# <a name="getting-started---net-image"></a><span data-ttu-id="0fcb7-102">Prise en main-image .NET</span><span class="sxs-lookup"><span data-stu-id="0fcb7-102">Getting started - .NET Image</span></span>

<span data-ttu-id="0fcb7-103">Comme nous l’avons décrit dans [prise en main](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle objet de carte sérialisée JSON.</span><span class="sxs-lookup"><span data-stu-id="0fcb7-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="0fcb7-104">Cette bibliothèque facilite le rendu de ce JSON dans une image PNG.</span><span class="sxs-lookup"><span data-stu-id="0fcb7-104">This library makes it easy to render that JSON into into a PNG image.</span></span>

<span data-ttu-id="0fcb7-105">Ce package peut même être utilisé sur un serveur pour générer des images, et implémente tout le goo « Magic STA thread » pour vous.</span><span class="sxs-lookup"><span data-stu-id="0fcb7-105">This package can even be used on a server to generate images, and implements all the "magic STA thread" goo for you.</span></span> 

## <a name="nuget-install"></a><span data-ttu-id="0fcb7-106">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="0fcb7-106">NuGet install</span></span>

<span data-ttu-id="0fcb7-107">[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="0fcb7-107">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf -IncludePrerelease
```

## <a name="next-steps"></a><span data-ttu-id="0fcb7-108">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0fcb7-108">Next steps</span></span>

<span data-ttu-id="0fcb7-109">Pour les prochaines étapes, voir [Effectuer le rendu d’une carte](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="0fcb7-109">See [Render a card](render-a-card.md) for the next steps!</span></span>