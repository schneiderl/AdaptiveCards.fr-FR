---
title: Style natif – Kit de développement logiciel (SDK) Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 8d5dd9bbf17800c55aae1d416b7e6d80ac697b25
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417612"
---
# <a name="native-styling---android"></a><span data-ttu-id="84ea4-102">Style natif – Android</span><span class="sxs-lookup"><span data-stu-id="84ea4-102">Native styling - Android</span></span>

<span data-ttu-id="84ea4-103">Le style natif n’est pas pris en charge sur le convertisseur Android. La version v1.2 introduit la prise en charge du style de certaines propriétés :</span><span class="sxs-lookup"><span data-stu-id="84ea4-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="84ea4-104">Sentiment d’action</span><span class="sxs-lookup"><span data-stu-id="84ea4-104">Action Sentiment</span></span>

<span data-ttu-id="84ea4-105">Le sentiment d’action est inclus dans la version **v1.2** et, même s’il ne prend pas en charge autant de styles que les autres versions, un style peut être appliqué à des actions associées à un sentiment *destructif* ou *positif* en implémentant un style valide et en ajoutant la ligne suivante dans le fichier styles.xml de votre projet.</span><span class="sxs-lookup"><span data-stu-id="84ea4-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="84ea4-106">Action incorporée</span><span class="sxs-lookup"><span data-stu-id="84ea4-106">Inline Action</span></span>

<span data-ttu-id="84ea4-107">Des entrées de texte avec une action incorporée permettent d’appliquer un style à l’action dont le rendu est effectué.</span><span class="sxs-lookup"><span data-stu-id="84ea4-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="84ea4-108">Cela permet d’appliquer un style à l’action, tel qu’un bouton (adaptiveInlineAction) ou une image (adaptiveInlineActionImage).</span><span class="sxs-lookup"><span data-stu-id="84ea4-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="84ea4-109">Tous les noms d’éléments doivent être conservés comme indiqué ici, car le convertisseur recherche ces noms précis.</span><span class="sxs-lookup"><span data-stu-id="84ea4-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>

## <a name="actionshowcard"></a><span data-ttu-id="84ea4-110">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="84ea4-110">Action.ShowCard</span></span>

<span data-ttu-id="84ea4-111">Vous pouvez appliquer un style à action. ShowCard en ajoutant des styles à votre thème dans styles.xml.</span><span class="sxs-lookup"><span data-stu-id="84ea4-111">Action.ShowCard can be styled by adding styles to your theme in styles.xml.</span></span>

```styles.xml
 <item name="adaptiveShowCardAction">@style/adaptiveShowCardAction</item>
```