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
# <a name="host-config---android"></a>Configuration de l’hôte-Android

Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig. (Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)

Pour créer un objet HostConfig à partir d’une chaîne, utilisez la méthode DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```