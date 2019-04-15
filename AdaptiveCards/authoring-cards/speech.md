---
title: Reconnaissance vocale et la personnalisation avancée
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 19e77b86da9d163f5fcf6a6074071a4638a8d793
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552611"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="030a6-102">Reconnaissance vocale et la personnalisation avancée</span><span class="sxs-lookup"><span data-stu-id="030a6-102">Speech and advanced customization</span></span>
<span data-ttu-id="030a6-103">Nous vivons dans une ère d’interaction vocale via des services tels que Cortana.</span><span class="sxs-lookup"><span data-stu-id="030a6-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="030a6-104">Des cartes adaptatives sont conçues dès le premier jour pour prendre en charge la reconnaissance vocale, l’activation de nouveaux scénarios de mains-full froids.</span><span class="sxs-lookup"><span data-stu-id="030a6-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="030a6-105">Le `speak` balise permet à la carte adaptative à être remis à un environnement où un affichage visuel n’est pas une expérience principale, comme à un tableau de bord de voiture tout en garantissant.</span><span class="sxs-lookup"><span data-stu-id="030a6-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="030a6-106">Parlez de propriété</span><span class="sxs-lookup"><span data-stu-id="030a6-106">Speak property</span></span>
<span data-ttu-id="030a6-107">Pour prendre en charge la reconnaissance vocale que nous avons un `speak` propriété qui contient le texte à dire à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="030a6-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="030a6-108">Le texte peut être annoté à l’aide du langage de balisage de synthèse vocale ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span><span class="sxs-lookup"><span data-stu-id="030a6-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)).</span></span> <span data-ttu-id="030a6-109">SSML contrôle la vitesse, le ton et inflexion de la reconnaissance vocale.</span><span class="sxs-lookup"><span data-stu-id="030a6-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="030a6-110">Il permet même vous à diffuser des flux audio ou d’un rendu un flux audio de synthèse vocale à partir de votre propre service, ce qui vous donne une grande souplesse pour la personnalisation.</span><span class="sxs-lookup"><span data-stu-id="030a6-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="030a6-111">Il existe deux modèles pour parlent de l’utilisation de propriété par une application hôte :</span><span class="sxs-lookup"><span data-stu-id="030a6-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="030a6-112">**Sur la distribution** : quand une carte est remise, le client peut choisir de lire la propriété de lecture de la carte décrire la carte dans sa globalité.</span><span class="sxs-lookup"><span data-stu-id="030a6-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="030a6-113">**À la demande** - pour prendre en charge un modèle plus riche d’accessibilité, le prend en charge du schéma une lecture de balise pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="030a6-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="030a6-114">Le client peut lire une propriété de lecture pour chaque élément dans la carte.</span><span class="sxs-lookup"><span data-stu-id="030a6-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="030a6-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="030a6-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="030a6-116">Création de contenu de reconnaissance vocale</span><span class="sxs-lookup"><span data-stu-id="030a6-116">Speech content design</span></span>

<span data-ttu-id="030a6-117">Contenu conçu pour la voix est différent du contenu conçu pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="030a6-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="030a6-118">Lorsque vous concevez une carte, vous concevez une expérience visuelle entière pour présenter des informations à un utilisateur d’une manière qui les delights.</span><span class="sxs-lookup"><span data-stu-id="030a6-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="030a6-119">Lors de la conception pour la reconnaissance vocale, vous devez considérer comment verbalement décrire le contenu d’une manière qui delights l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="030a6-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
