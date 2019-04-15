---
title: Cartes adaptatives pour développeurs de robots
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: 1acc30c0347ea5527de2af1fe74e605c7589cbc6
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59553281"
---
# <a name="adaptive-cards-for-bot-developers"></a>Cartes adaptatives pour développeurs de robots

Des cartes adaptatives sont parfaits pour les robots. Elles vous permettent de créer une carte qu’une seule fois et de la rendre parfaitement à l’intérieur de plusieurs applications, comme Microsoft Teams, votre propre site Web et bien plus encore.

> [!NOTE]
> Skype n’est pas pris en charge dans la version préliminaire actuelle. Consultez le [statut de partenaire](../resources/partners.md) page pour la dernière version.

## <a name="try-it-out"></a>Faire un essai

Cliquez sur le lien suivant et [communiquer avec notre robot lance](http://contososcubademo.azurewebsites.net/). Par exemple `I'm looking for scuba` et il vous aiderons à réserver le voyage de prendre des cours de vos rêves.  

Toutes les réponses du robot sont créés avec des cartes adaptatives.

[![Capture d’écran de conversation de plan](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)

**Obtenir le code**: la version complète [Contoso lance Bot de code source](https://github.com/matthidinger/ContosoScubaBot
) trouverez sur GitHub.


## <a name="bot-framework-integration"></a>Intégration de Bot Framework

Avec le [Bot Framework](https://dev.botframework.com/) vous pouvez écrire un seul robot est en mesure de conversation avec des utilisateurs sur plusieurs « canaux », tels que Skype, Microsoft Teams, Facebook Messenger, etc.

## <a name="walkthrough"></a>Démonstration

Il est assez simple pour ajouter une carte adaptative à votre robot.

### <a name="step-0-start-with-a-basic-message"></a>Étape 0 : Démarrer avec un message de base

Voici un Bot Framework standard `message` charge utile qui peut être remis à n’importe quel canal et affiche le texte à l’utilisateur.

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a>Étape 1 : Ajouter une carte adaptative `attachment`

Pour ajouter une richesse au-delà uniquement le texte, Bot Framework a un concept de `attachments`. 

Nous allons attacher une carte adaptative qui affiche le texte personnalisé.

![Base carte adaptative](media/bots/hello-adaptivecards.png)

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

### <a name="step-2-build-even-richer-cards"></a>Étape 2 : Créer des cartes encore plus riches 

Des cartes adaptatives offrent beaucoup plus que simplement personnalisable texte. 

Vous pouvez : 

* Ajouter `Images` sur votre carte
* Organiser votre contenu avec `Containers` et `Columns`
* Ajouter plusieurs types de `Actions`
* Collecter `Input` à partir de vos utilisateurs
* Disposer d’une carte `show another card`
* [Découvrez l’Explorateur de schémas complète](http://adaptivecards.io/explorer/)! 

## <a name="platform-sdks"></a>Kits SDK de plateforme

Si votre robot est développé à l’aide de .NET ou Node.js, nous avons des bibliothèques à facilitent la création des cartes adaptatives encore plus facile.

Plateforme|Installation|En savoir plus
--------|-------|----------
.NET | `Install-Package AdaptiveCards -IncludePrerelease` | [Documentation de .NET Framework Bot](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
NodeJS | `npm install adaptivecards` | [Bot Framework NodeJS Docs](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a>État du canal

Le Bot Framework vous permet de publier votre robot à plusieurs canaux. Nous travaillons avec différents canaux pour fournir une prise en charge complète pour des cartes adaptatives. Consultez le [statut de partenaire](../resources/partners.md) page pour la dernière version.


## <a name="dive-in"></a>Foncez !

Nous avons fait que gratter la surface dans ce didacticiel, donc Veuillez jetez un coup de œil sur les liens ci-dessous pour découvrir des façons plus que des cartes adaptatives peut améliorer votre robot.

* [Parcourir les cartes d’exemple](http://adaptivecards.io/samples/) d’inspiration
* Utilisez le [Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus les éléments disponibles
* Générer une carte à l’aide de la [visualiseur Interactive](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)
* [Nous contacter](http://adaptivecards.io/connect) avec vos commentaires
