---
title: Langue du modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: 42a1f43fbcfe1416820637af750acc960b9effde
ms.sourcegitcommit: 16a274ce5596001a1c5ab252d9d2a3db6a5a9a0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73750400"
---
# <a name="adaptive-cards-template-language"></a>Langue du modèle de cartes adaptatives

La création de modèles permet de séparer les **données** de la **disposition** dans votre carte adaptative. La langue du modèle est la syntaxe utilisée pour créer un modèle. 

> Pour obtenir une vue d' [ensemble de la création de modèles de cartes adaptatives](index.md) , consultez.

> [!IMPORTANT] 
> 
> Ces fonctionnalités sont **en préversion et sujettes à modification**. Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.

Lors de la création d’un modèle, vous pouvez spécifier les données Inline avec la charge utile `AdaptiveCard`, ou au moment de l’exécution à l’aide des [Kits SDK de création de modèles](sdk.md).

## <a name="specify-data-within-the-card"></a>Spécifier les données dans la carte

Pour fournir des données directement dans la charge utile de la carte, ajoutez simplement un attribut `$data` à votre `AdaptiveCard` (voir ci-dessous).

## <a name="binding-to-the-data"></a>Liaison aux données

Vous pouvez lier les données au sein de la `body` ou `actions` de la carte.

* La syntaxe de liaison commence par `{` et se termine par `}`. Par exemple, `{myProperty}`
* Notation de points pour accéder aux sous-objets
* Syntaxe de l’indexeur pour récupérer des propriétés par clé ou éléments dans un tableau
* Gestion des valeurs NULL gracieuses pour les hiérarchies profondes
* *Documentation de la syntaxe d’échappement bientôt disponible*

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "employee": {
            "name": "Matt",
            "manager": { "name": "Thomas" },
            "peers": [{
                "name": "Andrew" 
            }, { 
                "name": "Lei"
            }, { 
                "name": "Mary Anne"
            }, { 
                "name": "Adam"
            }]
        }
    },
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

## <a name="separating-the-template-from-the-data"></a>Séparation du modèle des données

En guise d’alternative (et plus probable), vous allez créer un « modèle » de carte réutilisable sans inclure les données. Ce modèle peut être stocké en tant que fichier et ajouté au contrôle de code source.

**EmployeeCardTemplate.json**

```json
{
    "type": "AdaptivCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi {employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: {employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: {employee.peers[0].name}, {employee.peers[1].name}, {employee.peers[2].name}"
        }
    ]
}
```

Ensuite, chargez-la et fournissez les données au moment de l’exécution à l’aide des [Kits SDK de création de modèles](sdk.md).

**Exemple JavaScript**

Utilisation du package [adaptivecards-Templating](https://npmjs.com/package/adaptivecards-templating) .

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

// Specify data at runtime
var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    "employee": {
        "name": "Matt",
        "manager": { "name": "Thomas" },
        "peers": [{
            "name": "Andrew" 
        }, { 
            "name": "Lei"
        }, { 
            "name": "Mary Anne"
        }, { 
            "name": "Adam"
        }]
    }
};

var card = template.expand(dataContext);
// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a>Prise en charge du concepteur

Le concepteur de cartes adaptatives a été mis à jour pour prendre en charge la création de modèles. 

> Essayez-le à l’adresse suivante :  **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**

[image ![](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Exemple d’éditeur de données** : spécifiez des exemples de données ici pour afficher la carte liée aux données en mode aperçu. Ce volet contient un petit bouton qui permet de remplir la structure de données à partir des données d’exemple existantes.
* **Structure de données** : il s’agit de la structure de vos exemples de données. Les champs peuvent être glissés sur l’aire de conception pour créer une liaison avec eux 
* **Mode aperçu** -Appuyez sur le bouton de barre d’outils pour basculer entre l’expérience de modification et l’exemple d’expérience de l’aperçu des données
* **Ouvrir l’exemple** : cliquez sur ce bouton pour ouvrir divers exemples de charge utile.

## <a name="advanced-binding"></a>Liaison avancée

### <a name="binding-scopes"></a>Portées de liaison

Il existe quelques mots clés réservés pour accéder à différentes étendues de liaison. 

*Remarque :* tous ces éléments ne sont pas implémentés dans la version préliminaire.

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Assignation d’un contexte de données à des éléments

Pour assigner un « contexte de données » à un élément, ajoutez un attribut `$data` à l’élément.

```json
{
    "type": "Container",
    "$data": "{mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': {mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: {$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a>Répétition d’éléments dans un tableau

Cette partie est un peu « Dark Magic ». Commentaires de bienvenue.

* Si la propriété `$data` d’objets est définie sur un **tableau**, l' **objet lui-même est répété pour chaque élément du tableau.** 
* À mesure qu’il est répété, les `$data` utilisées dans les liaisons de propriété sont limitées à l' **élément individuel** dans le tableau.

Par exemple, le `TextBlock` ci-dessous est répété 3 fois, car il est `$data` est un tableau. Notez que la propriété `text` est liée à la propriété `name` d’un objet individuel dans le tableau. 

```json
{
    "type": "Container",
    "items": [
        {
            "type": "TextBlock",
            "$data": [
                { "name": "Matt" }, 
                { "name": "David" }, 
                { "name": "Thomas" }
            ],
            "text": "{name}"
        }
    ]
}
```

**Ce qui donne :**

```json
{
    "type": "Container",
    "items": [ 
        {
            "type": "TextBlock",
            "text": "Matt"
        },
        {
            "type": "TextBlock",
            "text": "David"
        }
        {
            "type": "TextBlock",
            "text": "Thomas"
        }
    ]
}
```

## <a name="functions"></a>Fonctions

Aucun langage de création de modèles n’est terminé sans aucune fonction d’assistance. Nous allons fournir un ensemble standard de fonctions qui fonctionnent sur chaque kit de développement logiciel (SDK). 

La syntaxe ici est toujours active dans l’air. Veuillez recommencer, mais voici ce que nous avons planifié :

### <a name="string-functions"></a>Fonctions de chaîne

* substr
* indexOf *(ne fonctionne pas encore)*
* toUpper *(ne fonctionne pas encore)*
* toLower *(ne fonctionne pas encore)*

### <a name="number-functions"></a>Fonctions numériques

* Mise en forme (devise, décimal, etc.) *(ne fonctionne pas encore)*

### <a name="date-functions"></a>Fonctions de date

* Analyse des formats de chaîne de date bien connus *(ne fonctionne pas encore)*
* Mise en forme des représentations de date/heure connues *(ne fonctionnant pas encore)*

### <a name="conditional-functions"></a>Fonctions conditionnelles

* if (*expression*, *TrueValue*, *FalseValue*)

**exemple de`if`**

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a>Manipulation de données

* JSON. Parse-capacité à analyser une chaîne JSON 

**exemple de`JSON.parse`**

Il s’agit d’une réponse Azure DevOps où la propriété `message` est une chaîne sérialisée au format JSON. Pour accéder aux valeurs de la chaîne, nous devons utiliser la fonction `JSON.parse` dans notre modèle.

**Données** 

```json
{
    "id": "1291525457129548",
    "status": 4,
    "author": "Matt Hidinger",
    "message": "{\"type\":\"Deployment\",\"buildId\":\"9542982\",\"releaseId\":\"129\",\"buildNumber\":\"20180504.3\",\"releaseName\":\"Release-104\",\"repoProvider\":\"GitHub\"}",
    "start_time": "2018-05-04T18:05:33.3087147Z",
    "end_time": "2018-05-04T18:05:33.3087147Z"
}
```

**Syntaxe**

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

**Ce qui se traduit par**

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a>Fonctions personnalisées

Nous voulons nous assurer que les hôtes peuvent ajouter des fonctions personnalisées, ce qui signifie que nous avons besoin d’une prise en charge fiable de la prise en charge de secours si une fonction n’est pas prise en charge Nous sommes toujours en cours d’évaluation.

## <a name="conditional-layout"></a>Disposition conditionnelle

Pour supprimer l’intégralité d’un élément si une condition est remplie, utilisez la propriété `$when`. Si `$when` prend la valeur `false` l’élément ne s’affiche pas à l’utilisateur.

```json
{
    "type": "AdaptiveCard",
    "$data": {
        "price": "35"
    },
    "body": [
        {
            "type": "TextBlock",
            "$when": "{price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "{price <= 30}",
            "text": "Dang, this thing is cheap!",
            "color": "good"
        }
    ]
}
```

### <a name="composing-templates"></a>Composition de modèles

Il n’existe actuellement aucune prise en charge pour composer les « parties » du modèle. Toutefois, nous explorons les options et espérons partager plus tôt. Toutes les pensées ici Bienvenue !


## <a name="examples"></a>Exemples

Parcourez la [page d’exemples](https://adaptivecards.io/samples) mise à jour pour explorer toutes sortes de cartes basées sur un modèle.
