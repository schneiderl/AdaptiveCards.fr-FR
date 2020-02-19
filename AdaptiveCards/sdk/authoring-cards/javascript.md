---
title: SDK JavaScript pour cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 07/26/2019
ms.topic: article
ms.openlocfilehash: 4ddff841ec073c60a8aa6184f309e94052cb002d
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454802"
---
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="19b54-102">SDK JavaScript pour la création de cartes</span><span class="sxs-lookup"><span data-stu-id="19b54-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19b54-103">La bibliothèque pour sérialiser JSON est toujours en cours de développement et votre milage peut varier.</span><span class="sxs-lookup"><span data-stu-id="19b54-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="19b54-104">Comme nous l’avons décrit dans la [prise en main](../../authoring-cards/getting-started.md), une carte adaptative n’est rien de plus qu’un objet JSON sérialisé d’un modèle objet de carte.</span><span class="sxs-lookup"><span data-stu-id="19b54-104">As we described in the [Getting Started](../../authoring-cards/getting-started.md), an Adaptive Card is nothing more than a serialized JSON object of a card object model.</span></span>  <span data-ttu-id="19b54-105">Pour faciliter la manipulation du modèle objet, nous avons défini des bibliothèques qui définissent une hiérarchie de classes fortement typées qui est facile à sérialiser/désérialiser JSON.</span><span class="sxs-lookup"><span data-stu-id="19b54-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="19b54-106">Vous pouvez utiliser les outils de votre choix pour créer la carte adaptative JSON.</span><span class="sxs-lookup"><span data-stu-id="19b54-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="19b54-107">Le package `adaptivecards` NPM définit une bibliothèque pour travailler avec des cartes adaptatives dans JavaScript</span><span class="sxs-lookup"><span data-stu-id="19b54-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="19b54-108">Pour installer</span><span class="sxs-lookup"><span data-stu-id="19b54-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example"></a><span data-ttu-id="19b54-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="19b54-109">Example</span></span>

<span data-ttu-id="19b54-110">L’API suivante montre comment construire une carte adaptative à l’aide du modèle objet et la sérialiser au format JSON.</span><span class="sxs-lookup"><span data-stu-id="19b54-110">The following API shows how to construct an Adaptive Card using the object model and serialize it to JSON.</span></span>

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
