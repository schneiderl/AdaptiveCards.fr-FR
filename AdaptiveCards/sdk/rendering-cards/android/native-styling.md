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
# <a name="native-styling---android"></a>Style natif – Android

Le style natif n’est pas pris en charge sur le convertisseur Android. La version v1.2 introduit la prise en charge du style de certaines propriétés :

## <a name="action-sentiment"></a>Sentiment d’action

Le sentiment d’action est inclus dans la version **v1.2** et, même s’il ne prend pas en charge autant de styles que les autres versions, un style peut être appliqué à des actions associées à un sentiment *destructif* ou *positif* en implémentant un style valide et en ajoutant la ligne suivante dans le fichier styles.xml de votre projet.

```styles.xml
 <item name="adaptiveActionDestructive">@style/adaptiveActionDestructive</item>
 <item name="adaptiveActionPositive">@style/adaptiveActionPositive</item>
```

## <a name="inline-action"></a>Action incorporée

Des entrées de texte avec une action incorporée permettent d’appliquer un style à l’action dont le rendu est effectué. Cela permet d’appliquer un style à l’action, tel qu’un bouton (adaptiveInlineAction) ou une image (adaptiveInlineActionImage).

```styles.xml
 <item name="adaptiveInlineAction">@style/adaptiveInlineAction</item>
 <item name="adaptiveInlineActionImage">@style/adaptiveInlineActionImage</item>
```

> [!IMPORTANT]
> Tous les noms d’éléments doivent être conservés comme indiqué ici, car le convertisseur recherche ces noms précis.
