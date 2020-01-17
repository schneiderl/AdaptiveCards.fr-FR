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
# <a name="host-config---android"></a>Configuration de l’hôte-Android

Pour personnaliser le convertisseur, vous fournissez une instance de l’objet HostConfig. (Consultez [schéma de configuration](../../../rendering-cards/host-config.md) de l’hôte pour obtenir une description complète.)

Pour créer un objet HostConfig à partir d’une chaîne, utilisez la méthode DeserializeFromString

```java
HostConfig hostConfig = HostConfig.DeserializeFromString(hostConfigText);
```