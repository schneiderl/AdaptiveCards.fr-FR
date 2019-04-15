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
# <a name="extensibility---ios"></a><span data-ttu-id="67c5d-102">Extensibilité - iOS</span><span class="sxs-lookup"><span data-stu-id="67c5d-102">Extensibility - iOS</span></span>

## <a name="changing-per-element-rendering"></a><span data-ttu-id="67c5d-103">Modification par le rendu de l’élément</span><span class="sxs-lookup"><span data-stu-id="67c5d-103">Changing per element rendering</span></span>

<span data-ttu-id="67c5d-104">Les développeurs peuvent personnaliser l’apparence des éléments de AdaptiveCards renderred tels que TextBlock.</span><span class="sxs-lookup"><span data-stu-id="67c5d-104">Developers can customize the look of renderred AdaptiveCards elements such as TextBlock.</span></span>
<span data-ttu-id="67c5d-105">Exemple suivant montre comment changer les couleurs d’arrière-plan de NumberInput.</span><span class="sxs-lookup"><span data-stu-id="67c5d-105">Following example shows how one can change background color of NumberInput.</span></span>

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

 ## <a name="additional-property"></a><span data-ttu-id="67c5d-106">Propriété supplémentaire</span><span class="sxs-lookup"><span data-stu-id="67c5d-106">Additional Property</span></span>

 <span data-ttu-id="67c5d-107">Les développeurs peuvent également envoyer dans des propriétés supplémentaires dans le cadre de la charge utile json.</span><span class="sxs-lookup"><span data-stu-id="67c5d-107">Developers can also send in additional properties as part of json payload.</span></span>
<span data-ttu-id="67c5d-108">Par exemple, outre « espacement » et « id » de la charge utile json pour BaseCardElement, un peut ajouter rayon pour les angles du TextBlock à sa charge utile json.</span><span class="sxs-lookup"><span data-stu-id="67c5d-108">For example, in addition to "spacing" and "id" of json payload for BaseCardElement, one can add radius for corners of TextBlock to its json payload.</span></span>

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
 ## <a name="custom-parsing"></a><span data-ttu-id="67c5d-109">Personnaliser l’analyse</span><span class="sxs-lookup"><span data-stu-id="67c5d-109">Custom Parsing</span></span>

<span data-ttu-id="67c5d-110">Les développeurs peuvent également avoir l’analyse personnalisée et avoir le nouvel élément d’interface utilisateur ajouté à la carte adpative telles que de la barre de progression.</span><span class="sxs-lookup"><span data-stu-id="67c5d-110">Developers can also have custom parsing and have new UI element added to adpative card such as progress bar.</span></span> <span data-ttu-id="67c5d-111">Vérifiez les CustomProgressBarRenderer.mm en détail.</span><span class="sxs-lookup"><span data-stu-id="67c5d-111">Please check CustomProgressBarRenderer.mm for detail.</span></span>
<span data-ttu-id="67c5d-112">Analyseur personnalisé doit implémenter ACOIBaseCardElementParser protocole.</span><span class="sxs-lookup"><span data-stu-id="67c5d-112">Custom parser must implement ACOIBaseCardElementParser protocol.</span></span> <span data-ttu-id="67c5d-113">deserializeToCustomElement méthode doit analyse étant donné la charge utile json donnée comme NSData et retourner un pointeur vers l’objet UIView qui est ajouté à AdaptiveCard rendu objet.</span><span class="sxs-lookup"><span data-stu-id="67c5d-113">deserializeToCustomElement method should parses given json payload given as NSData and return a pointer to UIView object that will be added to AdaptiveCard rendered object.</span></span>

```objective-c
      CustomProgressBarRenderer *progressBarRenderer = [[CustomProgressBarRenderer alloc] init];
      [registration setCustomElementParser:progressBarRenderer];
```objective-c