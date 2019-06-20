---
title: Kit de développement logiciel (SDK) Android
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: b5f1279317e6b34d2e3bccee2625d972ac185e04
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67134277"
---
# <a name="getting-started---android"></a>Prise en main – Android

Ceci est un convertisseur qui cible les contrôles natifs Android.

## <a name="install-maven-package"></a>Installer le package Maven

[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Vous pouvez trouver les packages publiés ![ici](https://search.maven.org/search?q=g:io.adaptivecards)

Pour inclure une bibliothèque dans votre projet, vous devez inclure cette ligne dans le gradle.build de votre projet, dans la section dependencies :

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
Vous devez modifier le numéro de version en fonction de la version que vous souhaitez inclure dans votre projet.

## <a name="add-import"></a>Ajouter une importation

Pour inclure le modèle d’objet, ajoutez cette importation :

```
 import io.adaptivecards.objectmodel.*;
```

Pour inclure le convertisseur, ajoutez cette importation :

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>Étapes suivantes

Pour les prochaines étapes, voir [Effectuer le rendu d’une carte](render-a-card.md).
