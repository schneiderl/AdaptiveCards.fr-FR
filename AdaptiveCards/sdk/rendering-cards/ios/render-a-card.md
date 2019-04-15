---
title: Afficher une carte - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 625701e38389cc1a54682b72ce2315c14180e576
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552471"
---
# <a name="render-a-card---ios"></a><span data-ttu-id="cd34a-102">Afficher une carte - iOS</span><span class="sxs-lookup"><span data-stu-id="cd34a-102">Render a card - iOS</span></span>

<span data-ttu-id="cd34a-103">Voici comment effectuer le rendu d’une carte à l’aide du SDK iOS.</span><span class="sxs-lookup"><span data-stu-id="cd34a-103">Here's how to render a card using the iOS SDK.</span></span>

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="cd34a-104">Créer une carte à partir d’une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="cd34a-104">Create a card from a JSON string</span></span>

<span data-ttu-id="cd34a-105">AdaptiveCard est généré à partir de la chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="cd34a-105">AdaptiveCard is generated from JSON string</span></span>

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a><span data-ttu-id="cd34a-106">Afficher une carte</span><span class="sxs-lookup"><span data-stu-id="cd34a-106">Render a Card</span></span>

<span data-ttu-id="cd34a-107">Rederer prend carte adaptative et configuration de l’hôte. HostConfig peut être nil, et si elle est nulle, valeur de la valeur par défaut sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="cd34a-107">Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.</span></span>

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### <a name="example"></a><span data-ttu-id="cd34a-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="cd34a-108">Example</span></span>

```objective-c
ACRRenderResult *renderResult;
ACOHostConfigParseResult *hostconfigParseResult = [ACOHostConfig FromJson:self.hostconfig];
ACOAdaptiveCardsParseResult *cardParseResult       = [ACOAdaptiveCards FromJson:jsonStr];

// checking parse result
if(hostconfigParseResult.IsValid == YES && cardParseResult.IsValid == YES)
{
    renderResult = [ACRRenderer render:cardParseResult.card
                                config:hostconfigParseResult.config
                       widthConstraint:300.0];
}   
    
if(renderResult.Suceeded == YES)
{
    // access returned UIView object
    ACRView *adaptiveView = renderResult.view;
    [self.view addSubview:adcVc.view];
}
```

### <a name="render-a-card-as-uiviewcontroller"></a><span data-ttu-id="cd34a-109">Afficher une carte en tant que UIViewController</span><span class="sxs-lookup"><span data-stu-id="cd34a-109">Render a Card as UIViewController</span></span>

<span data-ttu-id="cd34a-110">Convertisseur de AdaptiveCard peut également retourner UIViewController.</span><span class="sxs-lookup"><span data-stu-id="cd34a-110">AdaptiveCard renderer can also return UIViewController.</span></span>

```objective-c
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];

renderResult.viewif(renderResult.Suceeded == YES)
{
    ACRViewController *adaptiveViewController = renderResult.viewcontroller;
    [self addChildViewController:adaptiveViewController];
    [self.view addSubview:adaptiveViewController.view];
    [adaptiveViewController didMoveToParentViewController:self];
    ...
}
```

<span data-ttu-id="cd34a-111">Retourné Qu'uiview utilise la mise en forme automatique.</span><span class="sxs-lookup"><span data-stu-id="cd34a-111">Returned UIView uses autolayout.</span></span> <span data-ttu-id="cd34a-112">La largeur sera contrainte à la valeur définie par widthConstraint.</span><span class="sxs-lookup"><span data-stu-id="cd34a-112">Width will be constraint to the value set by widthConstraint.</span></span> <span data-ttu-id="cd34a-113">Si la valeur 0 est utilisée, il ne sera pas lié.</span><span class="sxs-lookup"><span data-stu-id="cd34a-113">If 0 value is used, it won't be bound.</span></span>
<span data-ttu-id="cd34a-114">Hauteur n’est pas liée et lorsque retourné elle aura la hauteur de sommes de tout le contenu rendu.</span><span class="sxs-lookup"><span data-stu-id="cd34a-114">Height is not bound, and when returned it will have the height of sums of all contents rendered.</span></span> <span data-ttu-id="cd34a-115">Pour lier la dimension de la vue, utilisez NSLayoutConstraint.</span><span class="sxs-lookup"><span data-stu-id="cd34a-115">To bound the view dimension, please use NSLayoutConstraint.</span></span> <span data-ttu-id="cd34a-116">La dimension exacte est accessible à partir du contexte de viewDidLayoutSubview de viewcontroller de sa superview ou sa méthode portant le même nom si ACRViewController est utilisé.</span><span class="sxs-lookup"><span data-stu-id="cd34a-116">The exact dimension is accessible from the context of viewDidLayoutSubview of its superview's viewcontroller or its method with the same name if ACRViewController is used.</span></span>


### <a name="compact-style-inputchoiceset"></a><span data-ttu-id="cd34a-117">Style compact Input.ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="cd34a-117">Compact Style Input.ChoiceSet</span></span>

<span data-ttu-id="cd34a-118">Représentation de l’interface utilisateur de Input.ChoiceSet a UINavigationController, et il doit être présenté à un UIViewController actuellement actif pour une transition vers UIView qui permet la sélection de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cd34a-118">UI representation of Input.ChoiceSet has UINavigationController, and it needs to be presented to a presently active UIViewController to transition into UIView that allows user selection.</span></span>

<span data-ttu-id="cd34a-119">Pour cela, veuillez mettre en œuvre didFecthSecondaryView de ACRActionDelegate.</span><span class="sxs-lookup"><span data-stu-id="cd34a-119">To accomplish that, please implement didFecthSecondaryView of ACRActionDelegate.</span></span>

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

<span data-ttu-id="cd34a-120">Si le biais du délégué n’a pas été raccordé, faites-le.</span><span class="sxs-lookup"><span data-stu-id="cd34a-120">If the delgate has not been hooked up, do so.</span></span>

```objective-c
adaptiveView.acrActionDelegate = self
```