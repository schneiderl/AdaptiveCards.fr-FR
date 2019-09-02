---
title: Outils de cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: ad520693224509deaf0ea1c2cd6a837089dbf2d5
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137982"
---
# <a name="tools-and-samples"></a><span data-ttu-id="3b4d1-102">Outils et exemples</span><span class="sxs-lookup"><span data-stu-id="3b4d1-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="3b4d1-103">Concepteur de cartes</span><span class="sxs-lookup"><span data-stu-id="3b4d1-103">Card Designer</span></span> 

<span data-ttu-id="3b4d1-104">Vous avez besoin d’un outil pour concevoir vos cartes ?</span><span class="sxs-lookup"><span data-stu-id="3b4d1-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="3b4d1-105">Ne cherchez pas plus loin. Sur [https://adaptivecards.io/designer](https://adaptivecards.io/designer), vous trouverez un concepteur de cartes adaptatives basé sur le navigateur.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="3b4d1-106">[![capture d’écran du concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="3b4d1-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="3b4d1-107">Incorporer le concepteur dans votre application</span><span class="sxs-lookup"><span data-stu-id="3b4d1-107">Embed the designer into your app</span></span>

<span data-ttu-id="3b4d1-108">Mais pourquoi y envoyer vos utilisateurs quand vous pouvez **incorporer le concepteur de cartes directement dans votre application web** à l’aide de notre bibliothèque JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="3b4d1-109">Pour bien démarrer, consultez le [package adaptivecards-designer](https://npmjs.com/adaptivecards-designer).</span><span class="sxs-lookup"><span data-stu-id="3b4d1-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="3b4d1-110">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="3b4d1-110">Schema validation</span></span>

<span data-ttu-id="3b4d1-111">La validation de schéma est un excellent moyen de simplifier la création d’outils.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="3b4d1-112">Nous mettons à votre disposition un [fichier de schéma JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) complet pour la modification et la validation des cartes adaptatives dans JSON.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="3b4d1-113">Notez que l’URL de schéma a une version spécifique. Les versions plus récentes des cartes adaptatives auront une URL correspondante.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="3b4d1-114">Dans Visual Studio et Visual Studio Code, vous pouvez obtenir une fonctionnalité IntelliSense automatique en incluant une référence `$schema`.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![incorrect](media/tools/invalidjson1.png)

![complétion automatique](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="3b4d1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b4d1-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="3b4d1-118">Extension Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3b4d1-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="3b4d1-119">Nous avons créé une extension Visual Studio Code qui vous permet de visualiser la carte que vous modifiez en temps réel dans l’éditeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![extension](media/tools/vscode-extension.png)

<span data-ttu-id="3b4d1-121">Pour l’installer, ouvrez la Place de marché des extensions et recherchez **Adaptive Card Viewer**.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![place de marché](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="3b4d1-123">Utilisation</span><span class="sxs-lookup"><span data-stu-id="3b4d1-123">Usage</span></span>

<span data-ttu-id="3b4d1-124">Quand vous modifiez un fichier .json avec une propriété `$schema` de carte adaptative, vous pouvez la voir à l’aide de `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="3b4d1-125">Options</span><span class="sxs-lookup"><span data-stu-id="3b4d1-125">Options</span></span>

<span data-ttu-id="3b4d1-126">Le paramètre Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="3b4d1-127">Vous pouvez le définir dans les paramètres utilisateur ou dans les paramètres de l’espace de travail.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="3b4d1-128">Exemple de visualiseur WPF</span><span class="sxs-lookup"><span data-stu-id="3b4d1-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="3b4d1-129">L’[exemple de projet de visualiseur WPF](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser des cartes à l’aide de WPF/XAML sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="3b4d1-130">Un éditeur `hostconfig` est intégré pour modifier et voir les paramètres de configuration de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="3b4d1-131">Enregistrez ces paramètres au format JSON pour les utiliser dans le cadre du rendu de votre application.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="3b4d1-133">Exemple ImageRender WPF</span><span class="sxs-lookup"><span data-stu-id="3b4d1-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="3b4d1-134">L’[exemple de projet ImageRender](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) convertit n’importe quelle carte au format PNG à partir de la ligne de commande à l’aide de WPF.</span><span class="sxs-lookup"><span data-stu-id="3b4d1-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
