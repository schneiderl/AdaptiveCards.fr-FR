---
title: Langage de modèle de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 1b5a7df25eedb96ec6edfe02912d328ab59d2801
ms.sourcegitcommit: c921a7bb15a95c0ceb803ad375501ee3b8bef028
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83631343"
---
# <a name="adaptive-cards-template-language"></a>Langage de modèle de cartes adaptatives

La création de modèles permet de séparer les **données** de la **disposition** dans votre carte adaptative. Le langage de modèle est la syntaxe utilisée pour créer un modèle. 

> Lisez la [vue d’ensemble de la création de modèles de cartes adaptatives](index.md).

> [!IMPORTANT] 
> 
> **Changements cassants** dans la version **RC (Release Candidate) de mai 2020**
>
> Nous avons travaillé dur à la publication des modèles et nous sommes dans la dernière ligne droite ! Nous avons dû apporter des modifications mineures avant de finaliser la version.

## <a name="breaking-changes-as-of-may-2020"></a>Changements cassants de mai 2020

1. La syntaxe de liaison a changé et passe de `{...}` à `${...}`.
    * Par exemple : `"text": "Hello {name}"` devient `"text": "Hello ${name}"`
    
## <a name="binding-to-data"></a>Liaison de données

L’écriture d’un modèle est aussi simple que de remplacer le contenu « non statique » de votre carte par des « expressions de liaison ».

### <a name="static-card-payload"></a>Charge utile de carte statique

```json
{
   "type": "TextBlock",
   "text": "Matt"
}
```

### <a name="template-payload"></a>Charge utile de modèle

```json
{
   "type": "TextBlock",
   "text": "${firstName}"
}
```

* Les expressions de liaison peuvent être placées à n’importe quel endroit où le contenu statique peut se trouver.
* La syntaxe de liaison commence par `${` et se termine par `}`. Par exemple : `${myProperty}`
* Utilisez la *notation par points* pour accéder aux sous-objets d’une hiérarchie d’objets. Par exemple : `${myParent.myChild}`
* Grâce à une gestion appropriée des valeurs Null, vous n’obtiendrez pas d’exceptions si vous accédez à une propriété Null dans un graphique d’objet.
* Utilisez la *syntaxe d’indexeur* pour récupérer des propriétés par clé ou les éléments d’un tableau. Par exemple : `${myArray[0]}`

## <a name="providing-the-data"></a>Ajout des données

Maintenant que vous disposez d’un modèle, vous devez lui ajouter des données pour le finaliser. Pour ce faire, vous avez deux options :

1. **Option A : Inline dans la charge utile du modèle**. Vous pouvez fournir les données inline dans la charge utile du modèle `AdaptiveCard`. Pour ce faire, il vous suffit d’ajouter un attribut `$data` à l’objet racine `AdaptiveCard`.
2. **Option B : En tant qu’objet de données distinct**. Avec cette option, vous fournissez deux objets distincts au [SDK de création de modèles](sdk.md) au moment de l’exécution : `template` et `data`. Il s’agit de l’approche la plus courante, car en général, vous créez un modèle, puis vous y ajoutez des données dynamiques ultérieurement.

### <a name="option-a-inline-data"></a>Option A : Données inline

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
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
        }
    ]
}
```

### <a name="option-b-separating-the-template-from-the-data"></a>Option B : Séparation du modèle des données

Une autre approche, d’ailleurs plus vraisemblable, consiste à créer un modèle de carte réutilisable sans y inclure de données. Vous pouvez stocker ce modèle en tant que fichier et l’ajouter au contrôle de code source.

**EmployeeCardTemplate.json**

```json
{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hi ${employee.name}! Here's a bit about your org..."
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: ${employee.manager.name}"
        },
        {
            "type": "TextBlock",
            "text": "3 of your peers are: ${employee.peers[0].name}, ${employee.peers[1].name}, ${employee.peers[2].name}"
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
var card = template.expand({
    $root: {
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
    }
});

// Now you have an AdaptiveCard ready to render!
```

## <a name="designer-support"></a>Prise en charge du concepteur

Le concepteur de cartes adaptatives a été mis à jour pour prendre en charge la création de modèles. 

> Faites un essai sur : **[https://adaptivecards.io/designer](https://adaptivecards.io/designer)**

[![image](https://user-images.githubusercontent.com/1432195/53214462-88d46980-3601-11e9-908d-253a1bb940a8.png)](https://adaptivecards.io/designer)

* **Éditeur d’exemple de données** : spécifiez un exemple de données ici pour voir la carte liée aux données en « Mode Aperçu ». Ce volet contient un petit bouton permettant de remplir la structure de données avec un exemple de données existant.
* **Mode Aperçu** : appuyez sur le bouton de la barre d’outils pour basculer entre l’expérience de modification et l’expérience d’aperçu de l’exemple de données.
* **Ouvrir l’exemple** : cliquez sur ce bouton pour ouvrir divers exemples de charge utile.

## <a name="advanced-binding"></a>Liaison avancée

### <a name="binding-scopes"></a>Étendues de liaison

Des mots clés réservés vous donnent accès à différentes étendues de liaison. 

```json
{
    "${<property>}": "Implicitly binds to `$data.<property>`",
    "$data": "The current data object",
    "$root": "The root data object. Useful when iterating to escape to parent object",
    "$index": "The current index when iterating"
}
```

### <a name="assigning-a-data-context-to-elements"></a>Affectation d’un contexte de données à des éléments

Pour affecter un « contexte de données » à un élément, ajoutez un attribut `$data` à l’élément.

```json
{
    "type": "Container",
    "$data": "${mySubObject}",
    "items": [
        {
            "type": "TextBlock",
            "text": "This TextBlock is now scoped directly to 'mySubObject': ${mySubObjectProperty}"
        },
        {
            "type": "TextBlock",
            "text": "To break-out and access the root data, use: ${$root}"
        }
    ]
}
```

## <a name="repeating-items-in-an-array"></a>Répétition d’éléments dans un tableau

* Si la propriété `$data` d’un élément de carte adaptative est liée à un **tableau**, **cet élément est répété pour chaque élément du tableau**. 
* Toute expression de liaison (`${myProperty}`) utilisée dans les valeurs de propriété a pour étendue l’**élément individuel** dans le tableau.
* En cas de liaison à un tableau de chaînes, utilisez `${$data}` pour accéder à l’élément de chaîne individuel. Par exemple : `"text": "${$data}"`

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
            "text": "${name}"
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

## <a name="built-in-functions"></a>Fonctions intégrées

Aucun langage de création de modèles ne serait complet sans une suite de fonctions d’assistance. La création de modèles de cartes adaptatives s’appuie sur le [langage AEL](https://aka.ms/adaptive-expressions), qui est un standard ouvert permettant de déclarer des expressions pouvant être évaluées sur un grand nombre de plateformes différentes. Comme il s’agit d’un vrai sur-ensemble de « Logic Apps », vous pouvez utiliser une syntaxe similaire à celle de Power Automate, etc.

**Il ne s’agit là que d’un petit échantillon des fonctions intégrées.**

Consultez la liste complète des [fonctions prédéfinies du langage AEL](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-adaptive-expressions?view=azure-bot-service-4.0).

### <a name="conditional-evaluation"></a>Évaluation conditionnelle

* if(*expression*, *valeur_true*, *valeur_false*)

**Exemple `if`**

```json
{
    "type": "TextBlock",
    "color": "${if(priceChange >= 0, 'good', 'attention')}"
}
```

### <a name="parsing-json"></a>Analyse du JSON

* JSON (*jsonString*) - Analyser une chaîne JSON

**Exemple `json`**

Il s’agit d’une réponse Azure DevOps où la propriété `message` est une chaîne sérialisée au format JSON. Pour pouvoir accéder aux valeurs de la chaîne, nous devons utiliser la fonction `json` dans notre modèle.

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
    "text": "${json(message).releaseName}"
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

Les fonctions personnalisées sont prises en charge via les API des [SDK de création de modèles](sdk.md). 

## <a name="conditional-layout-with-when"></a>Disposition conditionnelle avec `$when`

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
            "$when": "${price > 30}",
            "text": "This thing is pricy!",
            "color": "attention",
        },
         {
            "type": "TextBlock",
            "$when": "${price <= 30}",
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
