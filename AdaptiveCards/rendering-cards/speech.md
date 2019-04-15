---
title: Gestion des voix
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: daea48607376c84f0e0f0af9450cac7dcdf67c0e
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552481"
---
# <a name="handling-speech"></a>Gestion des voix

En parole prise en charge des cartes adaptatives a le `speak` propriété qui contient des informations sur la façon dont une carte doit être lue à haute voix à un utilisateur.

La balise de reconnaissance vocale peut être annotée à l’aide de [un balisage SSML](https://msdn.microsoft.com/en-us/library/office/hh361578(v=office.14).aspx). SSML vous donne le contrôle la vitesse, le ton, de la capacité inflexion de la reconnaissance vocale.  Il permet même vous à diffuser des flux audio ou d’un rendu un flux audio de synthèse vocale à partir de votre propre service, ce qui vous donne une grande quantité de personnalisation.

Il existe 2 modèles pour parlent de l’utilisation de propriété par une application hôte :
* **sur la distribution** : quand une carte est remise à un client peut choisir de lire la propriété de lecture de la carte décrire la carte dans sa globalité.
* **à la demande** - pour prendre en charge un modèle d’accessibilité plus riche le prend en charge du schéma une lecture de balise par élément.  
Cela permet aux clients de lire chaque élément aux destinataires avec des normes d’accessibilité.

