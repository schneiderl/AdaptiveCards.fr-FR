---
title: Actions-SDK HTML .NET
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: f577c0bab73e2bd1f75bb22dd7a41a7dbfd63307
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454572"
---
# <a name="actions---net-html"></a>Actions-HTML .NET

La carte de niveau supérieur `actions` sera restituée en tant que `<button>`HTML. Dans la mesure où il s’agit d’une bibliothèque côté serveur, vous pouvez associer des gestionnaires d’événements côté client lorsque vous appuyez sur les boutons. Chaque `<button>` dans le code HTML aura des attributs que vous pouvez utiliser pour associer le comportement approprié.

Certains éléments ont une propriété `selectAction` (Container, Columns, image) qui les rend programmes appelables. Si un élément a un `selectAction` le convertisseur ajoute une classe CSS de `ac-selectable`, ainsi que les attributs ci-dessous.

Type d'action | Classe CSS | Attributs supplémentaires
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | `data-ac-url` (la propriété `url` de la carte)
`Action.Submit` | `ac-action-submit` | `data-ac-data` (la propriété `data` de la carte)
`Action.ShowCard` | `ac-action-showCard` | `data-ac-showcardid` (la `id` du `<div>` contenant la carte interne)