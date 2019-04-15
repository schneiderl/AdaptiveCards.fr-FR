---
title: Fonctionnalités de texte
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: ac8ec0c48e06377ebd17f1b31abe463c48809fe3
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553611"
---
# <a name="text-features"></a>Fonctionnalités de texte

`TextBlock` offre certaines fonctionnalités avancées pour la mise en forme et de la localisation du texte.

## <a name="markdown"></a>Markdown
Pour prendre en charge les balises inline, prennent en charge des cartes adaptatives un **sous-ensemble** de syntaxe Markdown.

_Prise en charge_

| Style de texte      | Markdown |
|-----------------|-----|
| **Gras**        | ```**Bold**``` |
| _Italique_        | ```_Italic_``` |
| Liste à puces     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Liste numérotée   | ```1. Green\r2. Orange\r3. Blue``` |
| Liens hypertexte      | ```[Title](url)``` |

_Non pris en charge_

* En-têtes
* Tables
* Images
* Quoi que ce soit pas dans le tableau ci-dessus

### <a name="markdown-example"></a>Exemple de markdown

Le ci-dessous charge utile rendrait quelque chose comme ceci :

![capture d’écran de markdown](media/text-features/markdown.png)

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Mise en forme de date/heure et la localisation

Parfois, vous ne savez pas le fuseau horaire de l’utilisateur recevant la carte, pour que des cartes adaptatives propose `DATE()` et `TIME()` mise en forme de fonctions pour localiser automatiquement l’heure sur l’appareil cible.

### <a name="datetime-example"></a>Exemple de date/heure

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "Your package will arrive on {{DATE(2017-02-14T06:00:00Z, SHORT)}} at {{TIME(2017-02-14T06:00:00Z)}}",
            "wrap": true
        }
    ]
}
```

Affiche la carte ci-dessus : 

> **Votre package arrivent sur le mardi 14 février 2017 à 6 h 00**

### <a name="datetime-function-rules"></a>Règles des fonctions de date/heure

Il existe des règles pour l’interpréter correctement la les fonctions de date/heure sur toutes les plateformes. Si les règles ne sont pas remplies, la chaîne brute s’affichera à l’utilisateur, et personne ne veut que.

1. **CASSE** (doit être le tout en majuscules)
1. **Aucun espace** entre le `{{`, `}}`, ou de parenthèses
1. **STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) mise en forme** (voir les exemples ci-dessous)
1. **DOIT être** une date et heure valides

### <a name="valid-formats"></a>Formats valides

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Date de mise en forme param

Pour les dates, un paramètre facultatif peut être spécifié pour mettre en forme la sortie.


|       Format        |            Exemple            |
|---------------------|-------------------------------|
| `COMPACT` (Valeur par défaut) |          "2/13/2017"          |
|       `SHORT`       |     « Lundi 13 février 2017 »     |
|       `LONG`        | « Lundi 13 février 2017 » |

