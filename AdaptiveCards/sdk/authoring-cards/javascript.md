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
# <a name="javascript-sdk-for-creating-cards"></a><span data-ttu-id="3ae92-102">SDK JavaScript pour la création de cartes</span><span class="sxs-lookup"><span data-stu-id="3ae92-102">JavaScript SDK for creating cards</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3ae92-103">La bibliothèque de sérialisation JSON est en cours de développement et votre milage peut-être varier.</span><span class="sxs-lookup"><span data-stu-id="3ae92-103">The library for serializing JSON is still in development and your milage may vary.</span></span>

<span data-ttu-id="3ae92-104">Comme décrit dans la section mise en route, une carte adaptative est rien de plus, un objet json sérialisé d’un modèle d’objet de carte.</span><span class="sxs-lookup"><span data-stu-id="3ae92-104">As we described in the getting started section, an adaptive card is nothing more then a serialized json object of a card object model.</span></span>  <span data-ttu-id="3ae92-105">Pour le rendre facile à manipuler le modèle objet, nous avons défini certaines bibliothèques qui définissent une hiérarchie de classe fortement typée qui est facile de sérialisation/désérialisation de json.</span><span class="sxs-lookup"><span data-stu-id="3ae92-105">To make it easy to manipulate the object model we have defined some libraries which define a strongly typed class hierarchy that is easy to serialize/deserialize json.</span></span>

<span data-ttu-id="3ae92-106">Vous pouvez utiliser les outils que vous souhaitez créer la carte adaptative json.</span><span class="sxs-lookup"><span data-stu-id="3ae92-106">You can use any tooling that you want to create the adaptive card json.</span></span>

<span data-ttu-id="3ae92-107">Le `adaptivecards` package npm définit une bibliothèque pour travailler avec des cartes adaptatives dans javascript</span><span class="sxs-lookup"><span data-stu-id="3ae92-107">The `adaptivecards` npm package defines a library for working with adaptive cards in javascript</span></span>

## <a name="to-install"></a><span data-ttu-id="3ae92-108">Pour installer</span><span class="sxs-lookup"><span data-stu-id="3ae92-108">To install</span></span>
```console
npm install adaptivecards
```

## <a name="example-creating"></a><span data-ttu-id="3ae92-109">Création de l’exemple</span><span class="sxs-lookup"><span data-stu-id="3ae92-109">Example creating</span></span> 
<span data-ttu-id="3ae92-110">Il existe des définitions d’interface dans `schema.d.ts` qui décrivent la forme du schéma</span><span class="sxs-lookup"><span data-stu-id="3ae92-110">There are interface definitions in `schema.d.ts` which describe the shape of the schema</span></span>

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

<span data-ttu-id="3ae92-111">Il existe également un modèle d’objet pour la création de cartes.</span><span class="sxs-lookup"><span data-stu-id="3ae92-111">There is also an object model for creating cards.</span></span>


```typescript
let card :IAdaptiveCard =  new AdaptiveCard();
card.body.add(new TextBlock() 
{
    text = "hello world"
});
```
