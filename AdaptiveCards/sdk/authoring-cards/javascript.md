---
title: SDK JavaScript pour cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 039171d895fac0975bf9eff4fe84fdf8b6f7e4af
ms.sourcegitcommit: f8de9c02b92cd8927a18e59e5650c92b2b78db06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68523834"
---
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="a423f-102">SDK JavaScript pour la création de cartes</span><span class="sxs-lookup"><span data-stu-id="a423f-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a423f-103">La bibliothèque pour sérialiser JSON est toujours en cours de développement et votre milage peut varier.</span><span class="sxs-lookup"><span data-stu-id="a423f-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="a423f-104">Comme nous l’avons décrit dans la [prise en main](../../authoring-cards/getting-started.md), une carte adaptative n’est rien de plus qu’un objet JSON sérialisé d’un modèle objet de carte.</span><span class="sxs-lookup"><span data-stu-id="a423f-104">As we described in the [Getting Started](../../authoring-cards/getting-started.md), an Adaptive Card is nothing more than a serialized JSON object of a card object model.</span></span>  <span data-ttu-id="a423f-105">Pour faciliter la manipulation du modèle objet, nous avons défini des bibliothèques qui définissent une hiérarchie de classes fortement typées qui est facile à sérialiser/désérialiser JSON.</span><span class="sxs-lookup"><span data-stu-id="a423f-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="a423f-106">Vous pouvez utiliser les outils de votre choix pour créer la carte adaptative JSON.</span><span class="sxs-lookup"><span data-stu-id="a423f-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="a423f-107">Le `adaptivecards` package NPM définit une bibliothèque pour travailler avec des cartes adaptatives dans JavaScript</span><span class="sxs-lookup"><span data-stu-id="a423f-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="a423f-108">Pour installer</span><span class="sxs-lookup"><span data-stu-id="a423f-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example"></a><span data-ttu-id="a423f-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="a423f-109">Example</span></span>

<span data-ttu-id="a423f-110">L’API suivante montre comment construire une carte adaptative à l’aide du modèle objet et la sérialiser au format JSON.</span><span class="sxs-lookup"><span data-stu-id="a423f-110">The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.</span></span>

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
