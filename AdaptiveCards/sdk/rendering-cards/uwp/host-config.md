---
title: Configuration de l’hôte-Kit UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 85c8807d2a368e00b414b427fae8a9f0253873c8
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553671"
---
# <a name="host-config---uwp"></a>Configuration de l’hôte-UWP

Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig. (Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)

> L’objet HostConfig sera instancié avec les valeurs par défaut, de sorte que vous pouvez définir uniquement les propriétés que vous souhaitez modifier.

Exemple :

```csharp
var hostConfig = new AdaptiveHostConfig() 
{
    FontSizes = {
        Small = 15,
        Normal = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};
renderer.HostConfig = hostConfig;
```

> Vous pouvez également charger le HostConfig à partir d’une chaîne JSON.

Exemple :

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

Lorsque vous le transmettez à UWPRenderer, vous définissez le HostConfig par défaut à utiliser pour chaque carte que vous affichez.