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
# <a name="host-config---android"></a>Configuration de l’hôte-Android

Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig. (Consultez [schéma de configuration](../../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)

Pour créer un objet ```HostConfig``` à partir d’une chaîne, utilisez la méthode ```DeserializeFromString``` comme suit :

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

HostConfig Config = HostConfig.DeserializeFromString(configJson);
```