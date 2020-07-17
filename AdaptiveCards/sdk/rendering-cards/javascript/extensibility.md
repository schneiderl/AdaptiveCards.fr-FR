---
title: Extensibilité-SDK JavaScript
author: matthidinger
ms.author: mahiding
ms.date: 07/16/2020
ms.topic: article
ms.openlocfilehash: 81c60e200d2fcbc844a3ae3f4fdefa0ddaa399d3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417536"
---
# <a name="extensibility---javascript"></a><span data-ttu-id="340e9-102">Extensibilité-JavaScript</span><span class="sxs-lookup"><span data-stu-id="340e9-102">Extensibility - JavaScript</span></span>

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a><span data-ttu-id="340e9-103">Extensibilité avec le kit de développement logiciel (SDK) JS version 2,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="340e9-103">Extensibility with the JS SDK version 2.0 and greater</span></span>

### <a name="before-you-start"></a><span data-ttu-id="340e9-104">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="340e9-104">Before you start</span></span>

> <span data-ttu-id="340e9-105">**Important**: la version 2,0 et ultérieure du kit de développement logiciel (SDK) js utilise des [décorateurs de machine à écrire](https://www.typescriptlang.org/docs/handbook/decorators.html).</span><span class="sxs-lookup"><span data-stu-id="340e9-105">**IMPORTANT**: Version 2.0 and greater of the JS SDK makes use of [TypeScript decorators](https://www.typescriptlang.org/docs/handbook/decorators.html).</span></span> <span data-ttu-id="340e9-106">Les décorateurs sont toujours une fonctionnalité expérimentale et doivent être explicitement activés dans votre `tsconfig.js` fichier :</span><span class="sxs-lookup"><span data-stu-id="340e9-106">Decorators are still an experimental feature and must be explicitly enabled in your `tsconfig.js` file:</span></span>

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
<span data-ttu-id="340e9-107">La version 2,0 du kit de développement logiciel (SDK) JS introduit des modifications importantes dans la façon dont les éléments et les actions personnalisés sont implémentés et inscrits.</span><span class="sxs-lookup"><span data-stu-id="340e9-107">Version 2.0 of the JS SDK introduces breaking changes in the way custom elements and actions are implemented and registered.</span></span> <span data-ttu-id="340e9-108">Pour obtenir un exemple d’implémentation et d’inscription d’un élément ou d’une action à l’aide des versions précédentes du kit de développement logiciel (SDK), consultez [extensibilité avec le kit de développement logiciel (SDK) js antérieur à la version 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).</span><span class="sxs-lookup"><span data-stu-id="340e9-108">For an example on how to implement and register an element or action using previous versions of the SDK, see [Extensibility with the JS SDK prior to version 2.0](#extensibility-with-the-js-sdk-prior-to-version-20).</span></span>


### <a name="custom-elements"></a><span data-ttu-id="340e9-109">Éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="340e9-109">Custom elements</span></span>
<span data-ttu-id="340e9-110">Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="340e9-110">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="340e9-111">Créer une nouvelle classe dérivant de`CardElement`</span><span class="sxs-lookup"><span data-stu-id="340e9-111">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="340e9-112">Créer son schéma en déclarant des définitions de propriétés statiques</span><span class="sxs-lookup"><span data-stu-id="340e9-112">Create its schema by declaring static property definitions</span></span>
- <span data-ttu-id="340e9-113">Implémenter ses `getJsonTypeName` méthodes, et `internalRender`</span><span class="sxs-lookup"><span data-stu-id="340e9-113">Implement its `getJsonTypeName`, and `internalRender` methods</span></span>
- <span data-ttu-id="340e9-114">L’inscrire dans le registre des éléments globaux ou utiliser un registre personnalisé par carte</span><span class="sxs-lookup"><span data-stu-id="340e9-114">Register it in the global element registry, or use a custom registry on a per-card basis</span></span>


<span data-ttu-id="340e9-115">Prenons un exemple et implémentons un élément de barre de progression simple :</span><span class="sxs-lookup"><span data-stu-id="340e9-115">Let's take an example and implement a simple Progress Bar element:</span></span>
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
<span data-ttu-id="340e9-116">Vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="340e9-116">That's it.</span></span> <span data-ttu-id="340e9-117">L’élément ProgressBar doit maintenant être inscrit pour être reconnu par le kit de développement logiciel (SDK).</span><span class="sxs-lookup"><span data-stu-id="340e9-117">The ProgressBar element now needs to be registered in order to be recognized by the SDK.</span></span> <span data-ttu-id="340e9-118">Vous pouvez l’inscrire globalement :</span><span class="sxs-lookup"><span data-stu-id="340e9-118">You can register it globally:</span></span>

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

<span data-ttu-id="340e9-119">Vous pouvez utiliser un registre par carte qui permet d’utiliser différents registres pour différentes cartes dans votre application :</span><span class="sxs-lookup"><span data-stu-id="340e9-119">Or you can use a per-card registry, which allows the use of different registries for different cards in your application:</span></span>

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

### <a name="custom-actions"></a><span data-ttu-id="340e9-120">Actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="340e9-120">Custom actions</span></span>
<span data-ttu-id="340e9-121">Les étapes d’implémentation d’une action personnalisée sont les mêmes que celles des éléments.</span><span class="sxs-lookup"><span data-stu-id="340e9-121">The steps to implementing a custom action are the same as those for elements.</span></span> <span data-ttu-id="340e9-122">La seule différence est que les actions sont inscrites dans les registres des actions, et non dans les registres des éléments.</span><span class="sxs-lookup"><span data-stu-id="340e9-122">The only difference is that actions are registered in action registries, and not in element registries.</span></span>

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

<span data-ttu-id="340e9-123">Inscrire la nouvelle action globalement :</span><span class="sxs-lookup"><span data-stu-id="340e9-123">Register the new action globally:</span></span>
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

<span data-ttu-id="340e9-124">Ou utilisez un registre par carte :</span><span class="sxs-lookup"><span data-stu-id="340e9-124">Or use a per-card registry:</span></span>
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

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a><span data-ttu-id="340e9-125">Extensibilité avec le kit de développement logiciel (SDK) JS antérieur à la version 2,0</span><span class="sxs-lookup"><span data-stu-id="340e9-125">Extensibility with the JS SDK prior to version 2.0</span></span>

### <a name="custom-elements"></a><span data-ttu-id="340e9-126">Éléments personnalisés</span><span class="sxs-lookup"><span data-stu-id="340e9-126">Custom elements</span></span>

<span data-ttu-id="340e9-127">Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="340e9-127">The steps for creating a custom Adaptive Card element type are:</span></span>
- <span data-ttu-id="340e9-128">Créer une nouvelle classe dérivant de`CardElement`</span><span class="sxs-lookup"><span data-stu-id="340e9-128">Create a new class deriving from `CardElement`</span></span>
- <span data-ttu-id="340e9-129">Implémenter `getJsonTypeName` ses `parse` méthodes,, `toJSON` `internalRender` et `renderSpeech`</span><span class="sxs-lookup"><span data-stu-id="340e9-129">Implement its `getJsonTypeName`, `parse`, `toJSON`, `internalRender` and `renderSpeech` methods</span></span>
- <span data-ttu-id="340e9-130">Inscrivez-le en l’ajoutant au registre des éléments du convertisseur</span><span class="sxs-lookup"><span data-stu-id="340e9-130">Register it by adding it to the renderer's element registry</span></span>

<span data-ttu-id="340e9-131">Prenons un exemple et implémentons un élément de barre de progression simple :</span><span class="sxs-lookup"><span data-stu-id="340e9-131">Let's take an example and implement a simple Progress Bar element:</span></span>

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

<span data-ttu-id="340e9-132">Vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="340e9-132">That's it.</span></span> <span data-ttu-id="340e9-133">À présent, il vous suffit d’inscrire la classe de barre de progression auprès du convertisseur :</span><span class="sxs-lookup"><span data-stu-id="340e9-133">Now just register the Progress Bar class with the renderer:</span></span>

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a><span data-ttu-id="340e9-134">Actions personnalisées</span><span class="sxs-lookup"><span data-stu-id="340e9-134">Custom actions</span></span>

<span data-ttu-id="340e9-135">Les étapes de création d’une action de carte adaptative personnalisée sont essentiellement les mêmes que celles des éléments personnalisés.</span><span class="sxs-lookup"><span data-stu-id="340e9-135">The steps for creating a custom Adaptive Card action are essentially the same as those for custom elements.</span></span> <span data-ttu-id="340e9-136">Voici un exemple simple d’action d’alerte qui affiche simplement une boîte de message avec du texte configurable :</span><span class="sxs-lookup"><span data-stu-id="340e9-136">Here is a simple example of an Alert Action that simply displays a message box with configurable text:</span></span>

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

<span data-ttu-id="340e9-137">Inscrivez maintenant la nouvelle action :</span><span class="sxs-lookup"><span data-stu-id="340e9-137">Now register the new action:</span></span>

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a><span data-ttu-id="340e9-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="340e9-138">Example</span></span>

<span data-ttu-id="340e9-139">Voici un exemple de carte qui utilise à la fois l’élément ProgressBar et l’action AlertAction :</span><span class="sxs-lookup"><span data-stu-id="340e9-139">Here is a sample card that uses both the ProgressBar element and AlertAction action:</span></span>
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

<span data-ttu-id="340e9-140">Et voici comment il est rendu : ![ image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span><span class="sxs-lookup"><span data-stu-id="340e9-140">And here is how it renders: ![image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)</span></span>
