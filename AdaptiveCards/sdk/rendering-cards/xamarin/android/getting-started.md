---
title: Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: a7fd40ac7f026e2a325e7dc52e10defe550fd43a
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146003"
---
# <a name="getting-started---xamarinandroid"></a><span data-ttu-id="76dc0-102">Prise en main-Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="76dc0-102">Getting started - Xamarin.Android</span></span>

<span data-ttu-id="76dc0-103">Il s’agit d’une bibliothèque de convertisseurs qui cible des applications Android xamarin natives et est basée sur le convertisseur Android que vous pouvez trouver [ici](../../android/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="76dc0-103">This is a renderer library which targets native xamarin android applications and is based on the Android renderer that you can find [here](../../android/getting-started.md).</span></span> 

## <a name="nuget-install"></a><span data-ttu-id="76dc0-104">Installation de NuGet</span><span class="sxs-lookup"><span data-stu-id="76dc0-104">NuGet install</span></span>

<span data-ttu-id="76dc0-105">[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)</span><span class="sxs-lookup"><span data-stu-id="76dc0-105">[![Nuget install](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)</span></span>

<span data-ttu-id="76dc0-106">Vous trouverez les packages publiés [ici](http://nuget.org)</span><span class="sxs-lookup"><span data-stu-id="76dc0-106">You can find the published packages [here](http://nuget.org)</span></span>

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## <a name="namespace"></a><span data-ttu-id="76dc0-107">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="76dc0-107">Namespace</span></span>

<span data-ttu-id="76dc0-108">Les espaces de noms nécessaires pour l’utilisation de cette bibliothèque sont</span><span class="sxs-lookup"><span data-stu-id="76dc0-108">The necessary namespaces for using this library are</span></span>
```csharp
// To import the base object model classes as AdaptiveCard, TextBlock, Column, ShowCardAction, ...
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;

// To import the AdaptiveCardRenderer class
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;

// To import the ICardActionHandler interface
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;

// To use feature registration and register custom behaviour 
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration;
```

## <a name="xamarinandroid-visualizer-sample"></a><span data-ttu-id="76dc0-109">Exemple de visualiseur Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="76dc0-109">Xamarin.Android Visualizer Sample</span></span>

<span data-ttu-id="76dc0-110">L' [exemple de visualiseur Xamarin. Android](https://github.com/Microsoft/AdaptiveCards/tree/master/source/xamarin/Xamarin.Droid.Sample) vous permet de visualiser des cartes à l’aide de Xamarin. Android.</span><span class="sxs-lookup"><span data-stu-id="76dc0-110">The [Xamarin.Android Visualizer sample](https://github.com/Microsoft/AdaptiveCards/tree/master/source/xamarin/Xamarin.Droid.Sample) lets you visualize cards using Xamarin.Android.</span></span> <span data-ttu-id="76dc0-111">Si vous avez déjà utilisé l’exemple d’application Android, vous découvrirez que l’expérience est vraiment similaire.</span><span class="sxs-lookup"><span data-stu-id="76dc0-111">If you have ever used the Android sample application you'll find the experience to be really similar.</span></span>

## <a name="next-steps"></a><span data-ttu-id="76dc0-112">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="76dc0-112">Next steps</span></span>

<span data-ttu-id="76dc0-113">Pour une vérification de démarrage rapide, [Affichez une carte](render-a-card.md) pour les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="76dc0-113">For a quick start check [Render a card](render-a-card.md) for the next steps!</span></span>

<span data-ttu-id="76dc0-114">Pour obtenir une vue plus détaillée des classes qui ont été liées pour la bibliothèque de convertisseurs Xamarin. Android, vous pouvez vérifier certaines des classes liées en cliquant sur celles-ci ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="76dc0-114">For a more in depth view of the classes that have been binded for the Xamarin.Android renderer library, you can check some of the binded classes by clicking on them below:</span></span>
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)