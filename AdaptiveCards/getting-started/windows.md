---
title: Cartes adaptatives pour développeurs Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 39bdc64ed3244aca68d36c886a9562d964ded217
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "76145389"
---
# <a name="adaptive-cards-for-windows-developers"></a>Cartes adaptatives pour développeurs Windows

## <a name="timeline"></a>Chronologie

La première expérience Windows compatible avec les cartes adaptatives est la Chronologie, une toute nouvelle expérience introduite pour la première fois dans Windows 10 1803. 

![Chronologie](media/windows/timeline.png)

### <a name="useractivity-api"></a>API UserActivity

L'API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) permet de renseigner une activité dans la Chronologie.

La carte adaptative sera fournie via la propriété `Content` de `VisualElement`, comme illustré ci-dessous :

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a>Module d’apprentissage

Il existe un excellent module d’apprentissage de 45 minutes qui couvre ces étapes de bout en bout.

[Intégrer des cartes adaptatives dans Chronologie Windows 10](https://docs.microsoft.com/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a>En savoir plus

Cette session de la conférence Build 2017 couvre en détail les activités de l'utilisateur.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Autres surfaces Windows
Nous n'avons rien à présenter pour le moment, mais nous préparons l'intégration de cartes adaptatives dans d'autres expériences Windows.

## <a name="dive-in"></a>Lancez-vous !

Ce didacticiel ne fait qu'effleurer le sujet. N'hésitez donc pas à revenir très bientôt et à utiliser les liens ci-dessous pour en savoir plus sur les cartes adaptatives.

* [Parcourir des exemples de cartes](http://adaptivecards.io/samples/) pour trouver l'inspiration
* Utiliser l'[Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus sur les éléments disponibles
* Générer une carte à l'aide du [Visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Nous contacter](http://adaptivecards.io/connect) pour nous faire part de vos commentaires
