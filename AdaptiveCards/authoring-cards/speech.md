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
# <a name="speech-and-advanced-customization"></a>Reconnaissance vocale et la personnalisation avancée
Nous vivons dans une ère d’interaction vocale via des services tels que Cortana.  Des cartes adaptatives sont conçues dès le premier jour pour prendre en charge la reconnaissance vocale, l’activation de nouveaux scénarios de mains-full froids.

Le `speak` balise permet à la carte adaptative à être remis à un environnement où un affichage visuel n’est pas une expérience principale, comme à un tableau de bord de voiture tout en garantissant. 

## <a name="speak-property"></a>Parlez de propriété
Pour prendre en charge la reconnaissance vocale que nous avons un `speak` propriété qui contient le texte à dire à l’utilisateur. Le texte peut être annoté à l’aide du langage de balisage de synthèse vocale ([SSML](https://msdn.microsoft.com/en-us/library/office/hh361578)). SSML contrôle la vitesse, le ton et inflexion de la reconnaissance vocale.  Il permet même vous à diffuser des flux audio ou d’un rendu un flux audio de synthèse vocale à partir de votre propre service, ce qui vous donne une grande souplesse pour la personnalisation.

Il existe deux modèles pour parlent de l’utilisation de propriété par une application hôte :

* **Sur la distribution** : quand une carte est remise, le client peut choisir de lire la propriété de lecture de la carte décrire la carte dans sa globalité.
* **À la demande** - pour prendre en charge un modèle plus riche d’accessibilité, le prend en charge du schéma une lecture de balise pour chaque élément. Le client peut lire une propriété de lecture pour chaque élément dans la carte.

### <a name="examples"></a>Exemples

```json
    "speak":"hello world!"

    "speak":"<s>This is sentence 1.</s><s>This is sentence two</s>"

    "speak":"<speak><audio src='https://www.soundjay.com/misc/bell-ringing-04.mp3'/><s>Time to wake up!</s></speak>"
```

## <a name="speech-content-design"></a>Création de contenu de reconnaissance vocale

Contenu conçu pour la voix est différent du contenu conçu pour l’affichage. Lorsque vous concevez une carte, vous concevez une expérience visuelle entière pour présenter des informations à un utilisateur d’une manière qui les delights. Lors de la conception pour la reconnaissance vocale, vous devez considérer comment verbalement décrire le contenu d’une manière qui delights l’utilisateur.  
