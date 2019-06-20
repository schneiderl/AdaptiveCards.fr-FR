---
title: Cartes adaptatives pour développeurs de bots
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: 1acc30c0347ea5527de2af1fe74e605c7589cbc6
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "59553281"
---
# <a name="adaptive-cards-for-bot-developers"></a>Cartes adaptatives pour développeurs de bots

Les cartes adaptatives conviennent parfaitement aux bots. Vous pouvez créer une carte une bonne fois pour toutes et la présenter dans différentes applications, comme Microsoft Teams, votre site web, etc.

> [!NOTE]
> Skype n'est pas pris en charge dans la préversion actuelle. Consultez la page [Statut partenaire](../resources/partners.md) pour accéder aux dernières informations.

## <a name="try-it-out"></a>Faire un essai

Cliquez sur le lien suivant et [parlez à notre Scuba Bot](http://contososcubademo.azurewebsites.net/). Dites `I'm looking for scuba` et il vous aidera à réserver le voyage de plongée de vos rêves.  

Toutes les réponses du bot sont créées à l'aide de cartes adaptatives.

[![Capture d'écran de la conversation de plongée](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Obtenez le code** : le [code source complet de Contoso Scuba Bot](https://github.com/matthidinger/ContosoScubaBot
) est disponible sur GitHub.


## <a name="bot-framework-integration"></a>Intégration de Bot Framework

[Bot Framework](https://dev.botframework.com/) vous permet de créer un bot capable de converser avec des utilisateurs sur plusieurs « canaux », comme Skype, Microsoft Teams, Facebook Messenger, etc.

## <a name="walkthrough"></a>Démonstration

L'ajout d'une carte adaptative à votre bot est très simple.

### <a name="step-0-start-with-a-basic-message"></a>Étape 0 : commencez avec un message de base

Voici une charge utile `message` d'un Bot Framework standard qui peut être transmise à n'importe quel canal et afficher du texte à l'utilisateur.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Étape 1 : ajoutez une carte adaptative `attachment`

Pour enrichir le contenu en plus du texte, le Bot Framework utilise le concept de `attachments`. 

Joignons une carte adaptative affichant du texte personnalisé.

![Carte adaptative de base](media/bots/hello-adaptivecards.png)

```json
{
  "type": "message",
  "text": "Plain text is ok, but sometimes I long for more...",
  "attachments": [
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "TextBlock",
            "text": "Hello World!",
            "size": "large"
          },
          {
            "type": "TextBlock",
            "text": "*Sincerely yours,*"
          },
          {
            "type": "TextBlock",
            "text": "Adaptive Cards",
            "separation": "none"
          }
        ],
        "actions": [
          {
            "type": "Action.OpenUrl",
            "url": "http://adaptivecards.io",
            "title": "Learn More"
          }
        ]
      }
    }
  ]
}
```

### <a name="step-2-build-even-richer-cards"></a>Étape 2 : créez des cartes encore plus riches 

Les cartes adaptatives offrent bien plus que du texte personnalisable. 

Vous pouvez : 

* Ajouter des `Images` à votre carte
* Organiser votre contenu avec des `Containers` et des `Columns`
* Ajouter différents types d'`Actions`
* Recueillir des `Input` auprès de vos utilisateurs
* Faire en sorte qu'une carte affiche une autre carte : `show another card`
* [Accédez à l'Explorateur de schémas complet](http://adaptivecards.io/explorer/) ! 

## <a name="platform-sdks"></a>Kits de développement logiciels (SDK) pour plateformes

Si vous développez votre bot via .NET ou NodeJS, nous disposons de bibliothèques pour faciliter la création de cartes adaptatives.

Plateforme|Installer|En savoir plus
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Documentation Bot Framework .NET](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Documentation Bot Framework NodeJS](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>État du canal

Bot Framework vous permet de publier votre bot sur différents canaux. Nous utilisons différents canaux pour fournir un support complet aux cartes adaptatives. Consultez la page [Statut partenaire](../resources/partners.md) pour accéder aux dernières informations.


## <a name="dive-in"></a>Lancez-vous !

Ce didacticiel ne fait qu'effleurer le sujet. Nous vous invitons donc à utiliser les liens ci-dessous pour en savoir plus sur l'amélioration de votre bot à l'aide de cartes adaptatives.

* [Parcourir des exemples de cartes](http://adaptivecards.io/samples/) pour trouver l'inspiration
* Utiliser l'[Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus sur les éléments disponibles
* Générer une carte à l'aide du [Visualiseur interactif](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Nous contacter](http://adaptivecards.io/connect) pour nous faire part de vos commentaires
