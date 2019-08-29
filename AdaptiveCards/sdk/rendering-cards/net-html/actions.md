---
title: Actions-SDK HTML .NET
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
# <a name="actions---net-html"></a><span data-ttu-id="88ac4-102">Actions-HTML .NET</span><span class="sxs-lookup"><span data-stu-id="88ac4-102">Actions - .NET HTML</span></span>

<span data-ttu-id="88ac4-103">La carte `actions` de niveau supérieur est restituée sous `<button>`forme de code html.</span><span class="sxs-lookup"><span data-stu-id="88ac4-103">Top-level card `actions` will render as an HTML `<button>`.</span></span> <span data-ttu-id="88ac4-104">Dans la mesure où il s’agit d’une bibliothèque côté serveur, vous pouvez associer des gestionnaires d’événements côté client lorsque vous appuyez sur les boutons.</span><span class="sxs-lookup"><span data-stu-id="88ac4-104">Since this is a server-side library it's up to you to wire up client-side event handlers when buttons are pressed.</span></span> <span data-ttu-id="88ac4-105">Chaque `<button>` dans le code html aura des attributs que vous pouvez utiliser pour associer le comportement approprié.</span><span class="sxs-lookup"><span data-stu-id="88ac4-105">Each `<button>` in the HTML will have attributes that you can use to wire up the proper behavior.</span></span>

<span data-ttu-id="88ac4-106">Certains éléments ont une `selectAction` propriété (Container, Columns, image) qui les rend programmes appelables.</span><span class="sxs-lookup"><span data-stu-id="88ac4-106">Some elements have a `selectAction` property (Container, Columns, Image) which makes them invokable.</span></span> <span data-ttu-id="88ac4-107">Si un élément a un `selectAction` convertisseur, ajoute une classe CSS de `ac-selectable`, ainsi que les attributs ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="88ac4-107">If an element has a `selectAction` the renderer will add a CSS class of `ac-selectable`, along with the below attributes.</span></span>

<span data-ttu-id="88ac4-108">Type d’action</span><span class="sxs-lookup"><span data-stu-id="88ac4-108">Action Type</span></span> | <span data-ttu-id="88ac4-109">Classe CSS</span><span class="sxs-lookup"><span data-stu-id="88ac4-109">CSS class</span></span> | <span data-ttu-id="88ac4-110">Attributs supplémentaires</span><span class="sxs-lookup"><span data-stu-id="88ac4-110">Additional attributes</span></span>
---|---|---
`Action.OpenUrl` | `ac-action-openUrl` | <span data-ttu-id="88ac4-111">`data-ac-url`(la `url` propriété de la carte)</span><span class="sxs-lookup"><span data-stu-id="88ac4-111">`data-ac-url` (the `url` property from the card)</span></span>
`Action.Submit` | `ac-action-submit` | <span data-ttu-id="88ac4-112">`data-ac-data`(la `data` propriété de la carte)</span><span class="sxs-lookup"><span data-stu-id="88ac4-112">`data-ac-data` (the `data` property from the card)</span></span>
`Action.ShowCard` | `ac-action-showCard` | <span data-ttu-id="88ac4-113">`data-ac-showcardid`(le `id` `<div>` du contenant la carte interne)</span><span class="sxs-lookup"><span data-stu-id="88ac4-113">`data-ac-showcardid` (the `id` of the `<div>` containing the inner card)</span></span>