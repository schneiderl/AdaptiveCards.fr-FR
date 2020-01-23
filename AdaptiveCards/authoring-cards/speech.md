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
# <a name="speech-and-advanced-customization"></a>Reconnaissance vocale et personnalisation avancée
Nous vivons à une époque d'interaction vocale grâce à des services tels que Cortana.  Dès le premier jour, les cartes adaptatives sont conçues pour prendre en charge la reconnaissance vocale, ce qui permet de créer de nouveaux scénarios mains libres.

La balise `speak` permet à la carte adaptative d'être distribuée dans un environnement où l'affichage visuel ne constitue pas l'expérience principale, comme un tableau de bord de voiture au volant. 

## <a name="speak-property"></a>Propriété Speak
Pour prendre en charge la reconnaissance vocale, nous disposons d'une propriété `speak` qui contient du texte à dire à l'utilisateur. Le texte peut être annoté en langage [SSML](https://msdn.microsoft.com/library/office/hh361578) (Speech Synthesis Markup Language). SSML contrôle la vitesse, le ton et l'inflexion de la voix.  Il vous permet même de diffuser de l'audio ou de restituer un flux audio TTS à partir de votre propre service, ce qui vous confère une grande flexibilité pour la personnalisation.

La propriété Speak peut être utilisée par une application hôte selon deux modèles :

* **À la livraison** : lors de la livraison d'une carte, le client peut choisir de lire la propriété Speak pour obtenir une description de la carte dans son ensemble.
* **À la demande** : afin de prendre en charge un modèle d'accessibilité plus riche, le schéma prend en charge une balise Speak pour chaque élément. Le client peut lire une propriété Speak pour chaque élément de la carte.

### <a name="examples"></a>Exemples

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Création de contenu de reconnaissance vocale

Le contenu conçu pour la reconnaissance vocale est différent de celui conçu pour l'affichage visuel. Lorsque vous concevez une carte, vous concevez une expérience visuelle complète afin de présenter les informations à l'utilisateur sous une forme agréable. Lors de la création de contenu pour la reconnaissance vocale, vous devez également réfléchir à la façon de décrire verbalement le contenu sous une forme plaisante pour l'utilisateur.  
