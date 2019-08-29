---
title: Configuration de l’hôte-Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c44cf609fd52423a1ca17988a875c6dc48550007
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553341"
---
# <a name="host-config---android"></a><span data-ttu-id="c5df9-102">Configuration de l’hôte-Android</span><span class="sxs-lookup"><span data-stu-id="c5df9-102">Host config - Android</span></span>

<span data-ttu-id="c5df9-103">Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig.</span><span class="sxs-lookup"><span data-stu-id="c5df9-103">To customize the renderer you provide an instance of the HostConfig object.</span></span> <span data-ttu-id="c5df9-104">(Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)</span><span class="sxs-lookup"><span data-stu-id="c5df9-104">(See [Host Config Schema](../../../rendering-cards/host-config.md) for the full description.)</span></span>

<span data-ttu-id="c5df9-105">Pour créer un objet HostConfig à partir d’une chaîne, utilisez la méthode DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="c5df9-105">To Create a HostConfig object from a string, use the DeserializeFromString method</span></span>

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```