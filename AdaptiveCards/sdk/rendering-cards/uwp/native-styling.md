---
title: Style natif-Kit de développement logiciel (SDK) UWP
author: matthidinger
ms.author: mahiding
ms.date: 08/15/2018
ms.topic: article
ms.openlocfilehash: da3c7616ce4fe307eda3073f7037842e3e3df81b
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417518"
---
# <a name="native-styling---uwp"></a>Style natif-UWP

Bien que la configuration de l’hôte vous permette d’accéder à la plupart des cas sur chaque plateforme, il est probable que vous deviez effectuer des styles natifs sur chaque plateforme. 

UWP facilite cette tâche en vous permettant de transmettre un ResourceDictionary pour un style, un comportement, des animations, etc. précis.

| Élément | Noms de style |
|---|---|
| AdaptiveCard | Carte adaptative.| 
| Action.OpenUrl  | Adaptative. action. OpenUrl  |
| Action.ShowCard | Adaptive. action. ShowCard |
| Action.Submit  | Adaptative. action. Submit  |
| Colonne | Adaptative. Column, adaptative. action. TAP |
| ColumnSet | Adaptive. ColumnSet, adaptatif. VerticalSeparator |
| Conteneur | Adaptative. Container|
| Entrée. ChoiceSet | Adaptative. Input. ChoiceSet, adaptative. Input. ChoiceSet. ComboBox, adaptative. Input. ChoiceSet. CheckBox, adaptative. Input. ChoiceSet. radio, adaptative. Input. ChoiceSet. ComboBoxItem |
| Entrée. date | Adaptative. Input. Text. date
| Entrée. nombre | Adaptative. Input. Text. Number |
| Input. Text | Adaptative. Input. Text |
| Input. Time | Adaptative. Input. Text. Time |
| Entrée. Toggle| Adaptative. Input. Toggle|
| Image  | Adaptive. image |
| ImageSet  | Adaptive. ImageSet |
| FactSet | Adaptive. FactSet, adaptative. fact. title, adaptatif. fact. Value |
| TextBlock  | Adaptive. TextBlock |

Cet exemple de dictionnaire de ressources XAML définit l’arrière-plan de tous les TextBlocks sur Aqua. Vous souhaiterez probablement une plus grande avancée que celle-ci😁

```xml
<ResourceDictionary
    xmlns="https://schemas.microsoft.com/winfx/2006/xaml/presentation" 
    xmlns:x="https://schemas.microsoft.com/winfx/2006/xaml">
    <Style x:Key="Adaptive.TextBlock" TargetType="TextBlock">
        <Setter Property="Background" Value="Aqua"></Setter>
    </Style>
</ResourceDictionary>
```
```csharp
// Use a ResourceDictionary instance
// DON'T use this property if rendering from a server
renderer.Resources = myResourceDictionary;
```
