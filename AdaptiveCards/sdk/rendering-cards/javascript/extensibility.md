---
title: Extensibilité-SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 07/16/2020
ms.topic: article
ms.openlocfilehash: 96da071980b8cf41b616297c44c70d181a4f6ac0
ms.sourcegitcommit: 65b792d73c264c943036343e05b75f2b0488e6e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "95001846"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="45a0a-102">Extensibilité-JavaScript</span><span class="sxs-lookup"><span data-stu-id="45a0a-102">Extensibility - JavaScript</span></span>

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a><span data-ttu-id="45a0a-103">Extensibilité avec le kit de développement logiciel (SDK) JS version 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="45a0a-103">Extensibility with the JS SDK version 2.0 and greater</span></span>

### <a name="before-you-start"></a><span data-ttu-id="45a0a-104">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="45a0a-104">Before you start</span></span>

> <span data-ttu-id="45a0a-105">**Important**: la version 2,0 et ultérieure du kit de développement logiciel (SDK) js utilise des [décorateurs de machine à écrire](https://www.typescriptlang.org/docs/handbook/decorators.html).</span><span class="sxs-lookup"><span data-stu-id="45a0a-105">**IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html).</span></span> <span data-ttu-id="45a0a-106">Les décorateurs sont toujours une fonctionnalité expérimentale et doivent être explicitement activés dans votre `tsconfig.js` fichier :</span><span class="sxs-lookup"><span data-stu-id="45a0a-106">Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:</span></span>

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
<span data-ttu-id="45a0a-107">La version 2,0 du kit de développement logiciel (SDK) JS introduit des modifications importantes dans la façon dont les éléments et les actions personnalisés sont implémentés et inscrits.</span><span class="sxs-lookup"><span data-stu-id="45a0a-107">Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered.</span></span> <span data-ttu-id="45a0a-108">Pour obtenir un exemple d’implémentation et d’inscription d’un élément ou d’une action à l’aide des versions précédentes du kit de développement logiciel (SDK), consultez [extensibilité avec le kit de développement logiciel (SDK) js antérieur à la version 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).</span><span class="sxs-lookup"><span data-stu-id="45a0a-108">For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).</span></span>


### <a name="custom-elements"></a><span data-ttu-id="45a0a-109">Éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="45a0a-109">Custom elements</span></span>
<span data-ttu-id="45a0a-110">Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="45a0a-110">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="45a0a-111">Créer une nouvelle classe dérivant de `CardElement`</span><span class="sxs-lookup"><span data-stu-id="45a0a-111">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="45a0a-112">Créer son schéma en déclarant des définitions de propriétés statiques</span><span class="sxs-lookup"><span data-stu-id="45a0a-112">Create its schema by declaring static property definitions</span></span>
- <span data-ttu-id="45a0a-113">Implémenter ses `getJsonTypeName` méthodes, et `internalRender`</span><span class="sxs-lookup"><span data-stu-id="45a0a-113">Implement its `getJsonTypeName`, and `internalRender` methods</span></span>
- <span data-ttu-id="45a0a-114">L’inscrire dans le registre des éléments globaux ou utiliser un registre personnalisé par carte</span><span class="sxs-lookup"><span data-stu-id="45a0a-114">Register it in the global element registry, or use a custom registry on a per-card basis</span></span>


<span data-ttu-id="45a0a-115">Prenons un exemple et implémentons un élément de barre de progression simple :</span><span class="sxs-lookup"><span data-stu-id="45a0a-115">Let's take an example and implement a simple Progress Bar element:</span></span>
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
<span data-ttu-id="45a0a-116">Vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="45a0a-116">That's it.</span></span> <span data-ttu-id="45a0a-117">L’élément ProgressBar doit maintenant être inscrit pour être reconnu par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="45a0a-117">The ProgressBar element now needs to be registered in order to be recognized by the SDK.</span></span> <span data-ttu-id="45a0a-118">Vous pouvez l’inscrire globalement :</span><span class="sxs-lookup"><span data-stu-id="45a0a-118">You can register it globally:</span></span>

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

<span data-ttu-id="45a0a-119">Vous pouvez utiliser un registre par carte qui permet d’utiliser différents registres pour différentes cartes dans votre application :</span><span class="sxs-lookup"><span data-stu-id="45a0a-119">Or you can use a per-card registry, which allows the use of different registries for different cards in your application:</span></span>

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### <a name="custom-inputs"></a><span data-ttu-id="45a0a-120">Entrées personnalisées</span><span class="sxs-lookup"><span data-stu-id="45a0a-120">Custom inputs</span></span>
<span data-ttu-id="45a0a-121">Une entrée est un type spécial d’élément dédié à la collecte des données entrées par l’utilisateur final qui peut ensuite être passée comme paramètre à des actions.</span><span class="sxs-lookup"><span data-stu-id="45a0a-121">An input is a special type of element dedicated to collecting data entered by the end user that can subsequently be passed as parameter to actions.</span></span>

<span data-ttu-id="45a0a-122">La version 2. x du kit de développement logiciel (SDK) Adaptive Cards JS introduit deux modifications notables lorsqu’il s’agit d’entrées :</span><span class="sxs-lookup"><span data-stu-id="45a0a-122">Versions 2.x of the Adaptive Cards JS SDK introduces two notable changes when it comes to inputs:</span></span>
- <span data-ttu-id="45a0a-123">**Validation des entrées :** il existe maintenant un mécanisme de validation d’entrée intégré qui gère automatiquement les erreurs de validation, notamment les signaux visuels</span><span class="sxs-lookup"><span data-stu-id="45a0a-123">**Input validation:** there is now a built-in input validation mechanism that automatically handles validation errors including visual cues</span></span>
- <span data-ttu-id="45a0a-124">**Améliorations de l’accessibilité :** les entrées intégrées offrent une meilleure prise en charge des fonctionnalités d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="45a0a-124">**Accessibility improvements:** built-in inputs have better support for accessibility features</span></span>

<span data-ttu-id="45a0a-125">Pour cette raison, l’implémentation d’entrées personnalisées requiert un peu plus de logique que l’implémentation d’éléments simples.</span><span class="sxs-lookup"><span data-stu-id="45a0a-125">Because of this, implementing custom inputs requires a little more logic than implementing simple elements.</span></span> <span data-ttu-id="45a0a-126">Le tableau ci-dessous répertorie toutes les méthodes qu’une implémentation d’entrée personnalisée doit implémenter pour partiocipate dans le mécanisme de validation d’entrée et être accessible :</span><span class="sxs-lookup"><span data-stu-id="45a0a-126">The table below lists all the methods a custom input implementation should to implement in order to partiocipate in the input validation mechanism and be accessible:</span></span>

| <span data-ttu-id="45a0a-127">Méthode</span><span class="sxs-lookup"><span data-stu-id="45a0a-127">Method</span></span> | <span data-ttu-id="45a0a-128">Description</span><span class="sxs-lookup"><span data-stu-id="45a0a-128">Description</span></span> |
| --------- | ------------- |
| `protected updateInputControlAriaLabelledBy()` | <span data-ttu-id="45a0a-129">Cette méthode est appelée pendant la séquence de validation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="45a0a-129">This method  is called during the input validation sequence.</span></span> <span data-ttu-id="45a0a-130">En cas d’échec de la validation d’une entrée, le message d’erreur qui lui est associé s’affiche et l’attribut du contrôle d’entrée sous-jacent `aria-labelledby` doit être mis à jour afin que l’entrée soit conforme aux exigences d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="45a0a-130">When an input fails validation, its associated error message is displayed and the underlying input control's `aria-labelledby` attribute needs to be updated in order for the input to comply with accessibility requirements.</span></span> <span data-ttu-id="45a0a-131">Les entrées personnalisées doivent remplacer `updateInputControlAriaLabelledBy` pour appliquer l' `aria-labelledby` attribut approprié au contrôle d’entrée sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="45a0a-131">Custom inputs SHOULD override `updateInputControlAriaLabelledBy` to apply the appropriate `aria-labelledby` attribute to the underlying input control.</span></span> <span data-ttu-id="45a0a-132">La `getAllLabelIds(): string[]` méthode peut être utilisée pour récupérer les ID de toutes les étiquettes qui doivent être spécifiées dans l' `aria-labelledby` attribut.</span><span class="sxs-lookup"><span data-stu-id="45a0a-132">The `getAllLabelIds(): string[]` method can be used to retrieve the Ids of all the labels that should be specified in the `aria-labelledby` attribute.</span></span>  |
| `protected internalRender(): HTMLElement` | <span data-ttu-id="45a0a-133">Tout comme pour tout autre élément personnalisé de carte adaptative, `internalRender` doit être substitué pour afficher votre entrée comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="45a0a-133">Just like for any other Adaptive Card custom element, `internalRender` MUST be overridden to render your input as desired.</span></span> <span data-ttu-id="45a0a-134">C’est là que vous souhaitez créer le contrôle d’entrée sous-jacent réel.</span><span class="sxs-lookup"><span data-stu-id="45a0a-134">This is where you'll want to create the actual underlying input control.</span></span> |
| `protected get isNullable(): boolean` | <span data-ttu-id="45a0a-135">Indique si l’entrée prend en charge les valeurs non définies (par exemple, Input. Text, contrairement à Input. Toggle). Les entrées personnalisées doivent remplacer cet accesseur Get de propriété pour indiquer s’ils prennent en charge des valeurs non définies.</span><span class="sxs-lookup"><span data-stu-id="45a0a-135">Indicates whether the input supports undefined values (for instance, Input.Text does, whereas Input.Toggle doesn't.) Custom inputs SHOULD override this property getter to indicate if they support undefined values.</span></span> <span data-ttu-id="45a0a-136">L’implémentation de base retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="45a0a-136">The base implementation returns `true`.</span></span> |
| `public focus()` | <span data-ttu-id="45a0a-137">Lorsque des erreurs de validation se produisent, le focus est automatiquement placé sur la première entrée qui n’a pas pu être validée.</span><span class="sxs-lookup"><span data-stu-id="45a0a-137">When validation errors are encountered, the focus is automatically placed on the first input that failed validation.</span></span> <span data-ttu-id="45a0a-138">Dans certains cas, l’implémentation de base de `focus` peut simplement fonctionner pour des entrées personnalisées.</span><span class="sxs-lookup"><span data-stu-id="45a0a-138">The base implementation of `focus` will in some cases just work for custom inputs.</span></span> <span data-ttu-id="45a0a-139">Lorsque cela n’est pas le cas, les contrôles d’entrée personnalisés doivent remplacer `focus` pour mettre explicitement le focus sur le contrôle d’entrée sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="45a0a-139">When that isn't the case, custom input controls MUST override `focus` to explicitly put the focus on the underlying input control.</span></span>  |
| `public abstract isSet(): boolean` | <span data-ttu-id="45a0a-140">Indique si la valeur de l’entrée a été définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="45a0a-140">Indicates whether the input's value has been set by the user.</span></span> <span data-ttu-id="45a0a-141">Cette méthode est appelée pendant la séquence de validation d’entrée pour déterminer si l’entrée réussit ou échoue à la validation.</span><span class="sxs-lookup"><span data-stu-id="45a0a-141">This method is called during the input validation sequence to determine if the input passes or fails validation.</span></span> <span data-ttu-id="45a0a-142">Les entrées personnalisées doivent `isSet` être substituées afin de participer au mécanisme de validation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="45a0a-142">Custom inputs MUST override `isSet` in order to participate in the input validation mechanism.</span></span> |
| `public isValid(): boolean` | <span data-ttu-id="45a0a-143">Indique si la valeur de l’entrée est valide.</span><span class="sxs-lookup"><span data-stu-id="45a0a-143">Indicates whether the value of the input is valid.</span></span> <span data-ttu-id="45a0a-144">Cette méthode est appelée pendant la séquence de validation d’entrée pour déterminer si l’entrée réussit ou échoue à la validation.</span><span class="sxs-lookup"><span data-stu-id="45a0a-144">This method is called during the input validation sequence to determine if the input passes or fails validation.</span></span> <span data-ttu-id="45a0a-145">Les entrées personnalisées doivent être substituées afin de `isValid` participer au mécanisme de validation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="45a0a-145">Custom inputs SHOULD override `isValid` in order to participate in the input validation mechanism.</span></span> <span data-ttu-id="45a0a-146">L’implémentation de base retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="45a0a-146">The base implementation returns `true`.</span></span> |
| `public abstract get value(): any` | <span data-ttu-id="45a0a-147">Retourne la valeur de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="45a0a-147">Returns the value of the input.</span></span> <span data-ttu-id="45a0a-148">Les entrées personnalisées doivent remplacer ceci afin que la valeur de l’entrée soit récupérée à partir du contrôle d’entrée sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="45a0a-148">Custom inputs MUST override this so that the value of the input is retrieved from the underlying input control.</span></span> |


### <a name="custom-actions"></a><span data-ttu-id="45a0a-149">Actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="45a0a-149">Custom actions</span></span>
<span data-ttu-id="45a0a-150">Les étapes d’implémentation d’une action personnalisée sont les mêmes que celles des éléments.</span><span class="sxs-lookup"><span data-stu-id="45a0a-150">The steps to implementing a custom action are the same as those for elements.</span></span> <span data-ttu-id="45a0a-151">La seule différence est que les actions sont inscrites dans les registres des actions, et non dans les registres des éléments.</span><span class="sxs-lookup"><span data-stu-id="45a0a-151">The only difference is that actions are registered in action registries, and not in element registries.</span></span>

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

<span data-ttu-id="45a0a-152">Inscrire la nouvelle action globalement :</span><span class="sxs-lookup"><span data-stu-id="45a0a-152">Register the new action globally:</span></span>
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

<span data-ttu-id="45a0a-153">Ou utilisez un registre par carte :</span><span class="sxs-lookup"><span data-stu-id="45a0a-153">Or use a per-card registry:</span></span>
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a><span data-ttu-id="45a0a-154">Extensibilité avec le kit de développement logiciel (SDK) JS antérieur à la version 2,0</span><span class="sxs-lookup"><span data-stu-id="45a0a-154">Extensibility with the JS SDK prior to version 2.0</span></span>

### <a name="custom-elements"></a><span data-ttu-id="45a0a-155">Éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="45a0a-155">Custom elements</span></span>

### <a name="before-you-start"></a><span data-ttu-id="45a0a-156">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="45a0a-156">Before you start</span></span>

> <span data-ttu-id="45a0a-157">**Important**: la version 2,0 et ultérieure du kit de développement logiciel (SDK) js utilise des [décorateurs de machine à écrire](https://www.typescriptlang.org/docs/handbook/decorators.html).</span><span class="sxs-lookup"><span data-stu-id="45a0a-157">**IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html).</span></span> <span data-ttu-id="45a0a-158">Les décorateurs sont toujours une fonctionnalité expérimentale et doivent être explicitement activés dans votre `tsconfig.js` fichier :</span><span class="sxs-lookup"><span data-stu-id="45a0a-158">Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:</span></span>

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
<span data-ttu-id="45a0a-159">La version 2,0 du kit de développement logiciel (SDK) JS introduit des modifications importantes dans la façon dont les éléments et les actions personnalisés sont implémentés et inscrits.</span><span class="sxs-lookup"><span data-stu-id="45a0a-159">Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered.</span></span> <span data-ttu-id="45a0a-160">Pour obtenir un exemple d’implémentation et d’inscription d’un élément ou d’une action à l’aide des versions précédentes du kit de développement logiciel (SDK), consultez [extensibilité avec le kit de développement logiciel (SDK) js antérieur à la version 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).</span><span class="sxs-lookup"><span data-stu-id="45a0a-160">For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).</span></span>


### <a name="custom-elements"></a><span data-ttu-id="45a0a-161">Éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="45a0a-161">Custom elements</span></span>
<span data-ttu-id="45a0a-162">Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="45a0a-162">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="45a0a-163">Créer une nouvelle classe dérivant de `CardElement`</span><span class="sxs-lookup"><span data-stu-id="45a0a-163">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="45a0a-164">Créer son schéma en déclarant des définitions de propriétés statiques</span><span class="sxs-lookup"><span data-stu-id="45a0a-164">Create its schema by declaring static property definitions</span></span>
- <span data-ttu-id="45a0a-165">Implémenter ses `getJsonTypeName` méthodes, et `internalRender`</span><span class="sxs-lookup"><span data-stu-id="45a0a-165">Implement its `getJsonTypeName`, and `internalRender` methods</span></span>
- <span data-ttu-id="45a0a-166">L’inscrire dans le registre des éléments globaux ou utiliser un registre personnalisé par carte</span><span class="sxs-lookup"><span data-stu-id="45a0a-166">Register it in the global element registry, or use a custom registry on a per-card basis</span></span>


<span data-ttu-id="45a0a-167">Prenons un exemple et implémentons un élément de barre de progression simple :</span><span class="sxs-lookup"><span data-stu-id="45a0a-167">Let's take an example and implement a simple Progress Bar element:</span></span>
```typescript
export class ProgressBar extends AC.CardElement {
    static readonly JsonTypeName = "ProgressBar";

    //#region Schema

    static readonly titleProperty = new AC.StringProperty(AC.Versions.v1_0, "title", true);
    static readonly valueProperty = new AC.NumProperty(AC.Versions.v1_0, "value");

    @AC.property(ProgressBar.titleProperty)
    get title(): string | undefined {
        return this.getValue(ProgressBar.titleProperty);
    }

    set title(value: string) {
        if (this.title !== value) {
            this.setValue(ProgressBar.titleProperty, value);

            this.updateLayout();
        }
    }

    @AC.property(ProgressBar.valueProperty)
    get value(): number {
        return this.getValue(ProgressBar.valueProperty);
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this.value !== adjustedValue) {
            this.setValue(ProgressBar.valueProperty, adjustedValue);

            this.updateLayout();
        }
    }

    //#endregion

    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new AC.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = AC.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return ProgressBar.JsonTypeName;
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (this.title) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }
}
```
<span data-ttu-id="45a0a-168">Vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="45a0a-168">That's it.</span></span> <span data-ttu-id="45a0a-169">L’élément ProgressBar doit maintenant être inscrit pour être reconnu par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="45a0a-169">The ProgressBar element now needs to be registered in order to be recognized by the SDK.</span></span> <span data-ttu-id="45a0a-170">Vous pouvez l’inscrire globalement :</span><span class="sxs-lookup"><span data-stu-id="45a0a-170">You can register it globally:</span></span>

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

<span data-ttu-id="45a0a-171">Vous pouvez utiliser un registre par carte qui permet d’utiliser différents registres pour différentes cartes dans votre application :</span><span class="sxs-lookup"><span data-stu-id="45a0a-171">Or you can use a per-card registry, which allows the use of different registries for different cards in your application:</span></span>

```typescript
// Create a custom registry for elements
let elementRegistry = new AC.CardObjectRegistry<AC.CardElement>();

// Populate it with the default set of elements
AC.GlobalRegistry.populateWithDefaultElements(elementRegistry);

// Register the custom ProgressBar element
elementRegistry.register(ProgressBar.JsonTypeName, ProgressBar);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setElementRegistry(elementRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "ProgressBar",
                title: "This is a progress bar",
                value: 45
            }
        ]
    },
    serializationContext
);
```

### <a name="custom-actions"></a><span data-ttu-id="45a0a-172">Actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="45a0a-172">Custom actions</span></span>
<span data-ttu-id="45a0a-173">Les étapes d’implémentation d’une action personnalisée sont les mêmes que celles des éléments.</span><span class="sxs-lookup"><span data-stu-id="45a0a-173">The steps to implementing a custom action are the same as those for elements.</span></span> <span data-ttu-id="45a0a-174">La seule différence est que les actions sont inscrites dans les registres des actions, et non dans les registres des éléments.</span><span class="sxs-lookup"><span data-stu-id="45a0a-174">The only difference is that actions are registered in action registries, and not in element registries.</span></span>

```typescript
export class AlertAction extends AC.Action {
    static readonly JsonTypeName = "Action.Alert";

    //#region Schema

    static readonly textProperty = new AC.StringProperty(AC.Versions.v1_0, "text", true);

    @AC.property(AlertAction.textProperty)
    text?: string;

    //#endregion

    getJsonTypeName(): string {
        return AlertAction.JsonTypeName;
    }

    execute() {
        alert(this.text);
    }
}
```

<span data-ttu-id="45a0a-175">Inscrire la nouvelle action globalement :</span><span class="sxs-lookup"><span data-stu-id="45a0a-175">Register the new action globally:</span></span>
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

<span data-ttu-id="45a0a-176">Ou utilisez un registre par carte :</span><span class="sxs-lookup"><span data-stu-id="45a0a-176">Or use a per-card registry:</span></span>
```typescript
// Create a custom registry for actions
let actionRegistry = new AC.CardObjectRegistry<AC.Action>();

// Populate it with the default set of actions
AC.GlobalRegistry.populateWithDefaultActions(actionRegistry);

// Register the custom AlertAction type
actionRegistry.register(AlertAction.JsonTypeName, AlertAction);

// Parse a card payload using the custom registry
let serializationContext = new AC.SerializationContext();
serializationContext.setActionRegistry(actionRegistry);

let card = new AC.AdaptiveCard();
card.parse(
    {
        type: "AdaptiveCard",
        version: "1.0",
        body: [
            {
                type: "TextBlock",
                text: "This demonstrates the AlertAction action."
            }
        ],
        actions: [
            {
                type: "Action.Alert",
                title: "Click me!",
                text: "Hello World"
            }
        ]
    },
    serializationContext
);
```

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a><span data-ttu-id="45a0a-177">Extensibilité avec le kit de développement logiciel (SDK) JS antérieur à la version 2,0</span><span class="sxs-lookup"><span data-stu-id="45a0a-177">Extensibility with the JS SDK prior to version 2.0</span></span>

### <a name="custom-elements"></a><span data-ttu-id="45a0a-178">Éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="45a0a-178">Custom elements</span></span>

<span data-ttu-id="45a0a-179">Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="45a0a-179">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="45a0a-180">Créer une nouvelle classe dérivant de `CardElement`</span><span class="sxs-lookup"><span data-stu-id="45a0a-180">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="45a0a-181">Implémenter `getJsonTypeName` ses `parse` méthodes,, `toJSON` `internalRender` et `renderSpeech`</span><span class="sxs-lookup"><span data-stu-id="45a0a-181">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="45a0a-182">Inscrivez-le en l’ajoutant au registre des éléments du convertisseur</span><span class="sxs-lookup"><span data-stu-id="45a0a-182">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="45a0a-183">Prenons un exemple et implémentons un élément de barre de progression simple :</span><span class="sxs-lookup"><span data-stu-id="45a0a-183">Let's take an example and implement a simple Progress Bar element:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class ProgressBar extends Adaptive.CardElement {
    private _title: string;
    private _value: number = 0;
    private _titleElement: HTMLElement;
    private _leftBarElement: HTMLElement;
    private _rightBarElement: HTMLElement;

    protected internalRender(): HTMLElement {
        let element = document.createElement("div");

        let textBlock = new Adaptive.TextBlock();
        textBlock.setParent(this);
        textBlock.text = this.title;
        textBlock.wrap = true;

        this._titleElement = textBlock.render();
        this._titleElement.style.marginBottom = "6px";

        let progressBarElement = document.createElement("div");
        progressBarElement.style.display = "flex";

        this._leftBarElement = document.createElement("div");
        this._leftBarElement.style.height = "6px";
        this._leftBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.foregroundColors.accent.default);

        this._rightBarElement = document.createElement("div");
        this._rightBarElement.style.height = "6px";
        this._rightBarElement.style.backgroundColor = Adaptive.stringToCssColor(this.hostConfig.containerStyles.emphasis.backgroundColor);

        progressBarElement.append(this._leftBarElement, this._rightBarElement);

        element.append(this._titleElement, progressBarElement);

        return element;
    }

    getJsonTypeName(): string {
        return "ProgressBar";
    }

    toJSON(): any {
        let result = super.toJSON();

        Adaptive.setProperty(result, "title", this.title);
        Adaptive.setProperty(result, "value", this.value);

        return result;
    }

    parse(json: any, errors?: Array<Adaptive.IValidationError>) {
        super.parse(json, errors);

        this.title = Adaptive.getStringValueOrDefault(json["title"], undefined);
        this.value = Adaptive.getValueOrDefault(json["value"], this._value);
    }

    updateLayout(processChildren: boolean = true) {
        super.updateLayout(processChildren);

        if (this.renderedElement) {
            if (Adaptive.isNullOrEmpty(this.title)) {
                this._titleElement.style.display = "none";
            }
            else {
                this._titleElement.style.removeProperty("display");
            }

            this._leftBarElement.style.flex = "1 1 " + this.value + "%";
            this._rightBarElement.style.flex = "1 1 " + (100 - this.value) + "%";
        }
    }

    renderSpeech(): string {
        return (Adaptive.isNullOrEmpty(this.title) ? "Progress" : this.title) + " " + Math.ceil(this.value) + "%";
    }

    get title(): string {
        return this._title;
    }

    set title(value: string) {
        if (this._title !== value) {
            this._title = value;

            this.updateLayout();
        }
    }

    get value(): number {
        return this._value;
    }

    set value(value: number) {
        let adjustedValue = value;

        if (adjustedValue < 0) {
            adjustedValue = 0;
        }
        else if (adjustedValue > 100) {
            adjustedValue = 100;
        }

        if (this._value !== adjustedValue) {
            this._value = adjustedValue;

            this.updateLayout();
        }
    }
}
```

<span data-ttu-id="45a0a-184">Vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="45a0a-184">That's it.</span></span> <span data-ttu-id="45a0a-185">À présent, il vous suffit d’inscrire la classe de barre de progression auprès du convertisseur :</span><span class="sxs-lookup"><span data-stu-id="45a0a-185">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a><span data-ttu-id="45a0a-186">Actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="45a0a-186">Custom actions</span></span>

<span data-ttu-id="45a0a-187">Les étapes de création d’une action de carte adaptative personnalisée sont essentiellement les mêmes que celles des éléments personnalisés.</span><span class="sxs-lookup"><span data-stu-id="45a0a-187">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="45a0a-188">Voici un exemple simple d’action d’alerte qui affiche simplement une boîte de message avec du texte configurable :</span><span class="sxs-lookup"><span data-stu-id="45a0a-188">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

```typescript
import * as Adaptive from "adaptivecards";

export class AlertAction extends Adaptive.Action {
    text: string;

    getJsonTypeName(): string {
        return "Action.ALert";
    }

    execute() {
        alert(this.text);
    }

    parse(json: any) {
        super.parse(json);

        this.text = Adaptive.getStringValueOrDefault(json["text"], "Alert!");
    }

    toJSON() {
        let result = super.toJSON();

        Adaptive.setProperty(result, "text", this.text);

        return result;
    }
}
```

<span data-ttu-id="45a0a-189">Inscrivez maintenant la nouvelle action :</span><span class="sxs-lookup"><span data-stu-id="45a0a-189">Now register the new action:</span></span>

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="45a0a-190">Exemple</span><span class="sxs-lookup"><span data-stu-id="45a0a-190">Example</span></span>

<span data-ttu-id="45a0a-191">Voici un exemple de carte qui utilise à la fois l’élément ProgressBar et l’action AlertAction :</span><span class="sxs-lookup"><span data-stu-id="45a0a-191">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "size": "Medium",
            "weight": "Bolder",
            "text": "Custom ProgressBar element"
        },
        {
            "type": "ProgressBar",
            "title": "Please wait...",
            "value": 10
        }
    ],
    "actions": [
        {
            "type": "Action.Alert",
            "title": "Click me",
            "text": "Hello world!"
        }
    ]
}
```

<span data-ttu-id="45a0a-192">Et voici comment il est rendu : ![ image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="45a0a-192">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
