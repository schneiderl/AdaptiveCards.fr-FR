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
# <a name="actions---net-html"></a><span data-ttu-id="d77ba-102">Actions-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="d77ba-102">Actions - .NET HTML</span></span>

<span data-ttu-id="d77ba-103">La carte de niveau supérieur `actions` sera restituée en tant que `<button>`HTML.</span><span class="sxs-lookup"><span data-stu-id="d77ba-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="d77ba-104">Dans la mesure où il s’agit d’une bibliothèque côté serveur, vous pouvez associer des gestionnaires d’événements côté client lorsque vous appuyez sur les boutons.</span><span class="sxs-lookup"><span data-stu-id="d77ba-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="d77ba-105">Chaque `<button>` dans le code HTML aura des attributs que vous pouvez utiliser pour associer le comportement approprié.</span><span class="sxs-lookup"><span data-stu-id="d77ba-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="d77ba-106">Certains éléments ont une propriété `selectAction` (Container, Columns, image) qui les rend programmes appelables.</span><span class="sxs-lookup"><span data-stu-id="d77ba-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="d77ba-107">Si un élément a un `selectAction` le convertisseur ajoute une classe CSS de `ac-selectable`, ainsi que les attributs ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d77ba-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="d77ba-108">Type d'action</span><span class="sxs-lookup"><span data-stu-id="d77ba-108">Action Type</span></span> | <span data-ttu-id="d77ba-109">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="d77ba-109">CSS class</span></span> | <span data-ttu-id="d77ba-110">Attributs supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d77ba-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="d77ba-111">`data-ac-url` (la propriété `url` de la carte)</span><span class="sxs-lookup"><span data-stu-id="d77ba-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="d77ba-112">`data-ac-data` (la propriété `data` de la carte)</span><span class="sxs-lookup"><span data-stu-id="d77ba-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="d77ba-113">`data-ac-showcardid` (la `id` du `<div>` contenant la carte interne)</span><span class="sxs-lookup"><span data-stu-id="d77ba-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>