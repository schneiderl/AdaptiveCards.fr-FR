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
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="97683-102">Cartes adaptatives pour développeurs de robots</span><span class="sxs-lookup"><span data-stu-id="97683-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="97683-103">Des cartes adaptatives sont parfaits pour les robots.</span><span class="sxs-lookup"><span data-stu-id="97683-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="97683-104">Elles vous permettent de créer une carte qu’une seule fois et de la rendre parfaitement à l’intérieur de plusieurs applications, comme Microsoft Teams, votre propre site Web et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="97683-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="97683-105">Skype n’est pas pris en charge dans la version préliminaire actuelle.</span><span class="sxs-lookup"><span data-stu-id="97683-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="97683-106">Consultez le [statut de partenaire](../resources/partners.md) page pour la dernière version.</span><span class="sxs-lookup"><span data-stu-id="97683-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="97683-107">Faire un essai</span><span class="sxs-lookup"><span data-stu-id="97683-107">Try it out</span></span>

<span data-ttu-id="97683-108">Cliquez sur le lien suivant et [communiquer avec notre robot lance](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="97683-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="97683-109">Par exemple `I'm looking for scuba` et il vous aiderons à réserver le voyage de prendre des cours de vos rêves.</span><span class="sxs-lookup"><span data-stu-id="97683-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="97683-110">Toutes les réponses du robot sont créés avec des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="97683-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="97683-111">[![Capture d’écran de conversation de plan](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="97683-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="97683-112">**Obtenir le code**: la version complète [Contoso lance Bot de code source](https://github.com/matthidinger/ContosoScubaBot
) trouverez sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="97683-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="97683-113">Intégration de Bot Framework</span><span class="sxs-lookup"><span data-stu-id="97683-113">Bot Framework Integration</span></span>

<span data-ttu-id="97683-114">Avec le [Bot Framework](https://dev.botframework.com/) vous pouvez écrire un seul robot est en mesure de conversation avec des utilisateurs sur plusieurs « canaux », tels que Skype, Microsoft Teams, Facebook Messenger, etc.</span><span class="sxs-lookup"><span data-stu-id="97683-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="97683-115">Démonstration</span><span class="sxs-lookup"><span data-stu-id="97683-115">Walkthrough</span></span>

<span data-ttu-id="97683-116">Il est assez simple pour ajouter une carte adaptative à votre robot.</span><span class="sxs-lookup"><span data-stu-id="97683-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="97683-117">Étape 0 : Démarrer avec un message de base</span><span class="sxs-lookup"><span data-stu-id="97683-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="97683-118">Voici un Bot Framework standard `message` charge utile qui peut être remis à n’importe quel canal et affiche le texte à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="97683-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="97683-119">Étape 1 : Ajouter une carte adaptative `attachment`</span><span class="sxs-lookup"><span data-stu-id="97683-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="97683-120">Pour ajouter une richesse au-delà uniquement le texte, Bot Framework a un concept de `attachments`.</span><span class="sxs-lookup"><span data-stu-id="97683-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="97683-121">Nous allons attacher une carte adaptative qui affiche le texte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="97683-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="97683-123">Étape 2 : Créer des cartes encore plus riches</span><span class="sxs-lookup"><span data-stu-id="97683-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="97683-124">Des cartes adaptatives offrent beaucoup plus que simplement personnalisable texte.</span><span class="sxs-lookup"><span data-stu-id="97683-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="97683-125">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="97683-125">You can:</span></span> 

* <span data-ttu-id="97683-126">Ajouter `Images` sur votre carte</span><span class="sxs-lookup"><span data-stu-id="97683-126">Add `Images` to your card</span></span>
* <span data-ttu-id="97683-127">Organiser votre contenu avec `Containers` et `Columns`</span><span class="sxs-lookup"><span data-stu-id="97683-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="97683-128">Ajouter plusieurs types de `Actions`</span><span class="sxs-lookup"><span data-stu-id="97683-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="97683-129">Collecter `Input` à partir de vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="97683-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="97683-130">Disposer d’une carte `show another card`</span><span class="sxs-lookup"><span data-stu-id="97683-130">Have one card `show another card`</span></span>
* <span data-ttu-id="97683-131">[Découvrez l’Explorateur de schémas complète](http://adaptivecards.io/explorer/)!</span><span class="sxs-lookup"><span data-stu-id="97683-131">[Check out the full schema explorer](http://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="97683-132">Kits SDK de plateforme</span><span class="sxs-lookup"><span data-stu-id="97683-132">Platform SDKs</span></span>

<span data-ttu-id="97683-133">Si votre robot est développé à l’aide de .NET ou Node.js, nous avons des bibliothèques à facilitent la création des cartes adaptatives encore plus facile.</span><span class="sxs-lookup"><span data-stu-id="97683-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="97683-134">Plateforme</span><span class="sxs-lookup"><span data-stu-id="97683-134">Platform</span></span>|<span data-ttu-id="97683-135">Installation</span><span class="sxs-lookup"><span data-stu-id="97683-135">Install</span></span>|<span data-ttu-id="97683-136">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="97683-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="97683-137">.NET</span><span class="sxs-lookup"><span data-stu-id="97683-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="97683-138">Documentation de .NET Framework Bot</span><span class="sxs-lookup"><span data-stu-id="97683-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="97683-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="97683-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="97683-140">Bot Framework NodeJS Docs</span><span class="sxs-lookup"><span data-stu-id="97683-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/en-us/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="97683-141">État du canal</span><span class="sxs-lookup"><span data-stu-id="97683-141">Channel status</span></span>

<span data-ttu-id="97683-142">Le Bot Framework vous permet de publier votre robot à plusieurs canaux.</span><span class="sxs-lookup"><span data-stu-id="97683-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="97683-143">Nous travaillons avec différents canaux pour fournir une prise en charge complète pour des cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="97683-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="97683-144">Consultez le [statut de partenaire](../resources/partners.md) page pour la dernière version.</span><span class="sxs-lookup"><span data-stu-id="97683-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="97683-145">Foncez !</span><span class="sxs-lookup"><span data-stu-id="97683-145">Dive in!</span></span>

<span data-ttu-id="97683-146">Nous avons fait que gratter la surface dans ce didacticiel, donc Veuillez jetez un coup de œil sur les liens ci-dessous pour découvrir des façons plus que des cartes adaptatives peut améliorer votre robot.</span><span class="sxs-lookup"><span data-stu-id="97683-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="97683-147">[Parcourir les cartes d’exemple](http://adaptivecards.io/samples/) d’inspiration</span><span class="sxs-lookup"><span data-stu-id="97683-147">[Browse Sample cards](http://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="97683-148">Utilisez le [Explorateur de schémas](http://adaptivecards.io/explorer) pour en savoir plus les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="97683-148">Use the [Schema Explorer](http://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="97683-149">Générer une carte à l’aide de la [visualiseur Interactive](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="97683-149">Build a card using the [Interactive Visualizer](http://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="97683-150">[Nous contacter](http://adaptivecards.io/connect) avec vos commentaires</span><span class="sxs-lookup"><span data-stu-id="97683-150">[Get in touch](http://adaptivecards.io/connect) with any feedback you have</span></span>
