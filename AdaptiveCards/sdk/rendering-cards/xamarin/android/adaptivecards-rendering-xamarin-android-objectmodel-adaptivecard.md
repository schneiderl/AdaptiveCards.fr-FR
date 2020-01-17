---
title: AdaptiveCard, classe-Xamarin. Android SDK
author: almedina-ms
ms.author: almedina
ms.date: 12/02/2019
ms.topic: article
ms.openlocfilehash: 0f64bf635023271d8b40bf55fce079300aae7652
ms.sourcegitcommit: 9a9973129c36a41f5e4af30d95ffc146820ad173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146083"
---
# <a name="adaptivecard"></a><span data-ttu-id="df81b-102">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="df81b-102">AdaptiveCard</span></span>

```csharp
public class AdaptiveCard : Java.Lang.Object 
```

<span data-ttu-id="df81b-103">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="df81b-103">**Namespace**</span></span>

```csharp
namespace AdaptiveCards.Rendering.Xamarin.Android.ObjectModel
```

## <a name="summary"></a><span data-ttu-id="df81b-104">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="df81b-104">Summary</span></span>

| <span data-ttu-id="df81b-105">Attributes</span><span class="sxs-lookup"><span data-stu-id="df81b-105">Attributes</span></span> | |
| ---- | --- |
| <span data-ttu-id="df81b-106">Actions</span><span class="sxs-lookup"><span data-stu-id="df81b-106">Actions</span></span> | <span data-ttu-id="df81b-107">Actions à afficher dans la barre d’action de la carte.</span><span class="sxs-lookup"><span data-stu-id="df81b-107">The Actions to show in the card’s action bar.</span></span> |
| <span data-ttu-id="df81b-108">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="df81b-108">BackgroundImage</span></span> | <span data-ttu-id="df81b-109">Spécifie l’image d’arrière-plan de la carte.</span><span class="sxs-lookup"><span data-stu-id="df81b-109">Specifies the background image of the card.</span></span> |
| <span data-ttu-id="df81b-110">Body</span><span class="sxs-lookup"><span data-stu-id="df81b-110">Body</span></span> | <span data-ttu-id="df81b-111">Éléments de carte à afficher dans la région de carte principale.</span><span class="sxs-lookup"><span data-stu-id="df81b-111">The card elements to show in the primary card region.</span></span> |
| <span data-ttu-id="df81b-112">type_élément</span><span class="sxs-lookup"><span data-stu-id="df81b-112">ElementType</span></span> | <span data-ttu-id="df81b-113">Doit être « AdaptiveCard ».</span><span class="sxs-lookup"><span data-stu-id="df81b-113">Must be "AdaptiveCard".</span></span> |
| <span data-ttu-id="df81b-114">FallbackText</span><span class="sxs-lookup"><span data-stu-id="df81b-114">FallbackText</span></span> | <span data-ttu-id="df81b-115">Texte affiché lorsque le client ne prend pas en charge la version spécifiée (peut contenir la démarque).</span><span class="sxs-lookup"><span data-stu-id="df81b-115">Text shown when the client doesn’t support the version specified (may contain markdown).</span></span> |
| <span data-ttu-id="df81b-116">Hauteur</span><span class="sxs-lookup"><span data-stu-id="df81b-116">Height</span></span> | |
| <span data-ttu-id="df81b-117">InputNecessityIndicators</span><span class="sxs-lookup"><span data-stu-id="df81b-117">InputNecessityIndicators</span></span> | |
| <span data-ttu-id="df81b-118">Langue</span><span class="sxs-lookup"><span data-stu-id="df81b-118">Language</span></span> | <span data-ttu-id="df81b-119">Le langage ISO-639-1 à 2 lettres utilisé dans la carte.</span><span class="sxs-lookup"><span data-stu-id="df81b-119">The 2-letter ISO-639-1 language used in the card.</span></span> <span data-ttu-id="df81b-120">Utilisé pour localiser des fonctions de date/heure.</span><span class="sxs-lookup"><span data-stu-id="df81b-120">Used to localize any date/time functions.</span></span> |
| <span data-ttu-id="df81b-121">MinHeight</span><span class="sxs-lookup"><span data-stu-id="df81b-121">MinHeight</span></span> | <span data-ttu-id="df81b-122">Spécifie la hauteur minimale de la carte.</span><span class="sxs-lookup"><span data-stu-id="df81b-122">Specifies the minimum height of the card.</span></span> |
| <span data-ttu-id="df81b-123">SelectAction</span><span class="sxs-lookup"><span data-stu-id="df81b-123">SelectAction</span></span> | <span data-ttu-id="df81b-124">Action qui est appelée lorsque la carte est activée ou sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="df81b-124">An Action that will be invoked when the card is tapped or selected.</span></span> <span data-ttu-id="df81b-125">Action. ShowCard n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="df81b-125">Action.ShowCard is not supported.</span></span> |
| <span data-ttu-id="df81b-126">Speak</span><span class="sxs-lookup"><span data-stu-id="df81b-126">Speak</span></span> | <span data-ttu-id="df81b-127">Spécifie ce qui doit être parlé pour cette carte entière.</span><span class="sxs-lookup"><span data-stu-id="df81b-127">Specifies what should be spoken for this entire card.</span></span> <span data-ttu-id="df81b-128">Il s’agit de texte simple ou de fragment SSML.</span><span class="sxs-lookup"><span data-stu-id="df81b-128">This is simple text or SSML fragment.</span></span> |
| <span data-ttu-id="df81b-129">Style</span><span class="sxs-lookup"><span data-stu-id="df81b-129">Style</span></span> | |
| <span data-ttu-id="df81b-130">Version</span><span class="sxs-lookup"><span data-stu-id="df81b-130">Version</span></span> | <span data-ttu-id="df81b-131">Version de schéma requise par cette carte.</span><span class="sxs-lookup"><span data-stu-id="df81b-131">Schema version that this card requires.</span></span> <span data-ttu-id="df81b-132">Si un client est inférieur à cette version, le fallbackText sera rendu.</span><span class="sxs-lookup"><span data-stu-id="df81b-132">If a client is lower than this version, the fallbackText will be rendered.</span></span> <span data-ttu-id="df81b-133">Remarque : la version n’est pas requise pour les cartes dans une action. ShowCard.</span><span class="sxs-lookup"><span data-stu-id="df81b-133">NOTE: Version is not required for cards within an Action.ShowCard.</span></span> <span data-ttu-id="df81b-134">Toutefois, il est requis pour la carte de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="df81b-134">However, it is required for the top-level card.</span></span> |
| <span data-ttu-id="df81b-135">VerticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="df81b-135">VerticalContentAlignment</span></span> | <span data-ttu-id="df81b-136">Définit la façon dont le contenu doit être aligné verticalement dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="df81b-136">Defines how the content should be aligned vertically within the container.</span></span> <span data-ttu-id="df81b-137">Concerne uniquement les cartes à hauteur fixe ou les cartes avec un minHeight spécifié.</span><span class="sxs-lookup"><span data-stu-id="df81b-137">Only relevant for fixed-height cards, or cards with a minHeight specified.</span></span> |

&nbsp;

<span data-ttu-id="df81b-138">**Constructeurs publics**</span><span class="sxs-lookup"><span data-stu-id="df81b-138">**Public Constructors**</span></span>

---

<a href="#ctor0"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor1"><div>
```csharp
AdaptiveCard(string version, string fallbackText, BackgroundImage backgroundImage, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

<a href="#ctor2"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight)
```
</div></a>

<a href="#ctor3"><div>
```csharp
AdaptiveCard(string version, string fallbackText, string backgroundImageUrl, ContainerStyle style, string speak, string language, VerticalContentAlignment verticalContentAlignment, HeightType height, long minHeight, BaseCardElementVector body, BaseActionElementVector actions)
```
</div></a>

&nbsp;
| <span data-ttu-id="df81b-139">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="df81b-139">Public methods</span></span> | |
| --- | ---- |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion)```](#deserializefromstring0) |
| ```static ParseResult``` | [```DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)```](#deserializefromstring1) |
| ```static AdaptiveCard``` | [```MakeFallbackTextCard(string fallbackText, string language, string speak)```](#makefallbacktextcard) |
| ```string``` | [```Serialize()```](#serialize) |
| ```JsonValue``` | [```SerializeToJsonValue()```](#serializetojsonvalue) |

&nbsp;
## <a name="public-constructors"></a><span data-ttu-id="df81b-140">Constructeurs publics</span><span class="sxs-lookup"><span data-stu-id="df81b-140">Public Constructors</span></span>
---

### <a id="ctor0"></a><span data-ttu-id="df81b-141">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="df81b-141">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-142">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="df81b-142">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight) 
```

| <span data-ttu-id="df81b-143">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-143">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-144">Version de</span><span class="sxs-lookup"><span data-stu-id="df81b-144">version</span></span> | ```string``` |
| <span data-ttu-id="df81b-145">fallbackText</span><span class="sxs-lookup"><span data-stu-id="df81b-145">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="df81b-146">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="df81b-146">backgroundImage</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| <span data-ttu-id="df81b-147">style</span><span class="sxs-lookup"><span data-stu-id="df81b-147">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="df81b-148">speak</span><span class="sxs-lookup"><span data-stu-id="df81b-148">speak</span></span> | ```string``` |
| <span data-ttu-id="df81b-149">language</span><span class="sxs-lookup"><span data-stu-id="df81b-149">language</span></span> | ```string``` |
| <span data-ttu-id="df81b-150">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="df81b-150">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="df81b-151">hauteur</span><span class="sxs-lookup"><span data-stu-id="df81b-151">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="df81b-152">minHeight</span><span class="sxs-lookup"><span data-stu-id="df81b-152">minHeight</span></span> | ```long``` |

&nbsp;&nbsp;

### <a id="ctor1"></a><span data-ttu-id="df81b-153">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="df81b-153">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-154">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="df81b-154">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    BackgroundImage backgroundImage, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment, 
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body, 
                    BaseActionElementVector actions)
```

| <span data-ttu-id="df81b-155">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-155">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-156">Version de</span><span class="sxs-lookup"><span data-stu-id="df81b-156">version</span></span> | ```string``` |
| <span data-ttu-id="df81b-157">fallbackText</span><span class="sxs-lookup"><span data-stu-id="df81b-157">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="df81b-158">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="df81b-158">backgroundImage</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BackgroundImage``` |
| <span data-ttu-id="df81b-159">style</span><span class="sxs-lookup"><span data-stu-id="df81b-159">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="df81b-160">speak</span><span class="sxs-lookup"><span data-stu-id="df81b-160">speak</span></span> | ```string``` |
| <span data-ttu-id="df81b-161">language</span><span class="sxs-lookup"><span data-stu-id="df81b-161">language</span></span> | ```string``` |
| <span data-ttu-id="df81b-162">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="df81b-162">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="df81b-163">hauteur</span><span class="sxs-lookup"><span data-stu-id="df81b-163">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="df81b-164">minHeight</span><span class="sxs-lookup"><span data-stu-id="df81b-164">minHeight</span></span> | ```long``` |
| <span data-ttu-id="df81b-165">corps</span><span class="sxs-lookup"><span data-stu-id="df81b-165">body</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| <span data-ttu-id="df81b-166">actions</span><span class="sxs-lookup"><span data-stu-id="df81b-166">actions</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;&nbsp;

### <a id="ctor2"></a><span data-ttu-id="df81b-167">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="df81b-167">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-168">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="df81b-168">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight) 
```

| <span data-ttu-id="df81b-169">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-169">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-170">Version de</span><span class="sxs-lookup"><span data-stu-id="df81b-170">version</span></span> | ```string``` |
| <span data-ttu-id="df81b-171">fallbackText</span><span class="sxs-lookup"><span data-stu-id="df81b-171">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="df81b-172">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="df81b-172">backgroundImage</span></span> | ```string``` |
| <span data-ttu-id="df81b-173">style</span><span class="sxs-lookup"><span data-stu-id="df81b-173">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="df81b-174">speak</span><span class="sxs-lookup"><span data-stu-id="df81b-174">speak</span></span> | ```string``` |
| <span data-ttu-id="df81b-175">language</span><span class="sxs-lookup"><span data-stu-id="df81b-175">language</span></span> | ```string``` |
| <span data-ttu-id="df81b-176">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="df81b-176">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="df81b-177">hauteur</span><span class="sxs-lookup"><span data-stu-id="df81b-177">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="df81b-178">minHeight</span><span class="sxs-lookup"><span data-stu-id="df81b-178">minHeight</span></span> | ```long``` |

&nbsp;&nbsp;

### <a id="ctor3"></a><span data-ttu-id="df81b-179">AdaptiveCard</span><span class="sxs-lookup"><span data-stu-id="df81b-179">AdaptiveCard</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-180">Ajouté dans la version 0,1</span><span class="sxs-lookup"><span data-stu-id="df81b-180">Added in version 0.1</span></span></p>

```csharp
public AdaptiveCard (string version, 
                    string fallbackText, 
                    string backgroundImageUrl, 
                    ContainerStyle style, 
                    string speak, 
                    string language, 
                    VerticalContentAlignment verticalContentAlignment,
                    HeightType height, 
                    long minHeight, 
                    BaseCardElementVector body,
                    BaseActionElementVector actions)

```

| <span data-ttu-id="df81b-181">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-181">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-182">Version de</span><span class="sxs-lookup"><span data-stu-id="df81b-182">version</span></span> | ```string``` |
| <span data-ttu-id="df81b-183">fallbackText</span><span class="sxs-lookup"><span data-stu-id="df81b-183">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="df81b-184">backgroundImage</span><span class="sxs-lookup"><span data-stu-id="df81b-184">backgroundImage</span></span> | ```string``` |
| <span data-ttu-id="df81b-185">style</span><span class="sxs-lookup"><span data-stu-id="df81b-185">style</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ContainerStyle``` |
| <span data-ttu-id="df81b-186">speak</span><span class="sxs-lookup"><span data-stu-id="df81b-186">speak</span></span> | ```string``` |
| <span data-ttu-id="df81b-187">language</span><span class="sxs-lookup"><span data-stu-id="df81b-187">language</span></span> | ```string``` |
| <span data-ttu-id="df81b-188">verticalContentAlignment</span><span class="sxs-lookup"><span data-stu-id="df81b-188">verticalContentAlignment</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.VerticalContentAlignment``` |
| <span data-ttu-id="df81b-189">hauteur</span><span class="sxs-lookup"><span data-stu-id="df81b-189">height</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.HeightType``` |
| <span data-ttu-id="df81b-190">minHeight</span><span class="sxs-lookup"><span data-stu-id="df81b-190">minHeight</span></span> | ```long``` |
| <span data-ttu-id="df81b-191">corps</span><span class="sxs-lookup"><span data-stu-id="df81b-191">body</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseCardElementVector``` |
| <span data-ttu-id="df81b-192">actions</span><span class="sxs-lookup"><span data-stu-id="df81b-192">actions</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.BaseActionElementVector``` |

&nbsp;

## <a name="public-methods"></a><span data-ttu-id="df81b-193">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="df81b-193">Public Methods</span></span>
---
### <a id="deserializefromstring0"></a><span data-ttu-id="df81b-194">DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="df81b-194">DeserializeFromString</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-195">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="df81b-195">Added in version 0.1.0</span></span></p>

```csharp
public static ParseResult DeserializeFromString (string jsonString, string rendererVersion)
```

<span data-ttu-id="df81b-196">Désérialise la carte adaptative donnée en tant que chaîne JSON pour la version de convertisseur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="df81b-196">Deserializes the given adaptive card as a json string for the specified renderer version.</span></span>

| <span data-ttu-id="df81b-197">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-197">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-198">jsonString</span><span class="sxs-lookup"><span data-stu-id="df81b-198">jsonString</span></span> | ```string``` |
| <span data-ttu-id="df81b-199">rendererVersion</span><span class="sxs-lookup"><span data-stu-id="df81b-199">rendererVersion</span></span> | ```string``` |

| <span data-ttu-id="df81b-200">Returns</span><span class="sxs-lookup"><span data-stu-id="df81b-200">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a><span data-ttu-id="df81b-201">Exemple</span><span class="sxs-lookup"><span data-stu-id="df81b-201">Sample</span></span>

```csharp
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version);
```

--- 
### <a id="deserializefromstring1"></a><span data-ttu-id="df81b-202">DeserializeFromString</span><span class="sxs-lookup"><span data-stu-id="df81b-202">DeserializeFromString</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-203">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="df81b-203">Added in version 0.1.0</span></span></p>

```csharp
public static ParseResult DeserializeFromString(string jsonString, string rendererVersion, ParseContext context)
```

<span data-ttu-id="df81b-204">Désérialise la carte adaptative donnée en tant que chaîne JSON pour la version du convertisseur spécifiée à l’aide d’un objet [ParseContext]() pour gérer l’analyse des éléments personnalisés.</span><span class="sxs-lookup"><span data-stu-id="df81b-204">Deserializes the given adaptive card as a json string for the specified renderer version using a [ParseContext]() object to handle custom element parsing.</span></span>

| <span data-ttu-id="df81b-205">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-205">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-206">jsonString</span><span class="sxs-lookup"><span data-stu-id="df81b-206">jsonString</span></span> | ```string``` |
| <span data-ttu-id="df81b-207">rendererVersion</span><span class="sxs-lookup"><span data-stu-id="df81b-207">rendererVersion</span></span> | ```string``` |
| <span data-ttu-id="df81b-208">context</span><span class="sxs-lookup"><span data-stu-id="df81b-208">context</span></span> | ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseContext``` |

| <span data-ttu-id="df81b-209">Returns</span><span class="sxs-lookup"><span data-stu-id="df81b-209">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.ParseResult``` | |

#### <a name="sample"></a><span data-ttu-id="df81b-210">Exemple</span><span class="sxs-lookup"><span data-stu-id="df81b-210">Sample</span></span>

```csharp
ParseContext parseContext = new ParseContext(elementParserRegistration, actionParserRegistration);
ParseResult parseResult = AdaptiveCard.DeserializeFromString(jsonText, AdaptiveCardRenderer.Version, parseContext);
```

---

### <a id="makefallbacktextcard"></a><span data-ttu-id="df81b-211">MakeFallbackTextCard</span><span class="sxs-lookup"><span data-stu-id="df81b-211">MakeFallbackTextCard</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-212">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="df81b-212">Added in version 0.1.0</span></span></p>

```csharp
public static AdaptiveCard MakeFallbackTextCard (string fallbackText, string language, string speak)
```

<span data-ttu-id="df81b-213">Désérialise la carte adaptative donnée en tant que chaîne JSON pour la version de convertisseur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="df81b-213">Deserializes the given adaptive card as a json string for the specified renderer version.</span></span>

| <span data-ttu-id="df81b-214">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df81b-214">Parameters</span></span> | |
| --- | --- |
| <span data-ttu-id="df81b-215">fallbackText</span><span class="sxs-lookup"><span data-stu-id="df81b-215">fallbackText</span></span> | ```string``` |
| <span data-ttu-id="df81b-216">language</span><span class="sxs-lookup"><span data-stu-id="df81b-216">language</span></span> | ```string``` |
| <span data-ttu-id="df81b-217">speak</span><span class="sxs-lookup"><span data-stu-id="df81b-217">speak</span></span> | ```string``` |

| <span data-ttu-id="df81b-218">Returns</span><span class="sxs-lookup"><span data-stu-id="df81b-218">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.AdaptiveCard``` | <span data-ttu-id="df81b-219">Carte adaptative qui contient le texte de secours pour une carte unrendereable</span><span class="sxs-lookup"><span data-stu-id="df81b-219">Adaptive card that contains the fallback text for an unrendereable card</span></span> |

#### <a name="sample"></a><span data-ttu-id="df81b-220">Exemple</span><span class="sxs-lookup"><span data-stu-id="df81b-220">Sample</span></span>

```csharp
AdaptiveCard adaptiveCard = AdaptiveCard.MakeFallbackTextCard("This card failed to render", "es", "Unrendereable card");
```

---

### <a id="serialize"></a><span data-ttu-id="df81b-221">Sérialiser</span><span class="sxs-lookup"><span data-stu-id="df81b-221">Serialize</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-222">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="df81b-222">Added in version 0.1.0</span></span></p>

```csharp
public string Serialize ()
```

<span data-ttu-id="df81b-223">Sérialise la carte adaptative sous sa forme de chaîne JSON.</span><span class="sxs-lookup"><span data-stu-id="df81b-223">Serializes the adaptive card into it's json string form.</span></span>

| <span data-ttu-id="df81b-224">Returns</span><span class="sxs-lookup"><span data-stu-id="df81b-224">Returns</span></span> | |
| --- | --- |
| ```string``` | <span data-ttu-id="df81b-225">Carte adaptative comme chaîne JSON</span><span class="sxs-lookup"><span data-stu-id="df81b-225">Adaptive card as a json string</span></span> |

#### <a name="sample"></a><span data-ttu-id="df81b-226">Exemple</span><span class="sxs-lookup"><span data-stu-id="df81b-226">Sample</span></span>

```csharp
string jsonString = parseResult.AdaptiveCard.Serialize();
```

---

### <a id="serializetojsonvalue"></a><span data-ttu-id="df81b-227">SerializeToJsonValue</span><span class="sxs-lookup"><span data-stu-id="df81b-227">SerializeToJsonValue</span></span>
<p style='text-align:right'><span data-ttu-id="df81b-228">Ajouté dans la version 0.1.0</span><span class="sxs-lookup"><span data-stu-id="df81b-228">Added in version 0.1.0</span></span></p>

```csharp
public JsonValue SerializeToJsonValue ()
```

<span data-ttu-id="df81b-229">Sérialise la carte adaptative dans un objet de valeur JSON.</span><span class="sxs-lookup"><span data-stu-id="df81b-229">Serializes the adaptive card into a json value object.</span></span>

| <span data-ttu-id="df81b-230">Returns</span><span class="sxs-lookup"><span data-stu-id="df81b-230">Returns</span></span> | |
| --- | --- |
| ```AdaptiveCards.Rendering.Xamarin.Android.ObjectModel.JsonValue``` | |

#### <a name="sample"></a><span data-ttu-id="df81b-231">Exemple</span><span class="sxs-lookup"><span data-stu-id="df81b-231">Sample</span></span>

```csharp
JsonValue value = parseResult.AdaptiveCard.SerializeToJsonValue();
```