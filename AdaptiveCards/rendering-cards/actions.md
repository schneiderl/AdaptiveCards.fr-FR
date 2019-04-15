---
title: Actions
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 42ba1ca4ba2ecd508bdee2f04061293d48349aab
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553371"
---
# <a name="actions"></a><span data-ttu-id="8e0d0-102">Actions</span><span class="sxs-lookup"><span data-stu-id="8e0d0-102">Actions</span></span>

<span data-ttu-id="8e0d0-103">Par défaut, les actions seront affiche sous forme de boutons sur la carte, mais c’est à votre application pour les rendre à fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="8e0d0-104">Chaque kit SDK comporte l’équivalent d’un `OnAction` événement que vous devez gérer.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="8e0d0-105">**Action.OpenUrl** -ouvrez spécifié `url`.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="8e0d0-106">**Action.Submit** - prendre le résultat de l’envoi et l’envoyer à la source.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="8e0d0-107">Comment vous l’envoyer à la source de la carte dépend entièrement de vous.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="8e0d0-108">**Action.ShowCard** - appelle une boîte de dialogue et restitue l’entrée secondaire dans cette boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="8e0d0-109">Notez que vous devez uniquement gérer cela si `ShowCardActionMode` est défini sur `popup`.</span><span class="sxs-lookup"><span data-stu-id="8e0d0-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>