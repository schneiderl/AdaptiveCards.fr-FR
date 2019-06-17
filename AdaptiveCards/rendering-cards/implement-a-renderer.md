---
title: Implémentation d’un Renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: b39493f82f3378e5a554abc6df890d6821869671
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138022"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="f7a8b-102">Spécification de convertisseur de carte adaptative</span><span class="sxs-lookup"><span data-stu-id="f7a8b-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="f7a8b-103">La spécification suivante décrit comment implémenter un convertisseur de carte adaptative sur n’importe quelle plateforme de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="f7a8b-104">Ce contenu n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-104">This content is not finished yet.</span></span> <span data-ttu-id="f7a8b-105">Revenez plus tard.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="f7a8b-106">Kit de développement logiciel de contrôle de version</span><span class="sxs-lookup"><span data-stu-id="f7a8b-106">SDK Versioning</span></span>

1. <span data-ttu-id="f7a8b-107">La version majeure et mineure de kit de développement logiciel **SHOULD** correspond à la `schema` version.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="f7a8b-108">Correctif/build **SHOULD** être utilisé pour les mises à jour de convertisseur qui n’ont pas les modifications de schéma.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="f7a8b-109">L’analyse JSON</span><span class="sxs-lookup"><span data-stu-id="f7a8b-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="f7a8b-110">Conditions d’erreur</span><span class="sxs-lookup"><span data-stu-id="f7a8b-110">Error conditions</span></span>
1. <span data-ttu-id="f7a8b-111">Un analyseur **doit** vérifier qu’il s’agit d’un contenu JSON valid</span><span class="sxs-lookup"><span data-stu-id="f7a8b-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="f7a8b-112">Un analyseur **doit** valider par rapport au schéma (propriétés requises, etc.)</span><span class="sxs-lookup"><span data-stu-id="f7a8b-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="f7a8b-113">Les erreurs ci-dessus **doit** être signalées à l’application hôte (exception ou équivalent)</span><span class="sxs-lookup"><span data-stu-id="f7a8b-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="f7a8b-114">Types inconnus</span><span class="sxs-lookup"><span data-stu-id="f7a8b-114">Unknown types</span></span>
1. <span data-ttu-id="f7a8b-115">Si vous rencontrez des types « inconnus » ils **doivent être supprimés** à partir du résultat</span><span class="sxs-lookup"><span data-stu-id="f7a8b-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="f7a8b-116">Toutes les modifications de la charge utile (comme ci-dessus) **SHOULD** soient signalés comme avertissements à l’application hôte</span><span class="sxs-lookup"><span data-stu-id="f7a8b-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="f7a8b-117">Propriétés inconnues</span><span class="sxs-lookup"><span data-stu-id="f7a8b-117">Unknown properties</span></span>
1. <span data-ttu-id="f7a8b-118">Un analyseur **doit** incluent **supplémentaires** propriétés sur les éléments</span><span class="sxs-lookup"><span data-stu-id="f7a8b-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="f7a8b-119">Considérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f7a8b-119">Additional considerations</span></span>
1. <span data-ttu-id="f7a8b-120">Le `speak` propriété peut contenir un balisage SSML et **doit** être renvoyé à l’application de l’hôte spécifié en tant que</span><span class="sxs-lookup"><span data-stu-id="f7a8b-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="f7a8b-121">L’analyse de configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="f7a8b-121">Parsing Host Config</span></span>
1. <span data-ttu-id="f7a8b-122">TODO</span><span class="sxs-lookup"><span data-stu-id="f7a8b-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="f7a8b-123">Contrôle de version</span><span class="sxs-lookup"><span data-stu-id="f7a8b-123">Versioning</span></span>

1. <span data-ttu-id="f7a8b-124">Un convertisseur **doit** implémenter une version particulière du schéma.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="f7a8b-125">Le `AdaptiveCard` constructeur **doit** donner le `version` propriété une valeur par défaut en fonction de la version actuelle du schéma</span><span class="sxs-lookup"><span data-stu-id="f7a8b-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="f7a8b-126">Si un convertisseur rencontre un `version` propriété dans le `AdaptiveCard` qui est supérieure à la version prise en charge, il **doit** retourner le `fallbackText` à la place.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="f7a8b-127">Rendu</span><span class="sxs-lookup"><span data-stu-id="f7a8b-127">Rendering</span></span>

<span data-ttu-id="f7a8b-128">Un `AdaptiveCard` se compose d’un `body` et `actions`.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="f7a8b-129">Le `body` est une collection de `CardElement`s qui sera un convertisseur d’énumérer et de restituer dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="f7a8b-130">Chaque élément **doit** stretch de la largeur de son parent (pensez `display: block` au format HTML).</span><span class="sxs-lookup"><span data-stu-id="f7a8b-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="f7a8b-131">Un convertisseur **doit** ignorer les types d’élément inconnu et continuer le reste de la charge utile de rendu.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="f7a8b-132">L’espacement et les séparateurs</span><span class="sxs-lookup"><span data-stu-id="f7a8b-132">Spacing and Separators</span></span>

1. <span data-ttu-id="f7a8b-133">Le `spacing` propriété sur chaque élément a un impact sur la quantité d’espace entre le **actuel** élément et celui **BEFORE** il.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="f7a8b-134">Espacement **doit uniquement** s’appliquent lorsqu’il est en fait un élément qui précède.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="f7a8b-135">(Par exemple, ne s’appliquent pas au premier élément dans un tableau)</span><span class="sxs-lookup"><span data-stu-id="f7a8b-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="f7a8b-136">Un convertisseur **doit** rechercher la quantité d’espace à utiliser à partir de la `hostConfig` espacement pour la valeur enum appliquée à l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="f7a8b-137">Si l’élément a un `separator` valeur `true`, puis une ligne visible **doit** être tracée entre l’élément actuel et celle qui précède.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="f7a8b-138">La ligne de séparation **doit** être dessiné en utilisant le `container.style.default.foregroundColor`.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="f7a8b-139">Un séparateur **doit uniquement** être dessiné Si l’élément **IS NOT** le premier dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="f7a8b-140">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f7a8b-140">Columns</span></span>

1. <span data-ttu-id="f7a8b-141">`Column` `width` **DOIT** être interprétées par « auto », « stretch » ou un ratio pondéré.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="f7a8b-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="f7a8b-142">TextBlock</span></span>

1. <span data-ttu-id="f7a8b-143">Un TextBlock **doit** occupe une seule ligne, sauf si le `wrap` propriété est `true`.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="f7a8b-144">Le bloc de texte **SHOULD** trim n’importe quel texte excessive des points de suspension (...)</span><span class="sxs-lookup"><span data-stu-id="f7a8b-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="f7a8b-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="f7a8b-145">Markdown</span></span>

1. <span data-ttu-id="f7a8b-146">Des cartes adaptatives autorisant pour un sous-ensemble de Markdown et **SHOULD** pris en charge dans `TextBlock`.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="f7a8b-147">Consultez complète [les exigences de markdown](../authoring-cards/text-features.md)</span><span class="sxs-lookup"><span data-stu-id="f7a8b-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="f7a8b-148">Fonctions de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f7a8b-148">Formatting functions</span></span>

1. <span data-ttu-id="f7a8b-149">`TextBlock` permet de [mise en forme de fonctions DATE/heure](../authoring-cards/text-features.md) qui **doit** pris en charge par chaque convertisseur.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="f7a8b-150">**DOIT de tous les échecs de** afficher la chaîne brute dans la carte.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="f7a8b-151">Aucun message convivial tentée.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-151">No friendly message attempted.</span></span> <span data-ttu-id="f7a8b-152">(En cours pour que le développeur soit conscient immédiatement il vise un problème)</span><span class="sxs-lookup"><span data-stu-id="f7a8b-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="f7a8b-153">TODO : Inclure des expressions régulières</span><span class="sxs-lookup"><span data-stu-id="f7a8b-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="f7a8b-154">Images</span><span class="sxs-lookup"><span data-stu-id="f7a8b-154">Images</span></span>

1. <span data-ttu-id="f7a8b-155">Un convertisseur **SHOULD** permettent d’héberger des applications de savoir lorsque toutes les images HTTP ont été téléchargées et la carte est « entièrement restituée »</span><span class="sxs-lookup"><span data-stu-id="f7a8b-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="f7a8b-156">Un convertisseur **doit** inspecter la configuration de l’hôte `maxImageSize` param lors du téléchargement des images HTTP</span><span class="sxs-lookup"><span data-stu-id="f7a8b-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="f7a8b-157">Un convertisseur **doit** prennent en charge `.png` et `.jpeg`</span><span class="sxs-lookup"><span data-stu-id="f7a8b-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="f7a8b-158">Un convertisseur **SHOULD** prennent en charge `.gif` images</span><span class="sxs-lookup"><span data-stu-id="f7a8b-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="f7a8b-159">Configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="f7a8b-159">Host Config</span></span>

* <span data-ttu-id="f7a8b-160">TODO : Que doivent contenir les valeurs par défaut ?</span><span class="sxs-lookup"><span data-stu-id="f7a8b-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="f7a8b-161">Doivent tous partager ?</span><span class="sxs-lookup"><span data-stu-id="f7a8b-161">Should they all share it?</span></span> <span data-ttu-id="f7a8b-162">Devons-nous incorporer un fichier hostConfig.json commun dans les fichiers binaires ?</span><span class="sxs-lookup"><span data-stu-id="f7a8b-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="f7a8b-163">TODO : Je pense que HostConfig a besoin de gérer les versions ainsi qu’à l’analyse ?</span><span class="sxs-lookup"><span data-stu-id="f7a8b-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="f7a8b-164">[`HostConfig`](host-config.md) est un objet de configuration partagée qui spécifie comment un convertisseur de carte adaptative génère l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="f7a8b-165">Ainsi, les propriétés qui sont indépendante de la plateforme à partager entre les convertisseurs sur différentes plateformes et appareils.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="f7a8b-166">Il permet également à créer des outils qui vous donne une idée de l’apparence que la carte aurait pour un environnement donné.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="f7a8b-167">Convertisseurs **doit** exposer un **configuration de l’hôte** paramètre pour héberger des applications</span><span class="sxs-lookup"><span data-stu-id="f7a8b-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="f7a8b-168">Tous les éléments **doit** un style en fonction de leurs paramètres respectifs de la configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="f7a8b-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="f7a8b-169">Style de la plateforme native</span><span class="sxs-lookup"><span data-stu-id="f7a8b-169">Native platform styling</span></span>

1. <span data-ttu-id="f7a8b-170">Chaque type d’élément **SHOULD** attacher un style de la plateforme native avec l’élément d’interface généré.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="f7a8b-171">Par exemple, au format HTML, nous avons ajouté une classe CSS pour les types d’élément, et dans XAML, nous attribuons un Style spécifique.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="f7a8b-172">Extensibilité</span><span class="sxs-lookup"><span data-stu-id="f7a8b-172">Extensibility</span></span> 

1. <span data-ttu-id="f7a8b-173">Un convertisseur **doit** permettent d’héberger des applications remplacer les convertisseurs d’élément par défaut.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="f7a8b-174">Par exemple, remplacez `TextBlock` avec leur propre logique de rendu.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="f7a8b-175">Un convertisseur **doit** permettent d’héberger des applications inscrire les types d’élément personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="f7a8b-176">Par exemple, ajouter la prise en charge pour un personnalisé `Rating` élément</span><span class="sxs-lookup"><span data-stu-id="f7a8b-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="f7a8b-177">Un convertisseur **doit** permettent d’héberger des applications supprimer la prise en charge pour un élément par défaut.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="f7a8b-178">Par exemple, supprimez `Action.Submit` s’ils ne veulent plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="f7a8b-179">Actions</span><span class="sxs-lookup"><span data-stu-id="f7a8b-179">Actions</span></span>

1. <span data-ttu-id="f7a8b-180">Si HostConfig `supportsInteractivity` est `false`, un convertisseur **ne doit pas** afficher toutes les actions.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="f7a8b-181">Le `actions` propriété **doit** être restitué sous forme de boutons dans une sorte de barre d’action, généralement en bas de la carte.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="f7a8b-182">Lorsque l’utilisateur appuie sur un bouton il **doit** permettent à l’application hôte gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="f7a8b-183">L’événement **doit** passe le long de toutes les propriétés associées avec l’action</span><span class="sxs-lookup"><span data-stu-id="f7a8b-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="f7a8b-184">L’événement **doit** transmettent le `AdaptiveCard` qui a été exécuté</span><span class="sxs-lookup"><span data-stu-id="f7a8b-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="f7a8b-185">Action</span><span class="sxs-lookup"><span data-stu-id="f7a8b-185">Action</span></span> | <span data-ttu-id="f7a8b-186">Comportement</span><span class="sxs-lookup"><span data-stu-id="f7a8b-186">Behavior</span></span>
--- | ---
<span data-ttu-id="f7a8b-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="f7a8b-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="f7a8b-188">Ouvrir une URL externe pour l’affichage</span><span class="sxs-lookup"><span data-stu-id="f7a8b-188">Open an external URL for viewing</span></span>
<span data-ttu-id="f7a8b-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="f7a8b-189">**Action.ShowCard**</span></span> | <span data-ttu-id="f7a8b-190">Demande une entrée secondaire à afficher à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="f7a8b-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="f7a8b-191">**Action.Submit**</span></span> | <span data-ttu-id="f7a8b-192">Demandez à tous les éléments d’entrée à collecter dans un objet qui est ensuite envoyé via une méthode définie par l’application hôte pour vous.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="f7a8b-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="f7a8b-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="f7a8b-194">`Action.OpenUrl` **DOIT** ouvrir une URL en utilisant le mécanisme de plateforme native</span><span class="sxs-lookup"><span data-stu-id="f7a8b-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="f7a8b-195">Si ce n’est pas possible il **doit** déclencher un événement à l’application hôte pour gérer l’ouverture de l’URL.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="f7a8b-196">Cet événement **doit** permettent à l’application hôte de substituer le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="f7a8b-197">Par exemple, leur permettent d’ouvrir l’URL dans leur propre application.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="f7a8b-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="f7a8b-198">Action.ShowCard</span></span>

1. <span data-ttu-id="f7a8b-199">`Action.ShowCard` **DOIT** pris en charge d’une certaine façon, en fonction du paramètre hostConfig.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="f7a8b-200">Il existe deux modes : inline et la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="f7a8b-201">Les cartes inline **SHOULD** activer/désactiver la visibilité de la carte automatiquement.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="f7a8b-202">En mode de menu contextuel, un événement **SHOULD** être déclenché à l’application hôte pour afficher la carte d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="f7a8b-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="f7a8b-203">Action.Submit</span></span>

<span data-ttu-id="f7a8b-204">L’Action Envoyer se comporte comme un envoi de formulaire HTML, à ceci près qu’où HTML déclenche généralement une requête HTTP post, des cartes adaptatives laisse jusqu'à chaque application hôte pour déterminer ce que « soumettre » signifie que leur.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="f7a8b-205">Lorsque cela **doit** déclencher un événement que l’utilisateur appuie sur l’action appelée.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="f7a8b-206">Le `data` propriété **doit** être inclus dans la charge utile de rappel.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="f7a8b-207">Pour `Action.Submit`, un convertisseur **doit** rassembler toutes les entrées sur la carte et de récupérer les valeurs.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="f7a8b-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="f7a8b-208">selectAction</span></span>

1. <span data-ttu-id="f7a8b-209">Si configuration de l’hôte `supportedInteractivity` est `false` un `selectAction` **ne doit pas** restituées en tant qu’une cible tactile.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="f7a8b-210">`Image`, `ColumnSet`, et `Column` offrent un `selectAction` propriété, laquelle **SHOULD** à exécuter lorsque l’utilisateur l’appelle, par exemple, en appuyant sur l’élément.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="f7a8b-211">Entrées</span><span class="sxs-lookup"><span data-stu-id="f7a8b-211">Inputs</span></span>

1. <span data-ttu-id="f7a8b-212">Si HostConfig `supportsInteractivity` est `false` un convertisseur **ne doit pas** afficher toutes les entrées.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="f7a8b-213">Entrées **SHOULD** afficher avec la plus haute fidélité possible.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="f7a8b-214">Par exemple, un `Input.Date` offrirait dans l’idéal, un sélecteur de dates à un utilisateur, mais si ce n’est pas possible sur votre pile de l’interface utilisateur, puis le convertisseur **doit** revenir au rendu d’une zone de texte standard.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="f7a8b-215">Un convertisseur **SHOULD** afficher le `placeholderText` si possible</span><span class="sxs-lookup"><span data-stu-id="f7a8b-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="f7a8b-216">Un convertisseur **ne** obligé d’implémenter la validation de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="f7a8b-217">Les utilisateurs de cartes adaptatives doivent planifier valider toutes les données reçues de leur côté.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="f7a8b-218">Liaison de la valeur d’entrée **doit** être correctement échappés</span><span class="sxs-lookup"><span data-stu-id="f7a8b-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="f7a8b-219">L’objet **doit** renvoyés à l’application hôte comme suit :</span><span class="sxs-lookup"><span data-stu-id="f7a8b-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="f7a8b-220">Nous ne faites pas les promesses de validation d’entrée dans des cartes adaptatives, il est donc à la partie réception à analyser correctement la réponse.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="f7a8b-221">Par exemple, un Input.Number peut renvoyer « hello » et ils doivent être préparées pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="f7a8b-222">Events</span><span class="sxs-lookup"><span data-stu-id="f7a8b-222">Events</span></span>

1. <span data-ttu-id="f7a8b-223">Un convertisseur **SHOULD** déclencher un événement lorsqu’une visibilité d’un élément a changé, ce qui permet l’application hôte faire défiler la carte dans sa position.</span><span class="sxs-lookup"><span data-stu-id="f7a8b-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
