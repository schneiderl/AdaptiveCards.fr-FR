---
title: Styles natifs-SDK .NET WPF
author: matthidinger
ms.author: mahiding
ms.date: 10/19/2017
ms.topic: article
ms.openlocfilehash: ee5bec1a11f39ad69d40e57410c105b50ba45981
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552721"
---
# <a name="native-styling---net-wpf"></a>Styles natifs-WPF .NET

Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme. 

WPF facilite cette opération en vous permettant de transmettre un ResourceDictionary pour un style, un comportement, des animations, etc. précis.

| Élément | Noms de style |
|---|---|
| AdaptiveCard | Adaptive.Card| 
| Action. OpenUrl  | Adaptative. action. OpenUrl  |
| Action. ShowCard | Adaptive.Action.ShowCard |
| Action. Submit  | Adaptative. action. Submit  |
| colonne | Adaptative. Column, adaptative. action. TAP |
| ColumnSet | Adaptive.ColumnSet, Adaptive.VerticalSeparator |
| Conteneur | Adaptive.Container|
| Input.ChoiceSet | Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem |
| Entrée. date | Adaptive.Input.Text.Date
| Entrée. nombre | Adaptative. Input. Text. Number |
| Input. Text | Adaptative. Input. Text |
| Input. Time | Adaptative. Input. Text. Time |
| Input.Toggle| Adaptive.Input.Toggle|
| Image  | Adaptive. image |
| ImageSet  | Adaptive.ImageSet |
| FactSet | Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value |
| TextBlock  | Adaptive. TextBlock |

Cet exemple de dictionnaire de ressources XAML définit l’arrière-plan de tous les TextBlocks sur Aqua. Vous souhaiterez probablement une plus grande avancée que celle-ci😁

```xml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;

// ... or load it from a file path
// USE this if rendering from a server
renderer.ResourcesPath = <path-to-my-resource-dictionary.xaml>;
```

> [!IMPORTANT]
> **Remarque sur la génération d’images côté serveur** Le convertisseur WPF fournit une méthode `RenderCardToImageAsync` qui peut être utilisée pour la génération d’images côté serveur. Vous devez uniquement utiliser la `ResourcesPath` propriété si elle est utilisée dans cet environnement. Consultez les documents de [rendu d’image](../net-image/getting-started.md) pour plus d’informations