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
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="1ef39-102">Cartes adaptatives pour les développeurs Windows</span><span class="sxs-lookup"><span data-stu-id="1ef39-102">Adaptive Cards for Windows Developers</span></span>



## <a name="timeline"></a><span data-ttu-id="1ef39-103">Chronologie</span><span class="sxs-lookup"><span data-stu-id="1ef39-103">Timeline</span></span>

<span data-ttu-id="1ef39-104">Expérience des première Windows pour prendre en charge que des cartes adaptatives est la chronologie, une toute nouvelle expérience introduite dans Windows 10 1803.</span><span class="sxs-lookup"><span data-stu-id="1ef39-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Chronologie](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="1ef39-106">UserActivity API</span><span class="sxs-lookup"><span data-stu-id="1ef39-106">UserActivity API</span></span>

<span data-ttu-id="1ef39-107">Le [ `Windows.ApplicationModel.UserActivities.UserActivity` ](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API est ce qui remplit une activité dans la chronologie.</span><span class="sxs-lookup"><span data-stu-id="1ef39-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="1ef39-108">La carte adaptative est fournie par le biais de la `Content` propriété du `VisualElement`, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="1ef39-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learn-more"></a><span data-ttu-id="1ef39-109">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="1ef39-109">Learn more</span></span>

<span data-ttu-id="1ef39-110">Cette session Build 2017 traite les activités des utilisateurs dans detial.</span><span class="sxs-lookup"><span data-stu-id="1ef39-110">This session at Build 2017 covers User Activities in detial.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="1ef39-111">Autres Surfaces de Windows</span><span class="sxs-lookup"><span data-stu-id="1ef39-111">Other Windows Surfaces</span></span>
<span data-ttu-id="1ef39-112">Nous n’y a rien à partager encore, mais nous travaillons sur l’incorporation des cartes adaptatives dans des expériences Windows.</span><span class="sxs-lookup"><span data-stu-id="1ef39-112">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="1ef39-113">Foncez !</span><span class="sxs-lookup"><span data-stu-id="1ef39-113">Dive in!</span></span>

<span data-ttu-id="1ef39-114">Nous avez tout juste abordé le dans ce didacticiel, par conséquent, revenez plus tard et parcourir les liens ci-dessous pour explorer davantage des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="1ef39-114">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="1ef39-115">[Parcourir les cartes d’exemple](http://adaptivecards.io/samples/) d’inspiration</span><span class="sxs-lookup"><span data-stu-id="1ef39-115">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="1ef39-116">Utilisez le [Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="1ef39-116">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="1ef39-117">Générer une carte à l’aide de la [visualiseur Interactive](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="1ef39-117">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="1ef39-118">[Nous contacter](http://adaptivecards.io/connect) avec vos commentaires</span><span class="sxs-lookup"><span data-stu-id="1ef39-118">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
