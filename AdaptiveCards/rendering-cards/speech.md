---
title: Gestion des voix
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 64eeaefbc2ac775b69bd48cc853beb729cb2c37f
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137992"
---
# <a name="handling-speech"></a><span data-ttu-id="9f06a-102">Gestion des voix</span><span class="sxs-lookup"><span data-stu-id="9f06a-102">Handling speech</span></span>

<span data-ttu-id="9f06a-103">En parole prise en charge des cartes adaptatives a le `speak` propriété qui contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9f06a-103">To support speech adaptive Cards has the `speak` property which contains information on how a card should be read aloud to a user.</span></span>

<span data-ttu-id="9f06a-104">La balise de reconnaissance vocale peut être annotée à l’aide de [un balisage SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span><span class="sxs-lookup"><span data-stu-id="9f06a-104">The speech tag can be annotated using  [SSML markup](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx).</span></span> <span data-ttu-id="9f06a-105">SSML vous donne le contrôle la vitesse, le ton, de la capacité inflexion de la reconnaissance vocale.</span><span class="sxs-lookup"><span data-stu-id="9f06a-105">SSML gives you the ability control the speed, tone, inflection of the speech.</span></span>  <span data-ttu-id="9f06a-106">Il permet même vous à diffuser des flux audio ou d’un rendu un flux audio de synthèse vocale à partir de votre propre service, ce qui vous donne une grande quantité de personnalisation.</span><span class="sxs-lookup"><span data-stu-id="9f06a-106">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of customization.</span></span>

<span data-ttu-id="9f06a-107">Il existe 2 modèles pour parlent de l’utilisation de propriété par une application hôte :</span><span class="sxs-lookup"><span data-stu-id="9f06a-107">There are 2 patterns for speak property usage by a host application:</span></span>
* <span data-ttu-id="9f06a-108">**sur la distribution** : quand une carte est remise à un client peut choisir de lire la propriété de lecture de la carte décrire la carte dans sa globalité.</span><span class="sxs-lookup"><span data-stu-id="9f06a-108">**on delivery** - When a card is delivered a client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="9f06a-109">**à la demande** - pour prendre en charge un modèle d’accessibilité plus riche le prend en charge du schéma une lecture de balise par élément.</span><span class="sxs-lookup"><span data-stu-id="9f06a-109">**on demand** - In order to support a richer accessibility model the schema supports a speak tag per element.</span></span>  
<span data-ttu-id="9f06a-110">Cela permet aux clients de lire chaque élément aux destinataires avec des normes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="9f06a-110">This allows for clients to read each element to recipients with accessibility requirements.</span></span>

