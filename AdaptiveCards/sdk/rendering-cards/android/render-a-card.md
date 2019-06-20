---
title: Effectuer le rendu d’une carte – Kit de développement logiciel (SDK) Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: a4eeda54a80c959ff9a1246371240954b4c3fb12
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134286"
---
# <a name="render-a-card---android"></a>Effectuer le rendu d’une carte – Android

Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel (SDK) Android.

## <a name="create-adaptive-card-object-instance-from-json-text"></a>Créer une instance d’objet carte adaptative à partir de texte JSON

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> **Changements importants pour la version v1.2**
> 
> 1. Le paramètre ElementParserRegistration est remplacé par ParseContext qui inclut une ElementParserRegistration et un objet ActionRegistration.
> ```java
> ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
> ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
> ```

## <a name="render-a-card"></a>Effectuer le rendu d’une carte

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```
