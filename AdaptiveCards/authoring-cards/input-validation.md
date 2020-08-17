---
title: Validation d'entrée
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
ms.openlocfilehash: 08fb2cb5b2b6fa1f227ec5a530f8063dc26b40e3
ms.sourcegitcommit: 19c08b1370305fb2965de0140c5e632356e78513
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879130"
---
# <a name="input-validation"></a>Validation d'entrée

Dans les versions 1.3 et ultérieures du schéma, le format Cartes adaptatives prend en charge la validation des entrées côté client des types Entrée.

### <a name="validation-properties"></a>Propriétés de validation

Les propriétés suivantes sont prises en charge pour la validation dans Cartes adaptatives :

| Entrée | Propriétés |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

Une propriété `errorMessage` est disponible sur tous les types d’entrée afin de spécifier quelle erreur doit être affichée à l’utilisateur s’il saisit une valeur non valide. 

> [!NOTE]
>
> Les propriétés min et max (y compris maxLength) de certaines plateformes peuvent être appliquées directement par le contrôle. Par exemple, une propriété min sur Input.Date peut être appliquée ne permettant pas aux utilisateurs de sélectionner une date antérieure au minimum dans un sélecteur de dates. Dans ce cas, il est possible que le message d’erreur ne s’affiche pas.

## <a name="labels"></a>Étiquettes

La propriété de chaîne `label` est une autre propriété ajoutée dans le schéma version 1.3 pour tous les éléments d’entrée. L’utilisation de la propriété `label` est la méthode recommandée pour étiqueter les entrées dans une carte adaptative, vis-à-vis de la propriété `placeholder` . Il s’agit d’un moyen simple et concis d’étiqueter les entrées pour les auteurs de cartes. Il présente les avantages suivants :
* Indicateurs de validation : comme indiqué ci-dessus, les entrées peuvent maintenant être marquées comme obligatoires, les étiquettes pour les entrées obligatoires auront un indicateur visuel à côté. Cet indicateur visuel est défini dans `HostConfig` et est rendu par défaut sous la forme d’un astérisque `*`.
* Accessibilité : avec une connexion entre les étiquettes et les entrées, les bibliothèques de renderers peuvent définir les propriétés nécessaires pour permettre aux utilisateurs qui se servent des technologies d’assistance (lecteurs d’écran) de pouvoir interagir correctement avec les entrées au sein des cartes adaptatives.
    * Étiquettes ou espaces réservés : comme Katie Sherwin l’explique dans l’article [Placeholders in form fields are harmful](https://www.nngroup.com/articles/form-design-placeholders/), l’utilisation d’espaces réservés a de nombreuses conséquences négatives, telles que la sollicitation de la mémoire à court terme des utilisateurs (ce qui leur rend la tâche plus difficile pour vérifier leurs entrées avant de les soumettre), des difficultés à les lire car, généralement, le texte des espaces réservés présente un contraste de couleurs très faible par rapport à son arrière-plan, l’impossibilité totale pour les lecteurs d’écran de lire le texte des espaces réservés, pour n’en citer que quelques-unes.
    * TextBlock et RichTextBlock : alors que l’utilisation d’autres éléments de carte comme les étiquettes peut sembler être une bonne solution, elle présente le problème de ne pas pouvoir appliquer de proximité entre les entrées et les étiquettes. Par contre, en utilisant la propriété `label`, nous pouvons garantir que les deux éléments visuels sont rendus les uns à côté des autres, ce qui aide les utilisateurs qui ont besoin d’une loupe d’écran.

## <a name="fields-to-be-validated-and-submitted"></a>Champs à valider et à envoyer

Les entrées seront validées lorsque l’utilisateur cliquera sur une action Action.Submit dans la carte. Les entrées qui seront validées et envoyées pour une action Action.Submit donnée sont les suivantes :

 - Entrées sur la même carte que l’action Action.Submit
 - Entrées sur toute carte parent de la carte contenant l’action Action.Submit dans le cas d’une carte sous une action Action.ShowCard

Si ces entrées sont validées, les valeurs de leurs champs sont renvoyées au client. Si elles ne sont pas validées, les messages d’erreur des entrées non valides s’affichent et la soumission n’est pas envoyée.

> [!NOTE]
>
> Les entrées ne seront **pas** validées ni envoyées si elles figurent sur une carte enfant ou frère de la carte contenant l’action Action.Submit. Cela comprend les cartes d’Action.ShowCards dans ActionSets dans le corps de cette carte. Il s’agit d’une modification du comportement par rapport aux versions de rendu antérieures à la version 2.0 qui s’applique aux cartes de toutes les versions de schéma, que les propriétés de validation d’entrée soient ou non utilisées. 

## <a name="other-considerations-and-known-issues"></a>Autres considérations et problèmes connus

 - Il n’est pas recommandé de créer des entrées avec des propriétés de validation susceptibles de ne pas être toujours visibles en raison de l’interaction avec Action.ToggleVisibility. Les messages d’erreur et les indications visuelles selon lesquelles l’entrée n’est pas valide ne s’afficheront pas si l’entrée n’est pas visible actuellement, ce qui peut entraîner une confusion pour les utilisateurs quant à la raison pour laquelle leur soumission est bloquée.

 - Le comportement de la validation d’entrée pour les hôtes utilisant des cartes d’affichage contextuelles à l’aide de la valeur `"actions":"showCard":"actionMode":"popup"` dans leur configuration d’hôte n’est pas bien défini. Il est possible que les cartes d’affichage contextuelles soient déconseillées dans une prochaine version.