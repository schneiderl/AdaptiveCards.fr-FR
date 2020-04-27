---
title: Langage de modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 08/01/2019
ms.topic: article
ms.openlocfilehash: ffd2ec065550f483bf602483eebf622565f7f47a
ms.sourcegitcommit: e6418d692296e06be7412c95c689843f9db5240d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82136175"
---
# <a name="adaptive-cards-template-language"></a>Langage de modèle de cartes adaptatives

La création de modèles permet de séparer les **données** de la **disposition** dans votre carte adaptative. Le langage de modèle est la syntaxe utilisée pour créer un modèle. 

> Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).

> [!IMPORTANT] 
> 
> Ces fonctionnalités sont **en préversion et sujettes à modification**. Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.

Quand vous créez un modèle, vous pouvez soit spécifier les données inline avec la charge utile `AdaptiveCard`, soit les spécifier au moment de l’exécution à l’aide des [kits SDK de création de modèles](sdk.md).

## <a name="specify-data-within-the-card"></a>Spécifier des données dans la carte

Pour fournir des données directement dans la charge utile de la carte, ajoutez simplement un attribut `$data` à votre `AdaptiveCard` (voir ci-dessous).

## <a name="binding-to-the-data"></a>Liaison aux données

Vous pouvez établir une liaison aux données au sein de l’élément `body` ou `actions` de la carte.

* La syntaxe de liaison commence par `{` et se termine par `}`. Par exemple : `{myProperty}`
* Notation par points pour accéder aux sous-objets
* Syntaxe d’indexeur pour récupérer des propriétés par clé ou des éléments dans un tableau
* Gestion appropriée des valeurs Null pour les hiérarchies profondes
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

Une autre approche, d’ailleurs plus vraisemblable, consiste à créer un « modèle » de carte réutilisable sans inclure les données. Vous pouvez stocker ce modèle en tant que fichier et l’ajouter au contrôle de code source.

**EmployeeCardTemplate.json**

```json
{
    "type": "AdaptiveCard",
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

Ensuite, chargez-le et fournissez les données au moment de l’exécution à l’aide des [kits SDK de création de modèles](sdk.md).

**Exemple JavaScript**

Cet exemple utilise le package [adaptivecards-templating](https://npmjs.com/package/adaptivecards-templating).

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

> Faites un essai sur : **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**

[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Éditeur d’exemple de données** : spécifiez un exemple de données ici pour voir la carte liée aux données en « Mode Aperçu ». Ce volet contient un petit bouton permettant de remplir la structure de données avec un exemple de données existant.
* **Structure de données** : il s’agit de la structure de votre exemple de données. Pour créer une liaison à des champs, faites-les glisser sur l’aire de conception. 
* **Mode Aperçu** : appuyez sur le bouton de la barre d’outils pour basculer entre l’expérience de modification et l’expérience d’aperçu de l’exemple de données.
* **Ouvrir l’exemple** : cliquez sur ce bouton pour ouvrir divers exemples de charge utile.

## <a name="advanced-binding"></a>Liaison avancée

### <a name="binding-scopes"></a>Étendues de liaison

Des mots clés réservés vous donnent accès à différentes étendues de liaison. 

*Remarque* : Ils ne sont pas tous implémentés dans la préversion.

```json
{
    "{<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating",
    "$host": "Access properties of the host *(not working yet)*"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Affectation d’un contexte de données à des éléments

Pour affecter un « contexte de données » à un élément, ajoutez un attribut `$data` à l’élément.

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

Cette partie relève un peu de la « magie noire ». Vos commentaires sont les bienvenus.

* Si la propriété `$data` d’un élément de carte adaptative est liée à un **tableau**, **cet élément est répété pour chaque élément du tableau**. 
* Toute expression de liaison (`{myProperty}`) utilisée dans les valeurs de propriété a pour étendue l’**élément individuel** dans le tableau.
* En cas de liaison à un tableau de chaînes, utilisez `{$data}` pour accéder à l’élément de chaîne individuel. Par exemple : `"text": "{$data}"`

Par exemple, le `TextBlock` ci-dessous est répété 3 fois car `$data` est un tableau. Notez que la propriété `text` est liée à la propriété `name` d’un objet individuel dans le tableau. 

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

Aucun langage de création de modèles ne serait complet sans des fonctions d’assistance. Nous allons proposer un ensemble standard de fonctions qui marcheront sur chaque SDK. 

La syntaxe présentée ici étant toujours en suspens, revenez plus tard. Voici toutefois une ébauche de ce que nous avons l’intention de faire :

### <a name="string-functions"></a>Fonctions de chaîne

* substr
* indexOf *(ne fonctionne pas encore)*
* toUpper *(ne fonctionne pas encore)*
* toLower *(ne fonctionne pas encore)*

### <a name="number-functions"></a>Fonctions numériques

* Mise en forme (devise, décimale, etc.) *(ne fonctionne pas encore)*

### <a name="date-functions"></a>Fonctions de date

* Analyse des formats de chaîne de date connus *(ne fonctionne pas encore)*
* Mise en forme des représentations de date/heure connues *(ne fonctionne pas encore)*

### <a name="conditional-functions"></a>Fonctions conditionnelles

* if(*expression*, *valeur_true*, *valeur_false*)

**Exemple `if`**

```json
{
    "type": "TextBlock",
    "color": "{if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="data-manipulation"></a>Manipulation de données

* JSON.parse : capacité à analyser une chaîne JSON 

**Exemple `JSON.parse`**

Il s’agit d’une réponse Azure DevOps où la propriété `message` est une chaîne sérialisée au format JSON. Pour pouvoir accéder aux valeurs de la chaîne, nous devons utiliser la fonction `JSON.parse` dans notre modèle.

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

**Utilisation**

```json
{
    "type": "TextBlock",
    "text": "{JSON.parse(message).releaseName}"
}
```

**Ce qui donne**

```json
{
    "type": "TextBlock",
    "text": "Release-104"
}
```

### <a name="custom-functions"></a>Fonctions personnalisées

Nous voulons nous assurer que les hôtes peuvent ajouter des fonctions personnalisées, ce qui signifie qu’il nous faut une stratégie de secours fiable pour gérer les fonctions non prises en charge. Ceci est encore à l’étude.

## <a name="conditional-layout"></a>Disposition conditionnelle

Pour supprimer un élément entier si une condition est remplie, utilisez la propriété `$when`. Si `$when` prend la valeur `false`, l’utilisateur ne voit pas l’élément.

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

À l’heure actuelle, il n’est pas possible de composer ensemble les « parties » d’un modèle. Toutefois, nous explorons différentes pistes et espérons vous en dire plus très bientôt. Vos idées sont les bienvenues !


## <a name="examples"></a>Exemples

Parcourez la [page d’exemples](https://adaptivecards.io/samples) mise à jour pour explorer toutes sortes de nouvelles cartes basées sur des modèles.
