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
# <a name="render-a-card---ios"></a>Afficher une carte - iOS

Voici comment effectuer le rendu d’une carte à l’aide du SDK iOS.

## <a name="create-a-card-from-a-json-string"></a>Créer une carte à partir d’une chaîne JSON

AdaptiveCard est généré à partir de la chaîne JSON

```objective-c
ACOParseResult *cardParseResult = [ACOAdaptiveCards FromJson:jsonStr];
/// access for parse warnings and errors
NSArray<NSError *> errors = cardParseResult.parseErrors;
NSArray<ACRParseWarning *> warnings = cardPraseResult.parseWarnings;
```

## <a name="render-a-card"></a>Afficher une carte

Rederer prend carte adaptative et configuration de l’hôte. HostConfig peut être nil, et si elle est nulle, valeur de la valeur par défaut sera utilisée.

```objective-c
ACRRenderResult *renderResult;
renderResult = [ACRRenderer render:cardParseResult.card
                            config:nil
                   widthConstraint:300.0];
``` 

### <a name="example"></a>Exemple

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

### <a name="render-a-card-as-uiviewcontroller"></a>Afficher une carte en tant que UIViewController

Convertisseur de AdaptiveCard peut également retourner UIViewController.

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

Retourné Qu'uiview utilise la mise en forme automatique. La largeur sera contrainte à la valeur définie par widthConstraint. Si la valeur 0 est utilisée, il ne sera pas lié.
Hauteur n’est pas liée et lorsque retourné elle aura la hauteur de sommes de tout le contenu rendu. Pour lier la dimension de la vue, utilisez NSLayoutConstraint. La dimension exacte est accessible à partir du contexte de viewDidLayoutSubview de viewcontroller de sa superview ou sa méthode portant le même nom si ACRViewController est utilisé.


### <a name="compact-style-inputchoiceset"></a>Style compact Input.ChoiceSet

Représentation de l’interface utilisateur de Input.ChoiceSet a UINavigationController, et il doit être présenté à un UIViewController actuellement actif pour une transition vers UIView qui permet la sélection de l’utilisateur.

Pour cela, veuillez mettre en œuvre didFecthSecondaryView de ACRActionDelegate.

```objective-c
- (void)didFetchSecondaryView:(ACOAdaptiveCard *)card navigationController:(UINavigationController *)navigationController{
    [self presentViewController:navigationController animated:YES completion:nil];
}  
```

Si le biais du délégué n’a pas été raccordé, faites-le.

```objective-c
adaptiveView.acrActionDelegate = self
```