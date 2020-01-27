---
title: Configuration de l’hôte-SDK iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: fa420c0a6e9e9b7e5713b6cc528de39335f0b56c
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727475"
---
# <a name="host-config---ios"></a>Configuration de l’hôte-iOS

L’hôte peut être configuré par le biais de HostConfig qui peuvent être générés par une chaîne JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

La valeur par défaut de HostConfig peut être instanciée

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Rendu d’une carte à l’aide de la configuration d’hôte

Rederer utilise une carte adaptative et une configuration d’hôte. HostConfig peut être Nil et, s’il est Nil, la valeur par défaut est utilisée.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```

## <a name="customization"></a>Personnalisation

Il existe trois façons de personnaliser le rendu de carte adaptative :

1. Configuration de l’hôte
2. XIB
3. Rendu d’élément personnalisé
