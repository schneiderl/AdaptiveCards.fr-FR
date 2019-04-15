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
# <a name="getting-started---javascript"></a>Mise en route - JavaScript

Comme décrit dans [mise en route](../../../authoring-cards/getting-started.md) page, une carte adaptative est un modèle d’objet de carte sérialisé en JSON. Il s’agit un kit SDK JavaScript pour la génération côté client HTML dans le navigateur.

> [!IMPORTANT]
> **Dernières modifications issues des v0.5**
> 
> 1. Package renommé à partir de `microsoft-adaptivecards` à `adaptivecards`
> 1. La méthode statique `AdaptiveCards.setHostConfig()` a été déplacé vers un membre d’instance de `AdaptiveCard`. Par exemple, `myCard.hostConfig = {}` 
> 1. `HostConfig` est devenu bien que différents renomme et se déplace. Consultez le [sample.json](https://github.com/Microsoft/AdaptiveCards/blob/master/samples/HostConfig/sample.json) configuration de l’hôte de structure en cours
> 1. Ont également été certaines modifications du schéma à partir de la version préliminaire v0.5, qui sont [décrites ici](https://github.com/Microsoft/AdaptiveCards/pull/633)
> 1. La méthode statique `renderCard()` fonction a été supprimée car il était redondant avec les méthodes de classe. Utilisez `adaptiveCard.render()` comme décrit ci-dessous. 


## <a name="install"></a>Installation

### <a name="node"></a>Nœud

[![installation de npm](https://img.shields.io/npm/v/adaptivecards.svg)](https://www.npmjs.com/package/adaptivecards)

```console
npm install adaptivecards --save
```

### <a name="cdn"></a>CDN

```html
<script src="https://unpkg.com/adaptivecards/dist/adaptivecards.js"></script>
```

## <a name="usage"></a>Utilisation

### <a name="import-the-module"></a>Importez le module

```js
// import the module
import * as AdaptiveCards from "adaptivecards";

// or require it
var AdaptiveCards = require("adaptivecards");

// or use the global variable if loaded from CDN
AdaptiveCards.renderCard(...);
```

## <a name="next-steps"></a>Étapes suivantes

Consultez [restituer une carte](render-a-card.md) pour les prochaines étapes !
