---
title: Cartes adaptatives pour développeurs de bots
author: matthidinger
ms.author: mahiding
ms.date: 05/30/2018
ms.topic: article
ms.openlocfilehash: e460bf50cdb4f0c1af54f5c7ad6c1d02db9af746
ms.sourcegitcommit: fec0fd2c23293127e8e8f7ca7821c04d46987f37
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86417494"
---
# <a name="adaptive-cards-for-bot-developers"></a><span data-ttu-id="d63d5-102">Cartes adaptatives pour développeurs de bots</span><span class="sxs-lookup"><span data-stu-id="d63d5-102">Adaptive Cards for Bot Developers</span></span>

<span data-ttu-id="d63d5-103">Les cartes adaptatives conviennent parfaitement aux bots.</span><span class="sxs-lookup"><span data-stu-id="d63d5-103">Adaptive Cards are a great fit for Bots.</span></span> <span data-ttu-id="d63d5-104">Vous pouvez créer une carte une bonne fois pour toutes et la présenter dans différentes applications, comme Microsoft Teams, votre site web, etc.</span><span class="sxs-lookup"><span data-stu-id="d63d5-104">They let you author a card once and have it render beautifully inside multiple apps, like  Microsoft Teams, your own website, and more.</span></span>

> [!NOTE]
> <span data-ttu-id="d63d5-105">Skype n'est pas pris en charge dans la préversion actuelle.</span><span class="sxs-lookup"><span data-stu-id="d63d5-105">Skype is not supported in the current preview.</span></span> <span data-ttu-id="d63d5-106">Consultez la page [Statut partenaire](../resources/partners.md) pour accéder aux dernières informations.</span><span class="sxs-lookup"><span data-stu-id="d63d5-106">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>

## <a name="try-it-out"></a><span data-ttu-id="d63d5-107">Essayer MSIX</span><span class="sxs-lookup"><span data-stu-id="d63d5-107">Try it out</span></span>

<span data-ttu-id="d63d5-108">Cliquez sur le lien suivant et [parlez à notre Scuba Bot](http://contososcubademo.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="d63d5-108">Click the following link and [talk to our Scuba Bot](http://contososcubademo.azurewebsites.net/).</span></span> <span data-ttu-id="d63d5-109">Dites `I'm looking for scuba` et il vous aidera à réserver le voyage de plongée de vos rêves.</span><span class="sxs-lookup"><span data-stu-id="d63d5-109">Say `I'm looking for scuba` and it'll help you book the scuba trip of your dreams.</span></span>  

<span data-ttu-id="d63d5-110">Toutes les réponses du bot sont créées à l'aide de cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="d63d5-110">All of the bot's responses are created with Adaptive Cards.</span></span>

<span data-ttu-id="d63d5-111">[![Capture d'écran de la conversation de plongée](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span><span class="sxs-lookup"><span data-stu-id="d63d5-111">[![Scuba chat screenshot](media/bots/scuba-chat.png)](http://contososcubademo.azurewebsites.net/)</span></span>

<span data-ttu-id="d63d5-112">**Obtenez le code** : le [code source complet de Contoso Scuba Bot](https://github.com/matthidinger/ContosoScubaBot
) est disponible sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="d63d5-112">**Get the code**: the full [Contoso Scuba Bot source code](https://github.com/matthidinger/ContosoScubaBot
) can be found on GitHub.</span></span>


## <a name="bot-framework-integration"></a><span data-ttu-id="d63d5-113">Intégration de Bot Framework</span><span class="sxs-lookup"><span data-stu-id="d63d5-113">Bot Framework Integration</span></span>

<span data-ttu-id="d63d5-114">[Bot Framework](https://dev.botframework.com/) vous permet de créer un bot capable de converser avec des utilisateurs sur plusieurs « canaux », comme Skype, Microsoft Teams, Facebook Messenger, etc.</span><span class="sxs-lookup"><span data-stu-id="d63d5-114">With the [Bot Framework](https://dev.botframework.com/) you can write a single bot that is able to chat with users across multiple "channels", like Skype, Microsoft Teams, Facebook Messenger, etc.</span></span>

## <a name="walkthrough"></a><span data-ttu-id="d63d5-115">Démonstration</span><span class="sxs-lookup"><span data-stu-id="d63d5-115">Walkthrough</span></span>

<span data-ttu-id="d63d5-116">L'ajout d'une carte adaptative à votre bot est très simple.</span><span class="sxs-lookup"><span data-stu-id="d63d5-116">It's pretty straight forward to add an Adaptive Card to your bot.</span></span>

### <a name="step-0-start-with-a-basic-message"></a><span data-ttu-id="d63d5-117">Étape 0 : commencez avec un message de base</span><span class="sxs-lookup"><span data-stu-id="d63d5-117">Step 0: Start with a basic message</span></span>

<span data-ttu-id="d63d5-118">Voici une charge utile `message` d'un Bot Framework standard qui peut être transmise à n'importe quel canal et afficher du texte à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d63d5-118">Here's a standard Bot Framework `message` payload that can be delivered to any channel and display text to the user.</span></span>

```json
{
   "type": "message",
   "text": "Plain text is ok, but sometimes I long for more..."
}
```

### <a name="step-1-add-an-adaptive-card-attachment"></a><span data-ttu-id="d63d5-119">Étape 1 : ajoutez une carte adaptative `attachment`</span><span class="sxs-lookup"><span data-stu-id="d63d5-119">Step 1: Add an Adaptive Card `attachment`</span></span>

<span data-ttu-id="d63d5-120">Pour enrichir le contenu en plus du texte, le Bot Framework utilise le concept de `attachments`.</span><span class="sxs-lookup"><span data-stu-id="d63d5-120">To add some richness beyond just text, the Bot Framework has a concept of `attachments`.</span></span> 

<span data-ttu-id="d63d5-121">Joignons une carte adaptative affichant du texte personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d63d5-121">Let's attach an Adaptive Card that displays custom text.</span></span>

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

### <a name="step-2-build-even-richer-cards"></a><span data-ttu-id="d63d5-123">Étape 2 : créez des cartes encore plus riches</span><span class="sxs-lookup"><span data-stu-id="d63d5-123">Step 2: Build even richer cards</span></span> 

<span data-ttu-id="d63d5-124">Les cartes adaptatives offrent bien plus que du texte personnalisable.</span><span class="sxs-lookup"><span data-stu-id="d63d5-124">Adaptive Cards offer much more than just customizable text.</span></span> 

<span data-ttu-id="d63d5-125">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="d63d5-125">You can:</span></span> 

* <span data-ttu-id="d63d5-126">Ajouter des `Images` à votre carte</span><span class="sxs-lookup"><span data-stu-id="d63d5-126">Add `Images` to your card</span></span>
* <span data-ttu-id="d63d5-127">Organiser votre contenu avec des `Containers` et des `Columns`</span><span class="sxs-lookup"><span data-stu-id="d63d5-127">Organize your content with `Containers` and `Columns`</span></span>
* <span data-ttu-id="d63d5-128">Ajouter différents types d'`Actions`</span><span class="sxs-lookup"><span data-stu-id="d63d5-128">Add multiple types of `Actions`</span></span>
* <span data-ttu-id="d63d5-129">Recueillir des `Input` auprès de vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d63d5-129">Collect `Input` from your users</span></span>
* <span data-ttu-id="d63d5-130">Faire en sorte qu'une carte affiche une autre carte : `show another card`</span><span class="sxs-lookup"><span data-stu-id="d63d5-130">Have one card `show another card`</span></span>
* <span data-ttu-id="d63d5-131">[Accédez à l'Explorateur de schémas complet](https://adaptivecards.io/explorer/) !</span><span class="sxs-lookup"><span data-stu-id="d63d5-131">[Check out the full schema explorer](https://adaptivecards.io/explorer/)!</span></span> 

## <a name="platform-sdks"></a><span data-ttu-id="d63d5-132">Kits de développement logiciels (SDK) pour plateformes</span><span class="sxs-lookup"><span data-stu-id="d63d5-132">Platform SDKs</span></span>

<span data-ttu-id="d63d5-133">Si vous développez votre bot via .NET ou NodeJS, nous disposons de bibliothèques pour faciliter la création de cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="d63d5-133">If your bot is developed using .NET or NodeJS we have libraries to make building Adaptive Cards even easier.</span></span>

<span data-ttu-id="d63d5-134">Plate-forme</span><span class="sxs-lookup"><span data-stu-id="d63d5-134">Platform</span></span>|<span data-ttu-id="d63d5-135">Installer</span><span class="sxs-lookup"><span data-stu-id="d63d5-135">Install</span></span>|<span data-ttu-id="d63d5-136">Pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="d63d5-136">Learn more</span></span>
--------|-------|----------
<span data-ttu-id="d63d5-137">.NET</span><span class="sxs-lookup"><span data-stu-id="d63d5-137">.NET</span></span> | `Install-Package AdaptiveCards -IncludePrerelease` | [<span data-ttu-id="d63d5-138">Documentation Bot Framework .NET</span><span class="sxs-lookup"><span data-stu-id="d63d5-138">Bot Framework .NET Docs</span></span>](https://docs.microsoft.com/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
<span data-ttu-id="d63d5-139">NodeJS</span><span class="sxs-lookup"><span data-stu-id="d63d5-139">NodeJS</span></span> | `npm install adaptivecards` | [<span data-ttu-id="d63d5-140">Documentation Bot Framework NodeJS</span><span class="sxs-lookup"><span data-stu-id="d63d5-140">Bot Framework NodeJS Docs</span></span>](https://docs.microsoft.com/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)


## <a name="channel-status"></a><span data-ttu-id="d63d5-141">État du canal</span><span class="sxs-lookup"><span data-stu-id="d63d5-141">Channel status</span></span>

<span data-ttu-id="d63d5-142">Bot Framework vous permet de publier votre bot sur différents canaux.</span><span class="sxs-lookup"><span data-stu-id="d63d5-142">The Bot Framework lets you publish your bot to multiple channels.</span></span> <span data-ttu-id="d63d5-143">Nous utilisons différents canaux pour fournir un support complet aux cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="d63d5-143">We're working with various channels to provide full support for Adaptive Cards.</span></span> <span data-ttu-id="d63d5-144">Consultez la page [Statut partenaire](../resources/partners.md) pour accéder aux dernières informations.</span><span class="sxs-lookup"><span data-stu-id="d63d5-144">See the [Partner Status](../resources/partners.md) page for the latest.</span></span>


## <a name="dive-in"></a><span data-ttu-id="d63d5-145">Lancez-vous !</span><span class="sxs-lookup"><span data-stu-id="d63d5-145">Dive in!</span></span>

<span data-ttu-id="d63d5-146">Ce didacticiel ne fait qu'effleurer le sujet. Nous vous invitons donc à utiliser les liens ci-dessous pour en savoir plus sur l'amélioration de votre bot à l'aide de cartes adaptatives.</span><span class="sxs-lookup"><span data-stu-id="d63d5-146">We've just scratched the surface in this tutorial, so please take a look at the links below to explore more ways that Adaptive Cards can enhance your bot.</span></span>

* <span data-ttu-id="d63d5-147">[Parcourir des exemples de cartes](https://adaptivecards.io/samples/) pour trouver l'inspiration</span><span class="sxs-lookup"><span data-stu-id="d63d5-147">[Browse Sample cards](https://adaptivecards.io/samples/) for inspiration</span></span>
* <span data-ttu-id="d63d5-148">Utiliser l'[Explorateur de schémas](https://adaptivecards.io/explorer) pour en savoir plus sur les éléments disponibles</span><span class="sxs-lookup"><span data-stu-id="d63d5-148">Use the [Schema Explorer](https://adaptivecards.io/explorer) to learn the available elements</span></span>
* <span data-ttu-id="d63d5-149">Générer une carte à l'aide du [Visualiseur interactif](https://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span><span class="sxs-lookup"><span data-stu-id="d63d5-149">Build a card using the [Interactive Visualizer](https://adaptivecards.io/visualizer/index.html?hostApp=Skype)</span></span>
* <span data-ttu-id="d63d5-150">[Nous contacter](https://adaptivecards.io/connect) pour nous faire part de vos commentaires</span><span class="sxs-lookup"><span data-stu-id="d63d5-150">[Get in touch](https://adaptivecards.io/connect) with any feedback you have</span></span>
