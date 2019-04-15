---
title: Configuration de l’hôte - Kit de développement logiciel .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: c3414860ee9822a02dbf36ff11fd83488fedf34e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552911"
---
# <a name="host-config---net-wpf"></a>Configuration - .NET WPF de l’hôte

Un [configuration de l’hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagée comprennent tous les convertisseurs. Cela vous permet de définir des styles courants (par exemple, famille de polices, tailles de police par défaut espacement) et les comportements (par exemple, un nombre maximal d’actions) qui seront automatiquement interprétées par chaque convertisseur de plateforme. 

L’objectif est que l’interface utilisateur native généré par chaque convertisseur de plateforme paraîtra très similaire avec un minimum de travail de votre part.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig() 
{
    FontFamily = "Comic Sans",
    FontSizes = {
        Small = 15,
        Default = 20,
        Medium = 25,
        Large = 30,
        ExtraLarge= 40
    }
};

// Or parse from JSON
renderer.HostConfig  = AdaptiveHostConfig.FromJson(@"{
    ""fontFamily"": ""Comic Sans"",
    ""fontSizes"": {
        ""small"": 25,
        ""default"": 26,
        ""medium"": 27,
        ""large"": 28,
        ""extraLarge"": 29
    }
}");
```