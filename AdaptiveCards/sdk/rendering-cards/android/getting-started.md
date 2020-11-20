---
title: Kit de développement logiciel (SDK) Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 864bb96c5875365845f7b9a7955b8a5380f034d9
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001786"
---
# <a name="getting-started---android"></a>Prise en main – Android

Ceci est un convertisseur qui cible les contrôles natifs Android.

## <a name="install-maven-package"></a>Installer le package Maven

[![Maven central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

Vous trouverez les packages publiés [ici](https://search.maven.org/artifact/io.adaptivecards/adaptivecards-android)

Pour inclure une bibliothèque dans votre projet, vous devez inclure cette ligne dans le gradle.build de votre projet, dans la section dependencies :

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
Vous devez modifier le numéro de version en fonction de la version que vous souhaitez inclure dans votre projet.

## <a name="add-import"></a>Ajouter à l’importation

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
