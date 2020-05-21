---
title: Effectuer le rendu d’une carte – Kit de développement logiciel (SDK) iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 3970a6ee0673388069cedbcfbe3ef1e6670eb748
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631397"
---
# <a name="render-a-card---ios"></a><span data-ttu-id="3c4bf-102">Effectuer le rendu d’une carte – iOS</span><span class="sxs-lookup"><span data-stu-id="3c4bf-102">Render a card - iOS</span></span>

<span data-ttu-id="3c4bf-103">Voici comment effectuer le rendu d’une carte à l’aide du Kit de développement logiciel (SDK) iOS.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-103">Here's how to render a card using the iOS SDK.</span></span>

## <a name="create-a-card-from-a-json-string"></a><span data-ttu-id="3c4bf-104">Créer une carte à partir d’une chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="3c4bf-104">Create a card from a JSON string</span></span>

<span data-ttu-id="3c4bf-105">Une AdaptiveCard est générée à partir de la chaîne JSON :</span><span class="sxs-lookup"><span data-stu-id="3c4bf-105">AdaptiveCard is generated from JSON string</span></span>

```objective-c

NSString *jsonStr = @"{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";
ACOAdaptiveCardParseResult *cardParseResult = [ACOAdaptiveCard fromJson:jsonStr];

/// access for parse warnings and errors
NSArray<NSError *> *errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> *warnings = cardParseResult.parseWarnings;
```

## <a name="render-a-card"></a><span data-ttu-id="3c4bf-106">Afficher une carte</span><span class="sxs-lookup"><span data-stu-id="3c4bf-106">Render a Card</span></span>

<span data-ttu-id="3c4bf-107">Rederer utilise une carte adaptative et une configuration d’hôte. HostConfig peut être Nil et, s’il est Nil, la valeur par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-107">Rederer takes adaptive card and host config. HostConfig can be nil, and if nil, default value will be used.</span></span>
<span data-ttu-id="3c4bf-108">L’UIView retourné utilise autolayout.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-108">Returned UIView uses autolayout.</span></span> <span data-ttu-id="3c4bf-109">La largeur sera contrainte à la valeur définie par widthConstraint.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-109">Width will be constraint to the value set by widthConstraint.</span></span> <span data-ttu-id="3c4bf-110">Si la valeur 0 est utilisée, elle n’est pas liée.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-110">If 0 value is used, it won't be bound.</span></span>
<span data-ttu-id="3c4bf-111">La hauteur n’est pas liée et, quand elle est retournée, elle a la hauteur des sommes de tous les contenus rendus.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-111">Height is not bound, and when returned it will have the height of sums of all contents rendered.</span></span> <span data-ttu-id="3c4bf-112">Pour lier la dimension de la vue, utilisez NSLayoutConstraint.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-112">To bound the view dimension, please use NSLayoutConstraint.</span></span> <span data-ttu-id="3c4bf-113">La dimension exacte est accessible à partir du contexte de la viewDidLayoutSubview du viewcontroller de sa superview, ou sa méthode du même nom en cas d’utilisation d’ACRViewController.</span><span class="sxs-lookup"><span data-stu-id="3c4bf-113">The exact dimension is accessible from the context of viewDidLayoutSubview of its superview's viewcontroller or its method with the same name if ACRViewController is used.</span></span>

```objective-c
ACRRenderResult *renderResult = nil;
if(cardParseResult.isValid){
    renderResult = [ACRRenderer render:cardParseResult.card config:nil widthConstraint:335];
}
``` 
### <a name="example"></a><span data-ttu-id="3c4bf-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c4bf-114">Example</span></span>

```objective-c
--------------------------------------------------------------------------------
ViewController.m
--------------------------------------------------------------------------------
#import "ViewController.h"
#import <SafariServices/SafariServices.h>

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];

    NSString *jsonStr = @"{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";
    ACRRenderResult *renderResult = nil;
    ACOAdaptiveCardParseResult *cardParseResult = [ACOAdaptiveCard fromJson:jsonStr];
    if(cardParseResult.isValid){
        renderResult = [ACRRenderer render:cardParseResult.card config:nil widthConstraint:335];
    }

    if(renderResult.succeeded)
    {
        ACRView *ad = renderResult.view;
        ad.acrActionDelegate = self;
        
        UIView *view = self.view;
        view.autoresizingMask |= UIViewAutoresizingFlexibleHeight;
        [self.view addSubview:ad];
        ad.translatesAutoresizingMaskIntoConstraints = NO;
        
        [NSLayoutConstraint constraintWithItem:ad attribute:NSLayoutAttributeCenterX relatedBy:NSLayoutRelationEqual toItem:view attribute:NSLayoutAttributeCenterX multiplier:1.0 constant:0].active = YES;

        [NSLayoutConstraint constraintWithItem:ad attribute:NSLayoutAttributeCenterY relatedBy:NSLayoutRelationEqual toItem:view attribute:NSLayoutAttributeCenterY multiplier:1.0 constant:3].active = YES;
    }
}

- (void)didFetchUserResponses:(ACOAdaptiveCard *)card action:(ACOBaseActionElement *)action
{
    if(action.type == ACROpenUrl){
        NSURL *url = [NSURL URLWithString:[action url]];
        SFSafariViewController *svc = [[SFSafariViewController alloc] initWithURL:url];
        [self presentViewController:svc animated:YES completion:nil];
    }
}

@end

```

```swift
--------------------------------------------------------------------------------
ViewController.swift
--------------------------------------------------------------------------------

import UIKit
import SafariServices

class ViewController: UIViewController, ACRActionDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        let jsonStr = "{ \"type\": \"AdaptiveCard\", \"version\": \"1.0\", \"body\": [ { \"type\": \"Image\", \"url\": \"http://adaptivecards.io/content/adaptive-card-50.png\", \"horizontalAlignment\":\"center\" }, { \"type\": \"TextBlock\", \"horizontalAlignment\":\"center\", \"text\": \"Hello **Adaptive Cards!**\" } ], \"actions\": [ { \"type\": \"Action.OpenUrl\", \"title\": \"Learn more\", \"url\": \"http://adaptivecards.io\" }, { \"type\": \"Action.OpenUrl\", \"title\": \"GitHub\", \"url\": \"http://github.com/Microsoft/AdaptiveCards\" } ] }";

        let cardParseResult = ACOAdaptiveCard.fromJson(jsonStr);
        if((cardParseResult?.isValid)!){
            let renderResult = ACRRenderer.render(cardParseResult!.card, config: nil, widthConstraint: 335);

            if(renderResult?.succeeded ?? false)
            {
                let ad = renderResult?.view;
                ad!.acrActionDelegate = (self as ACRActionDelegate);
                self.view.autoresizingMask = [.flexibleHeight];
                self.view.addSubview(ad!);
                ad!.translatesAutoresizingMaskIntoConstraints = false;
    
                NSLayoutConstraint(item: ad!, attribute: .centerX, relatedBy: .equal, toItem: view, attribute: .centerX, multiplier: 1.0, constant: 0).isActive = true;
                NSLayoutConstraint(item: ad!, attribute: .centerY, relatedBy: .equal, toItem: view, attribute: .centerY, multiplier: 1.0, constant: 3).isActive = true;
            }
        }
    }

    func didFetchUserResponses(_ card: ACOAdaptiveCard, action: ACOBaseActionElement)
    {
        if(action.type == ACRActionType.openUrl){
            let url = URL.init(string:action.url());
            let svc = SFSafariViewController.init(url: url!);
            self.present(svc, animated: true, completion: nil);
        }
    }

}
```
