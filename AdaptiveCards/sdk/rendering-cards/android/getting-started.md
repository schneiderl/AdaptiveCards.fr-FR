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
# <a name="getting-started---android"></a><span data-ttu-id="b1b54-102">Prise en main – Android</span><span class="sxs-lookup"><span data-stu-id="b1b54-102">Getting started - Android</span></span>

<span data-ttu-id="b1b54-103">Ceci est un convertisseur qui cible les contrôles natifs Android.</span><span class="sxs-lookup"><span data-stu-id="b1b54-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="b1b54-104">Installer le package Maven</span><span class="sxs-lookup"><span data-stu-id="b1b54-104">Install Maven package</span></span>

<span data-ttu-id="b1b54-105">[![Maven central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="b1b54-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="b1b54-106">Vous trouverez les packages publiés [ici](https://search.maven.org/artifact/io.adaptivecards/adaptivecards-android)</span><span class="sxs-lookup"><span data-stu-id="b1b54-106">You can find the published packages [here](https://search.maven.org/artifact/io.adaptivecards/adaptivecards-android)</span></span>

<span data-ttu-id="b1b54-107">Pour inclure une bibliothèque dans votre projet, vous devez inclure cette ligne dans le gradle.build de votre projet, dans la section dependencies :</span><span class="sxs-lookup"><span data-stu-id="b1b54-107">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="b1b54-108">Vous devez modifier le numéro de version en fonction de la version que vous souhaitez inclure dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="b1b54-108">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="b1b54-109">Ajouter à l’importation</span><span class="sxs-lookup"><span data-stu-id="b1b54-109">Add import</span></span>

<span data-ttu-id="b1b54-110">Pour inclure le modèle d’objet, ajoutez cette importation :</span><span class="sxs-lookup"><span data-stu-id="b1b54-110">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="b1b54-111">Pour inclure le convertisseur, ajoutez cette importation :</span><span class="sxs-lookup"><span data-stu-id="b1b54-111">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="b1b54-112">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b1b54-112">Next steps</span></span>

<span data-ttu-id="b1b54-113">Pour les prochaines étapes, voir [Effectuer le rendu d’une carte](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="b1b54-113">See [Render a card](render-a-card.md) for the next steps!</span></span>
