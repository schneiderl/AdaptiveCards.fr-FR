---
title: Vue d’ensemble de la création de modèles
author: matthidinger
ms.author: mahiding
ms.date: 07/29/2019
ms.topic: article
ms.openlocfilehash: fdfe7b46614f046155ab84a5a487105d55afd7cb
ms.sourcegitcommit: ef03c0eff3272a36cfa88daf99c4d57e4bae9599
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72042536"
---
# <a name="adaptive-cards-templating-preview"></a>Création de modèles de cartes adaptatives (préversion)

Nous sommes heureux de partager une préversion de nouveaux outils qui vous aideront à **créer**, **réutiliser** et **partager** des cartes adaptatives. 

> [!IMPORTANT] 
> 
> Ces fonctionnalités sont **en préversion et sujettes à modification**. Vos commentaires sont non seulement bienvenus, mais essentiels pour garantir que nous fournissions les fonctionnalités dont **vous** avez besoin.

## <a name="how-can-templating-help-you"></a>Comment la création de modèles peut-elle vous aider ?

La création de modèles permet de séparer des **données** d’une **disposition** dans une carte adaptative. 

### <a name="it-helps-design-a-card-once-and-then-populate-it-with-real-data"></a>Elle permet de concevoir une carte une seule fois, puis de peupler celles-ci de données réelles

Aujourd’hui, il est impossible de créer une carte à l’aide du [concepteur de carte adaptative](https://adaptivecards.io/designer) et d’utiliser ce JSON pour alimenter la charge utile avec du **contenu dynamique**. Pour ce faire, vous devez écrire du code personnalisé pour générer une chaîne JSON, ou utiliser les kits de développement logiciel (SDK) Modèle objet pour créer un modèle objet représentant votre carte et le sérialiser dans JSON. Dans les deux cas, le concepteur effectue une opération unidirectionnelle ponctuelle et facilite l’ajustement du modèle de carte une fois celle-ci convertie en code.

### <a name="it-makes-tranmissions-over-the-wire-smaller"></a>Il réduit le volume des transmissions par câble

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

Le langue de modèle est la syntaxe utilisée pour créer un modèle de carte adaptative. 

> [!NOTE]
> 
> Suivez avec l’exemple ci-dessous en ouvrant un nouvel onglet pour
>
> **https://vnext.adaptivecards.io/designer**
> 
> Cliquez sur le bouton **Mode Aperçu** pour basculer entre le mode création et le mode aperçu.

![Capture d’écran du concepteur](content/2019-08-01-13-58-27.png)

Le [« Concepteur vNext »](https://vnext.adaptivecards.io/designer) ajoute la prise en charge de la création de modèles et de la fourniture d’**exemples de données** pour afficher un aperçu de la carte en cours de conception.

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
                            "url": "{photo}",
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
                            "text": "Hi {name}!",
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
            "text": "Your manager is: **{manager.name}**"
        },
        {
            "type": "TextBlock",
            "text": "Your peers are:"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "{peers}",
                    "title": "{name}",
                    "value": "{title}"
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
> Au cours de la période de préversion initiale, nous ne disposons que d’un ensemble limité de kits de développement logiciel (SDK). Lors de la mise en production, des bibliothèques de création de modèles seront disponibles pour chaque plateforme de cartes adaptatives prise en charge.

Plateforme | Installer | Documentation
--- | --- | ---
JavaScript | `npm install adaptivecards-templating` | [Documentation](https://www.npmjs.com/package/adaptivecards-templating)
.NET | `nuget install AdaptiveCards.Templating` | [Documentation](https://docs.microsoft.com/en-us/adaptive-cards/templating/sdk#net)

### <a name="javascript-example"></a>Exemple JavaScript

Le code JavaScript ci-dessous montre le modèle général qui sera utilisé pour peupler un modèle de données.

```js
var template = new ACData.Template({ 
    // EmployeeCardTemplate goes here
});

var dataContext = new ACData.EvaluationContext();
dataContext.$root = {
    // Data goes here
};

var card = template.expand(dataContext);
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

La création de modèles et la séparation de la présentation et des données nous rapprochent de l’objectif de notre mission : « un écosystème pour l’échange de contenu de carte de manière commune et cohérente ».

Nous sommes impatients de pouvoir partager des informations supplémentaires dès que possible. En attendant, veuillez nous faire part de vos commentaires ici, sur [GitHub](https://github.com/microsoft/AdaptiveCards) ou sur Twitter **[@MattHidinger](https://twitter.com/matthidinger)** / **#AdaptiveCards**. 
