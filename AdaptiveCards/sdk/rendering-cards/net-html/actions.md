---
title: Actions - Kit de développement logiciel .NET HTML
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: 99bf6121489391c207a71b45264dc68aa2c6116e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553311"
---
# <a name="actions---net-html"></a>Actions - .NET HTML

Carte de niveau supérieur `actions` seront restituées sous la forme d’un élément HTML `<button>`. Dans la mesure où il s’agit d’une bibliothèque côté serveur, que c’est à vous pour associer des gestionnaires d’événements côté client lorsque les boutons sont enfoncés. Chaque `<button>` dans le code HTML a les attributs que vous pouvez utiliser pour associer le comportement approprié.

Certains éléments ont un `selectAction` propriété (Image de conteneur, colonnes,), ce qui les rend appelables. Si un élément a un `selectAction` le convertisseur ajoutera une classe CSS de `ac-selectable`, avec la sous attributs.

Type d'action | Classe CSS | Attributs supplémentaires
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` (le `url` propriété à partir de la carte)
`Action.Submit` | `ac-action-submit` | `data-ac-data` (le `data` propriété à partir de la carte)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` (le `id` de la `<div>` contenant la carte interne)