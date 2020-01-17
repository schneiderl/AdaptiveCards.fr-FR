---
title: Kit de développement logiciel (SDK) Android
author: almedina-ms
ms.author: almedina
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: d15e0963427babe045a4db6f93800e09e0d95da9
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145499"
---
# <a name="getting-started---android"></a><span data-ttu-id="d003d-102">Prise en main – Android</span><span class="sxs-lookup"><span data-stu-id="d003d-102">Getting started - Android</span></span>

<span data-ttu-id="d003d-103">Ceci est un convertisseur qui cible les contrôles natifs Android.</span><span class="sxs-lookup"><span data-stu-id="d003d-103">This is a renderer which targets Android native controls.</span></span>

## <a name="install-maven-package"></a><span data-ttu-id="d003d-104">Installer le package Maven</span><span class="sxs-lookup"><span data-stu-id="d003d-104">Install Maven package</span></span>

<span data-ttu-id="d003d-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span><span class="sxs-lookup"><span data-stu-id="d003d-105">[![Maven Central](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)</span></span>

<span data-ttu-id="d003d-106">Vous pouvez trouver les packages publiés</span><span class="sxs-lookup"><span data-stu-id="d003d-106">You can find the published packages</span></span> ![ici](https://search.maven.org/search?q=g:io.adaptivecards)

<span data-ttu-id="d003d-108">Pour inclure une bibliothèque dans votre projet, vous devez inclure cette ligne dans le gradle.build de votre projet, dans la section dependencies :</span><span class="sxs-lookup"><span data-stu-id="d003d-108">To include library to your project you must include this line into your project gradle.build under the dependencies section</span></span>

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
<span data-ttu-id="d003d-109">Vous devez modifier le numéro de version en fonction de la version que vous souhaitez inclure dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="d003d-109">You need to change the version number depending on the version you want to include into your project</span></span>

## <a name="add-import"></a><span data-ttu-id="d003d-110">Ajouter une importation</span><span class="sxs-lookup"><span data-stu-id="d003d-110">Add import</span></span>

<span data-ttu-id="d003d-111">Pour inclure le modèle d’objet, ajoutez cette importation :</span><span class="sxs-lookup"><span data-stu-id="d003d-111">To include the object model, add this import</span></span>

```
 import io.adaptivecards.objectmodel.*;
```

<span data-ttu-id="d003d-112">Pour inclure le convertisseur, ajoutez cette importation :</span><span class="sxs-lookup"><span data-stu-id="d003d-112">To include the renderer, add this import</span></span>

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a><span data-ttu-id="d003d-113">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d003d-113">Next steps</span></span>

<span data-ttu-id="d003d-114">Pour les prochaines étapes, voir [Effectuer le rendu d’une carte](render-a-card.md).</span><span class="sxs-lookup"><span data-stu-id="d003d-114">See [Render a card](render-a-card.md) for the next steps!</span></span>
