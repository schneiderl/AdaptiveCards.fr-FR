---
title: Actions - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: ff8d4924f5394b7882110f5fa38c6833fd2c3896
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553581"
---
# <a name="actions---ios"></a><span data-ttu-id="24c41-102">Actions - iOS</span><span class="sxs-lookup"><span data-stu-id="24c41-102">Actions - iOS</span></span>

<span data-ttu-id="24c41-103">Les développeurs peuvent recevoir des actions telles SubmitAction et le OpenUrl en implémentant ACRActionDelegate et définissez-le sur l’instance de AdaptiveCard.</span><span class="sxs-lookup"><span data-stu-id="24c41-103">Developers can receive actions such SubmitAction and OpenUrl by implementing ACRActionDelegate, and set it to instance of AdaptiveCard.</span></span>

```objective-c
//// delegate implementation
- (void) didFetchUserResponses:(ACOAdaptiveCard *)card action:(ACOBaseActionElement *)action
{
     if(action.type == ACROpenUrl){
         NSURL *url = [NSURL URLWithString:[action url]];
         SFSafariViewController *svc = [[SFSafariViewController alloc] initWithURL:url];
         [self presentViewController:svc animated:YES completion:nil];
     }
     else if(action.type == ACRSubmit){
         /// inputs can be examined by method inputs
         NSData * userInputsAsJson = [card inputs];
         NSString *str = [[NSString alloc] initWithData:userInputsAsJson encoding:NSUTF8StringEncoding];
         NSLog(@"user response fetched: %@ with %@", str, [action data]);
     }
}

/// register the delegate with ACRView instance
adaptiveView.acrActionDelegate = self;

/// if using ACRViewController, pass delegate as argument
ACRRenderResult *renderResult = [ACRRenderer renderAsViewController:card config:config frame:frame delegate:acrActionDelegate];
```