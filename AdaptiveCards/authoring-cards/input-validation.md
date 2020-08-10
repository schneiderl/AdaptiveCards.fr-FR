---
title: Validation d'entrée
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
ms.openlocfilehash: 4c8aa73a218946944b25557eae141e231e8a6ac5
ms.sourcegitcommit: 2a394b75439b382d7bc3134078ecff02429617b8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544961"
---
# <a name="input-validation"></a>Validation d'entrée

Dans les versions 1.3 et ultérieures du schéma, le format Cartes adaptatives prend en charge la validation des entrées côté client des types Entrée.

### <a name="validation-properties"></a>Propriétés de validation

Les propriétés suivantes sont prises en charge pour la validation dans Cartes adaptatives :

| Entrée | Propriétés |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

Une propriété `errorMessage` est disponible sur tous les types d’entrée afin de spécifier quelle erreur doit être affichée à l’utilisateur s’il saisit une valeur non valide. 

> [!NOTE]
>
> Les propriétés min et max (y compris maxLength) de certaines plateformes peuvent être appliquées directement par le contrôle. Par exemple, une propriété min sur Input.Date peut être appliquée ne permettant pas aux utilisateurs de sélectionner une date antérieure au minimum dans un sélecteur de dates. Dans ce cas, il est possible que le message d’erreur ne s’affiche pas.

## <a name="fields-to-be-validated-and-submitted"></a>Champs à valider et à envoyer

Les entrées seront validées lorsque l’utilisateur cliquera sur une action Action.Submit dans la carte. Les entrées qui seront validées et envoyées pour une action Action.Submit donnée sont les suivantes :

 - Entrées sur la même carte que l’action Action.Submit
 - Entrées sur toute carte parent de la carte contenant l’action Action.Submit dans le cas d’une carte sous une action Action.ShowCard

Si ces entrées sont validées, les valeurs de leurs champs sont renvoyées au client. Si elles ne sont pas validées, les messages d’erreur des entrées non valides s’affichent et la soumission n’est pas envoyée.

> [!NOTE]
>
> Les entrées ne seront **pas** validées ni envoyées si elles figurent sur une carte enfant ou frère de la carte contenant l’action Action.Submit. Cela comprend les cartes d’Action.ShowCards dans ActionSets dans le corps de cette carte. Il s’agit d’une modification du comportement par rapport aux versions de rendu antérieures à la version 2.0 qui s’applique aux cartes de toutes les versions de schéma, que les propriétés de validation d’entrée soient ou non utilisées. 

## <a name="other-considerations-and-known-issues"></a>Autres considérations et problèmes connus

 - Il n’est pas recommandé de créer des entrées avec des propriétés de validation susceptibles de ne pas être toujours visibles en raison de l’interaction avec Action.ToggleVisibility. Les messages d’erreur et les indications visuelles selon lesquelles l’entrée n’est pas valide ne s’afficheront pas si l’entrée n’est pas visible actuellement, ce qui peut entraîner une confusion pour les utilisateurs quant à la raison pour laquelle leur soumission est bloquée.

 - Le comportement de la validation d’entrée pour les hôtes utilisant des cartes d’affichage contextuelles à l’aide de la valeur `"actions":"showCard":"actionMode":"popup"` dans leur configuration d’hôte n’est pas bien défini. Il est possible que les cartes d’affichage contextuelles soient déconseillées dans une prochaine version.

