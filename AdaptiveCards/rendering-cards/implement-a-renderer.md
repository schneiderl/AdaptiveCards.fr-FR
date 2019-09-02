---
title: Implémentation d’un renderer
author: matthidinger
ms.author: mahiding
ms.date: 09/15/2017
ms.topic: article
ms.openlocfilehash: b39493f82f3378e5a554abc6df890d6821869671
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67138022"
---
# <a name="adaptive-card-renderer-specification"></a><span data-ttu-id="f58f6-102">Spécification de renderer de carte adaptative</span><span class="sxs-lookup"><span data-stu-id="f58f6-102">Adaptive Card Renderer Specification</span></span>

<span data-ttu-id="f58f6-103">La spécification suivante décrit comment implémenter un renderer de carte adaptative sur une plateforme d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f58f6-103">The following specification describes how implement an Adaptive Card renderer on any UI platform.</span></span>

> [!IMPORTANT]
> 
> <span data-ttu-id="f58f6-104">Ce contenu n’est pas encore terminé.</span><span class="sxs-lookup"><span data-stu-id="f58f6-104">This content is not finished yet.</span></span> <span data-ttu-id="f58f6-105">N’hésitez pas à y revenir sous peu.</span><span class="sxs-lookup"><span data-stu-id="f58f6-105">Check back shortly.</span></span>

## <a name="sdk-versioning"></a><span data-ttu-id="f58f6-106">Gestion des versions de l’API</span><span class="sxs-lookup"><span data-stu-id="f58f6-106">SDK Versioning</span></span>

1. <span data-ttu-id="f58f6-107">La version principale et la version mineure du SDK **DOIVENT** correspondre à la version de `schema`.</span><span class="sxs-lookup"><span data-stu-id="f58f6-107">The SDK major and minor version **SHOULD** match the `schema` version.</span></span> 
1. <span data-ttu-id="f58f6-108">Un correctif/une build **DOIT** être utilisé(e) pour les mises à jour du renderer qui n’ont pas de modifications de schéma.</span><span class="sxs-lookup"><span data-stu-id="f58f6-108">Patch/build **SHOULD** be used for renderer updates that don't have schema changes.</span></span>

## <a name="parsing-json"></a><span data-ttu-id="f58f6-109">Analyse du JSON</span><span class="sxs-lookup"><span data-stu-id="f58f6-109">Parsing JSON</span></span>

### <a name="error-conditions"></a><span data-ttu-id="f58f6-110">Conditions d’erreur</span><span class="sxs-lookup"><span data-stu-id="f58f6-110">Error conditions</span></span>
1. <span data-ttu-id="f58f6-111">Un analyseur **DOIT** vérifier qu’il s’agit de contenu JSON valide.</span><span class="sxs-lookup"><span data-stu-id="f58f6-111">A parser **MUST** check that it's valid JSON content</span></span>
1. <span data-ttu-id="f58f6-112">Un analyseur **DOIT** effectuer une validation par rapport au schéma (propriétés requises, etc.).</span><span class="sxs-lookup"><span data-stu-id="f58f6-112">A parser **MUST** validate against the schema (required properties, etc)</span></span>
1. <span data-ttu-id="f58f6-113">Les erreurs ci-dessus **DOIVENT** être signalées à l’application hôte (exception ou équivalent).</span><span class="sxs-lookup"><span data-stu-id="f58f6-113">The above errors **MUST** be reported to the host app (exception or equivalent)</span></span>

### <a name="unknown-types"></a><span data-ttu-id="f58f6-114">Types inconnus</span><span class="sxs-lookup"><span data-stu-id="f58f6-114">Unknown types</span></span>
1. <span data-ttu-id="f58f6-115">Si des « types » inconnus sont détectés, ils **DOIVENT ÊTRE SUPPRIMÉS** du résultat.</span><span class="sxs-lookup"><span data-stu-id="f58f6-115">If unknown "types" are encountered they **MUST BE DROPPED** from the result</span></span>
1. <span data-ttu-id="f58f6-116">Toute modification de la charge utile (comme ci-dessus) **DOIT** être signalée comme avertissement à l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="f58f6-116">Any alterations of the payload (like above) **SHOULD** be reported as warnings to the host app</span></span>

### <a name="unknown-properties"></a><span data-ttu-id="f58f6-117">Propriétés inconnues</span><span class="sxs-lookup"><span data-stu-id="f58f6-117">Unknown properties</span></span>
1. <span data-ttu-id="f58f6-118">Un analyseur **DOIT** inclure des propriétés **supplémentaires** sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="f58f6-118">A parser **MUST** include **additional** properties on elements</span></span>

### <a name="additional-considerations"></a><span data-ttu-id="f58f6-119">Considérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f58f6-119">Additional considerations</span></span>
1. <span data-ttu-id="f58f6-120">La propriété `speak` peut contenir du balisage SSML et **DOIT** être retournée à l’application hôte telle qu’elle est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f58f6-120">The `speak` property may contain SSML markup and **MUST** be returned to the host app as-specified</span></span>

## <a name="parsing-host-config"></a><span data-ttu-id="f58f6-121">Analyse de la configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="f58f6-121">Parsing Host Config</span></span>
1. <span data-ttu-id="f58f6-122">TODO</span><span class="sxs-lookup"><span data-stu-id="f58f6-122">TODO</span></span>

## <a name="versioning"></a><span data-ttu-id="f58f6-123">Contrôle de version</span><span class="sxs-lookup"><span data-stu-id="f58f6-123">Versioning</span></span>

1. <span data-ttu-id="f58f6-124">Un renderer **DOIT** implémenter une version particulière du schéma.</span><span class="sxs-lookup"><span data-stu-id="f58f6-124">A renderer **MUST** implement a particular version of the schema.</span></span> 
1. <span data-ttu-id="f58f6-125">Le constructeur `AdaptiveCard` **DOIT** attribuer à la propriété `version` une valeur par défaut basée sur la version actuelle du schéma.</span><span class="sxs-lookup"><span data-stu-id="f58f6-125">The `AdaptiveCard` constructor **MUST** give the `version` property a default value based on the current schema version</span></span> 
1. <span data-ttu-id="f58f6-126">Si un renderer rencontre une propriété `version` dans le `AdaptiveCard` qui est supérieure à la version prise en charge, il **DOIT** retourner le `fallbackText` à la place.</span><span class="sxs-lookup"><span data-stu-id="f58f6-126">If a renderer encounters a `version` property in the `AdaptiveCard` that is higher than the supported version, it **MUST** return the `fallbackText` instead.</span></span>

## <a name="rendering"></a><span data-ttu-id="f58f6-127">Rendu</span><span class="sxs-lookup"><span data-stu-id="f58f6-127">Rendering</span></span>

<span data-ttu-id="f58f6-128">Un `AdaptiveCard` est constitué d’un `body` et d’`actions`.</span><span class="sxs-lookup"><span data-stu-id="f58f6-128">An `AdaptiveCard` consists of a `body` and `actions`.</span></span> <span data-ttu-id="f58f6-129">Le `body` est une collection de `CardElement`s qu’un renderer énumère et affiche dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="f58f6-129">The `body` is a collection of `CardElement`s that a renderer will enumerate and render in order.</span></span> 

1. <span data-ttu-id="f58f6-130">Chaque élément **DOIT** s’étendre à la largeur de son parent (pensez à `display: block` HTML).</span><span class="sxs-lookup"><span data-stu-id="f58f6-130">Each Element **MUST** stretch to the width of its parent (think `display: block` in HTML).</span></span>
1. <span data-ttu-id="f58f6-131">Un renderer **DOIT** ignorer les types d’éléments inconnus et continuer le rendu du reste de la charge utile.</span><span class="sxs-lookup"><span data-stu-id="f58f6-131">A renderer **MUST** ignore unknown element types, and continue rendering the rest of the payload.</span></span>

### <a name="spacing-and-separators"></a><span data-ttu-id="f58f6-132">Espacement et séparateurs</span><span class="sxs-lookup"><span data-stu-id="f58f6-132">Spacing and Separators</span></span>

1. <span data-ttu-id="f58f6-133">La propriété `spacing` sur chaque élément influence la quantité d’espace entre l’élément **ACTUEL** et celui qui le **PRÉCÈDE**.</span><span class="sxs-lookup"><span data-stu-id="f58f6-133">The `spacing` property on every element influences the amount of space between the **CURRENT** element and the one **BEFORE** it.</span></span>
1. <span data-ttu-id="f58f6-134">L’espacement **DOIT UNIQUEMENT** s’appliquer quand il existe réellement un élément qui le précède.</span><span class="sxs-lookup"><span data-stu-id="f58f6-134">Spacing **MUST ONLY** apply when there actually is an element preceding it.</span></span> <span data-ttu-id="f58f6-135">(Par exemple, il ne s’applique pas au premier élément d’un tableau.)</span><span class="sxs-lookup"><span data-stu-id="f58f6-135">(E.g., won't apply to the first item in an array)</span></span>
1. <span data-ttu-id="f58f6-136">Un renderer **DOIT** rechercher la quantité d’espace à utiliser à partir de l’espacement `hostConfig` pour la valeur enum appliquée à l’élément actuel.</span><span class="sxs-lookup"><span data-stu-id="f58f6-136">A renderer **MUST** look up the amount of space to use from the `hostConfig` spacing for the enum value applied to the current element.</span></span>
1. <span data-ttu-id="f58f6-137">Si la valeur `separator` de l’élément est `true`, une ligne visible **DOIT** être dessinée entre l’élément actuel et celui qui le précède.</span><span class="sxs-lookup"><span data-stu-id="f58f6-137">If the element has a `separator` value of `true`, then a visible line **MUST** be drawn between the current element and the one before it.</span></span>
1. <span data-ttu-id="f58f6-138">La ligne de séparation **DOIT** être dessinée à l’aide du `container.style.default.foregroundColor`.</span><span class="sxs-lookup"><span data-stu-id="f58f6-138">The separator line **MUST** be drawn using the `container.style.default.foregroundColor`.</span></span>
1. <span data-ttu-id="f58f6-139">Un séparateur **DOIT UNIQUEMENT** être dessiné si l’élément **N’EST PAS** le premier dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="f58f6-139">A separator **MUST ONLY** be drawn if the item **IS NOT** the first in the array.</span></span>

### <a name="columns"></a><span data-ttu-id="f58f6-140">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f58f6-140">Columns</span></span>

1. <span data-ttu-id="f58f6-141">`Column` `width` **DOIT** être interprété par « auto », « stretch » ou un rapport pondéré.</span><span class="sxs-lookup"><span data-stu-id="f58f6-141">`Column` `width` **MUST** be interpreted by "auto", "stretch" or a weighted ratio.</span></span>

### <a name="textblock"></a><span data-ttu-id="f58f6-142">TextBlock</span><span class="sxs-lookup"><span data-stu-id="f58f6-142">TextBlock</span></span>

1. <span data-ttu-id="f58f6-143">Un TextBlock **DOIT** occuper une seule ligne, sauf si la propriété `wrap` est `true`.</span><span class="sxs-lookup"><span data-stu-id="f58f6-143">A TextBlock **MUST** take up a single line unless the `wrap` property is `true`.</span></span> 
1. <span data-ttu-id="f58f6-144">Le bloc de texte **DOIT** supprimer tout texte excédentaire avec des points de suspension (...).</span><span class="sxs-lookup"><span data-stu-id="f58f6-144">The text block **SHOULD** trim any excess text with an ellipsis (...)</span></span>

#### <a name="markdown"></a><span data-ttu-id="f58f6-145">Markdown</span><span class="sxs-lookup"><span data-stu-id="f58f6-145">Markdown</span></span>

1. <span data-ttu-id="f58f6-146">Les cartes adaptatives autorisent un sous-ensemble de Markdown et `TextBlock`DOIVENT**être prises en charge dans**.</span><span class="sxs-lookup"><span data-stu-id="f58f6-146">Adaptive Cards allow for a subset of Markdown and **SHOULD** be supported in `TextBlock`.</span></span> 
1. <span data-ttu-id="f58f6-147">Voir les [conditions requises complètes pour le Markdown](../authoring-cards/text-features.md).</span><span class="sxs-lookup"><span data-stu-id="f58f6-147">See full [markdown requirements](../authoring-cards/text-features.md)</span></span>

#### <a name="formatting-functions"></a><span data-ttu-id="f58f6-148">Fonctions de mise en forme</span><span class="sxs-lookup"><span data-stu-id="f58f6-148">Formatting functions</span></span>

1. <span data-ttu-id="f58f6-149">`TextBlock` autorise les [fonctions de mise en forme de DATE/HEURE](../authoring-cards/text-features.md) qui **DOIVENT** être prises en charge sur chaque renderer.</span><span class="sxs-lookup"><span data-stu-id="f58f6-149">`TextBlock` allows [DATE/TIME formatting functions](../authoring-cards/text-features.md) that **MUST** be supported on every renderer.</span></span>
1. <span data-ttu-id="f58f6-150">**TOUTES LES DÉFAILLANCES DOIVENT** afficher la chaîne brute dans la carte.</span><span class="sxs-lookup"><span data-stu-id="f58f6-150">**ALL FAILURES MUST** display the raw string in the card.</span></span> <span data-ttu-id="f58f6-151">Aucun message convivial n’est tenté.</span><span class="sxs-lookup"><span data-stu-id="f58f6-151">No friendly message attempted.</span></span> <span data-ttu-id="f58f6-152">(L’objectif est de permettre au développeur de savoir immédiatement qu’il y a un problème.)</span><span class="sxs-lookup"><span data-stu-id="f58f6-152">(The goal being to make the developer immediately aware there is a problem)</span></span>

1. <span data-ttu-id="f58f6-153">TODO: Inclure regex</span><span class="sxs-lookup"><span data-stu-id="f58f6-153">TODO: Include regex</span></span>

### <a name="images"></a><span data-ttu-id="f58f6-154">Images</span><span class="sxs-lookup"><span data-stu-id="f58f6-154">Images</span></span>

1. <span data-ttu-id="f58f6-155">Un renderer **DOIT** permettre aux applications hôtes de savoir quand toutes les images HTTP ont été téléchargées et que la carte est « entièrement affichée ».</span><span class="sxs-lookup"><span data-stu-id="f58f6-155">A renderer **SHOULD** allow host apps to know when all HTTP images have been downloaded and the card is "fully rendered"</span></span>
1. <span data-ttu-id="f58f6-156">Un renderer **DOIT** inspecter le paramètre `maxImageSize` de configuration de l’hôte lors du téléchargement d’images HTTP</span><span class="sxs-lookup"><span data-stu-id="f58f6-156">A renderer **MUST** inspect the Host Config `maxImageSize` param when downloading HTTP images</span></span>
1. <span data-ttu-id="f58f6-157">Un renderer **DOIT** prendre en charge `.png` et `.jpeg`.</span><span class="sxs-lookup"><span data-stu-id="f58f6-157">A renderer **MUST** support `.png` and `.jpeg`</span></span>
1. <span data-ttu-id="f58f6-158">Un renderer **DOIT** prendre en charge les images `.gif`.</span><span class="sxs-lookup"><span data-stu-id="f58f6-158">A renderer **SHOULD** support `.gif` images</span></span>

### <a name="host-config"></a><span data-ttu-id="f58f6-159">Configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="f58f6-159">Host Config</span></span>

* <span data-ttu-id="f58f6-160">TODO: Quelles doivent-être les valeurs par défaut ?</span><span class="sxs-lookup"><span data-stu-id="f58f6-160">TODO: What should the defaults be?</span></span> <span data-ttu-id="f58f6-161">Doivent-ils tous les partager ?</span><span class="sxs-lookup"><span data-stu-id="f58f6-161">Should they all share it?</span></span> <span data-ttu-id="f58f6-162">Devons-nous incorporer un fichier hostConfig.json commun dans les fichiers binaires ?</span><span class="sxs-lookup"><span data-stu-id="f58f6-162">Should we embed a common hostConfig.json file in the binaries?</span></span>
* <span data-ttu-id="f58f6-163">TODO: Je pense que HostConfig a également besoin d’une gestion des versions pour l’analyse.</span><span class="sxs-lookup"><span data-stu-id="f58f6-163">TODO: I think HostConfig needs to be versioned as well for parsing?</span></span>

<span data-ttu-id="f58f6-164">[`HostConfig`](host-config.md) est un objet de configuration partagé qui spécifie comment un renderer de carte adaptative génère l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f58f6-164">[`HostConfig`](host-config.md) is a shared configuration object that specifies how an Adaptive Card Renderer generates UI.</span></span>  

<span data-ttu-id="f58f6-165">Cela permet aux propriétés qui sont indépendantes de la plateforme d’être partagées par les renderers sur différents appareils et plateformes.</span><span class="sxs-lookup"><span data-stu-id="f58f6-165">This allows properties which are platform agnostic to be shared among renderers on different platforms and devices.</span></span> <span data-ttu-id="f58f6-166">Cela permet également de créer des outils qui vous donnent une idée de l’apparence de la carte pour un environnement donné.</span><span class="sxs-lookup"><span data-stu-id="f58f6-166">It also allows tooling to be created which gives you an idea of the look and feel that card would have for a given environment.</span></span>

1. <span data-ttu-id="f58f6-167">Les renderers **DOIVENT** exposer un paramètre de **Configuration d’hôte** pour héberger des applications.</span><span class="sxs-lookup"><span data-stu-id="f58f6-167">Renderers **MUST** expose a **Host Config** parameter to host apps</span></span>
1. <span data-ttu-id="f58f6-168">Un style **DOIT** être appliqué à tous les éléments en fonction de leurs paramètres de configuration d’hôte respectifs.</span><span class="sxs-lookup"><span data-stu-id="f58f6-168">All elements **MUST** be styled according to their respective Host Config settings</span></span>

### <a name="native-platform-styling"></a><span data-ttu-id="f58f6-169">Style de plateforme natif</span><span class="sxs-lookup"><span data-stu-id="f58f6-169">Native platform styling</span></span>

1. <span data-ttu-id="f58f6-170">Chaque type d’élément **DOIT** attacher un style de plateforme natif à l’élément d’interface utilisateur généré.</span><span class="sxs-lookup"><span data-stu-id="f58f6-170">Each element type **SHOULD** attach a native platform style with the generated UI element.</span></span> <span data-ttu-id="f58f6-171">Par exemple, dans le code HTML nous avons ajouté une classe CSS aux types d’éléments et, en XAML, nous affectons un style spécifique.</span><span class="sxs-lookup"><span data-stu-id="f58f6-171">E.g., in HTML we added a CSS class to the element types, and in XAML we assign a specific Style.</span></span>

## <a name="extensibility"></a><span data-ttu-id="f58f6-172">Extensibilité</span><span class="sxs-lookup"><span data-stu-id="f58f6-172">Extensibility</span></span> 

1. <span data-ttu-id="f58f6-173">Un renderer **DOIT** autoriser les applications hôtes à remplacer les renderers d’éléments par défaut</span><span class="sxs-lookup"><span data-stu-id="f58f6-173">A renderer **MUST** allow host apps to override default element renderers.</span></span> <span data-ttu-id="f58f6-174">(par exemple remplacer le rendu `TextBlock` par leur propre logique).</span><span class="sxs-lookup"><span data-stu-id="f58f6-174">E.g., replace `TextBlock` rendering with their own logic.</span></span>
1. <span data-ttu-id="f58f6-175">Un renderer **DOIT** autoriser les applications hôtes à inscrire des types d’éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="f58f6-175">A renderer **MUST** allow host apps to register custom element types.</span></span> <span data-ttu-id="f58f6-176">(par exemple ajouter la prise en charge d’un élément personnalisé `Rating`).</span><span class="sxs-lookup"><span data-stu-id="f58f6-176">E.g., add support for a custom `Rating` element</span></span>
1. <span data-ttu-id="f58f6-177">Un renderer **DOIT** autoriser les applications hôtes à supprimer la prise en charge d’un élément par défaut</span><span class="sxs-lookup"><span data-stu-id="f58f6-177">A renderer **MUST** allow host apps to remove support for a default element.</span></span> <span data-ttu-id="f58f6-178">(par exemple supprimer `Action.Submit` si elles ne souhaitent pas qu’il soit pris en charge).</span><span class="sxs-lookup"><span data-stu-id="f58f6-178">E.g., remove `Action.Submit` if they don't want it supported.</span></span>

## <a name="actions"></a><span data-ttu-id="f58f6-179">Actions</span><span class="sxs-lookup"><span data-stu-id="f58f6-179">Actions</span></span>

1. <span data-ttu-id="f58f6-180">Si `supportsInteractivity` de configuration de l’hôte est `false`, un renderer **NE DOIT PAS** afficher d’action.</span><span class="sxs-lookup"><span data-stu-id="f58f6-180">If HostConfig `supportsInteractivity` is `false`, a renderer **MUST NOT** render any actions.</span></span>
1. <span data-ttu-id="f58f6-181">La propriété `actions` **DOIT** être rendue sous forme de boutons dans un type de barre d’action, généralement au bas de la carte.</span><span class="sxs-lookup"><span data-stu-id="f58f6-181">The `actions` property **MUST** be rendered as buttons in some kind of action bar, usually at the bottom of the card.</span></span> 
1. <span data-ttu-id="f58f6-182">Quand un bouton est enfoncé, il **DOIT** permettre à l’application hôte de gérer l’événement.</span><span class="sxs-lookup"><span data-stu-id="f58f6-182">When a button is tapped it **MUST** allow the host app to handle the event.</span></span> 
1. <span data-ttu-id="f58f6-183">L’événement **DOIT** transmettre toutes les propriétés associées avec l’action.</span><span class="sxs-lookup"><span data-stu-id="f58f6-183">The event **MUST** pass along all associated properties with the action</span></span>
1. <span data-ttu-id="f58f6-184">L’événement **DOIT** transmettre le `AdaptiveCard` qui a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="f58f6-184">The event **MUST** pass along the `AdaptiveCard` which was executed</span></span>

<span data-ttu-id="f58f6-185">Action</span><span class="sxs-lookup"><span data-stu-id="f58f6-185">Action</span></span> | <span data-ttu-id="f58f6-186">Comportement</span><span class="sxs-lookup"><span data-stu-id="f58f6-186">Behavior</span></span>
--- | ---
<span data-ttu-id="f58f6-187">**Action.OpenUrl**</span><span class="sxs-lookup"><span data-stu-id="f58f6-187">**Action.OpenUrl**</span></span> | <span data-ttu-id="f58f6-188">Ouvrir une URL externe pour l’affichage</span><span class="sxs-lookup"><span data-stu-id="f58f6-188">Open an external URL for viewing</span></span>
<span data-ttu-id="f58f6-189">**Action.ShowCard**</span><span class="sxs-lookup"><span data-stu-id="f58f6-189">**Action.ShowCard**</span></span> | <span data-ttu-id="f58f6-190">Demande de présenter une sous-carte à l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="f58f6-190">Requests a sub-card to be shown to the user.</span></span>
<span data-ttu-id="f58f6-191">**Action.Submit**</span><span class="sxs-lookup"><span data-stu-id="f58f6-191">**Action.Submit**</span></span> | <span data-ttu-id="f58f6-192">Demande de regrouper tous les éléments d’entrée au sein d’un même objet, qui vous est ensuite envoyé par le biais d’une méthode définie par l’application hôte</span><span class="sxs-lookup"><span data-stu-id="f58f6-192">Ask for all of the input elements to be gathered up into an object which is then sent to you through some method defined by the host application.</span></span>

### <a name="actionopenurl"></a><span data-ttu-id="f58f6-193">Action.OpenUrl</span><span class="sxs-lookup"><span data-stu-id="f58f6-193">Action.OpenUrl</span></span>
1. <span data-ttu-id="f58f6-194">`Action.OpenUrl` **DOIT** ouvrir une URL à l’aide du mécanisme de plateforme natif.</span><span class="sxs-lookup"><span data-stu-id="f58f6-194">`Action.OpenUrl` **SHOULD** open a URL using the native platform mechanism</span></span>
1. <span data-ttu-id="f58f6-195">Si ce n’est pas possible, il **DOIT** déclencher un événement sur l’application hôte pour gérer l’ouverture de l’URL.</span><span class="sxs-lookup"><span data-stu-id="f58f6-195">If this is not possible it **MUST** raise an event to the host app to handle opening the URL.</span></span> <span data-ttu-id="f58f6-196">Cet événement **DOIT** permettre à l’application hôte de remplacer le comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="f58f6-196">This event **MUST** allow the host app to override the default behavior.</span></span> <span data-ttu-id="f58f6-197">(par exemple, lui laisser ouvrir l’URL dans sa propre application).</span><span class="sxs-lookup"><span data-stu-id="f58f6-197">E.g., let them open the URL within their own app.</span></span>

### <a name="actionshowcard"></a><span data-ttu-id="f58f6-198">Action.ShowCard</span><span class="sxs-lookup"><span data-stu-id="f58f6-198">Action.ShowCard</span></span>

1. <span data-ttu-id="f58f6-199">`Action.ShowCard` **DOIT** être pris en charge d’une certaine manière, en fonction du paramètre hostConfig.</span><span class="sxs-lookup"><span data-stu-id="f58f6-199">`Action.ShowCard` **MUST** be supported in some way, based on the hostConfig setting.</span></span> <span data-ttu-id="f58f6-200">Il existe deux modes : inline et popup.</span><span class="sxs-lookup"><span data-stu-id="f58f6-200">There are two modes: inline, and popup.</span></span> <span data-ttu-id="f58f6-201">Les cartes inline **DOIVENT** basculer automatiquement la visibilité de la carte.</span><span class="sxs-lookup"><span data-stu-id="f58f6-201">Inline cards **SHOULD** toggle the card visibility automatically.</span></span> <span data-ttu-id="f58f6-202">En mode popup, un événement **DOIT** être déclenché sur l’application hôte pour afficher la carte d’une certaine façon.</span><span class="sxs-lookup"><span data-stu-id="f58f6-202">In popup mode, an event **SHOULD** be fired to the host app to show the card in some way.</span></span>

### <a name="actionsubmit"></a><span data-ttu-id="f58f6-203">Action.Submit</span><span class="sxs-lookup"><span data-stu-id="f58f6-203">Action.Submit</span></span>

<span data-ttu-id="f58f6-204">L’action Submit se comporte comme un envoi de formulaire HTML, sauf que là où le code HTML déclenche généralement une requête HTTP, les cartes adaptatives laissent à chaque application hôte le soin de déterminer ce que signifie pour elles « envoi ».</span><span class="sxs-lookup"><span data-stu-id="f58f6-204">The Submit Action behaves like an HTML form submit, except that where HTML typically triggers an HTTP post, Adaptive Cards leaves it up to each host app to determine what "submit" means to them.</span></span> 

1. <span data-ttu-id="f58f6-205">Quand cela **DOIT** déclencher un événement, l’utilisateur appuie sur l’action appelée.</span><span class="sxs-lookup"><span data-stu-id="f58f6-205">When this **MUST** raise an event the user taps the action invoked.</span></span>  
1. <span data-ttu-id="f58f6-206">La propriété `data` **DOIT** être incluse dans la charge utile de rappel.</span><span class="sxs-lookup"><span data-stu-id="f58f6-206">The `data` property **MUST** be included in the callback payload.</span></span>
1. <span data-ttu-id="f58f6-207">Pour `Action.Submit`, un renderer **DOIT** recueillir toutes les entrées sur la carte et récupérer leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="f58f6-207">For `Action.Submit`, a renderer **MUST** gather all inputs on the card and retrieve their values.</span></span> 

### <a name="selectaction"></a><span data-ttu-id="f58f6-208">selectAction</span><span class="sxs-lookup"><span data-stu-id="f58f6-208">selectAction</span></span>

1. <span data-ttu-id="f58f6-209">Si `supportedInteractivity` de la configuration de l’hôte est `false`, un `selectAction` **NE DOIT PAS** être affiché en tant que cible tactile.</span><span class="sxs-lookup"><span data-stu-id="f58f6-209">If Host Config `supportedInteractivity` is `false` then a `selectAction` **MUST NOT** render as a touch target.</span></span>
1. <span data-ttu-id="f58f6-210">`Image`, `ColumnSet` et `Column` offrent une propriété `selectAction`, qui **DOIT** être exécutée quand l’utilisateur l’appelle, par exemple en appuyant sur l’élément.</span><span class="sxs-lookup"><span data-stu-id="f58f6-210">`Image`, `ColumnSet`, and `Column` offer a `selectAction` property, which **SHOULD** be executed when the user invokes it, e.g., by tapping the element.</span></span>

## <a name="inputs"></a><span data-ttu-id="f58f6-211">Entrées</span><span class="sxs-lookup"><span data-stu-id="f58f6-211">Inputs</span></span>

1. <span data-ttu-id="f58f6-212">Si `supportsInteractivity` de configuration de l’hôte est `false`, un renderer **NE DOIT PAS** afficher d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f58f6-212">If HostConfig `supportsInteractivity` is `false` a renderer **MUST NOT** render any inputs.</span></span>
2. <span data-ttu-id="f58f6-213">Les entrées **DOIVENT** être affichées avec la fidélité la plus élevée possible.</span><span class="sxs-lookup"><span data-stu-id="f58f6-213">Inputs **SHOULD** render with the highest fidelity possible.</span></span> <span data-ttu-id="f58f6-214">Par exemple, dans l’idéal un `Input.Date` proposera un sélecteur de date à un utilisateur, mais si cela n’est pas possible sur votre pile d’interface utilisateur, le renderer **DOIT** revenir au rendu d’une zone de texte standard.</span><span class="sxs-lookup"><span data-stu-id="f58f6-214">For example, an `Input.Date` would ideally offer a date picker to a user, but if this isn't possible on your UI stack, then the renderer **MUST** fall back to rendering a standard text box.</span></span>
3. <span data-ttu-id="f58f6-215">Un renderer **DOIT** afficher le `placeholderText` si possible.</span><span class="sxs-lookup"><span data-stu-id="f58f6-215">A renderer **SHOULD** display the `placeholderText` if possible</span></span>
4. <span data-ttu-id="f58f6-216">Un renderer **N’EST PAS OBLIGÉ** d’implémenter la validation de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="f58f6-216">A renderer **DOES NOT** have to implement validation of the input.</span></span> <span data-ttu-id="f58f6-217">Les utilisateurs de cartes adaptatives doivent prévoir de valider toutes les données reçues à leur extrémité.</span><span class="sxs-lookup"><span data-stu-id="f58f6-217">Users of Adaptive Cards must plan to validate any received data on their end.</span></span>
5. <span data-ttu-id="f58f6-218">La liaison de valeur d’entrée **DOIT** être correctement placée dans une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="f58f6-218">Input value binding **MUST** be properly escaped</span></span>

6. <span data-ttu-id="f58f6-219">L’objet **DOIT** être retourné à l’application hôte comme suit :</span><span class="sxs-lookup"><span data-stu-id="f58f6-219">The object **MUST** be returned to the host app as follows:</span></span>

   <span data-ttu-id="f58f6-220">Nous n’offrons aucune promesse de validation d’entrée dans les cartes adaptatives ; il incombe donc à la partie réceptrice d’analyser correctement la réponse.</span><span class="sxs-lookup"><span data-stu-id="f58f6-220">We do not make any promises of input validation in adaptive cards, so it's up to the receiving party to properly parse the response.</span></span> <span data-ttu-id="f58f6-221">Par exemple, un Input.Number pourrait retourner « Hello », et vous devez être préparé à cela.</span><span class="sxs-lookup"><span data-stu-id="f58f6-221">E.g., a Input.Number could return "hello" and they need to be prepared for that.</span></span>


## <a name="events"></a><span data-ttu-id="f58f6-222">Événements</span><span class="sxs-lookup"><span data-stu-id="f58f6-222">Events</span></span>

1. <span data-ttu-id="f58f6-223">Un renderer **DOIT** déclencher un événement quand la visibilité d’un élément a changé, permettant à l’application hôte de faire défiler la carte vers la position.</span><span class="sxs-lookup"><span data-stu-id="f58f6-223">A renderer **SHOULD** fire an event when an element's visibility has changed, allowing the host app to scroll the card into position.</span></span>
