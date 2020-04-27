---
title: Gestion de la parole
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: fb56c97da3cca776da0fc7ea65a9726c8826e910
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "76145539"
---
# <a name="handling-speech"></a>Gestion de la parole

Pour prendre en charge la parole, les cartes adaptatives disposent de la propriété `speak`, qui contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.

La balise de parole peut être annotée à l’aide du [balisage SSML](https://msdn.microsoft.com/library/office/hh361578(v=office.14).aspx). SSML vous donne la possibilité de contrôler la vitesse, le ton et l’inflexion de la parole.  Il vous permet même de diffuser de l’audio ou de restituer un flux audio TTS à partir de votre propre service, ce qui vous donne beaucoup de personnalisation.

La propriété Speak peut être utilisée par une application hôte selon deux modèles :
* **À la livraison** : lors de la livraison d’une carte, un client peut choisir de lire la propriété Speak pour obtenir une description de la carte dans son ensemble.
* **À la demande** : afin de prendre en charge un modèle d’accessibilité plus riche, le schéma prend en charge une balise speak par élément.  
Cela permet aux clients de lire chaque élément aux destinataires ayant des besoins d’accessibilité.

