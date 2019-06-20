---
title: Configuration d’hôte – Kit de développement logiciel (SDK) WPF .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 9ca540cbbb445f306f073f1936af46f8c2def99b
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134305"
---
# <a name="host-config---net-wpf"></a>Configuration – WPF .NET

Une [configuration d’hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagé que tous les convertisseurs comprennent. Elle vous permet de définir des styles (par exemple, famille de polices, tailles de police, espacement par défaut) et des comportements (par exemple, nombre maximal d’actions) communs qui sont automatiquement interprétés par le convertisseur de chaque plateforme. 

L’objectif est que l’interface utilisateur native générée par le convertisseur de chaque plateforme se présente de façon très similaire avec un minimum de travail de votre part.

```csharp
// Construct programmatically
renderer.HostConfig = new AdaptiveHostConfig()
{
    FontStyles = new FontStylesConfig()
    {
        Default = new FontStyleConfig()
        {
            FontFamily = "Consolas",
            FontSizes = {
                Small = 15,
                Default = 20,
                Medium = 25,
                Large = 30,
                ExtraLarge= 40
            }
        },
    }
};

// Or parse from JSON
renderer.HostConfig = AdaptiveHostConfig.FromJson(@"{
    ""fontStyles"": {
        ""default"": {
            ""fontFamily"": ""Consolas"",
            ""fontSizes"": {
                ""small"": 15,
                ""default"": 20,
                ""medium"": 25,
                ""large"": 30,
                ""extraLarge"": 40
            }
        }
    }}");
```
