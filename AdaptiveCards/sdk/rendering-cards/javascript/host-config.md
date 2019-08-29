---
title: Configuration de l’hôte-SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 11/28/2017
ms.topic: article
ms.openlocfilehash: 1809a022481e4fb28d2db454cfe90e07d09279ff
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553601"
---
# <a name="host-config---javascript"></a>Configuration de l’hôte-JavaScript

```js
// Create an AdaptiveCard instance
var adaptiveCard = new AdaptiveCards.AdaptiveCard();

// Set its hostConfig property unless you want to use the default Host Config
// Host Config defines the style and behavior of a card
adaptiveCard.hostConfig = new AdaptiveCards.HostConfig({
    fontFamily: "Segoe UI, Helvetica Neue, sans-serif"
    // More host config options
});

// Render the card to an HTML element:
var renderedCard = adaptiveCard.render();
```

## <a name="customization"></a>Personnalisation

Il existe trois façons de personnaliser le rendu de carte adaptative: 
1. Configuration de l’hôte
2. Styles CSS
3. Rendu d’élément personnalisé

### <a name="hostconfig"></a>HostConfig 

Une [configuration d’hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagé que tous les convertisseurs comprennent. Elle vous permet de définir des styles (par exemple, famille de polices, tailles de police, espacement par défaut) et des comportements (par exemple, nombre maximal d’actions) communs qui sont automatiquement interprétés par le convertisseur de chaque plateforme. 

L’objectif est que l’interface utilisateur native générée par le convertisseur de chaque plateforme se présente de façon très similaire avec un minimum de travail de votre part.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```