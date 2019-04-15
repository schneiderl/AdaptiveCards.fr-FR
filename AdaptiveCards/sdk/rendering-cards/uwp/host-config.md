---
title: Configuration - SDK UWP de l’hôte
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
# <a name="host-config---uwp"></a><span data-ttu-id="42e89-102">Configuration de l’hôte - UWP</span><span class="sxs-lookup"><span data-stu-id="42e89-102">Host config - UWP</span></span>

<span data-ttu-id="42e89-103">Pour personnaliser le convertisseur vous fournir une instance de l’objet HostConfig.</span><span class="sxs-lookup"><span data-stu-id="42e89-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="42e89-104">(Consultez [schéma de configuration d’hôte](../../../rendering-cards/host-config.md) pour la description complète.)</span><span class="sxs-lookup"><span data-stu-id="42e89-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

> <span data-ttu-id="42e89-105">L’objet HostConfig sera instancié avec les valeurs par défaut, vous pouvez donc définir uniquement les propriétés que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="42e89-105">The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.</span></span>

<span data-ttu-id="42e89-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="42e89-106">Example:</span></span>

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

> <span data-ttu-id="42e89-107">Vous pouvez également charger le HostConfig à partir d’une chaîne JSON.</span><span class="sxs-lookup"><span data-stu-id="42e89-107">Alternatively, you can load the HostConfig from a JSON string.</span></span>

<span data-ttu-id="42e89-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="42e89-108">Example:</span></span>

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

<span data-ttu-id="42e89-109">Quand vous passez dans à la UWPRenderer vous définissez la valeur par défaut HostConfig à utiliser pour chaque carte que vous effectuez le rendu.</span><span class="sxs-lookup"><span data-stu-id="42e89-109">When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.</span></span>