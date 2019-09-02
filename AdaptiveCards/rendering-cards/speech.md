---
title: Gestion de la parole
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 64eeaefbc2ac775b69bd48cc853beb729cb2c37f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137992"
---
# <a name="handling-speech"></a><span data-ttu-id="7b8ec-102">Gestion de la parole</span><span class="sxs-lookup"><span data-stu-id="7b8ec-102">Handling speech</span></span>

<span data-ttu-id="7b8ec-103">Pour prendre en charge la parole, les cartes adaptatives disposent de la propriété `speak`, qui contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7b8ec-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="7b8ec-104">La balise de parole peut être annotée à l’aide du [balisage SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="7b8ec-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="7b8ec-105">SSML vous donne la possibilité de contrôler la vitesse, le ton et l’inflexion de la parole.</span><span class="sxs-lookup"><span data-stu-id="7b8ec-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="7b8ec-106">Il vous permet même de diffuser de l’audio ou de restituer un flux audio TTS à partir de votre propre service, ce qui vous donne beaucoup de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="7b8ec-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="7b8ec-107">La propriété Speak peut être utilisée par une application hôte selon deux modèles :</span><span class="sxs-lookup"><span data-stu-id="7b8ec-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="7b8ec-108">**À la livraison** : lors de la livraison d’une carte, un client peut choisir de lire la propriété Speak pour obtenir une description de la carte dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="7b8ec-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="7b8ec-109">**À la demande** : afin de prendre en charge un modèle d’accessibilité plus riche, le schéma prend en charge une balise speak par élément.</span><span class="sxs-lookup"><span data-stu-id="7b8ec-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="7b8ec-110">Cela permet aux clients de lire chaque élément aux destinataires ayant des besoins d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="7b8ec-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

