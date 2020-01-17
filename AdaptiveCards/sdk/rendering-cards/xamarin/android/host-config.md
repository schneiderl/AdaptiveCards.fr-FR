---
title: Configuration de l’hôte-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 554b32d9d088e82fb0fd48bec4b94340e843abeb
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146123"
---
# <a name="host-config---android"></a><span data-ttu-id="d5a4c-102">Configuration de l’hôte-Android</span><span class="sxs-lookup"><span data-stu-id="d5a4c-102">Host config - Android</span></span>

<span data-ttu-id="d5a4c-103">Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig.</span><span class="sxs-lookup"><span data-stu-id="d5a4c-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="d5a4c-104">(Consultez [schéma de configuration](../../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)</span><span class="sxs-lookup"><span data-stu-id="d5a4c-104">(See [Host Config Schema](../../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="d5a4c-105">Pour créer un objet ```HostConfig``` à partir d’une chaîne, utilisez la méthode ```DeserializeFromString``` comme suit :</span><span class="sxs-lookup"><span data-stu-id="d5a4c-105">To create a ```HostConfig``` object from a string, use the ```DeserializeFromString``` method like this:</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

HostConfig Config = HostConfig.DeserializeFromString(configJson);
```