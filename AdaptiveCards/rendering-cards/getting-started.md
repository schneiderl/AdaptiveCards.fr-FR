---
title: Rendu des cartes à l’intérieur de votre application
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 0a9507c56a8bae9f038c220cdf55e34b2c3b0829
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552921"
---
# <a name="rendering-cards-inside-your-application"></a>Rendu des cartes à l’intérieur de votre application

Il est facile d’effectuer le rendu des cartes adaptatives à l’intérieur de votre application. Nous fournir des kits de développement logiciel pour les toutes les plateformes courants, ainsi que fournir un [détaillées spécification](implement-a-renderer.md) pour la création de votre propre convertisseur de carte adaptative.

1. **Installer un kit de développement logiciel de convertisseur** : pour votre plateforme cible.
2. **Créer une instance de convertisseur** - configuré avec les gestionnaires d’événements style, règles et l’action de votre application.
3. **Afficher une carte à une interface utilisateur native** - appliqué automatiquement à votre application.

## <a name="adaptive-cards-sdks"></a>Kits de développement logiciel des cartes adaptatives

|Plateforme|Installation|Build|Documentation|État|
|---|---|---|---|---|
| JavaScript | [![installation de npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Docs](../sdk/rendering-cards/javascript/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Docs](../sdk/rendering-cards/net-wpf/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Docs](../sdk/rendering-cards/net-html/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Docs](../sdk/rendering-cards/uwp/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Docs](../sdk/rendering-cards/android/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Docs](../sdk/rendering-cards/ios/getting-started.md) |  ![État de la build](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Créez une instance du convertisseur

L’étape suivante consiste à créer une instance d’un `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Raccorder des événements d’action

Par défaut, les actions seront affiche sous forme de boutons sur la carte, mais c’est à votre application pour les rendre à fonctionner comme prévu. Chaque kit SDK comporte l’équivalent d’un `OnAction` événement que vous devez gérer.

* **Action.OpenUrl** -ouvrez spécifié `url`.  
* **Action.Submit** - prendre le résultat de l’envoi et l’envoyer à la source. Comment vous l’envoyer à la source de la carte dépend entièrement de vous.
* **Action.ShowCard** - appelle une boîte de dialogue et restitue l’entrée secondaire dans cette boîte de dialogue. Notez que vous devez uniquement gérer cela si `ShowCardActionMode` est défini sur `popup`.

## <a name="render-a-card"></a>Afficher une carte

Une fois que vous acquérez une charge utile de carte, simplement appeler le convertisseur et transmettez la carte. Vous allez revenir à un objet d’interface utilisateur natif constitué par le contenu de la carte. Maintenant simplement placer cette interface utilisateur quelque part dans votre application.

## <a name="customization"></a>Personnalisation

Il existe plusieurs façons de que personnaliser ce qui est rendu. 

### <a name="hostconfig"></a>HostConfig

Un [HostConfig](host-config.md) est un objet de configuration partagée, inter-plateformes qui contrôle les styles de base et le comportement des cartes à l’intérieur de votre application. Il définit des éléments tels que les tailles de police, l’espacement entre les éléments, couleurs, le nombre d’actions prises en charge, etc. 

### <a name="native-platform-styling"></a>Style de la plateforme native

La plupart des infrastructures d’interface utilisateur vous permettent d’appliquer un style la carte de rendu en utilisant le style de cadre de l’interface utilisateur natif. Par exemple, au format HTML, vous pouvez spécifier des classes CSS pour HTML, ou dans XAML, vous pouvez passer dans un ResourceDictionary personnalisé pour un contrôle précis de la sortie.

### <a name="customize-per-element-rendering"></a>Personnaliser le rendu de chaque élément

Chaque SDK vous permet de substituer le rendu d’un élément, ou même ajouter la prise en charge pour les éléments entièrement nouveaux que vous définissez.  Par exemple, vous pouvez modifier le `Input.Date` convertisseur pour émettre votre propre contrôle personnalisé tout en conservant le reste de la sortie du convertisseur. Ou vous pouvez ajouter la prise en charge pour un personnalisé `Rating` élément vous définissez.



