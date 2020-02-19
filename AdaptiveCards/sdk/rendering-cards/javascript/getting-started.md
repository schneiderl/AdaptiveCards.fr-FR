---
title: SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 29786fe5e533e67558df88f58b1330aa6646b532
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454621"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="1134e-102">Prise en main-JavaScript</span><span class="sxs-lookup"><span data-stu-id="1134e-102">Getting started - JavaScript</span></span>

<span data-ttu-id="1134e-103">Comme nous l’avons décrit dans [prise en main](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle objet de carte sérialisée JSON.</span><span class="sxs-lookup"><span data-stu-id="1134e-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="1134e-104">Il s’agit d’un kit de développement logiciel (SDK) JavaScript permettant de générer du code HTML côté client dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="1134e-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

## <a name="install"></a><span data-ttu-id="1134e-105">Install</span><span class="sxs-lookup"><span data-stu-id="1134e-105">Install</span></span>

### <a name="node"></a><span data-ttu-id="1134e-106">Nœud</span><span class="sxs-lookup"><span data-stu-id="1134e-106">Node</span></span>

<span data-ttu-id="1134e-107">[![Installation npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="1134e-107">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards
```

### <a name="cdn"></a><span data-ttu-id="1134e-108">CDN</span><span class="sxs-lookup"><span data-stu-id="1134e-108">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="1134e-109">Utilisation</span><span class="sxs-lookup"><span data-stu-id="1134e-109">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="1134e-110">Importer le module</span><span class="sxs-lookup"><span data-stu-id="1134e-110">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="1134e-111">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1134e-111">Next steps</span></span>

<span data-ttu-id="1134e-112">Pour les prochaines étapes, voir [Effectuer le rendu d’une carte](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="1134e-112">See [Render a card](render-a-card.md) for the next steps!</span></span>
