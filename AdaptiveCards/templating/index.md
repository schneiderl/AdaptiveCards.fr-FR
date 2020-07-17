---
title: Vue d’ensemble de la création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 05/18/2020
ms.topic: article
ms.openlocfilehash: 41eb972603b1688a1f1857cec83208b9b55b02c3
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417619"
---
# <a name="adaptive-cards-templating"></a>Création de modèles de cartes adaptatives

Nous sommes heureux de partager une préversion de nouveaux outils qui vous aideront à **créer**, **réutiliser** et **partager** des cartes adaptatives. 

> [!IMPORTANT] 
> 
> **Changements cassants** dans la version **RC (Release Candidate) de mai 2020**
>
> La version Release Candidate de la création de modèles contient des changements cassants mineurs que vous devez connaître si vous utilisez les anciens packages. Voir ci-dessous pour plus de détails.


## <a name="breaking-changes-as-of-may-2020"></a>Changements cassants de mai 2020

1. La syntaxe de liaison a changé et passe de `{...}` à `${...}`. 
    * Par exemple : `"text": "Hello {name}"` devient `"text": "Hello ${name}"`
2. L’API JavaScript ne contient plus d’objet `EvaluationContext`. Passez simplement vos données à la fonction `expand`. Consultez la [page du SDK](sdk.md) pour obtenir les détails complets.
3. L’API .NET a été reconçue pour correspondre davantage à l’API JavaScript. Consultez la [page du SDK](sdk.md) pour obtenir les détails complets.

## <a name="how-can-templating-help-you"></a>Comment la création de modèles peut vous aider

La création de modèles permet de séparer des **données** d’une **disposition** dans une carte adaptative. 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a>Elle permet de concevoir une carte une seule fois, puis de peupler celles-ci de données réelles

Aujourd’hui, il est impossible de créer une carte à l’aide du [concepteur de carte adaptative](https://adaptivecards.io/designer) et d’utiliser ce JSON pour alimenter la charge utile avec du **contenu dynamique**. Pour ce faire, vous devez écrire du code personnalisé pour générer une chaîne JSON, ou utiliser les kits de développement logiciel (SDK) Modèle objet pour créer un modèle objet représentant votre carte et le sérialiser dans JSON. Dans les deux cas, le concepteur effectue une opération unidirectionnelle ponctuelle et facilite l’ajustement du modèle de carte une fois celle-ci convertie en code.

### <a name="it-makes-transmissions-over-the-wire-smaller"></a>Il réduit le volume des transmissions par câble

Imaginez un monde où un modèle et des données peuvent être combinés **directement sur le client**. Cela signifie que, si vous utilisez le même modèle plusieurs fois, ou souhaitez le mettre à jour avec de nouvelles données, vous devez simplement envoyer de nouvelles données à l’appareil qui réutilise le même modèle indéfiniment.

### <a name="it-helps-you-create-a-great-looking-card-from-just-the-data-you-provide"></a>Il vous aide à créer une carte de bel aspect simplement à partir des données que vous fournissez

Nous pensons que les cartes adaptatives sont remarquables, mais que se passerait-il si vous n’aviez pas à écrire de carte adaptative pour tout ce que vous voulez afficher à un utilisateur ? Un service de modèles (décrit ci-dessous) nous permet de créer un monde où chacun peut contribuer, découvrir et partager des modèles sur tout type de données. 

Partagez au sein de vos propres projets, de votre organisation ou avec l’Internet entier.

### <a name="ai-and-other-services-could-improve-user-experiences"></a>L’intelligence artificielle et d’autres services peuvent améliorer l’expérience utilisateur

En séparant les données du contenu, la solution ouvre la porte à l’intelligence artificielle et à d’autres services pour analyser les données des cartes que nous voyons et améliorer la productivité des utilisateurs ou nous aider à trouver des informations.

## <a name="what-is-adaptive-cards-templating"></a>Qu’est-ce que la création de modèles de cartes adaptatives ?

Il est composé de 3 composants principaux :

1. Le **[langage de gabarit](language.md)** est la syntaxe utilisée pour le créer un modèle. Le concepteur vous permet même d’afficher un aperçu de vos modèles au moment de la conception en incluant des « exemples de données ».
2. Des **[kits de développement (SDK) de modèles](sdk.md)** existent sur toutes les plateformes de carte adaptative prises en charge. Ces kits de développement logiciel (SDK) permettent de peupler un modèle de données réelles, sur le serveur principal ou directement sur le client. 
3. Le **[service de modèles](service.md)** est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.

## <a name="template-language"></a>Langage de modèle

Le langage de modèle est la syntaxe utilisée pour créer un modèle de carte adaptative. 

> [!NOTE]
> 
> Suivez avec l’exemple ci-dessous en ouvrant un nouvel onglet pour
>
> **https://adaptivecards.io/designer**
> 
> Cliquez sur le bouton **Mode Aperçu** pour basculer entre le mode création et le mode aperçu.

![Capture d’écran du concepteur](content/2019-08-01-13-58-27.png)

Le concepteur vient d’être mis à jour et prend maintenant en charge la création de modèles et fournit des **exemples de données** pour voir un aperçu de la carte en cours de conception.

Collez l’exemple ci-dessous dans le volet de l’**éditeur de charge utile de carte** : 

**EmployeeCardTemplate.json**

```json
{
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "ColumnSet",
            "style": "accent",
            "bleed": true,
            "columns": [
                {
                    "type": "Column",
                    "width": "auto",
                    "items": [
                        {
                            "type": "Image",
                            "url": "${photo}",
                            "altText": "Profile picture",
                            "size": "Small",
                            "style": "Person"
                        }
                    ]
                },
                {
                    "type": "Column",
                    "width": "stretch",
                    "items": [
                        {
                            "type": "TextBlock",
                            "text": "Hi ${name}!",
                            "size": "Medium"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Here's a bit about your org...",
                            "spacing": "None"
                        }
                    ]
                }
            ]
        },
        {
            "type": "TextBlock",
            "text": "Your manager is: **${manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "${peers}",
                    "title": "${name}",
                    "value": "${title}"
                }
            ]
        }
    ]
}
```

Collez ensuite les données JSON ci-dessous dans l’**éditeur d’exemple de données**. 

L’**exemple de données** vous permet de voir exactement comment votre carte apparaîtra au moment de l’exécution, quand elle recevra des données réelles.

**EmployeeData**

```json
{
    "name": "Matt",
    "photo": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
    "manager": {
        "name": "Thomas",
        "title": "PM Lead"
    },
    "peers": [
        {
            "name": "Lei",
            "title": "Sr Program Manager"
        },
        {
            "name": "Andrew",
            "title": "Program Manager II"
        },
        {
            "name": "Mary Anne",
            "title": "Program Manager"
        }
    ]
}
```

Cliquez sur le bouton **Mode Aperçu**. Le rendu de la carte doit être conforme à l’exemple de données fourni ci-dessus. N’hésitez pas à apporter des ajustements à l’exemple de données et observez en temps réel la mise à jour de la carte.

**Félicitations**, vous venez de créer votre premier modèle de carte adaptative. Voyons à présent comment peupler le modèle de données réelles.

> En savoir plus sur le [langage de modèle](language.md)

## <a name="sdk-support"></a>Prise en charge du Kit de développement logiciel (SDK)

Les kits de développement logiciel (SDK) de création de modèles permettent de remplir un modèle de données réelles.

> [!NOTE]
>
> À ce jour, les kits SDK de création de modèles sont disponibles pour .NET et NodeJS. Nous publierons au fur et à mesure les kits SDK pour toutes les autres plateformes de cartes adaptatives comme iOS, Android, UWP, etc.

Plate-forme | Package | Installer | Documentation
--- | --- | --- | ---
JavaScript | [![Installation npm](https://img.shields.io/npm/v/adaptivecards-templating.svg)](https://www.npmjs.com/package/adaptivecards-templating) | `npm install adaptivecards-templating` | [Documentation](https://www.npmjs.com/package/adaptivecards-templating)
.NET | [![Installation NuGet](https://img.shields.io/nuget/vpre/AdaptiveCards.Templating.svg)](https://www.nuget.org/packages/AdaptiveCards.Templating) | `dotnet add package AdaptiveCards.Templating` | [Documentation](https://docs.microsoft.com/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a>Exemple JavaScript

Le code JavaScript ci-dessous montre le modèle général qui sera utilisé pour peupler un modèle de données.

```js
var template = new ACData.Template({ 
    // Card Template JSON
});

var card = template.expand({
    $root: {
        // Data Fields
    }
});

// Now you have an AdaptiveCard ready to render!
```

### <a name="c-example"></a>Exemple C#

Le code C# ci-dessous montre le modèle général qui sera utilisé pour renseigner un modèle de données.

```csharp
var template = new AdaptiveCards.Templating.AdaptiveCardTemplate(cardJson);
   
var card = template.Expand(new {Key="Value"});

// Now you have an AdaptiveCard ready to render!
```

> En savoir plus sur les [Kits de développement logiciel (SDK) de création de modèles](sdk.md)

## <a name="template-service"></a>Service de modèles

Le service de modèles de cartes adaptatives est un service de preuve de concept qui permet à quiconque de trouver, modifier et partager un ensemble de modèles bien connus.

Il est utile si vous voulez afficher des données sans vous ennuyer à écrire une carte adaptative personnalisée pour celles-ci.

L’API permettant d’obtenir un modèle est assez simple, mais le service offre en fait bien plus, notamment la possibilité d’analyser vos données et de trouver un modèle susceptible de vous convenir.

`HTTP GET https://templates.adaptivecards.io/graph.microsoft.com/Profile.json`

Tous les modèles sont des fichiers JSON plats stockés dans un référentiel GitHub afin que tout le monde puisse y contribuer, comme à tout autre code open source.

> En savoir plus sur [le service de modèles de carte](service.md)

## <a name="whats-next-and-sending-feedback"></a>Étapes suivantes et envoi de commentaires

La création de modèles et la séparation de la présentation et des données nous rapprochent de l’objectif de notre mission : « un écosystème pour un échange de contenu standardisé entre les applications et les services ». Nous avons beaucoup à dire dans ce domaine, donc restez à l’écoute et partagez votre expérience sur [GitHub](https://github.com/Microsoft/AdaptiveCards/issues) !
