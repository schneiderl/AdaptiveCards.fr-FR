---
title: Extensibilité-Kit de développement logiciel (SDK) iOS
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: 13245ced3f4f657e13793bfdf1d212e44d2b6a41
ms.sourcegitcommit: 1e18c5dc0cf85d26f66335e312348bbfb903d95a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77454762"
---
# <a name="extensibility---ios"></a>Extensibilité-iOS

## <a name="changing-per-element-rendering"></a>Modification par élément rendu

Les développeurs peuvent personnaliser l’apparence des éléments renderred AdaptiveCards tels que TextBlock.
L’exemple suivant montre comment modifier la couleur d’arrière-plan de NumberInput.

```objective-c
ACRRegistration *registration = [ACRRegistration getInstance];
// register custom renderer with registration
// custom renderer must implement ACRIBaseCardElementRenderer protocol
// for more information, please refer to CustomInputNumberRenderer.mm
 [registration setBaseCardElementRenderer:[CustomInputNumberRenderer getInstance] cardElementType:ACRNumberInput];
 ...
/// CustiomInputNumberRenderer.mm
- (UIView *)render:(UIView<ACRIContentHoldingView> *)viewGroup
              rootViewController:(UIViewController *)vc
              inputs:(NSArray *)inputs
     baseCardElement:(ACOBaseCardElement *)acoElem
          hostConfig:(ACOHostConfig *)acoConfig
  {
      ACRInputNumberRenderer *defaultRenderer = [ACRInputNumberRenderer getInstance];
 
      UIView *input = [defaultRenderer render:viewGroup
                           rootViewController:vc
                                       inputs:inputs
                              baseCardElement:acoElem
                                   hostConfig:acoConfig];
      if(input)
      {   
          // customize background color of input
          [input setBackgroundColor: [UIColor colorWithRed:1.0
                                                     green:59.0/255.0
                                                      blue:48.0/255.0
                                                     alpha:1.0]];
      }
      return input;
  }
  ```

 ## <a name="additional-property"></a>Propriété supplémentaire

 Les développeurs peuvent également envoyer des propriétés supplémentaires dans le cadre de la charge utile JSON.
Par exemple, en plus de « l’espacement » et de l’ID de charge utile JSON pour BaseCardElement, vous pouvez ajouter RADIUS pour les angles de TextBlock à sa charge utile JSON.

 ```objective-c
 "type":"TextBlock",
 ...
 "radius":20,
 ...
 ```

 ```objective-c
         NSData *additionalProperty = [acoElem additionalProperty];
          if(additionalProperty) {
              NSDictionary *dictionary = [NSJSONSerialization JSONObjectWithData:additionalProperty options:NSJSONReadingMutableLeaves error:nil];
              radiusForMyTextBlock = dictionary[@"radius"];
          ...
```
 ## <a name="custom-parsing"></a>Analyse personnalisée

Les développeurs peuvent également avoir une analyse personnalisée et ajouter un nouvel élément d’interface utilisateur à la carte Adpative, comme la barre de progression. Pour plus d’informations, consultez CustomProgressBarRenderer.mm.
L’analyseur personnalisé doit implémenter le protocole ACOIBaseCardElementParser. la méthode deserializeToCustomElement doit analyser la charge utile JSON donnée en tant que NSData et retourner un pointeur vers l’objet UIView qui sera ajouté à AdaptiveCard objet rendu.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c