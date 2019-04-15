---
title: Style natif - Kit de développement logiciel .NET WPF
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
# <a name="native-styling---net-wpf"></a>Style natif - .NET WPF

Tandis que la configuration de l’hôte vous aidera à la plupart de la façon dont il sur chaque plateforme, il est probable que vous devrez faire certains styles natif sur chaque plateforme. 

WPF facilite cette procédure en vous permettant de passer un ResourceDictionary pour style affiné, comportement, animations, etc.

| Élément | Noms de style |
|---|---|
| AdaptiveCard | Adaptive.Card| 
| Action.OpenUrl  | Adaptive.Action.OpenUrl  |
| Action.ShowCard | Adaptive.Action.ShowCard |
| Action.Submit  | Adaptive.Action.Submit  |
| colonne | Adaptive.Column, Adaptive.Action.Tap |
| ColumnSet | Adaptive.ColumnSet, Adaptive.VerticalSeparator |
| Conteneur | Adaptive.Container|
| Input.ChoiceSet | Adaptive.Input.ChoiceSet,  Adaptive.Input.ChoiceSet.ComboBox, Adaptive.Input.ChoiceSet.CheckBox,  Adaptive.Input.ChoiceSet.Radio,  Adaptive.Input.ChoiceSet.ComboBoxItem |
| Input.Date | Adaptive.Input.Text.Date
| Input.Number | Adaptive.Input.Text.Number |
| Input.Text | Adaptive.Input.Text |
| Input.Time | Adaptive.Input.Text.Time |
| Input.Toggle| Adaptive.Input.Toggle|
| Image  | Adaptive.Image |
| ImageSet  | Adaptive.ImageSet |
| FactSet | Adaptive.FactSet, Adaptive.Fact.Title, Adaptive.Fact.Value |
| TextBlock  | Adaptive.TextBlock |

Cet exemple de dictionnaire de ressource de XAML qui définit l’arrière-plan de toutes les TextBlocks sur « cyan ». Vous souhaiterez probablement que quelque chose plus avancé que cela 😁

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
> **Une remarque sur la génération d’image côté serveur** WPF le convertisseur fournit une `RenderCardToImageAsync` méthode qui peut être utilisé pour la génération d’images du côté serveur. Vous devez utiliser uniquement le `ResourcesPath` propriété si utilisés dans cet environnement. Consultez le [rendu de l’Image](../net-image/getting-started.md) docs pour en savoir plus