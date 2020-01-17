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
# <a name="feature-registration"></a>Inscription des fonctionnalités

```csharp
public class FeatureRegistration : Java.Lang.Object 
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a>Récapitulatif

| Méthodes publiques | |
| --- | ---- |
| ```void``` | [```AddFeature(string featureName, string featureVersion)```](#addfeature) |
| ```string``` | [```GetFeatureVersion(string featureName)```](#getfeatureversion) |
| ```void``` | [```RemoveFeature (string featureName)```](#removefeature) |

## <a name="public-methods"></a>Méthodes publiques

---

### <a id="addfeature"></a>AddFeature
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public void AddFeature (string featureName, 
                        string featureVersion)
```

Ajoute une fonctionnalité contenant son nom et sa version à l’inscription de la fonctionnalité de convertisseur.

| Paramètres | |
| --- | --- |
| NomFonctionnalité | ```string``` |
| featureVersion | ```string``` |

#### <a name="sample"></a>Exemple

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```

---

### <a id="getfeatureversion"></a>GetFeatureVersion
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public string GetFeatureVersion (string featureName)
```

Récupère la version pour une fonctionnalité donnée. 

| Paramètres | |
| --- | --- |
| NomFonctionnalité | ```string``` |

| Returns | |
| --- | --- |
| ```string``` | Version de fonctionnalité pour la fonctionnalité donnée |

#### <a name="sample"></a>Exemple

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
string featureVersion = featureRegistration.GetFeatureVersion("MyFeature"); // 1.2.0
```

---

### <a id="removefeature"></a>RemoveFeature
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public void RemoveFeature (string featureName)
```

Supprime la fonctionnalité donnée du dictionnaire de fonctionnalités.

| Paramètres | |
| --- | --- |
| NomFonctionnalité | ```string``` |

#### <a name="sample"></a>Exemple

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
featureRegistration.RemoveFeature("MyFeature");
```