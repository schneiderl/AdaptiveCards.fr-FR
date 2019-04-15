---
title: Configuration de l’hôte - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: b788ecc5c2371d2575e0165296365238535dd7c5
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553701"
---
# <a name="host-config---ios"></a>Configuration de l’hôte - iOS

Hôte peut être configuré via HostConfig qui peut être générée par la chaîne JSON

```objective-c
ACOParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
```

Par défaut HostConfig peut être instancié.

```objective-c
ACOHostConfig *defaultConfig = [[ACHostConfig alloc] init];
```

## <a name="render-a-card-using-host-config"></a>Afficher une carte à l’aide de la configuration de l’hôte

Rederer prend carte adaptative et configuration de l’hôte. HostConfig peut être nil, et si elle est nulle, valeur de la valeur par défaut sera utilisée.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:hostconfigParseResult.config
                   widthConstraint:300.0];
```