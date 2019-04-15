---
title: Kit de développement logiciel JavaScript pour des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 6372f2f23a817ecc4d07d950d6513d14357547b7
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552661"
---
# <a name="javascript-sdk-for-creating-cards"></a>SDK JavaScript pour la création de cartes

> [!IMPORTANT]
> La bibliothèque de sérialisation JSON est en cours de développement et votre milage peut-être varier.

Comme décrit dans la section mise en route, une carte adaptative est rien de plus, un objet json sérialisé d’un modèle d’objet de carte.  Pour le rendre facile à manipuler le modèle objet, nous avons défini certaines bibliothèques qui définissent une hiérarchie de classe fortement typée qui est facile de sérialisation/désérialisation de json.

Vous pouvez utiliser les outils que vous souhaitez créer la carte adaptative json.

Le `adaptivecards` package npm définit une bibliothèque pour travailler avec des cartes adaptatives dans javascript

## <a name="to-install"></a>Pour installer
```console
npm install adaptivecards
```

## <a name="example-creating"></a>Création de l’exemple 
Il existe des définitions d’interface dans `schema.d.ts` qui décrivent la forme du schéma

```typescript
let card = {
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "Container",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "Meow!"
                },
                {
                    "type": "Image",
                    "url": "http://adaptivecards.io/content/cats/1.png"
                }
            ]
        }
    ]
};
```

Il existe également un modèle d’objet pour la création de cartes.


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
