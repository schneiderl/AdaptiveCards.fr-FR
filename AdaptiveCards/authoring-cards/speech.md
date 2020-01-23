---
title: Reconnaissance vocale et personnalisation avancée
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 1dfd9b0c45a280905223e3286998b333b0a6ec6a
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145340"
---
# <a name="speech-and-advanced-customization"></a><span data-ttu-id="8aa20-102">Reconnaissance vocale et personnalisation avancée</span><span class="sxs-lookup"><span data-stu-id="8aa20-102">Speech and advanced customization</span></span>
<span data-ttu-id="8aa20-103">Nous vivons à une époque d'interaction vocale grâce à des services tels que Cortana.</span><span class="sxs-lookup"><span data-stu-id="8aa20-103">We live in an era of speech interaction via services like Cortana.</span></span>  <span data-ttu-id="8aa20-104">Dès le premier jour, les cartes adaptatives sont conçues pour prendre en charge la reconnaissance vocale, ce qui permet de créer de nouveaux scénarios mains libres.</span><span class="sxs-lookup"><span data-stu-id="8aa20-104">Adaptive cards are designed from day one to support speech, enabling cool new hands-full scenarios.</span></span>

<span data-ttu-id="8aa20-105">La balise `speak` permet à la carte adaptative d'être distribuée dans un environnement où l'affichage visuel ne constitue pas l'expérience principale, comme un tableau de bord de voiture au volant.</span><span class="sxs-lookup"><span data-stu-id="8aa20-105">The `speak` tag enables the adaptive card to be delivered to an environment where a visual display is not primary experience, such as to a car dashboard while driving.</span></span> 

## <a name="speak-property"></a><span data-ttu-id="8aa20-106">Propriété Speak</span><span class="sxs-lookup"><span data-stu-id="8aa20-106">Speak property</span></span>
<span data-ttu-id="8aa20-107">Pour prendre en charge la reconnaissance vocale, nous disposons d'une propriété `speak` qui contient du texte à dire à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8aa20-107">To support speech we have a `speak` property which contains text to say to the user.</span></span> <span data-ttu-id="8aa20-108">Le texte peut être annoté en langage [SSML](https://msdn.microsoft.com/library/office/hh361578) (Speech Synthesis Markup Language).</span><span class="sxs-lookup"><span data-stu-id="8aa20-108">The text can be annotated using speech synthesis markup language ([SSML](https://msdn.microsoft.com/library/office/hh361578)).</span></span> <span data-ttu-id="8aa20-109">SSML contrôle la vitesse, le ton et l'inflexion de la voix.</span><span class="sxs-lookup"><span data-stu-id="8aa20-109">SSML controls the speed, tone, and inflection of the speech.</span></span>  <span data-ttu-id="8aa20-110">Il vous permet même de diffuser de l'audio ou de restituer un flux audio TTS à partir de votre propre service, ce qui vous confère une grande flexibilité pour la personnalisation.</span><span class="sxs-lookup"><span data-stu-id="8aa20-110">It even allows you to stream audio or a render a TTS audio stream from your own service, giving you a great deal of flexibility for customization.</span></span>

<span data-ttu-id="8aa20-111">La propriété Speak peut être utilisée par une application hôte selon deux modèles :</span><span class="sxs-lookup"><span data-stu-id="8aa20-111">There are two patterns for speak property usage by a host application:</span></span>

* <span data-ttu-id="8aa20-112">**À la livraison** : lors de la livraison d'une carte, le client peut choisir de lire la propriété Speak pour obtenir une description de la carte dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="8aa20-112">**On delivery** - When a card is delivered, the client may opt to read the Speak property for the card to describe the card as a whole.</span></span>
* <span data-ttu-id="8aa20-113">**À la demande** : afin de prendre en charge un modèle d'accessibilité plus riche, le schéma prend en charge une balise Speak pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="8aa20-113">**On demand** - In order to support a richer accessibility model, the schema supports a speak tag for each element.</span></span> <span data-ttu-id="8aa20-114">Le client peut lire une propriété Speak pour chaque élément de la carte.</span><span class="sxs-lookup"><span data-stu-id="8aa20-114">The client may read a Speak property  for each element in the card.</span></span>

### <a name="examples"></a><span data-ttu-id="8aa20-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="8aa20-115">Examples</span></span>

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a><span data-ttu-id="8aa20-116">Création de contenu de reconnaissance vocale</span><span class="sxs-lookup"><span data-stu-id="8aa20-116">Speech content design</span></span>

<span data-ttu-id="8aa20-117">Le contenu conçu pour la reconnaissance vocale est différent de celui conçu pour l'affichage visuel.</span><span class="sxs-lookup"><span data-stu-id="8aa20-117">Content designed for speech is different from content designed for visual display.</span></span> <span data-ttu-id="8aa20-118">Lorsque vous concevez une carte, vous concevez une expérience visuelle complète afin de présenter les informations à l'utilisateur sous une forme agréable.</span><span class="sxs-lookup"><span data-stu-id="8aa20-118">When you design a card, you are designing an entire visual experience to present information to a user in a way that delights them.</span></span> <span data-ttu-id="8aa20-119">Lors de la création de contenu pour la reconnaissance vocale, vous devez également réfléchir à la façon de décrire verbalement le contenu sous une forme plaisante pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8aa20-119">When designing for speech, you should think about how to verbally describe the content in a way that delights the user.</span></span>  
