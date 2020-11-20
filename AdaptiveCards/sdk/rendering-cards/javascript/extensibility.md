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
# <a name="extensibility---javascript"></a>Extensibilité-JavaScript

## <a name="extensibility-with-the-js-sdk-version-20-and-greater"></a>Extensibilité avec le kit de développement logiciel (SDK) JS version 2,0 et versions ultérieures

### <a name="before-you-start"></a>Avant de commencer

> **Important**: la version 2,0 et ultérieure du kit de développement logiciel (SDK) js utilise des [décorateurs de machine à écrire](https://www.typescriptlang.org/docs/handbook/decorators.html). Les décorateurs sont toujours une fonctionnalité expérimentale et doivent être explicitement activés dans votre `tsconfig.js` fichier :

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
La version 2,0 du kit de développement logiciel (SDK) JS introduit des modifications importantes dans la façon dont les éléments et les actions personnalisés sont implémentés et inscrits. Pour obtenir un exemple d’implémentation et d’inscription d’un élément ou d’une action à l’aide des versions précédentes du kit de développement logiciel (SDK), consultez [extensibilité avec le kit de développement logiciel (SDK) js antérieur à la version 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).


### <a name="custom-elements"></a>Éléments personnalisés
Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :
- Créer une nouvelle classe dérivant de `CardElement`
- Créer son schéma en déclarant des définitions de propriétés statiques
- Implémenter ses `getJsonTypeName` méthodes, et `internalRender`
- L’inscrire dans le registre des éléments globaux ou utiliser un registre personnalisé par carte


Prenons un exemple et implémentons un élément de barre de progression simple :
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
Vous avez terminé. L’élément ProgressBar doit maintenant être inscrit pour être reconnu par le kit de développement logiciel (SDK). Vous pouvez l’inscrire globalement :

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

Vous pouvez utiliser un registre par carte qui permet d’utiliser différents registres pour différentes cartes dans votre application :

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

### <a name="custom-inputs"></a>Entrées personnalisées
Une entrée est un type spécial d’élément dédié à la collecte des données entrées par l’utilisateur final qui peut ensuite être passée comme paramètre à des actions.

La version 2. x du kit de développement logiciel (SDK) Adaptive Cards JS introduit deux modifications notables lorsqu’il s’agit d’entrées :
- **Validation des entrées :** il existe maintenant un mécanisme de validation d’entrée intégré qui gère automatiquement les erreurs de validation, notamment les signaux visuels
- **Améliorations de l’accessibilité :** les entrées intégrées offrent une meilleure prise en charge des fonctionnalités d’accessibilité

Pour cette raison, l’implémentation d’entrées personnalisées requiert un peu plus de logique que l’implémentation d’éléments simples. Le tableau ci-dessous répertorie toutes les méthodes qu’une implémentation d’entrée personnalisée doit implémenter pour partiocipate dans le mécanisme de validation d’entrée et être accessible :

| Méthode | Description |
| --------- | ------------- |
| `protected updateInputControlAriaLabelledBy()` | Cette méthode est appelée pendant la séquence de validation d’entrée. En cas d’échec de la validation d’une entrée, le message d’erreur qui lui est associé s’affiche et l’attribut du contrôle d’entrée sous-jacent `aria-labelledby` doit être mis à jour afin que l’entrée soit conforme aux exigences d’accessibilité. Les entrées personnalisées doivent remplacer `updateInputControlAriaLabelledBy` pour appliquer l' `aria-labelledby` attribut approprié au contrôle d’entrée sous-jacent. La `getAllLabelIds(): string[]` méthode peut être utilisée pour récupérer les ID de toutes les étiquettes qui doivent être spécifiées dans l' `aria-labelledby` attribut.  |
| `protected internalRender(): HTMLElement` | Tout comme pour tout autre élément personnalisé de carte adaptative, `internalRender` doit être substitué pour afficher votre entrée comme vous le souhaitez. C’est là que vous souhaitez créer le contrôle d’entrée sous-jacent réel. |
| `protected get isNullable(): boolean` | Indique si l’entrée prend en charge les valeurs non définies (par exemple, Input. Text, contrairement à Input. Toggle). Les entrées personnalisées doivent remplacer cet accesseur Get de propriété pour indiquer s’ils prennent en charge des valeurs non définies. L’implémentation de base retourne `true` . |
| `public focus()` | Lorsque des erreurs de validation se produisent, le focus est automatiquement placé sur la première entrée qui n’a pas pu être validée. Dans certains cas, l’implémentation de base de `focus` peut simplement fonctionner pour des entrées personnalisées. Lorsque cela n’est pas le cas, les contrôles d’entrée personnalisés doivent remplacer `focus` pour mettre explicitement le focus sur le contrôle d’entrée sous-jacent.  |
| `public abstract isSet(): boolean` | Indique si la valeur de l’entrée a été définie par l’utilisateur. Cette méthode est appelée pendant la séquence de validation d’entrée pour déterminer si l’entrée réussit ou échoue à la validation. Les entrées personnalisées doivent `isSet` être substituées afin de participer au mécanisme de validation d’entrée. |
| `public isValid(): boolean` | Indique si la valeur de l’entrée est valide. Cette méthode est appelée pendant la séquence de validation d’entrée pour déterminer si l’entrée réussit ou échoue à la validation. Les entrées personnalisées doivent être substituées afin de `isValid` participer au mécanisme de validation d’entrée. L’implémentation de base retourne `true` . |
| `public abstract get value(): any` | Retourne la valeur de l’entrée. Les entrées personnalisées doivent remplacer ceci afin que la valeur de l’entrée soit récupérée à partir du contrôle d’entrée sous-jacent. |


### <a name="custom-actions"></a>Actions personnalisées
Les étapes d’implémentation d’une action personnalisée sont les mêmes que celles des éléments. La seule différence est que les actions sont inscrites dans les registres des actions, et non dans les registres des éléments.

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

Inscrire la nouvelle action globalement :
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

Ou utilisez un registre par carte :
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

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a>Extensibilité avec le kit de développement logiciel (SDK) JS antérieur à la version 2,0

### <a name="custom-elements"></a>Éléments personnalisés

### <a name="before-you-start"></a>Avant de commencer

> **Important**: la version 2,0 et ultérieure du kit de développement logiciel (SDK) js utilise des [décorateurs de machine à écrire](https://www.typescriptlang.org/docs/handbook/decorators.html). Les décorateurs sont toujours une fonctionnalité expérimentale et doivent être explicitement activés dans votre `tsconfig.js` fichier :

```json
{
   "compilerOptions": {
       "experimentalDecorators": true
   }
}
```
La version 2,0 du kit de développement logiciel (SDK) JS introduit des modifications importantes dans la façon dont les éléments et les actions personnalisés sont implémentés et inscrits. Pour obtenir un exemple d’implémentation et d’inscription d’un élément ou d’une action à l’aide des versions précédentes du kit de développement logiciel (SDK), consultez [extensibilité avec le kit de développement logiciel (SDK) js antérieur à la version 2,0](#extensibility-with-the-js-sdk-prior-to-version-20).


### <a name="custom-elements"></a>Éléments personnalisés
Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :
- Créer une nouvelle classe dérivant de `CardElement`
- Créer son schéma en déclarant des définitions de propriétés statiques
- Implémenter ses `getJsonTypeName` méthodes, et `internalRender`
- L’inscrire dans le registre des éléments globaux ou utiliser un registre personnalisé par carte


Prenons un exemple et implémentons un élément de barre de progression simple :
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
Vous avez terminé. L’élément ProgressBar doit maintenant être inscrit pour être reconnu par le kit de développement logiciel (SDK). Vous pouvez l’inscrire globalement :

```typescript
AC.GlobalRegistry.elements.register(ProgressBar.JsonTypeName, ProgressBar);
```

Vous pouvez utiliser un registre par carte qui permet d’utiliser différents registres pour différentes cartes dans votre application :

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

### <a name="custom-actions"></a>Actions personnalisées
Les étapes d’implémentation d’une action personnalisée sont les mêmes que celles des éléments. La seule différence est que les actions sont inscrites dans les registres des actions, et non dans les registres des éléments.

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

Inscrire la nouvelle action globalement :
```typescript
AC.GlobalRegistry.actions.register(AlertAction.JsonTypeName, AlertAction);
```

Ou utilisez un registre par carte :
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

## <a name="extensibility-with-the-js-sdk-prior-to-version-20"></a>Extensibilité avec le kit de développement logiciel (SDK) JS antérieur à la version 2,0

### <a name="custom-elements"></a>Éléments personnalisés

Les étapes de création d’un type d’élément de carte adaptative personnalisé sont les suivantes :
- Créer une nouvelle classe dérivant de `CardElement`
- Implémenter `getJsonTypeName` ses `parse` méthodes,, `toJSON` `internalRender` et `renderSpeech`
- Inscrivez-le en l’ajoutant au registre des éléments du convertisseur

Prenons un exemple et implémentons un élément de barre de progression simple :

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

Vous avez terminé. À présent, il vous suffit d’inscrire la classe de barre de progression auprès du convertisseur :

```typescript
Adaptive.AdaptiveCard.elementTypeRegistry.registerType("ProgressBar", () => { return new ProgressBar(); });
```

## <a name="custom-actions"></a>Actions personnalisées

Les étapes de création d’une action de carte adaptative personnalisée sont essentiellement les mêmes que celles des éléments personnalisés. Voici un exemple simple d’action d’alerte qui affiche simplement une boîte de message avec du texte configurable :

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

Inscrivez maintenant la nouvelle action :

```typescript
Adaptive.AdaptiveCard.actionTypeRegistry.registerType("Action.Alert", () => { return new AlertAction(); });
```

## <a name="example"></a>Exemple

Voici un exemple de carte qui utilise à la fois l’élément ProgressBar et l’action AlertAction :
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

Et voici comment il est rendu : ![ image](https://user-images.githubusercontent.com/1334689/52665466-8155e780-2ec0-11e9-841a-7d272ad1d103.png)
