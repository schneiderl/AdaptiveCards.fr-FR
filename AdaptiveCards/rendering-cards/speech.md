---
title: Gestion de la parole
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: fb56c97da3cca776da0fc7ea65a9726c8826e910
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145539"
---
# <a name="handling-speech"></a><span data-ttu-id="30231-102">Gestion de la parole</span><span class="sxs-lookup"><span data-stu-id="30231-102">Handling speech</span></span>

<span data-ttu-id="30231-103">Pour prendre en charge la parole, les cartes adaptatives disposent de la propriété `speak`, qui contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30231-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="30231-104">La balise de parole peut être annotée à l’aide du [balisage SSML](https://msdn.microsoft.com/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="30231-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="30231-105">SSML vous donne la possibilité de contrôler la vitesse, le ton et l’inflexion de la parole.</span><span class="sxs-lookup"><span data-stu-id="30231-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="30231-106">Il vous permet même de diffuser de l’audio ou de restituer un flux audio TTS à partir de votre propre service, ce qui vous donne beaucoup de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="30231-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="30231-107">La propriété Speak peut être utilisée par une application hôte selon deux modèles :</span><span class="sxs-lookup"><span data-stu-id="30231-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="30231-108">**À la livraison** : lors de la livraison d’une carte, un client peut choisir de lire la propriété Speak pour obtenir une description de la carte dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="30231-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="30231-109">**À la demande** : afin de prendre en charge un modèle d’accessibilité plus riche, le schéma prend en charge une balise speak par élément.</span><span class="sxs-lookup"><span data-stu-id="30231-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="30231-110">Cela permet aux clients de lire chaque élément aux destinataires ayant des besoins d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="30231-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

