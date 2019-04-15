---
title: KIT DE DÉVELOPPEMENT LOGICIEL .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: a3f63fc812c97014af06dd1a197b24c5d07361c2
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553621"
---
# <a name="getting-started---net-wpf"></a><span data-ttu-id="5aecf-102">Mise en route - .NET WPF</span><span class="sxs-lookup"><span data-stu-id="5aecf-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="5aecf-103">Comme décrit dans [mise en route](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle d’objet de carte sérialisé en JSON.</span><span class="sxs-lookup"><span data-stu-id="5aecf-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="5aecf-104">Cette bibliothèque rend plus facile rendre ce code JSON dans UI WPF que vous pouvez utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="5aecf-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="5aecf-105">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="5aecf-105">NuGet install</span></span>

<span data-ttu-id="5aecf-106">[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="5aecf-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="5aecf-107">Package d’entrée améliorées Xceed</span><span class="sxs-lookup"><span data-stu-id="5aecf-107">Xceed enhanced input package</span></span>

<span data-ttu-id="5aecf-108">Ce package facultatif améliore les contrôles d’entrée de carte adaptative au-delà de ce que WPF fournit prêts à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="5aecf-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="5aecf-109">Il a une dépendance `Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="5aecf-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="5aecf-110">[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="5aecf-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="5aecf-111">Visualiseur WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="5aecf-111">WPF Visualizer Sample</span></span>

![Capture d’écran de visualiseur](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="5aecf-113">Le [visualiseur de WPF, exemple](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser les cartes à l’aide de WPF.</span><span class="sxs-lookup"><span data-stu-id="5aecf-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="5aecf-114">Un `Host Config` éditeur est intégré pour la modification et l’affichage des paramètres de configuration d’hôte.</span><span class="sxs-lookup"><span data-stu-id="5aecf-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="5aecf-115">Enregistrer ces paramètres en tant que JSON pour les utiliser dans un rendu dans votre application.</span><span class="sxs-lookup"><span data-stu-id="5aecf-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5aecf-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5aecf-116">Next steps</span></span>

<span data-ttu-id="5aecf-117">Consultez [restituer une carte](render-a-card.md) pour les prochaines étapes !</span><span class="sxs-lookup"><span data-stu-id="5aecf-117">See [Render a card](render-a-card.md) for the next steps!</span></span>
