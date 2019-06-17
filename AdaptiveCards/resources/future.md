---
title: Feuille de route des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138002"
---
# <a name="future-work"></a><span data-ttu-id="f8c83-102">Travaux futurs</span><span class="sxs-lookup"><span data-stu-id="f8c83-102">Future work</span></span>

<span data-ttu-id="f8c83-103">Nous avons fait des progrès considérables définissant des cartes adaptatives, mais il existe toujours un grand nombre de tâches à effectuer.</span><span class="sxs-lookup"><span data-stu-id="f8c83-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="f8c83-104">Notre espoir est que via les Communautés de développeurs active comme botness et des partenaires comme Slack et Kik, nous pouvons créer un écosystème exceptionnel de cartes d’inter-plateformes.</span><span class="sxs-lookup"><span data-stu-id="f8c83-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="f8c83-105">Feuille de route</span><span class="sxs-lookup"><span data-stu-id="f8c83-105">Roadmap</span></span>

<span data-ttu-id="f8c83-106">Vous pouvez voir notre [actuel (non finale) feuille de route ici](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="f8c83-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="f8c83-107">Notez que quoi que ce soit ici est susceptible de changer et n’est pas une garantie de livraison.</span><span class="sxs-lookup"><span data-stu-id="f8c83-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="f8c83-108">Idées futures</span><span class="sxs-lookup"><span data-stu-id="f8c83-108">Future ideas</span></span>

<span data-ttu-id="f8c83-109">Voici quelques idées futures, que nous avons, qui sont simplement dans la scène réfléchi.</span><span class="sxs-lookup"><span data-stu-id="f8c83-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="f8c83-110">Si vous êtes intéressé par un de ces, faites-le nous savoir dans un commentaire.</span><span class="sxs-lookup"><span data-stu-id="f8c83-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="f8c83-111">Excellents cartes qui recherchent des données</span><span class="sxs-lookup"><span data-stu-id="f8c83-111">Great looking Cards from Data</span></span>

<span data-ttu-id="f8c83-112">Nous savons de nombreux auteurs de carte disposez déjà de données bien définies derrière leurs cartes.</span><span class="sxs-lookup"><span data-stu-id="f8c83-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="f8c83-113">Notre objectif est d’Explorer un modèle de création de modèles qui permettrait de cartes à générer (côté serveur ou côté client) basé sur les données et un référentiel de modèles bien définis et personnalisables.</span><span class="sxs-lookup"><span data-stu-id="f8c83-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="f8c83-114">Rendre des cartes réactive</span><span class="sxs-lookup"><span data-stu-id="f8c83-114">Make cards responsive</span></span>

<span data-ttu-id="f8c83-115">Dispositions de la carte doivent être réactives à l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="f8c83-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="f8c83-116">Des cartes adaptatives sont adaptables aux différents appareils, les styles de l’expérience utilisateur et et infrastructures d’interface utilisateur, mais ils ne sont pas réactives encore.</span><span class="sxs-lookup"><span data-stu-id="f8c83-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="f8c83-117">Propriétés supplémentaires doivent être définies sur les éléments qui permettent les producteurs de carte fournir les indications nécessaires pour les bibliothèques de rendu afin qu’ils peuvent modifier intelligemment la disposition d’une façon qui conserve l’intention de la carte.</span><span class="sxs-lookup"><span data-stu-id="f8c83-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="f8c83-118">Exploration réactive</span><span class="sxs-lookup"><span data-stu-id="f8c83-118">Responsive exploration</span></span>

* <span data-ttu-id="f8c83-119">Ajouter un **importance** propriété qui annote l’importance du contenu.</span><span class="sxs-lookup"><span data-stu-id="f8c83-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="f8c83-120">Contenu moins importante peut être supprimé pour s’ajuster à la quantité d’espace disponible</span><span class="sxs-lookup"><span data-stu-id="f8c83-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="f8c83-121">Ajouter **contraintes** et **stratégie** propriétés décrivant comment réagir lorsque les contraintes ne peuvent pas être satisfaites.</span><span class="sxs-lookup"><span data-stu-id="f8c83-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="f8c83-122">Masquer le contenu ou réduire le contenu à la plus petite taille.</span><span class="sxs-lookup"><span data-stu-id="f8c83-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="f8c83-123">Ajoutez un seuil qui, lorsque dépassée, change `columnSet` à carrousel de colonnes.</span><span class="sxs-lookup"><span data-stu-id="f8c83-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="f8c83-124">Nouveaux types d’élément</span><span class="sxs-lookup"><span data-stu-id="f8c83-124">New element types</span></span>

* <span data-ttu-id="f8c83-125">Mappages ?</span><span class="sxs-lookup"><span data-stu-id="f8c83-125">Maps?</span></span> <span data-ttu-id="f8c83-126">-intégrer une carte dans une carte avec la stratégie de secours en bitmap ou l’interactivité</span><span class="sxs-lookup"><span data-stu-id="f8c83-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="f8c83-127">*Quels éléments souhaitez-vous ou devez*?</span><span class="sxs-lookup"><span data-stu-id="f8c83-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="f8c83-128">Nouvelles bibliothèques de rendu</span><span class="sxs-lookup"><span data-stu-id="f8c83-128">New rendering libraries</span></span>

* <span data-ttu-id="f8c83-129">Réagir ?</span><span class="sxs-lookup"><span data-stu-id="f8c83-129">React?</span></span>
* <span data-ttu-id="f8c83-130">Xamarin ?</span><span class="sxs-lookup"><span data-stu-id="f8c83-130">Xamarin?</span></span>
* <span data-ttu-id="f8c83-131">*Quelles infrastructures voulez-vous ?*</span><span class="sxs-lookup"><span data-stu-id="f8c83-131">*What frameworks do you want?*</span></span>
