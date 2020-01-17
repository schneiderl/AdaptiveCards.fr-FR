---
title: CardRendererRegistration, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 4254c1c3c0f275434fae2a92e20679b6fa136b16
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76145983"
---
# <a name="cardrendererregistration"></a>CardRendererRegistration

```csharp
public class CardRendererRegistration : Java.Lang.Object
```

**Namespace**
```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.Renderer.Registration
```

### <a name="summary"></a>Récapitulatif

| Méthodes publiques | |
| --- | ---- |
| ```void``` | [```RegisterFeatureRegistration (FeatureRegistration featureRegistration)```](#registerfeatureregistration) |

## <a name="public-methods"></a>Méthodes publiques

--- 

### <a id="registerfeatureregistration"></a>RegisterFeatureRegistration
<p style='text-align:right'>Ajouté dans la version 0.1.0</p>

```csharp
public void RegisterFeatureRegistration (FeatureRegistration featureRegistration)
```

Inscrit un objet [```FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) pour le convertisseur de carte à utiliser.

| Paramètres | |
| --- | --- |
| featureRegistration | [```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.FeatureRegistration```](adaptivecards-rendering-xamarin-android-objectmodel-featureregistration.md) |

#### <a name="sample"></a>Exemple

```csharp
FeatureRegistration featureRegistration = new FeatureRegistration();
featureRegistration.AddFeature("MyFeature", "1.2.0");
CardRendererRegistration.Instance.RegisterFeatureRegistration(featureRegistration);
```