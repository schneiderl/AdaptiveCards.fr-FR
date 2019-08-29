---
title: Configuration de l’hôte-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: dc5b6767d5f8611111b56f30f05a7b5fc8d1cbf4
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552411"
---
# <a name="host-config---net-html"></a>Configuration de l’hôte-HTML .NET

Une [configuration d’hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagé que tous les convertisseurs comprennent. Elle vous permet de définir des styles (par exemple, famille de polices, tailles de police, espacement par défaut) et des comportements (par exemple, nombre maximal d’actions) communs qui sont automatiquement interprétés par le convertisseur de chaque plateforme. 

L’objectif est que l’interface utilisateur native générée par le convertisseur de chaque plateforme se présente de façon très similaire avec un minimum de travail de votre part.

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