---
title: Xamarin.Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: cd8dccd2aece23dd67ee8d601e8efaa2a1bcd4f2
ms.sourcegitcommit: 588f3e97ed3de96dfff54906ac666ce42ef1e7f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928829"
---
# <a name="getting-started---xamarinandroid"></a>Prise en main-Xamarin. Android

Il s’agit d’une bibliothèque de convertisseurs qui cible des applications Android xamarin natives et est basée sur le convertisseur Android que vous pouvez trouver [ici](../../android/getting-started.md). 

## <a name="nuget-install"></a>Installation de NuGet

[![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Xamarin.Android.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Xamarin.Android)

Vous trouverez les packages publiés [ici](http://nuget.org)

```console
Install-Package AdaptiveCards.Rendering.Xamarin.Android -Version 0.1.0-alpha
```

## <a name="namespace"></a>Espace de noms

Les espaces de noms nécessaires pour l’utilisation de cette bibliothèque sont
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

## <a name="xamarinandroid-visualizer-sample"></a>Exemple de visualiseur Xamarin. Android

L' [exemple de visualiseur Xamarin. Android](https://github.com/Microsoft/AdaptiveCards/tree/main/source/xamarin/Xamarin.Droid.Sample) vous permet de visualiser des cartes à l’aide de Xamarin. Android. Si vous avez déjà utilisé l’exemple d’application Android, vous découvrirez que l’expérience est vraiment similaire.

## <a name="next-steps"></a>Étapes suivantes

Pour une vérification de démarrage rapide, [Affichez une carte](render-a-card.md) pour les étapes suivantes.

Pour obtenir une vue plus détaillée des classes qui ont été liées pour la bibliothèque de convertisseurs Xamarin. Android, vous pouvez vérifier certaines des classes liées en cliquant sur celles-ci ci-dessous :
* [```AdaptiveCard```](adaptivecards-rendering-xamarin-android-objectmodel-adaptivecard.md)
* [```AdaptiveCardRenderer```](adaptivecards-rendering-xamarin-android-renderer-adaptivecardrenderer.md)
* [```CardRendererRegistration```](adaptivecards-rendering-xamarin-android-renderer-cardrendererregistration.md)
* [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md)
* [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md)
* [```RenderedAdaptiveCard```](adaptivecards-rendering-xamarin-android-renderer-renderedadaptivecard.md)
