---
title: Feuille de route des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/16/2018
ms.topic: article
ms.openlocfilehash: f879c164b3471347ba8fa058827b3d79b09be4cd
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138002"
---
# <a name="future-work"></a><span data-ttu-id="0e517-102">Travail à venir</span><span class="sxs-lookup"><span data-stu-id="0e517-102">Future work</span></span>

<span data-ttu-id="0e517-103">Même si nous avançons à grands pas dans la définition des cartes adaptatives, il reste encore beaucoup de travail à faire.</span><span class="sxs-lookup"><span data-stu-id="0e517-103">While we have made excellent progress defining adaptive cards, there is still lots of work to do.</span></span> <span data-ttu-id="0e517-104">Nous espérons qu’avec des communautés de développeurs actives comme botness et d’excellents partenaires comme Slack et Kik, nous pourrons créer un excellent écosystème de cartes multiplateformes.</span><span class="sxs-lookup"><span data-stu-id="0e517-104">Our hope is that through active developer communities like botness, and great partners like Slack and Kik, we can create a great ecosystem of cross-platform cards.</span></span>

## <a name="roadmap"></a><span data-ttu-id="0e517-105">Feuille de route</span><span class="sxs-lookup"><span data-stu-id="0e517-105">Roadmap</span></span>

<span data-ttu-id="0e517-106">Vous pouvez consulter notre [feuille de route actuelle (non finale) ici](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span><span class="sxs-lookup"><span data-stu-id="0e517-106">You can see our [current (non-final) roadmap here](https://portal.productboard.com/adaptivecards/1-adaptive-cards-portal/tabs/1-backlog).</span></span> <span data-ttu-id="0e517-107">Notez que tout ce qui se trouve ici peut faire l’objet de modifications, et qu’il ne s’agit pas d’une garantie d’expédition.</span><span class="sxs-lookup"><span data-stu-id="0e517-107">Note that anything on here is subject to change, and is not a guarantee of shipping.</span></span>

## <a name="future-ideas"></a><span data-ttu-id="0e517-108">Idées pour l’avenir</span><span class="sxs-lookup"><span data-stu-id="0e517-108">Future ideas</span></span>

<span data-ttu-id="0e517-109">Voici quelques idées pour l’avenir, qui n’en sont encore qu’à l’étape du brainstorming.</span><span class="sxs-lookup"><span data-stu-id="0e517-109">The following are some future ideas we have, which are simply in the brainstorm stage.</span></span> <span data-ttu-id="0e517-110">Si elles vous intéressent, faites-le nous savoir dans un commentaire.</span><span class="sxs-lookup"><span data-stu-id="0e517-110">If you're interested in any of these, let us know in a comment.</span></span>

### <a name="great-looking-cards-from-data"></a><span data-ttu-id="0e517-111">Jolies cartes à partir des données</span><span class="sxs-lookup"><span data-stu-id="0e517-111">Great looking Cards from Data</span></span>

<span data-ttu-id="0e517-112">Nous savons que de nombreux auteurs de cartes ont déjà des données bien définies sous-jacentes à leurs cartes.</span><span class="sxs-lookup"><span data-stu-id="0e517-112">We know many card authors already have well-defined data behind their cards.</span></span> <span data-ttu-id="0e517-113">Notre plan consiste à explorer un modèle de création de modèles qui permettrait la génération de cartes (côté serveur ou côté client) en fonction des données et un référentiel de modèles bien définis et personnalisables.</span><span class="sxs-lookup"><span data-stu-id="0e517-113">Our plan is to explore a templating model that would allow cards to be generated (server side or client side) based on the data and a repository of well-defined and customizable templates.</span></span>

### <a name="make-cards-responsive"></a><span data-ttu-id="0e517-114">Rendre les cartes réactives</span><span class="sxs-lookup"><span data-stu-id="0e517-114">Make cards responsive</span></span>

<span data-ttu-id="0e517-115">Les dispositions de cartes doivent être réactives à l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="0e517-115">Card layouts should be reactive to available space.</span></span> <span data-ttu-id="0e517-116">Les cartes adaptatives sont adaptables à différents appareils, styles d’expérience utilisateur et frameworks d’interface utilisateur, mais elles ne sont pas encore réactives.</span><span class="sxs-lookup"><span data-stu-id="0e517-116">Adaptive cards are adaptable to different devices, ux styles and and ui frameworks, but they are not reactive yet.</span></span> <span data-ttu-id="0e517-117">Des propriétés supplémentaires doivent être définies sur les éléments afin de permettre aux producteurs de cartes de fournir aux bibliothèques de rendu les indications nécessaires leur permettant de changer intelligemment la disposition d’une manière qui conserve l’intention de la carte.</span><span class="sxs-lookup"><span data-stu-id="0e517-117">Additional properties must be defined on elements which allow card producers to provide the necessary hints to the rendering libraries so that they can intelligently change the layout in a way which maintains the intent of the card.</span></span>

### <a name="responsive-exploration"></a><span data-ttu-id="0e517-118">Exploration réactive</span><span class="sxs-lookup"><span data-stu-id="0e517-118">Responsive exploration</span></span>

* <span data-ttu-id="0e517-119">Ajouter une propriété d’**importance** qui annote l’importance du contenu.</span><span class="sxs-lookup"><span data-stu-id="0e517-119">Add an **importance** property which annotates importance of content.</span></span> <span data-ttu-id="0e517-120">Le contenu moins important peut être supprimé afin que le contenu restant tienne dans l’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="0e517-120">Less important content can be dropped to fit available space</span></span>
* <span data-ttu-id="0e517-121">Ajouter des **contraintes** et des propriétés de **stratégie** décrivant comment réagir quand les contraintes ne peuvent pas être satisfaites.</span><span class="sxs-lookup"><span data-stu-id="0e517-121">Add **constraints** and **policy** properties describing how to react when constraints can't be met.</span></span> 
  * <span data-ttu-id="0e517-122">Masquer le contenu ou réduire le contenu à une taille plus petite.</span><span class="sxs-lookup"><span data-stu-id="0e517-122">Hide content or collapse content to smaller size.</span></span>
  * <span data-ttu-id="0e517-123">Ajouter un seuil qui, en cas de dépassement, change `columnSet` en carrousel de colonnes.</span><span class="sxs-lookup"><span data-stu-id="0e517-123">Add a threshold that, when exceeded, changes `columnSet` to carousel of columns.</span></span>

### <a name="new-element-types"></a><span data-ttu-id="0e517-124">Nouveaux types d’éléments</span><span class="sxs-lookup"><span data-stu-id="0e517-124">New element types</span></span>

* <span data-ttu-id="0e517-125">Cartes ?</span><span class="sxs-lookup"><span data-stu-id="0e517-125">Maps?</span></span> <span data-ttu-id="0e517-126">- Incorporer une carte géographique dans une carte adaptative avec interactivité ou retour à la bitmap.</span><span class="sxs-lookup"><span data-stu-id="0e517-126">- embed a map into a card with interactivity or fallback to bitmap</span></span>
* <span data-ttu-id="0e517-127">*Quels éléments souhaitez-vous ou vous faut-il* ?</span><span class="sxs-lookup"><span data-stu-id="0e517-127">*What elements do you want or need*?</span></span>

### <a name="new-rendering-libraries"></a><span data-ttu-id="0e517-128">Nouvelles bibliothèques de rendu</span><span class="sxs-lookup"><span data-stu-id="0e517-128">New rendering libraries</span></span>

* <span data-ttu-id="0e517-129">React ?</span><span class="sxs-lookup"><span data-stu-id="0e517-129">React?</span></span>
* <span data-ttu-id="0e517-130">Xamarin ?</span><span class="sxs-lookup"><span data-stu-id="0e517-130">Xamarin?</span></span>
* <span data-ttu-id="0e517-131">*Quels frameworks souhaitez-vous ?*</span><span class="sxs-lookup"><span data-stu-id="0e517-131">*What frameworks do you want?*</span></span>
