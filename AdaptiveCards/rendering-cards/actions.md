---
title: Actions
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 34283b52f0c4902c71ea33634676832c7dfec5c9
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "77454942"
---
# <a name="actions"></a><span data-ttu-id="e0e4d-102">Actions</span><span class="sxs-lookup"><span data-stu-id="e0e4d-102">Actions</span></span>

<span data-ttu-id="e0e4d-103">Par défaut, les actions s’affichent sous la forme de boutons sur la carte, mais c’est à votre application de faire en sorte qu’elles se comportent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-103">By default, the actions will render as buttons on the card, but it's up to your app to make them behave as you expect.</span></span> <span data-ttu-id="e0e4d-104">Chaque SDK a l’équivalent d’un événement `OnAction` que vous devez gérer.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-104">Each SDK has the equivalent of an `OnAction` event that you must handle.</span></span>

* <span data-ttu-id="e0e4d-105">**Action.OpenUrl** : ouvrir le `url` spécifié.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-105">**Action.OpenUrl** - open the specified `url`.</span></span>  
* <span data-ttu-id="e0e4d-106">**Action.Submit** : prendre le résultat de l’envoi et l’envoyer à la source.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-106">**Action.Submit** - take the result of the submit and send it to the source.</span></span> <span data-ttu-id="e0e4d-107">La façon dont vous l’envoyez à la source de la carte dépend entièrement de vous.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-107">How you send it to the source of the card is entirely up to you.</span></span>
* <span data-ttu-id="e0e4d-108">**Action.ShowCard** : appelle une boîte de dialogue et affiche la sous-carte dans cette boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-108">**Action.ShowCard** - invokes a dialog and renders the sub-card into that dialog.</span></span> <span data-ttu-id="e0e4d-109">Notez que vous devez uniquement gérer cela si `ShowCardActionMode` a la valeur `popup`.</span><span class="sxs-lookup"><span data-stu-id="e0e4d-109">Note that you only need to handle this if `ShowCardActionMode` is set to `popup`.</span></span>