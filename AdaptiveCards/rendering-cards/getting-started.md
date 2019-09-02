---
title: Rendu de cartes à l’intérieur de votre application
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 0a5f99268ce483fddd99f4493b386db796c3e9d2
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138092"
---
# <a name="rendering-cards-inside-your-application"></a>Rendu de cartes à l’intérieur de votre application

Il est facile d’afficher des cartes adaptatives à l’intérieur de votre application. Nous fournissons des SDK pour toutes les plateformes courantes, ainsi qu’une [spécification détaillée](implement-a-renderer.md) pour créer votre propre renderer de carte adaptative.

1. **Installez un SDK de renderer** pour votre plateforme cible.
2. **Créez une instance de renderer** configurée avec le style, les règles et les gestionnaires d’événements d’actions de votre application.
3. **Affichez une carte dans l’interface utilisateur native**, affectée automatiquement du style de votre application.

## <a name="adaptive-cards-sdks"></a>SDK de cartes adaptatives

|Plateforme|Installer|Build|Documentation|État|
|---|---|---|---|---|
| JavaScript | [![Installation npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/nodejs)| [Documentation](../sdk/rendering-cards/javascript/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20564.svg) |
| .NET WPF | [![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet)| [Documentation](../sdk/rendering-cards/net-wpf/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| .NET HTML | [![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Html.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Html) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet) | [Documentation](../sdk/rendering-cards/net-html/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20596.svg) |
| Windows UWP | [![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Uwp.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Uwp) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/uwp) | [Documentation](../sdk/rendering-cards/uwp/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/56cf629e-8f3a-4412-acbc-bf69366c552c/20583.svg) |
| Android | [![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/android) | [Documentation](../sdk/rendering-cards/android/getting-started.md) | ![État de la build](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/17651.svg)
| iOS | [![CocoaPods](https://img.shields.io/cocoapods/v/AdaptiveCards.svg)](https://cocoapods.org/pods/AdaptiveCards) | [Source](https://github.com/Microsoft/AdaptiveCards/tree/master/source/ios) | [Documentation](../sdk/rendering-cards/ios/getting-started.md) |  ![État de la build](https://img.shields.io/vso/build/Microsoft/8d47e068-03c8-4cdc-aa9b-fc6929290322/16990.svg) |

## <a name="create-an-instance-of-the-renderer"></a>Créer une instance du renderer

L’étape suivante consiste à créer une instance de `AdaptiveCardRenderer`. 

### <a name="hook-up-action-events"></a>Raccorder des événements d’actions

Par défaut, les actions s’affichent sous la forme de boutons sur la carte, mais c’est à votre application de faire en sorte qu’elles se comportent comme prévu. Chaque SDK a l’équivalent d’un événement `OnAction` que vous devez gérer.

* **Action.OpenUrl** : ouvrir le `url` spécifié.  
* **Action.Submit** : prendre le résultat de l’envoi et l’envoyer à la source. La façon dont vous l’envoyez à la source de la carte dépend entièrement de vous.
* **Action.ShowCard** : appelle une boîte de dialogue et affiche la sous-carte dans cette boîte de dialogue. Notez que vous devez uniquement gérer cela si `ShowCardActionMode` a la valeur `popup`.

## <a name="render-a-card"></a>Effectuer le rendu d’une carte

Une fois que vous avez acquis une charge utile de carte, il vous suffit d’appeler le renderer et de transmettre la carte. Vous récupérerez un objet d’interface utilisateur natif composé du contenu de la carte. Maintenant, il vous suffit de placer cette interface utilisateur quelque part dans votre application.

## <a name="customization"></a>Personnalisation

Il existe plusieurs façons de personnaliser ce qui est rendu. 

### <a name="hostconfig"></a>HostConfig

Un [HostConfig](host-config.md) est un objet de configuration multiplateforme et partagé qui contrôle le style et le comportement de base des cartes à l’intérieur de votre application. Il définit des éléments tels que les tailles de police, l’espacement entre les éléments, les couleurs, le nombre d’actions prises en charge, et ainsi de suite. 

### <a name="native-platform-styling"></a>Style de plateforme natif

La plupart des frameworks d’interface utilisateur vous permettent d’appliquer un style à la carte rendue à l’aide du style de framework d’interface utilisateur natif. Par exemple, en HTML vous pouvez spécifier des classes CSS pour le code HTML, et en XAML vous pouvez passer un ResourceDictionary personnalisé pour obtenir un contrôle affiné de la sortie.

### <a name="customize-per-element-rendering"></a>Personnaliser le rendu par élément

Chaque SDK vous permet de remplacer le rendu d’un élément, ou même d’ajouter la prise en charge d’éléments entièrement nouveaux que vous définissez.  Par exemple, vous pouvez modifier le renderer `Input.Date` pour émettre votre propre contrôle personnalisé tout en conservant le reste de la sortie du renderer. Vous pouvez aussi ajouter la prise en charge d’un élément `Rating` personnalisé que vous définissez.



