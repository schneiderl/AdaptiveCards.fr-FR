---
title: Configuration de l’hôte-Kit UWP SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6f14830a643b064c6169cf3143bbc7cd4ce45937
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454972"
---
# <a name="host-config---uwp"></a><span data-ttu-id="ca758-102">Configuration de l’hôte-UWP</span><span class="sxs-lookup"><span data-stu-id="ca758-102">Host config - UWP</span></span>

<span data-ttu-id="ca758-103">Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig.</span><span class="sxs-lookup"><span data-stu-id="ca758-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="ca758-104">(Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)</span><span class="sxs-lookup"><span data-stu-id="ca758-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

> <span data-ttu-id="ca758-105">L’objet HostConfig sera instancié avec les valeurs par défaut, de sorte que vous pouvez définir uniquement les propriétés que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="ca758-105">The HostConfig object will be instantiated with defaults, so you can set just the properties you want to change.</span></span>

<span data-ttu-id="ca758-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ca758-106">Example:</span></span>

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

> <span data-ttu-id="ca758-107">Vous pouvez également charger le HostConfig à partir d’une chaîne JSON.</span><span class="sxs-lookup"><span data-stu-id="ca758-107">Alternatively, you can load the HostConfig from a JSON string.</span></span>

<span data-ttu-id="ca758-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ca758-108">Example:</span></span>

```csharp
var hostConfig = AdaptiveHostConfig.FromJsonString(jsonString); 

renderer.HostConfig = hostConfig;
```

<span data-ttu-id="ca758-109">Lorsque vous le transmettez à UWPRenderer, vous définissez le HostConfig par défaut à utiliser pour chaque carte que vous affichez.</span><span class="sxs-lookup"><span data-stu-id="ca758-109">When you pass it in to the UWPRenderer you are setting the default HostConfig to use for every card you render.</span></span>