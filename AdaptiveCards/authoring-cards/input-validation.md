---
title: Validation d'entrée
author: rebeccaanne
ms.author: rebecch
ms.date: 07/24/2020
ms.topic: article
ms.openlocfilehash: 4c8aa73a218946944b25557eae141e231e8a6ac5
ms.sourcegitcommit: 2a394b75439b382d7bc3134078ecff02429617b8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544961"
---
# <a name="input-validation"></a><span data-ttu-id="179cf-102">Validation d'entrée</span><span class="sxs-lookup"><span data-stu-id="179cf-102">Input Validation</span></span>

<span data-ttu-id="179cf-103">Dans les versions 1.3 et ultérieures du schéma, le format Cartes adaptatives prend en charge la validation des entrées côté client des types Entrée.</span><span class="sxs-lookup"><span data-stu-id="179cf-103">In versions 1.3 and later of the schema, AdaptiveCards supports client side input validation of Input types.</span></span>

### <a name="validation-properties"></a><span data-ttu-id="179cf-104">Propriétés de validation</span><span class="sxs-lookup"><span data-stu-id="179cf-104">Validation Properties</span></span>

<span data-ttu-id="179cf-105">Les propriétés suivantes sont prises en charge pour la validation dans Cartes adaptatives :</span><span class="sxs-lookup"><span data-stu-id="179cf-105">The following properties are supported for validation in AdaptiveCards:</span></span>

| <span data-ttu-id="179cf-106">Entrée</span><span class="sxs-lookup"><span data-stu-id="179cf-106">Input</span></span> | <span data-ttu-id="179cf-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="179cf-107">Properties</span></span> |
| --- | --- | 
| `Input.ChoiceSet` | `isRequired` | 
| `Input.Date` | `isRequired` <br> `min`<br> `max` | 
| `Input.Number` | `isRequired` <br> `min`<br> `max` |
| `Input.Text` | `isRequired` <br> `regex` <br> `maxLength` |
| `Input.Time` | `isRequired` <br> `min`<br> `max` | 
| `Input.Toggle` | `isRequired` | 

<span data-ttu-id="179cf-108">Une propriété `errorMessage` est disponible sur tous les types d’entrée afin de spécifier quelle erreur doit être affichée à l’utilisateur s’il saisit une valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="179cf-108">An `errorMessage` property is available on all input types to specify what error a user should be shown if they enter an invalid value.</span></span> 

> [!NOTE]
>
> <span data-ttu-id="179cf-109">Les propriétés min et max (y compris maxLength) de certaines plateformes peuvent être appliquées directement par le contrôle.</span><span class="sxs-lookup"><span data-stu-id="179cf-109">Min and max properties (including maxLength) on some platforms may be enforced directly by the control.</span></span> <span data-ttu-id="179cf-110">Par exemple, une propriété min sur Input.Date peut être appliquée ne permettant pas aux utilisateurs de sélectionner une date antérieure au minimum dans un sélecteur de dates.</span><span class="sxs-lookup"><span data-stu-id="179cf-110">For example, a min property on Input.Date may be enforced by not allowing users to select a date before the minimum in a date picker.</span></span> <span data-ttu-id="179cf-111">Dans ce cas, il est possible que le message d’erreur ne s’affiche pas.</span><span class="sxs-lookup"><span data-stu-id="179cf-111">In that case, the error message may not be shown.</span></span>

## <a name="fields-to-be-validated-and-submitted"></a><span data-ttu-id="179cf-112">Champs à valider et à envoyer</span><span class="sxs-lookup"><span data-stu-id="179cf-112">Fields to be validated and submitted</span></span>

<span data-ttu-id="179cf-113">Les entrées seront validées lorsque l’utilisateur cliquera sur une action Action.Submit dans la carte.</span><span class="sxs-lookup"><span data-stu-id="179cf-113">Inputs will be validated when the user clicks on an Action.Submit action in the card.</span></span> <span data-ttu-id="179cf-114">Les entrées qui seront validées et envoyées pour une action Action.Submit donnée sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="179cf-114">Those inputs which will be validated and submitted for a given Action.Submit action are:</span></span>

 - <span data-ttu-id="179cf-115">Entrées sur la même carte que l’action Action.Submit</span><span class="sxs-lookup"><span data-stu-id="179cf-115">Inputs on the same card as the Action.Submit</span></span>
 - <span data-ttu-id="179cf-116">Entrées sur toute carte parent de la carte contenant l’action Action.Submit dans le cas d’une carte sous une action Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="179cf-116">Inputs on any parent cards of the card containing the Action.Submit in the case of a card under an Action.ShowCard</span></span>

<span data-ttu-id="179cf-117">Si ces entrées sont validées, les valeurs de leurs champs sont renvoyées au client.</span><span class="sxs-lookup"><span data-stu-id="179cf-117">If those inputs pass validation, the values in their fields will be passed back to the client.</span></span> <span data-ttu-id="179cf-118">Si elles ne sont pas validées, les messages d’erreur des entrées non valides s’affichent et la soumission n’est pas envoyée.</span><span class="sxs-lookup"><span data-stu-id="179cf-118">If they do not pass validation, the error messages for the invalid inputs will be shown, and the submit will not be sent.</span></span>

> [!NOTE]
>
> <span data-ttu-id="179cf-119">Les entrées ne seront **pas** validées ni envoyées si elles figurent sur une carte enfant ou frère de la carte contenant l’action Action.Submit.</span><span class="sxs-lookup"><span data-stu-id="179cf-119">Inputs will **not** be validated or submitted if they are on a card that is a child or sibling card of the card containing the Action.Submit.</span></span> <span data-ttu-id="179cf-120">Cela comprend les cartes d’Action.ShowCards dans ActionSets dans le corps de cette carte.</span><span class="sxs-lookup"><span data-stu-id="179cf-120">This includes cards from Action.ShowCards in ActionSets in the body of that card.</span></span> <span data-ttu-id="179cf-121">Il s’agit d’une modification du comportement par rapport aux versions de rendu antérieures à la version 2.0 qui s’applique aux cartes de toutes les versions de schéma, que les propriétés de validation d’entrée soient ou non utilisées.</span><span class="sxs-lookup"><span data-stu-id="179cf-121">This is a change in behavior from renderer versions prior to 2.0, and applies to cards of all schema versions, regardless of whether input validation properties are used.</span></span> 

## <a name="other-considerations-and-known-issues"></a><span data-ttu-id="179cf-122">Autres considérations et problèmes connus</span><span class="sxs-lookup"><span data-stu-id="179cf-122">Other Considerations and Known Issues</span></span>

 - <span data-ttu-id="179cf-123">Il n’est pas recommandé de créer des entrées avec des propriétés de validation susceptibles de ne pas être toujours visibles en raison de l’interaction avec Action.ToggleVisibility.</span><span class="sxs-lookup"><span data-stu-id="179cf-123">It is not recommended to create inputs with validation properties that may not always be visible due to interaction with Action.ToggleVisibility.</span></span> <span data-ttu-id="179cf-124">Les messages d’erreur et les indications visuelles selon lesquelles l’entrée n’est pas valide ne s’afficheront pas si l’entrée n’est pas visible actuellement, ce qui peut entraîner une confusion pour les utilisateurs quant à la raison pour laquelle leur soumission est bloquée.</span><span class="sxs-lookup"><span data-stu-id="179cf-124">Error messages and visual indications that the input is invalid will not be shown if the input is not currently visible, which may cause confusion for users as to why their submit is blocked.</span></span>

 - <span data-ttu-id="179cf-125">Le comportement de la validation d’entrée pour les hôtes utilisant des cartes d’affichage contextuelles à l’aide de la valeur `"actions":"showCard":"actionMode":"popup"` dans leur configuration d’hôte n’est pas bien défini.</span><span class="sxs-lookup"><span data-stu-id="179cf-125">Behavior of input validation for hosts using popup show cards using the  `"actions":"showCard":"actionMode":"popup"` value in their host config is not well defined.</span></span> <span data-ttu-id="179cf-126">Il est possible que les cartes d’affichage contextuelles soient déconseillées dans une prochaine version.</span><span class="sxs-lookup"><span data-stu-id="179cf-126">Popup show cards may be deprecated in a future release.</span></span>

