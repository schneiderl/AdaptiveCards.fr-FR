---
title: Stylisation Native-Kit de développement logiciel (SDK) iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f9ed839a19ac778381fa36361ad37e95b7ab5e08
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727471"
---
# <a name="native-styling---ios"></a>Stylisation Native-iOS

Utilisez XIB pour un style affiné.

Les XIB suivants existent

| XIB | Utilisation |
|---|---|
| ACRButton. XIB | boutons |
| ACRCellForCompactMode. XIB   | Mode compact ChoiceSet|
| ACRDatePicker. XIB | DatePicker pour Input. date |
| ACRDateTextField. XIB  | TextField pour Input. date |
| ACRInputTableView. XIB   | Conteneur pour les entrées |
| ACRLabelView. XIB  | TextBlock |
| ACRPickerView. XIB | ChoiceSet |
| ACRQuickActionMultilineView. XIB  | Actions rapides avec des lignes multilignes |
| ACRQuickActionView. XIB | Actions rapides |
| ACRTextField. XIB | Entrée |

XIB peut être modifié à l’aide de XCode IB.
Une fois les XIB modifiés dans la spécification.
À partir d’un terminal
```
ibtool --compile name.nib name.xib 
```

Par exemple, pour le style d’un bouton
```
ibtool --compile ACRButton.nib ACRButton.xib 
```

Les fichiers de plume générés peuvent être ensuite remplacés à AdaptiveCards. Framework
