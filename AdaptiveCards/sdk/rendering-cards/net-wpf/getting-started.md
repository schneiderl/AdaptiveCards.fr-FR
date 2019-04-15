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
# <a name="getting-started---net-wpf"></a>Mise en route - .NET WPF

Comme décrit dans [mise en route](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle d’objet de carte sérialisé en JSON. Cette bibliothèque rend plus facile rendre ce code JSON dans UI WPF que vous pouvez utiliser dans votre application.

## <a name="nuget-install"></a>Installation de NuGet

[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf)

```console
Install-Package AdaptiveCards.Rendering.Wpf
```

### <a name="xceed-enhanced-input-package"></a>Package d’entrée améliorées Xceed

Ce package facultatif améliore les contrôles d’entrée de carte adaptative au-delà de ce que WPF fournit prêts à l’emploi. Il a une dépendance `Extended.Wpf.Toolkit`

[![Installation de NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Rendering.Wpf.Xceed.svg)](https://www.nuget.org/packages/AdaptiveCards.Rendering.Wpf.Xceed)

```console
Install-Package AdaptiveCards.Rendering.Wpf.Xceed
```

## <a name="wpf-visualizer-sample"></a>Visualiseur WPF, exemple

![Capture d’écran de visualiseur](../../../resources/media/tools/wpfvisualizer.png)

Le [visualiseur de WPF, exemple](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser les cartes à l’aide de WPF.  Un `Host Config` éditeur est intégré pour la modification et l’affichage des paramètres de configuration d’hôte. Enregistrer ces paramètres en tant que JSON pour les utiliser dans un rendu dans votre application.

## <a name="next-steps"></a>Étapes suivantes

Consultez [restituer une carte](render-a-card.md) pour les prochaines étapes !
