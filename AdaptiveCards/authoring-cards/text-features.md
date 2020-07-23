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
# <a name="text-features"></a><span data-ttu-id="c4684-102">Fonctionnalités de texte</span><span class="sxs-lookup"><span data-stu-id="c4684-102">Text features</span></span>

<span data-ttu-id="c4684-103">[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) propose des fonctionnalités avancées pour la mise en forme et la localisation du texte.</span><span class="sxs-lookup"><span data-stu-id="c4684-103">[TextBlock](https://adaptivecards.io/explorer/TextBlock.html) offers advanced features for formatting and localizing the text.</span></span>

## <a name="markdown-commonmark-subset"></a><span data-ttu-id="c4684-104">Markdown (sous-ensemble Commonmark)</span><span class="sxs-lookup"><span data-stu-id="c4684-104">Markdown (Commonmark subset)</span></span>

<span data-ttu-id="c4684-105">Pour prendre en charge le balisage inline, les cartes adaptatives prennent en charge un **sous-ensemble** de la syntaxe Markdown [Commonmark](https://commonmark.org/help/).</span><span class="sxs-lookup"><span data-stu-id="c4684-105">To support inline markup, Adaptive Cards support a **subset** of the [Commonmark](https://commonmark.org/help/) Markdown syntax.</span></span>

> [!NOTE]
>
> <span data-ttu-id="c4684-106">[RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) ne prend pas en charge Markdown, mais offre un large choix d’options de configuration de texte directement dans le [TextRun](https://adaptivecards.io/explorer/TextRun.html)</span><span class="sxs-lookup"><span data-stu-id="c4684-106">[RichTextBlock](https://adaptivecards.io/explorer/RichTextBlock.html) does not support markdown, but offers a wide array of text configuration options directly within the the [TextRun](https://adaptivecards.io/explorer/TextRun.html)</span></span>

<span data-ttu-id="c4684-107">_Pris en charge_</span><span class="sxs-lookup"><span data-stu-id="c4684-107">_Supported_</span></span>

| <span data-ttu-id="c4684-108">Style de texte</span><span class="sxs-lookup"><span data-stu-id="c4684-108">Text Style</span></span>      | <span data-ttu-id="c4684-109">Markdown</span><span class="sxs-lookup"><span data-stu-id="c4684-109">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="c4684-110">**Gras**</span><span class="sxs-lookup"><span data-stu-id="c4684-110">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="c4684-111">_Italique_</span><span class="sxs-lookup"><span data-stu-id="c4684-111">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="c4684-112">Liste à puces</span><span class="sxs-lookup"><span data-stu-id="c4684-112">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="c4684-113">Liste numérotée</span><span class="sxs-lookup"><span data-stu-id="c4684-113">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="c4684-114">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="c4684-114">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="c4684-115">_Non pris en charge_</span><span class="sxs-lookup"><span data-stu-id="c4684-115">_Not supported_</span></span>

* <span data-ttu-id="c4684-116">En-têtes</span><span class="sxs-lookup"><span data-stu-id="c4684-116">Headers</span></span>
* <span data-ttu-id="c4684-117">Tableaux</span><span class="sxs-lookup"><span data-stu-id="c4684-117">Tables</span></span>
* <span data-ttu-id="c4684-118">Images</span><span class="sxs-lookup"><span data-stu-id="c4684-118">Images</span></span>
* <span data-ttu-id="c4684-119">Tout ce qui ne figure pas dans le tableau ci-dessus</span><span class="sxs-lookup"><span data-stu-id="c4684-119">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="c4684-120">Exemple Markdown</span><span class="sxs-lookup"><span data-stu-id="c4684-120">Markdown Example</span></span>

<span data-ttu-id="c4684-121">Le résultat de la charge utile ci-dessous serait semblable à :</span><span class="sxs-lookup"><span data-stu-id="c4684-121">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="c4684-123">Mise en forme et localisation de la date/heure</span><span class="sxs-lookup"><span data-stu-id="c4684-123">Date/Time formatting and localization</span></span>

<span data-ttu-id="c4684-124">Vous ne connaissez pas toujours le fuseau horaire de l'utilisateur qui reçoit la carte. La fonctionnalité Cartes adaptatives propose donc des fonctions de mise en forme `DATE()` et `TIME()` pour localiser automatiquement la date et l'heure sur l'appareil cible.</span><span class="sxs-lookup"><span data-stu-id="c4684-124">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="c4684-125">Exemple de date/heure</span><span class="sxs-lookup"><span data-stu-id="c4684-125">Date/Time Example</span></span>

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

<span data-ttu-id="c4684-126">La carte ci-dessus affichera :</span><span class="sxs-lookup"><span data-stu-id="c4684-126">The above card will display:</span></span> 

> <span data-ttu-id="c4684-127">**Votre colis arrivera le mar 14 fév 2017 à 6h00**</span><span class="sxs-lookup"><span data-stu-id="c4684-127">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="c4684-128">Règles relatives aux fonctions Date/Heure</span><span class="sxs-lookup"><span data-stu-id="c4684-128">Date/Time function rules</span></span>

<span data-ttu-id="c4684-129">Il existe des règles pour interpréter correctement les fonctions Date/Heure sur chaque plateforme.</span><span class="sxs-lookup"><span data-stu-id="c4684-129">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="c4684-130">Si ces règles ne sont pas respectées, l'utilisateur verra la chaîne brute, ce qui n'est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="c4684-130">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="c4684-131">**SENSIBLE À LA CASSE** (tout en majuscules)</span><span class="sxs-lookup"><span data-stu-id="c4684-131">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="c4684-132">**AUCUN ESPACE** entre les accolades `{{` et `}}`, ou entre les parenthèses</span><span class="sxs-lookup"><span data-stu-id="c4684-132">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="c4684-133">**MISE EN FORME [RFC 3389](https://tools.ietf.org/html/rfc3339) STRICTE** (voir exemples ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="c4684-133">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="c4684-134">La date et l'heure **DOIVENT ÊTRE** valides</span><span class="sxs-lookup"><span data-stu-id="c4684-134">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="c4684-135">Formats valides</span><span class="sxs-lookup"><span data-stu-id="c4684-135">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="c4684-136">Paramètre de mise en forme de date</span><span class="sxs-lookup"><span data-stu-id="c4684-136">Date formatting param</span></span>

<span data-ttu-id="c4684-137">Pour les dates, un paramètre de mise en forme facultatif peut être spécifié.</span><span class="sxs-lookup"><span data-stu-id="c4684-137">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="c4684-138">Format</span><span class="sxs-lookup"><span data-stu-id="c4684-138">Format</span></span>        |            <span data-ttu-id="c4684-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4684-139">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="c4684-140">`COMPACT` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="c4684-140">`COMPACT` (Default)</span></span> |          <span data-ttu-id="c4684-141">« 13/02/2017 »</span><span class="sxs-lookup"><span data-stu-id="c4684-141">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="c4684-142">« Lun 13 fév 2017 »</span><span class="sxs-lookup"><span data-stu-id="c4684-142">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="c4684-143">« Lundi 13 février 2017 »</span><span class="sxs-lookup"><span data-stu-id="c4684-143">"Monday, February 13th, 2017"</span></span> |

