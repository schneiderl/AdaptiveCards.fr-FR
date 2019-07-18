---
title: Effectuer le rendu d’une carte – Kit de développement logiciel (SDK) Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 55e0fa828abf3b9af857d1deb7ecd3744b5a7280
ms.sourcegitcommit: 8c8067206f283d97a5aa4ec65ba23d3fe18962f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299524"
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

1. Le paramètre ElementParserRegistration est passé à ParseContext, qui comprend un ElementParserRegistration et un objet ActionParserRegistration

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

ou Gestionnaire de configuration

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a>Effectuer le rendu d’une carte

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
