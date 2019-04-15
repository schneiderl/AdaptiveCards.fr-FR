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
# <a name="text-features"></a><span data-ttu-id="c533b-102">Fonctionnalités de texte</span><span class="sxs-lookup"><span data-stu-id="c533b-102">Text features</span></span>

<span data-ttu-id="c533b-103">`TextBlock` offre certaines fonctionnalités avancées pour la mise en forme et de la localisation du texte.</span><span class="sxs-lookup"><span data-stu-id="c533b-103">`TextBlock` offers some advanced features for formatting and localizing the text.</span></span>

## <a name="markdown"></a><span data-ttu-id="c533b-104">Markdown</span><span class="sxs-lookup"><span data-stu-id="c533b-104">Markdown</span></span>
<span data-ttu-id="c533b-105">Pour prendre en charge les balises inline, prennent en charge des cartes adaptatives un **sous-ensemble** de syntaxe Markdown.</span><span class="sxs-lookup"><span data-stu-id="c533b-105">To support inline markup, Adaptive Cards support a **subset** of Markdown syntax.</span></span>

<span data-ttu-id="c533b-106">_Prise en charge_</span><span class="sxs-lookup"><span data-stu-id="c533b-106">_Supported_</span></span>

| <span data-ttu-id="c533b-107">Style de texte</span><span class="sxs-lookup"><span data-stu-id="c533b-107">Text Style</span></span>      | <span data-ttu-id="c533b-108">Markdown</span><span class="sxs-lookup"><span data-stu-id="c533b-108">Markdown</span></span> |
|-----------------|-----|
| <span data-ttu-id="c533b-109">**Gras**</span><span class="sxs-lookup"><span data-stu-id="c533b-109">**Bold**</span></span>        | ```**Bold**``` |
| <span data-ttu-id="c533b-110">_Italique_</span><span class="sxs-lookup"><span data-stu-id="c533b-110">_Italic_</span></span>        | ```_Italic_``` |
| <span data-ttu-id="c533b-111">Liste à puces</span><span class="sxs-lookup"><span data-stu-id="c533b-111">Bullet list</span></span>     | ```- Item 1\r- Item 2\r- Item 3``` | 
| <span data-ttu-id="c533b-112">Liste numérotée</span><span class="sxs-lookup"><span data-stu-id="c533b-112">Numbered list</span></span>   | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="c533b-113">Liens hypertexte</span><span class="sxs-lookup"><span data-stu-id="c533b-113">Hyperlinks</span></span>      | ```[Title](url)``` |

<span data-ttu-id="c533b-114">_Non pris en charge_</span><span class="sxs-lookup"><span data-stu-id="c533b-114">_Not supported_</span></span>

* <span data-ttu-id="c533b-115">En-têtes</span><span class="sxs-lookup"><span data-stu-id="c533b-115">Headers</span></span>
* <span data-ttu-id="c533b-116">Tables</span><span class="sxs-lookup"><span data-stu-id="c533b-116">Tables</span></span>
* <span data-ttu-id="c533b-117">Images</span><span class="sxs-lookup"><span data-stu-id="c533b-117">Images</span></span>
* <span data-ttu-id="c533b-118">Quoi que ce soit pas dans le tableau ci-dessus</span><span class="sxs-lookup"><span data-stu-id="c533b-118">Anything not in the table above</span></span>

### <a name="markdown-example"></a><span data-ttu-id="c533b-119">Exemple de markdown</span><span class="sxs-lookup"><span data-stu-id="c533b-119">Markdown Example</span></span>

<span data-ttu-id="c533b-120">Le ci-dessous charge utile rendrait quelque chose comme ceci :</span><span class="sxs-lookup"><span data-stu-id="c533b-120">The below payload would render something like this:</span></span>

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

## <a name="datetime-formatting-and-localization"></a><span data-ttu-id="c533b-122">Mise en forme de date/heure et la localisation</span><span class="sxs-lookup"><span data-stu-id="c533b-122">Date/Time formatting and localization</span></span>

<span data-ttu-id="c533b-123">Parfois, vous ne savez pas le fuseau horaire de l’utilisateur recevant la carte, pour que des cartes adaptatives propose `DATE()` et `TIME()` mise en forme de fonctions pour localiser automatiquement l’heure sur l’appareil cible.</span><span class="sxs-lookup"><span data-stu-id="c533b-123">Sometimes you won't know the timezone of the user receiving the card, so Adaptive Cards offers `DATE()` and `TIME()` formatting functions to automatically localize the time on the target device.</span></span>

### <a name="datetime-example"></a><span data-ttu-id="c533b-124">Exemple de date/heure</span><span class="sxs-lookup"><span data-stu-id="c533b-124">Date/Time Example</span></span>

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

<span data-ttu-id="c533b-125">Affiche la carte ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="c533b-125">The above card will display:</span></span> 

> <span data-ttu-id="c533b-126">**Votre package arrivent sur le mardi 14 février 2017 à 6 h 00**</span><span class="sxs-lookup"><span data-stu-id="c533b-126">**Your package will arrive on Tue, Feb 14th, 2017 at 6:00 AM**</span></span>

### <a name="datetime-function-rules"></a><span data-ttu-id="c533b-127">Règles des fonctions de date/heure</span><span class="sxs-lookup"><span data-stu-id="c533b-127">Date/Time function rules</span></span>

<span data-ttu-id="c533b-128">Il existe des règles pour l’interpréter correctement la les fonctions de date/heure sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="c533b-128">There are some rules to properly interpret the the date/time functions on every platform.</span></span> <span data-ttu-id="c533b-129">Si les règles ne sont pas remplies, la chaîne brute s’affichera à l’utilisateur, et personne ne veut que.</span><span class="sxs-lookup"><span data-stu-id="c533b-129">If the rules aren't met then the raw string will be displayed to the user, and no one wants that.</span></span>

1. <span data-ttu-id="c533b-130">**CASSE** (doit être le tout en majuscules)</span><span class="sxs-lookup"><span data-stu-id="c533b-130">**CASE SENSITIVE** (must be all caps)</span></span>
1. <span data-ttu-id="c533b-131">**Aucun espace** entre le `{{`, `}}`, ou de parenthèses</span><span class="sxs-lookup"><span data-stu-id="c533b-131">**NO SPACES** between the `{{`, `}}`, or parentheses</span></span>
1. <span data-ttu-id="c533b-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) mise en forme** (voir les exemples ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="c533b-132">**STRICT [RFC 3389](https://tools.ietf.org/html/rfc3339) FORMATTING** (See examples below)</span></span>
1. <span data-ttu-id="c533b-133">**DOIT être** une date et heure valides</span><span class="sxs-lookup"><span data-stu-id="c533b-133">**MUST BE** a valid date and time</span></span>

### <a name="valid-formats"></a><span data-ttu-id="c533b-134">Formats valides</span><span class="sxs-lookup"><span data-stu-id="c533b-134">Valid formats</span></span>

* `2017-02-14T06:08:00Z`
* `2017-02-14T06:08:00-07:00`
* `2017-02-14T06:08:00+07:00`

### <a name="date-formatting-param"></a><span data-ttu-id="c533b-135">Date de mise en forme param</span><span class="sxs-lookup"><span data-stu-id="c533b-135">Date formatting param</span></span>

<span data-ttu-id="c533b-136">Pour les dates, un paramètre facultatif peut être spécifié pour mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="c533b-136">For dates, an optional param may be specified to format the output.</span></span>


|       <span data-ttu-id="c533b-137">Format</span><span class="sxs-lookup"><span data-stu-id="c533b-137">Format</span></span>        |            <span data-ttu-id="c533b-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="c533b-138">Example</span></span>            |
|---------------------|-------------------------------|
| <span data-ttu-id="c533b-139">`COMPACT` (Valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="c533b-139">`COMPACT` (Default)</span></span> |          <span data-ttu-id="c533b-140">"2/13/2017"</span><span class="sxs-lookup"><span data-stu-id="c533b-140">"2/13/2017"</span></span>          |
|       `SHORT`       |     <span data-ttu-id="c533b-141">« Lundi 13 février 2017 »</span><span class="sxs-lookup"><span data-stu-id="c533b-141">"Mon, Feb 13th, 2017"</span></span>     |
|       `LONG`        | <span data-ttu-id="c533b-142">« Lundi 13 février 2017 »</span><span class="sxs-lookup"><span data-stu-id="c533b-142">"Monday, February 13th, 2017"</span></span> |

