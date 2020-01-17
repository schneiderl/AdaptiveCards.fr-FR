---
title: Configuration de l’hôte-Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 091e2093c380affc8c895d069a2f52061b991d2f
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145489"
---
# <a name="host-config---android"></a><span data-ttu-id="160e0-102">Configuration de l’hôte-Android</span><span class="sxs-lookup"><span data-stu-id="160e0-102">Host config - Android</span></span>

<span data-ttu-id="160e0-103">Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig.</span><span class="sxs-lookup"><span data-stu-id="160e0-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="160e0-104">(Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)</span><span class="sxs-lookup"><span data-stu-id="160e0-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="160e0-105">Pour créer un objet HostConfig à partir d’une chaîne, utilisez la méthode DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="160e0-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```