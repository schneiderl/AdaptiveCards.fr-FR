---
title: Effectuer le rendu d’une carte – Kit de développement logiciel (SDK) Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: c9fbfa788af0b0c7f16824bf9c369fa59a1b80f5
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145469"
---
# <a name="render-a-card---android"></a><span data-ttu-id="4d77e-102">Effectuer le rendu d’une carte – Android</span><span class="sxs-lookup"><span data-stu-id="4d77e-102">Render a card - Android</span></span>

<span data-ttu-id="4d77e-103">Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel (SDK) Android.</span><span class="sxs-lookup"><span data-stu-id="4d77e-103">Here's how to render a card using the Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="4d77e-104">Créer une instance d’objet carte adaptative à partir de texte JSON</span><span class="sxs-lookup"><span data-stu-id="4d77e-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```java
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, elementParserRegistration);
AdaptiveCard adaptiveCard = parseResult.GetAdaptiveCard();
```
> [!IMPORTANT]
> <span data-ttu-id="4d77e-105">**Changements importants pour la version v1.2**</span><span class="sxs-lookup"><span data-stu-id="4d77e-105">**Breaking changes for v1.2**</span></span>
> 

1. <span data-ttu-id="4d77e-106">Le paramètre ElementParserRegistration est passé à ParseContext, qui comprend un ElementParserRegistration et un objet ActionParserRegistration</span><span class="sxs-lookup"><span data-stu-id="4d77e-106">ElementParserRegistration parameter changed to ParseContext which includes an ElementParserRegistration and an ActionParserRegistration object</span></span>

```java
ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

<span data-ttu-id="4d77e-107">ou</span><span class="sxs-lookup"><span data-stu-id="4d77e-107">or</span></span>

```java
ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.VERSION, context);
```

## <a name="render-a-card"></a><span data-ttu-id="4d77e-108">Effectuer le rendu d’une carte</span><span class="sxs-lookup"><span data-stu-id="4d77e-108">Render a card</span></span>

```java
RenderedAdaptiveCard renderedCard = AdaptiveCardRenderer.getInstance().render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.getView();
```
