---
title: Cartes adaptatives pour les développeurs Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 20b324c12cd7cec10f2142fc2cf76039b5c329de
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552851"
---
# <a name="adaptive-cards-for-windows-developers"></a>Cartes adaptatives pour les développeurs Windows



## <a name="timeline"></a>Chronologie

Expérience des première Windows pour prendre en charge que des cartes adaptatives est la chronologie, une toute nouvelle expérience introduite dans Windows 10 1803. 

![Chronologie](media/windows/timeline.png)

### <a name="useractivity-api"></a>UserActivity API

Le [ `Windows.ApplicationModel.UserActivities.UserActivity` ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API est ce qui remplit une activité dans la chronologie.

La carte adaptative est fournie par le biais de la `Content` propriété du `VisualElement`, comme indiqué ci-dessous :

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a>En savoir plus

Cette session Build 2017 traite les activités des utilisateurs dans detial.

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a>Autres Surfaces de Windows
Nous n’y a rien à partager encore, mais nous travaillons sur l’incorporation des cartes adaptatives dans des expériences Windows.

## <a name="dive-in"></a>Foncez !

Nous avez tout juste abordé le dans ce didacticiel, par conséquent, revenez plus tard et parcourir les liens ci-dessous pour explorer davantage des cartes adaptatives.

* [Parcourir les cartes d’exemple](http://adaptivecards.io/samples/) d’inspiration
* Utilisez le [Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus les éléments disponibles
* Générer une carte à l’aide de la [visualiseur Interactive](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Nous contacter](http://adaptivecards.io/connect) avec vos commentaires
