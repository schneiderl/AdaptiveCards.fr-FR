---
title: Afficher une carte - SDK UWP
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 1a72cb9ba72811d4e98a48116fa08245e13a6392
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552431"
---
# <a name="render-a-card---uwp"></a><span data-ttu-id="a7f7d-102">Afficher une carte - UWP</span><span class="sxs-lookup"><span data-stu-id="a7f7d-102">Render a card - UWP</span></span>

<span data-ttu-id="a7f7d-103">Voici comment effectuer le rendu d’une carte à l’aide du SDK UWP.</span><span class="sxs-lookup"><span data-stu-id="a7f7d-103">Here's how to render a card using the UWP SDK.</span></span>

## <a name="create-an-instance-of-your-renderer"></a><span data-ttu-id="a7f7d-104">Créez une instance de votre convertisseur</span><span class="sxs-lookup"><span data-stu-id="a7f7d-104">Create an instance of your renderer</span></span>

<span data-ttu-id="a7f7d-105">Créez une instance de la bibliothèque de convertisseur.</span><span class="sxs-lookup"><span data-stu-id="a7f7d-105">Create an instance of the renderer library.</span></span> 

```csharp
using AdaptiveCards.Rendering.Uwp;
// ...

var renderer = new AdaptiveCardRenderer();
```

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="a7f7d-106">Créer une carte à partir d’une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="a7f7d-106">Create a card from a JSON string</span></span>

```csharp
var card = AdaptiveCard.FromJsonString(jsonString);
```

## <a name="create-a-card-from-a-json-object"></a><span data-ttu-id="a7f7d-107">Créer une carte à partir d’un objet JSON</span><span class="sxs-lookup"><span data-stu-id="a7f7d-107">Create a card from a JSON object</span></span>

```csharp
var card = AdaptiveCard.FromJson(jsonObject);
```

## <a name="render-a-card"></a><span data-ttu-id="a7f7d-108">Afficher une carte</span><span class="sxs-lookup"><span data-stu-id="a7f7d-108">Render a card</span></span>

<span data-ttu-id="a7f7d-109">Acquérir une carte à partir d’une source et le rendre.</span><span class="sxs-lookup"><span data-stu-id="a7f7d-109">Acquire a card from a source and render it.</span></span>

```csharp
RenderedAdaptiveCard renderedAdaptiveCard =  renderer.RenderAdaptiveCard(card);

// Check if the render was successful
if (renderedAdaptiveCard.FrameworkElement != null)
{
    // Get the framework element
    var uiCard = renderedAdaptiveCard.FrameworkElement;

    // Add it to your UI
    myGrid.Children.Add(uiCard);
}
```

## <a name="example"></a><span data-ttu-id="a7f7d-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="a7f7d-110">Example</span></span>

<span data-ttu-id="a7f7d-111">Voici un exemple à partir du convertisseur UWP.</span><span class="sxs-lookup"><span data-stu-id="a7f7d-111">Here is an example from the UWP renderer.</span></span>

```csharp
var renderer = new AdaptiveCardRenderer();
var card = AdaptiveCard.FromJsonString(jsonString);
var renderedAdaptiveCard = renderer.RenderAdaptiveCard(card.AdaptiveCard);
if (renderedAdaptiveCard.FrameworkElement != null)
{
    myGrid.Children.Add(renderedAdaptiveCard.FrameworkElement);
}
...
```