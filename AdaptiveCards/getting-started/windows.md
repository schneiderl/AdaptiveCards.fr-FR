---
title: Cartes adaptatives pour développeurs Windows
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: f6ae9b99decf8176af68334a681eb9e370f04484
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631327"
---
# <a name="adaptive-cards-for-windows-developers"></a><span data-ttu-id="2f1bf-102">Cartes adaptatives pour développeurs Windows</span><span class="sxs-lookup"><span data-stu-id="2f1bf-102">Adaptive Cards for Windows Developers</span></span>

## <a name="timeline"></a><span data-ttu-id="2f1bf-103">Chronologie</span><span class="sxs-lookup"><span data-stu-id="2f1bf-103">Timeline</span></span>

<span data-ttu-id="2f1bf-104">La première expérience Windows compatible avec les cartes adaptatives est la Chronologie, une toute nouvelle expérience introduite pour la première fois dans Windows 10 1803.</span><span class="sxs-lookup"><span data-stu-id="2f1bf-104">The first Windows experience to supports Adaptive Cards is Timeline, a brand new experience first introduced in Windows 10 1803.</span></span> 

![Chronologie](media/windows/timeline.png)

### <a name="useractivity-api"></a><span data-ttu-id="2f1bf-106">API UserActivity</span><span class="sxs-lookup"><span data-stu-id="2f1bf-106">UserActivity API</span></span>

<span data-ttu-id="2f1bf-107">L'API [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) permet de renseigner une activité dans la Chronologie.</span><span class="sxs-lookup"><span data-stu-id="2f1bf-107">The [`Windows.ApplicationModel.UserActivities.UserActivity`](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity) API is what populates an Activity into Timeline.</span></span>

<span data-ttu-id="2f1bf-108">La carte adaptative sera fournie via la propriété `Content` de `VisualElement`, comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2f1bf-108">The Adaptive Card will be supplied via the `Content` property of `VisualElement`, as seen below:</span></span>

```csharp
UserActivity userActivity = await channel.GetOrCreateUserActivityAsync(activityId, new HostName("contoso.com"));
userActivity.ActivationUri = new Uri("rss-reader:article?" + article.Link);
userActivity.DisplayText = article.Title; //used for details tile text
userActivity.VisualElements.Content = AdaptiveCardBuilder.CreateAdaptiveCardFromJson(jsonString);
await userActivity.SaveAsync();
```

### <a name="learning-module"></a><span data-ttu-id="2f1bf-109">Module d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="2f1bf-109">Learning Module</span></span>

<span data-ttu-id="2f1bf-110">Il existe un excellent module d’apprentissage de 45 minutes qui couvre ces étapes de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="2f1bf-110">There is a great 45-min learn module that covers these steps end-to-end.</span></span>

[<span data-ttu-id="2f1bf-111">Intégrer des cartes adaptatives dans Chronologie Windows 10</span><span class="sxs-lookup"><span data-stu-id="2f1bf-111">Integrate adaptive cards into Windows 10 Timeline</span></span>](https://docs.microsoft.com/learn/modules/integrate-app-into-windows-10-timeline/)

### <a name="learn-more"></a><span data-ttu-id="2f1bf-112">Pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="2f1bf-112">Learn more</span></span>

<span data-ttu-id="2f1bf-113">Cette session de la conférence Build 2017 couvre en détail les activités de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f1bf-113">This session at Build 2017 covers User Activities in detail.</span></span>

<iframe src="https://channel9.msdn.com/Events/Build/2017/B8108/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

## <a name="other-windows-surfaces"></a><span data-ttu-id="2f1bf-114">Autres surfaces Windows</span><span class="sxs-lookup"><span data-stu-id="2f1bf-114">Other Windows Surfaces</span></span>
<span data-ttu-id="2f1bf-115">Nous n'avons rien à présenter pour le moment, mais nous préparons l'intégration de cartes adaptatives dans d'autres expériences Windows.</span><span class="sxs-lookup"><span data-stu-id="2f1bf-115">We don't have anything to share just yet, but we're working on incorporating Adaptive Cards into more Windows experiences.</span></span>

## <a name="dive-in"></a><span data-ttu-id="2f1bf-116">Lancez-vous !</span><span class="sxs-lookup"><span data-stu-id="2f1bf-116">Dive in!</span></span>

<span data-ttu-id="2f1bf-117">Ce didacticiel ne fait qu'effleurer le sujet. N'hésitez donc pas à revenir très bientôt et à utiliser les liens ci-dessous pour en savoir plus sur les cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="2f1bf-117">We've barely scratched the surface in this tutorial, so check back soon and browse the links below to explore more about Adaptive Cards.</span></span>

* <span data-ttu-id="2f1bf-118">[Parcourir des exemples de cartes](http://adaptivecards.io/samples/) pour trouver l'inspiration</span><span class="sxs-lookup"><span data-stu-id="2f1bf-118">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="2f1bf-119">Utiliser l'[Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus sur les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="2f1bf-119">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="2f1bf-120">Générer une carte à l'aide du [Visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="2f1bf-120">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="2f1bf-121">[Nous contacter](http://adaptivecards.io/connect) pour nous faire part de vos commentaires</span><span class="sxs-lookup"><span data-stu-id="2f1bf-121">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
