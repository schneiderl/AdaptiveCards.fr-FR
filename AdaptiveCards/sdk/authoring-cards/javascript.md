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
# <a name="javascript-sdk-for-creating-cards"></a>SDK JavaScript pour la création de cartes

> [!IMPORTANT]
> La bibliothèque pour sérialiser JSON est toujours en cours de développement et votre milage peut varier.

Comme nous l’avons décrit dans la [prise en main](../../authoring-cards/getting-started.md), une carte adaptative n’est rien de plus qu’un objet JSON sérialisé d’un modèle objet de carte.  Pour faciliter la manipulation du modèle objet, nous avons défini des bibliothèques qui définissent une hiérarchie de classes fortement typées qui est facile à sérialiser/désérialiser JSON.

Vous pouvez utiliser les outils de votre choix pour créer la carte adaptative JSON.

Le package `adaptivecards` NPM définit une bibliothèque pour travailler avec des cartes adaptatives dans JavaScript

## <a name="to-install"></a>Pour installer
```console
npm install adaptivecards
```

## <a name="example"></a>Exemple

L’API suivante montre comment construire une carte adaptative à l’aide du modèle objet et la sérialiser au format JSON.

```typescript
let card = new Adaptive.AdaptiveCard();
card.version = new Adaptive.Version(1, 0);

let textBlock = new Adaptive.TextBlock();
textBlock.text = "Hello World";

card.addItem(textBlock);

let json = card.toJSON();
```
