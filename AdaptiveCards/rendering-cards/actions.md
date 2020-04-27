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
# <a name="actions"></a>Actions

Par défaut, les actions s’affichent sous la forme de boutons sur la carte, mais c’est à votre application de faire en sorte qu’elles se comportent comme prévu. Chaque SDK a l’équivalent d’un événement `OnAction` que vous devez gérer.

* **Action.OpenUrl** : ouvrir le `url` spécifié.  
* **Action.Submit** : prendre le résultat de l’envoi et l’envoyer à la source. La façon dont vous l’envoyez à la source de la carte dépend entièrement de vous.
* **Action.ShowCard** : appelle une boîte de dialogue et affiche la sous-carte dans cette boîte de dialogue. Notez que vous devez uniquement gérer cela si `ShowCardActionMode` a la valeur `popup`.