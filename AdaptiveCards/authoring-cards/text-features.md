---
title: Fonctionnalités de texte
author: matthidinger
ms.author: mahiding
ms.date: 11/09/2017
ms.topic: article
ms.openlocfilehash: f7ea40b80df4d976c0a8a86b15254018fdf2fac6
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454872"
---
# <a name="text-features"></a><span data-ttu-id="75c41-102">Fonctionnalités de texte</span><span class="sxs-lookup"><span data-stu-id="75c41-102">Text features</span></span>

<span data-ttu-id="75c41-103">`TextBlock` propose des fonctionnalités avancées pour la mise en forme et la localisation du texte.</span><span class="sxs-lookup"><span data-stu-id="75c41-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="75c41-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="75c41-104">Markdown</span></span>
<span data-ttu-id="75c41-105">Pour prendre en charge les marques de révision incluses, les cartes adaptatives prennent en charge un **sous-ensemble** de la syntaxe Markdown.</span><span class="sxs-lookup"><span data-stu-id="75c41-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="75c41-106">_Pris en charge_</span><span class="sxs-lookup"><span data-stu-id="75c41-106">_Supported_</span></span>

| <span data-ttu-id="75c41-107">Style de texte</span><span class="sxs-lookup"><span data-stu-id="75c41-107">Text Style</span></span>      | <span data-ttu-id="75c41-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="75c41-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="75c41-109">**Gras**</span><span class="sxs-lookup"><span data-stu-id="75c41-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="75c41-110">_Italique_</span><span class="sxs-lookup"><span data-stu-id="75c41-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="75c41-111">Liste à puces</span><span class="sxs-lookup"><span data-stu-id="75c41-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="75c41-112">Liste numérotée</span><span class="sxs-lookup"><span data-stu-id="75c41-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="75c41-113">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="75c41-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="75c41-114">_Non pris en charge_</span><span class="sxs-lookup"><span data-stu-id="75c41-114">_Not supported_</span></span>

* <span data-ttu-id="75c41-115">En-têtes</span><span class="sxs-lookup"><span data-stu-id="75c41-115">Headers</span></span>
* <span data-ttu-id="75c41-116">Tableaux</span><span class="sxs-lookup"><span data-stu-id="75c41-116">Tables</span></span>
* <span data-ttu-id="75c41-117">Images</span><span class="sxs-lookup"><span data-stu-id="75c41-117">Images</span></span>
* <span data-ttu-id="75c41-118">Tout ce qui ne figure pas dans le tableau ci-dessus</span><span class="sxs-lookup"><span data-stu-id="75c41-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="75c41-119">Exemple Markdown</span><span class="sxs-lookup"><span data-stu-id="75c41-119">Markdown Example</span></span>

<span data-ttu-id="75c41-120">Le résultat de la charge utile ci-dessous serait semblable à :</span><span class="sxs-lookup"><span data-stu-id="75c41-120">The below payload would render something like this:</span></span>

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
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="75c41-122">Mise en forme et localisation de la date/heure</span><span class="sxs-lookup"><span data-stu-id="75c41-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="75c41-123">Vous ne connaissez pas toujours le fuseau horaire de l'utilisateur qui reçoit la carte. La fonctionnalité Cartes adaptatives propose donc des fonctions de mise en forme `DATE()` et `TIME()` pour localiser automatiquement la date et l'heure sur l'appareil cible.</span><span class="sxs-lookup"><span data-stu-id="75c41-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="75c41-124">Exemple de date/heure</span><span class="sxs-lookup"><span data-stu-id="75c41-124">Date/Time Example</span></span>

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

<span data-ttu-id="75c41-125">La carte ci-dessus affichera :</span><span class="sxs-lookup"><span data-stu-id="75c41-125">The above card will display:</span></span> 

> <span data-ttu-id="75c41-126">**Votre colis arrivera le mar 14 fév 2017 à 6h00**</span><span class="sxs-lookup"><span data-stu-id="75c41-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="75c41-127">Règles relatives aux fonctions Date/Heure</span><span class="sxs-lookup"><span data-stu-id="75c41-127">Date/Time function rules</span></span>

<span data-ttu-id="75c41-128">Il existe des règles pour interpréter correctement les fonctions Date/Heure sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="75c41-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="75c41-129">Si ces règles ne sont pas respectées, l'utilisateur verra la chaîne brute, ce qui n'est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="75c41-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="75c41-130">**SENSIBLE À LA CASSE** (tout en majuscules)</span><span class="sxs-lookup"><span data-stu-id="75c41-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="75c41-131">**AUCUN ESPACE** entre les accolades `{{` et `}}`, ou entre les parenthèses</span><span class="sxs-lookup"><span data-stu-id="75c41-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="75c41-132">**MISE EN FORME [RFC 3389](https://tools.ietf.org/html/rfc3339) STRICTE** (voir exemples ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="75c41-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="75c41-133">La date et l'heure **DOIVENT ÊTRE** valides</span><span class="sxs-lookup"><span data-stu-id="75c41-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="75c41-134">Formats valides</span><span class="sxs-lookup"><span data-stu-id="75c41-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="75c41-135">Paramètre de mise en forme de date</span><span class="sxs-lookup"><span data-stu-id="75c41-135">Date formatting param</span></span>

<span data-ttu-id="75c41-136">Pour les dates, un paramètre de mise en forme facultatif peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="75c41-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="75c41-137">Format</span><span class="sxs-lookup"><span data-stu-id="75c41-137">Format</span></span>        |            <span data-ttu-id="75c41-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="75c41-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="75c41-139">`COMPACT` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="75c41-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="75c41-140">« 13/02/2017 »</span><span class="sxs-lookup"><span data-stu-id="75c41-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="75c41-141">« Lun 13 fév 2017 »</span><span class="sxs-lookup"><span data-stu-id="75c41-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="75c41-142">« Lundi 13 février 2017 »</span><span class="sxs-lookup"><span data-stu-id="75c41-142">"Monday, February 13th, 2017"</span></span> |

