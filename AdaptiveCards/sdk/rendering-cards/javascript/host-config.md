---
title: Configuration - SDK JavaScript de l’hôte
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
# <a name="host-config---javascript"></a>Host config - JavaScript

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

Il existe 3 façons de personnaliser le rendu de la carte adaptative : 
1. Configuration de l’hôte
2. Styles CSS
3. Rendu de l’élément personnalisé

### <a name="hostconfig"></a>HostConfig 

Un [configuration de l’hôte](../../../rendering-cards/host-config.md) est un objet de configuration partagée comprennent tous les convertisseurs. Cela vous permet de définir des styles courants (par exemple, famille de polices, tailles de police par défaut espacement) et les comportements (par exemple, un nombre maximal d’actions) qui seront automatiquement interprétées par chaque convertisseur de plateforme. 

L’objectif est que l’interface utilisateur native généré par chaque convertisseur de plateforme paraîtra très similaire avec un minimum de travail de votre part.

```javascript
var renderOptions = {
    ...
    hostConfig: {
        // Define your host config object here
        // See the HostConfig docs for details
    }
};
```