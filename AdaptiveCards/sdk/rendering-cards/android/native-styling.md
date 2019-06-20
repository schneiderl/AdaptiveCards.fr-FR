---
title: Style natif – Kit de développement logiciel (SDK) Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: ebb033c68b9aedcaacb1989ffb1bec48707a9026
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134247"
---
# <a name="native-styling---android"></a><span data-ttu-id="0fef8-102">Style natif – Android</span><span class="sxs-lookup"><span data-stu-id="0fef8-102">Native styling - Android</span></span>

<span data-ttu-id="0fef8-103">Le style natif n’est pas pris en charge sur le convertisseur Android. La version v1.2 introduit la prise en charge du style de certaines propriétés :</span><span class="sxs-lookup"><span data-stu-id="0fef8-103">Native styling is not supported on the android renderer, v1.2 introduces the support for styling some properties:</span></span>

## <a name="action-sentiment"></a><span data-ttu-id="0fef8-104">Sentiment d’action</span><span class="sxs-lookup"><span data-stu-id="0fef8-104">Action Sentiment</span></span>

<span data-ttu-id="0fef8-105">Le sentiment d’action est inclus dans la version **v1.2** et, même s’il ne prend pas en charge autant de styles que les autres versions, un style peut être appliqué à des actions associées à un sentiment *destructif* ou *positif* en implémentant un style valide et en ajoutant la ligne suivante dans le fichier styles.xml de votre projet.</span><span class="sxs-lookup"><span data-stu-id="0fef8-105">Action sentiment is included in **v1.2** and while not supporting as many styles as other versions, actions with *destructive* or *positive* sentiment can be styled by implementing a valid style and adding the following line into the styles.xml for your project</span></span>

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a><span data-ttu-id="0fef8-106">Action incorporée</span><span class="sxs-lookup"><span data-stu-id="0fef8-106">Inline Action</span></span>

<span data-ttu-id="0fef8-107">Des entrées de texte avec une action incorporée permettent d’appliquer un style à l’action dont le rendu est effectué.</span><span class="sxs-lookup"><span data-stu-id="0fef8-107">Text inputs with an inline action allows styling for the action being rendered.</span></span> <span data-ttu-id="0fef8-108">Cela permet d’appliquer un style à l’action, tel qu’un bouton (adaptiveInlineAction) ou une image (adaptiveInlineActionImage).</span><span class="sxs-lookup"><span data-stu-id="0fef8-108">This allows styling the action as a button (adaptiveInlineAction) or as an image (adaptiveInlineActionImage)</span></span>

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> <span data-ttu-id="0fef8-109">Tous les noms d’éléments doivent être conservés comme indiqué ici, car le convertisseur recherche ces noms précis.</span><span class="sxs-lookup"><span data-stu-id="0fef8-109">All item names must be kept as shown here as the renderer looks for those exact names</span></span>
