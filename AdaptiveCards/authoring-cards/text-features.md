---
title: Fonctionnalités de texte
author: matthidinger
ms.author: mahiding
ms.date: 06/18/2020
ms.topic: article
ms.openlocfilehash: d685007cb24e7fa8ef15b53ee5547708fba6b490
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417504"
---
# <a name="text-features"></a>Fonctionnalités de texte

[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) propose des fonctionnalités avancées pour la mise en forme et la localisation du texte.

## <a name="markdown-commonmark-subset"></a>Markdown (sous-ensemble Commonmark)

Pour prendre en charge le balisage inline, les cartes adaptatives prennent en charge un **sous-ensemble** de la syntaxe Markdown [Commonmark](https://commonmark.org/help/).

> [!NOTE]
>
> [RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) ne prend pas en charge Markdown, mais offre un large choix d’options de configuration de texte directement dans le [TextRun](https://adaptivecards.io/explorer/TextRun.html)

_Pris en charge_

| Style de texte      | Markdown |
|-----------------|-----|
| **Gras**        | ```**Bold**``` |
| _Italique_        | ```_Italic_``` |
| Liste à puces     | ```- Item 1\r- Item 2\r- Item 3``` | 
| Liste numérotée   | ```1. Green\r2. Orange\r3. Blue``` |
| Liens hypertexte      | ```[Title](url)``` |

_Non pris en charge_

* En-têtes
* Tableaux
* Images
* Tout ce qui ne figure pas dans le tableau ci-dessus

### <a name="markdown-example"></a>Exemple Markdown

Le résultat de la charge utile ci-dessous serait semblable à :

![capture d'écran Markdown](media/text-features/markdown.png)

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
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a>Mise en forme et localisation de la date/heure

Vous ne connaissez pas toujours le fuseau horaire de l'utilisateur qui reçoit la carte. La fonctionnalité Cartes adaptatives propose donc des fonctions de mise en forme `DATE()` et `TIME()` pour localiser automatiquement la date et l'heure sur l'appareil cible.

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

La carte ci-dessus affichera : 

> **Votre colis arrivera le mar 14 fév 2017 à 6h00**

### <a name="datetime-function-rules"></a>Règles relatives aux fonctions Date/Heure

Il existe des règles pour interpréter correctement les fonctions Date/Heure sur chaque plateforme. Si ces règles ne sont pas respectées, l'utilisateur verra la chaîne brute, ce qui n'est pas souhaitable.

1. **SENSIBLE À LA CASSE** (tout en majuscules)
1. **AUCUN ESPACE** entre les accolades `{{` et `}}`, ou entre les parenthèses
1. **MISE EN FORME [RFC 3389](https://tools.ietf.org/html/rfc3339) STRICTE** (voir exemples ci-dessous)
1. La date et l'heure **DOIVENT ÊTRE** valides

### <a name="valid-formats"></a>Formats valides

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a>Paramètre de mise en forme de date

Pour les dates, un paramètre de mise en forme facultatif peut être spécifié.


|       Format        |            Exemple            |
|---------------------|-------------------------------|
| `COMPACT` (par défaut) |          « 13/02/2017 »          |
|       `SHORT`       |     « Lun 13 fév 2017 »     |
|       `LONG`        | « Lundi 13 février 2017 » |

