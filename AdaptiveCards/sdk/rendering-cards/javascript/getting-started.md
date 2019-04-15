---
title: Kit de développement logiciel JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 9684b96bba5168a1f07549468274ce5d74c01820
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553461"
---
# <a name="getting-started---javascript"></a><span data-ttu-id="3cdfb-102">Mise en route - JavaScript</span><span class="sxs-lookup"><span data-stu-id="3cdfb-102">Getting started - JavaScript</span></span>

<span data-ttu-id="3cdfb-103">Comme décrit dans [mise en route](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle d’objet de carte sérialisé en JSON.</span><span class="sxs-lookup"><span data-stu-id="3cdfb-103">As we described in [Getting Started](../../../authoring-cards/getting-started.md) page, an Adaptive Card is a JSON-serialized card object model.</span></span> <span data-ttu-id="3cdfb-104">Il s’agit un kit SDK JavaScript pour la génération côté client HTML dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="3cdfb-104">This is a JavaScript SDK for generating client-side HTML in the browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3cdfb-105">**Dernières modifications issues des v0.5**</span><span class="sxs-lookup"><span data-stu-id="3cdfb-105">**Breaking changes from v0.5**</span></span>
> 
> 1. <span data-ttu-id="3cdfb-106">Package renommé à partir de `microsoft-adaptivecards` à `adaptivecards`</span><span class="sxs-lookup"><span data-stu-id="3cdfb-106">Package renamed from `microsoft-adaptivecards` to `adaptivecards`</span></span>
> 1. <span data-ttu-id="3cdfb-107">La méthode statique `AdaptiveCards.setHostConfig()` a été déplacé vers un membre d’instance de `AdaptiveCard`.</span><span class="sxs-lookup"><span data-stu-id="3cdfb-107">The static `AdaptiveCards.setHostConfig()` has been moved to an instance member of `AdaptiveCard`.</span></span> <span data-ttu-id="3cdfb-108">Par exemple, `myCard.hostConfig = {}`</span><span class="sxs-lookup"><span data-stu-id="3cdfb-108">E.g., `myCard.hostConfig = {}`</span></span> 
> 1. <span data-ttu-id="3cdfb-109">`HostConfig` est devenu bien que différents renomme et se déplace.</span><span class="sxs-lookup"><span data-stu-id="3cdfb-109">`HostConfig` has gone though various renames and moves.</span></span> <span data-ttu-id="3cdfb-110">Consultez le [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) configuration de l’hôte de structure en cours</span><span class="sxs-lookup"><span data-stu-id="3cdfb-110">See the [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) Host Config for current structure</span></span>
> 1. <span data-ttu-id="3cdfb-111">Ont également été certaines modifications du schéma à partir de la version préliminaire v0.5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)</span><span class="sxs-lookup"><span data-stu-id="3cdfb-111">There have also been some schema changes from the v0.5 preview, which are [outlined here](https://github.com/Microsoft/AdaptiveCards/pull/633)</span></span>
> 1. <span data-ttu-id="3cdfb-112">La méthode statique `renderCard()` fonction a été supprimée car il était redondant avec les méthodes de classe.</span><span class="sxs-lookup"><span data-stu-id="3cdfb-112">The static `renderCard()` function was removed as it was redundant with the class methods.</span></span> <span data-ttu-id="3cdfb-113">Utilisez `adaptiveCard.render()` comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3cdfb-113">Use `adaptiveCard.render()` as described below.</span></span> 


## <a name="install"></a><span data-ttu-id="3cdfb-114">Installation</span><span class="sxs-lookup"><span data-stu-id="3cdfb-114">Install</span></span>

### <a name="node"></a><span data-ttu-id="3cdfb-115">Nœud</span><span class="sxs-lookup"><span data-stu-id="3cdfb-115">Node</span></span>

<span data-ttu-id="3cdfb-116">[![installation de npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span><span class="sxs-lookup"><span data-stu-id="3cdfb-116">[![npm install](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)</span></span>

```console
npm install adaptivecards --save
```

### <a name="cdn"></a><span data-ttu-id="3cdfb-117">CDN</span><span class="sxs-lookup"><span data-stu-id="3cdfb-117">CDN</span></span>

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a><span data-ttu-id="3cdfb-118">Utilisation</span><span class="sxs-lookup"><span data-stu-id="3cdfb-118">Usage</span></span>

### <a name="import-the-module"></a><span data-ttu-id="3cdfb-119">Importez le module</span><span class="sxs-lookup"><span data-stu-id="3cdfb-119">Import the module</span></span>

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a><span data-ttu-id="3cdfb-120">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3cdfb-120">Next steps</span></span>

<span data-ttu-id="3cdfb-121">Consultez [restituer une carte](render-a-card.md) pour les prochaines étapes !</span><span class="sxs-lookup"><span data-stu-id="3cdfb-121">See [Render a card](render-a-card.md) for the next steps!</span></span>
