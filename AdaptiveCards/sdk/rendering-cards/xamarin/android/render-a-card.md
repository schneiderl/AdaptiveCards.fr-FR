---
title: Rendu d’une carte Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: dc1d48e05e99d6254b9253efa7145cefeb2ed17c
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145973"
---
# <a name="render-a-card---xamarinandroid"></a><span data-ttu-id="a8fd2-102">Rendu d’une carte Xamarin. Android</span><span class="sxs-lookup"><span data-stu-id="a8fd2-102">Render a card - Xamarin.Android</span></span>

<span data-ttu-id="a8fd2-103">Voici comment afficher une carte à l’aide de Xamarin. Android SDK.</span><span class="sxs-lookup"><span data-stu-id="a8fd2-103">Here's how to render a card using the Xamarin.Android SDK.</span></span>

## <a name="create-adaptive-card-object-instance-from-json-text"></a><span data-ttu-id="a8fd2-104">Créer une instance d’objet carte adaptative à partir de texte JSON</span><span class="sxs-lookup"><span data-stu-id="a8fd2-104">Create Adaptive Card Object Instance from JSON Text</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
AdaptiveCard adaptiveCard = parseResult.AdaptiveCard;
```

<span data-ttu-id="a8fd2-105">vous pouvez également utiliser un objet ```ParseContext``` pour pouvoir désérialiser des éléments personnalisés inclus dans votre carte adaptative comme suit :</span><span class="sxs-lookup"><span data-stu-id="a8fd2-105">or you can also use a ```ParseContext``` object to be able to deserialize custom elements that are included in your adaptive card like this:</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(); // Empty parseContext so only known elements up to v1.2 will be parsed
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

<span data-ttu-id="a8fd2-106">ou</span><span class="sxs-lookup"><span data-stu-id="a8fd2-106">or</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
// ...

ParseContext context = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, context);
```

## <a name="render-a-card"></a><span data-ttu-id="a8fd2-107">Effectuer le rendu d’une carte</span><span class="sxs-lookup"><span data-stu-id="a8fd2-107">Render a card</span></span>

<span data-ttu-id="a8fd2-108">Pour pouvoir afficher une carte, vous aurez besoin d’informations</span><span class="sxs-lookup"><span data-stu-id="a8fd2-108">To be able to render a card you'll need some information</span></span>
* <span data-ttu-id="a8fd2-109">Context : peut être obtenu à partir de l’activité dans laquelle la carte est hébergée</span><span class="sxs-lookup"><span data-stu-id="a8fd2-109">context: Obtainable from the Activity the card is hosted in</span></span>
* <span data-ttu-id="a8fd2-110">fragmentManager : peut également être récupéré à partir de l’activité d’hébergement</span><span class="sxs-lookup"><span data-stu-id="a8fd2-110">fragmentManager: can also be retrieved from the hosting activity</span></span>
* <span data-ttu-id="a8fd2-111">cardActionHandler : instance de [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) pour gérer le comportement de l’action</span><span class="sxs-lookup"><span data-stu-id="a8fd2-111">cardActionHandler: instance of [```ICardActionHandler```](adaptivecards-renderin-xamarin-android-renderer-actionhandler-icardactionhandler.md) to manage the action behaviour</span></span>

```csharp
using AdaptiveCards.Rendering.Xamarin.Android.ObjectModel;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer;
using AdaptiveCards.Rendering.Xamarin.Android.Renderer.ActionHandler;
// ...

var renderedCard = AdaptiveCardRenderer.Instance.Render(context, fragmentManager, adaptiveCard, cardActionHandler, hostConfig);
View v = renderedCard.View;
```
