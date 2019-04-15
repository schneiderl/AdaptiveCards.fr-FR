---
title: Extensibilité - iOS SDK
author: matthidinger
ms.author: mahiding
ms.date: 06/26/2017
ms.topic: article
ms.openlocfilehash: c3dcae7ef2347201b5f7ce02baf3204db7ee27d6
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553561"
---
# <a name="extensibility---ios"></a>Extensibilité - iOS

## <a name="changing-per-element-rendering"></a>Modification par le rendu de l’élément

Les développeurs peuvent personnaliser l’apparence des éléments de AdaptiveCards renderred tels que TextBlock.
Exemple suivant montre comment changer les couleurs d’arrière-plan de NumberInput.

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

 Les développeurs peuvent également envoyer dans des propriétés supplémentaires dans le cadre de la charge utile json.
Par exemple, outre « espacement » et « id » de la charge utile json pour BaseCardElement, un peut ajouter rayon pour les angles du TextBlock à sa charge utile json.

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
 ## <a name="custom-parsing"></a>Personnaliser l’analyse

Les développeurs peuvent également avoir l’analyse personnalisée et avoir le nouvel élément d’interface utilisateur ajouté à la carte adpative telles que de la barre de progression. Vérifiez les CustomProgressBarRenderer.mm en détail.
Analyseur personnalisé doit implémenter ACOIBaseCardElementParser protocole. deserializeToCustomElement méthode doit analyse étant donné la charge utile json donnée comme NSData et retourner un pointeur vers l’objet UIView qui est ajouté à AdaptiveCard rendu objet.

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c