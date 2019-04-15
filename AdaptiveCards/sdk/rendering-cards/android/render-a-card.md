---
title: Afficher une carte - Kit de développement logiciel Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: b93ce97a41152641892e6a69d5221842181fcb72
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552511"
---
# <a name="render-a-card---android"></a>Afficher une carte - Android

Voici comment effectuer le rendu d’une carte à l’aide du Kit Android SDK.

## <a name="create-adaptive-card-object-instance-from-json-text"></a>Créer l’Instance d’objet de carte adaptative du texte JSON

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```

## <a name="render-a-card"></a>Afficher une carte

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```