---
title: SDK .NET WPF
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
# <a name="getting-started---net-wpf"></a><span data-ttu-id="38410-102">Prise en main-WPF .NET</span><span class="sxs-lookup"><span data-stu-id="38410-102">Getting started - .NET WPF</span></span>

<span data-ttu-id="38410-103">Comme nous l’avons décrit dans [prise en main](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle objet de carte sérialisée JSON.</span><span class="sxs-lookup"><span data-stu-id="38410-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="38410-104">Cette bibliothèque permet de rendre facilement ce JSON dans l’interface utilisateur WPF que vous pouvez utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="38410-104">This library makes it easy to render that JSON into WPF UI that you can use within your app.</span></span>

## <a name="nuget-install"></a><span data-ttu-id="38410-105">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="38410-105">NuGet install</span></span>

<span data-ttu-id="38410-106">[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span><span class="sxs-lookup"><span data-stu-id="38410-106">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a><span data-ttu-id="38410-107">Xceed package d’entrée amélioré</span><span class="sxs-lookup"><span data-stu-id="38410-107">Xceed enhanced input package</span></span>

<span data-ttu-id="38410-108">Ce package facultatif améliore les contrôles d’entrée de carte adaptative au-delà de ce que WPF prête à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="38410-108">This optional package enhances the Adaptive Card Input controls beyond what WPF provides out of the box.</span></span> <span data-ttu-id="38410-109">Il a une dépendance sur`Extended.Wpf.Toolkit`</span><span class="sxs-lookup"><span data-stu-id="38410-109">It has a dependency on `Extended.Wpf.Toolkit`</span></span>

<span data-ttu-id="38410-110">[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span><span class="sxs-lookup"><span data-stu-id="38410-110">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="38410-111">Exemple de visualiseur WPF</span><span class="sxs-lookup"><span data-stu-id="38410-111">WPF Visualizer Sample</span></span>

![Capture d’écran du visualiseur](../../../resources/media/tools/wpfvisualizer.png)

<span data-ttu-id="38410-113">L' [exemple du visualiseur WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser des cartes à l’aide de WPF.</span><span class="sxs-lookup"><span data-stu-id="38410-113">The [WPF Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF.</span></span>  <span data-ttu-id="38410-114">Un `Host Config` éditeur est intégré pour la modification et l’affichage des paramètres de configuration de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="38410-114">A `Host Config` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="38410-115">Enregistrez ces paramètres en tant que JSON pour les utiliser dans le rendu de votre application.</span><span class="sxs-lookup"><span data-stu-id="38410-115">Save these settings as a JSON to use them in rendering in your application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="38410-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="38410-116">Next steps</span></span>

<span data-ttu-id="38410-117">Pour les prochaines étapes, voir [Effectuer le rendu d’une carte](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="38410-117">See [Render a card](render-a-card.md) for the next steps!</span></span>
