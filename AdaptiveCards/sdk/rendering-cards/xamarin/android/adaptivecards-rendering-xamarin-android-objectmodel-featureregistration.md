---
title: FeatureRegistration, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: c1975197996e54626b464abe9181f0b02895ee4d
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146143"
---
# <a name="feature-registration"></a><span data-ttu-id="b2c25-102">Inscription des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="b2c25-102">Feature Registration</span></span>

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

<span data-ttu-id="b2c25-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="b2c25-103">**Namespace**</span></span>
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a><span data-ttu-id="b2c25-104">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="b2c25-104">Summary</span></span>

| <span data-ttu-id="b2c25-105">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="b2c25-105">Public methods</span></span> | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## <a name="public-methods"></a><span data-ttu-id="b2c25-106">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="b2c25-106">Public Methods</span></span>

---

### <a id="addfeature"></a><span data-ttu-id="b2c25-107">AddFeature</span><span class="sxs-lookup"><span data-stu-id="b2c25-107">AddFeature</span></span>
<p style='text-align:right'><span data-ttu-id="b2c25-108">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="b2c25-108">Added in version 0.1.0</span></span></p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

<span data-ttu-id="b2c25-109">Ajoute une fonctionnalité contenant son nom et sa version à l’inscription de la fonctionnalité de convertisseur.</span><span class="sxs-lookup"><span data-stu-id="b2c25-109">Adds a feature containing its name and version to the renderer feature registration.</span></span>

| <span data-ttu-id="b2c25-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2c25-110">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="b2c25-111">NomFonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b2c25-111">featureName</span></span> | ```string``` |
| <span data-ttu-id="b2c25-112">featureVersion</span><span class="sxs-lookup"><span data-stu-id="b2c25-112">featureVersion</span></span> | ```string``` |

#### <a name="sample"></a><span data-ttu-id="b2c25-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2c25-113">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a><span data-ttu-id="b2c25-114">GetFeatureVersion</span><span class="sxs-lookup"><span data-stu-id="b2c25-114">GetFeatureVersion</span></span>
<p style='text-align:right'><span data-ttu-id="b2c25-115">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="b2c25-115">Added in version 0.1.0</span></span></p>

```csharp
public string GetFeatureVersion (string featureName)
```

<span data-ttu-id="b2c25-116">Récupère la version pour une fonctionnalité donnée.</span><span class="sxs-lookup"><span data-stu-id="b2c25-116">Retrieves the version for a given feature.</span></span> 

| <span data-ttu-id="b2c25-117">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2c25-117">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="b2c25-118">NomFonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b2c25-118">featureName</span></span> | ```string``` |

| <span data-ttu-id="b2c25-119">Returns</span><span class="sxs-lookup"><span data-stu-id="b2c25-119">Returns</span></span> | |
| --- | --- |
| ```string``` | <span data-ttu-id="b2c25-120">Version de fonctionnalité pour la fonctionnalité donnée</span><span class="sxs-lookup"><span data-stu-id="b2c25-120">Feature version for the given feature</span></span> |

#### <a name="sample"></a><span data-ttu-id="b2c25-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2c25-121">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a><span data-ttu-id="b2c25-122">RemoveFeature</span><span class="sxs-lookup"><span data-stu-id="b2c25-122">RemoveFeature</span></span>
<p style='text-align:right'><span data-ttu-id="b2c25-123">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="b2c25-123">Added in version 0.1.0</span></span></p>

```csharp
public void RemoveFeature (string featureName)
```

<span data-ttu-id="b2c25-124">Supprime la fonctionnalité donnée du dictionnaire de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="b2c25-124">Removes the given feature from the feature dictionary.</span></span>

| <span data-ttu-id="b2c25-125">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2c25-125">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="b2c25-126">NomFonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b2c25-126">featureName</span></span> | ```string``` |

#### <a name="sample"></a><span data-ttu-id="b2c25-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2c25-127">Sample</span></span>

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```