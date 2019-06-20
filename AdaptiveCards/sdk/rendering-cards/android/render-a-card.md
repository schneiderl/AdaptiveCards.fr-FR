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
# <a name="render-a-card---android"></a><span data-ttu-id="54c6f-102">Effectuer le rendu d’une carte – Android</span><span class="sxs-lookup"><span data-stu-id="54c6f-102">Render a card - Android</span></span>

<span data-ttu-id="54c6f-103">Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel (SDK) Android.</span><span class="sxs-lookup"><span data-stu-id="54c6f-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="54c6f-104">Créer une instance d’objet carte adaptative à partir de texte JSON</span><span class="sxs-lookup"><span data-stu-id="54c6f-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="54c6f-105">**Changements importants pour la version v1.2**</span><span class="sxs-lookup"><span data-stu-id="54c6f-105">**Breaking changes for v1.2**</span></span>
> 
> 1. <span data-ttu-id="54c6f-106">Le paramètre ElementParserRegistration est remplacé par ParseContext qui inclut une ElementParserRegistration et un objet ActionRegistration.</span><span class="sxs-lookup"><span data-stu-id="54c6f-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionRegistration object</span></span>
> ```java
> ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
> ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
> ```

## <a name="render-a-card"></a><span data-ttu-id="54c6f-107">Effectuer le rendu d’une carte</span><span class="sxs-lookup"><span data-stu-id="54c6f-107">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, getSupportFragmentManager(), adaptiveCard, cardActionHandler, new HostConfig());
View v = renderedCard.getView();
```
