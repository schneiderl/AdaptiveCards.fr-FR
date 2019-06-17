---
title: Outils des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: ad520693224509deaf0ea1c2cd6a837089dbf2d5
ms.sourcegitcommit: e002a988c570072d5bc24a1242eaaac0c9ce90df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67137982"
---
# <a name="tools-and-samples"></a><span data-ttu-id="681f0-102">Outils et des exemples</span><span class="sxs-lookup"><span data-stu-id="681f0-102">Tools and Samples</span></span>

## <a name="card-designer"></a><span data-ttu-id="681f0-103">Concepteur de carte</span><span class="sxs-lookup"><span data-stu-id="681f0-103">Card Designer</span></span> 

<span data-ttu-id="681f0-104">Vous avez besoin d’un outil concevoir vos cartes ?</span><span class="sxs-lookup"><span data-stu-id="681f0-104">Need for a tool to design your cards?</span></span> <span data-ttu-id="681f0-105">Ne cherchez plus que le concepteur basée sur navigateur de carte adaptative à [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="681f0-105">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="681f0-106">[![capture d’écran de concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="681f0-106">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

### <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="681f0-107">Incorporer le concepteur dans votre application</span><span class="sxs-lookup"><span data-stu-id="681f0-107">Embed the designer into your app</span></span>

<span data-ttu-id="681f0-108">Mais pourquoi diriger vos utilisateurs il dès que possible **incorporer le Concepteur de carte directement dans votre site web** application à l’aide de notre bibliothèque JavaScript.</span><span class="sxs-lookup"><span data-stu-id="681f0-108">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="681f0-109">Découvrez le [adaptivecards-concepteur](https://npmjs.com/adaptivecards-designer) package pour commencer.</span><span class="sxs-lookup"><span data-stu-id="681f0-109">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

## <a name="schema-validation"></a><span data-ttu-id="681f0-110">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="681f0-110">Schema validation</span></span>

<span data-ttu-id="681f0-111">Validation de schéma constitue un moyen efficace de faire plus simple de création et l’activation des outils.</span><span class="sxs-lookup"><span data-stu-id="681f0-111">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

<span data-ttu-id="681f0-112">Nous avons fourni un complète [fichier de schéma JSON](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) pour l’édition et la validation des cartes adaptatives dans json.</span><span class="sxs-lookup"><span data-stu-id="681f0-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/1.2.0/adaptive-card.json) for editing and validating adaptive cards in json.</span></span> <span data-ttu-id="681f0-113">Notez que l’URL de schéma est créée, les versions plus récentes des cartes adaptatives aura une URL correspondante.</span><span class="sxs-lookup"><span data-stu-id="681f0-113">Note that the schema URL is versioned, newer versions of Adaptive Cards will have a corresponding URL.</span></span>

<span data-ttu-id="681f0-114">Dans Visual Studio et Visual Studio Code, vous pouvez obtenir Intellisense automatique en incluant un `$schema` référence.</span><span class="sxs-lookup"><span data-stu-id="681f0-114">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![bad](media/tools/invalidjson1.png)

![Saisie semi-automatique](media/tools/autocomplete.png)

## <a name="example"></a><span data-ttu-id="681f0-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="681f0-117">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

## <a name="visual-studio-code-extension"></a><span data-ttu-id="681f0-118">Extension de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="681f0-118">Visual Studio Code Extension</span></span>

<span data-ttu-id="681f0-119">Nous avons créé une extension de code de Visual Studio qui vous permet de visualiser la carte que vous modifiez en temps réel à l’intérieur de l’éditeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="681f0-119">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![extension](media/tools/vscode-extension.png)

<span data-ttu-id="681f0-121">Pour installer, ouvrez Extensions Marketplace et recherchez **ADAPTATIF visionneuse carte**.</span><span class="sxs-lookup"><span data-stu-id="681f0-121">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="681f0-123">Utilisation</span><span class="sxs-lookup"><span data-stu-id="681f0-123">Usage</span></span>

<span data-ttu-id="681f0-124">Lorsque vous modifiez un fichier .json avec une carte adaptative `$schema` propriété que vous pouvez afficher à l’aide de `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="681f0-124">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/1.2.0/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="681f0-125">Options</span><span class="sxs-lookup"><span data-stu-id="681f0-125">Options</span></span>

<span data-ttu-id="681f0-126">Le paramètre de Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="681f0-126">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="681f0-127">Cela peut être défini dans les paramètres de l’utilisateur ou de paramètres de l’espace de travail.</span><span class="sxs-lookup"><span data-stu-id="681f0-127">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="681f0-128">Visualiseur WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="681f0-128">WPF Visualizer Sample</span></span>

<span data-ttu-id="681f0-129">Le [exemple de projet WPF visualiseur](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser les cartes à l’aide de WPF/Xaml sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="681f0-129">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="681f0-130">Un `hostconfig` éditeur est intégré pour la modification et l’affichage des paramètres de configuration d’hôte.</span><span class="sxs-lookup"><span data-stu-id="681f0-130">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="681f0-131">Enregistrer ces paramètres en tant que JSON pour les utiliser dans un rendu dans votre application.</span><span class="sxs-lookup"><span data-stu-id="681f0-131">Save these settings as a JSON to use them in rendering in your application.</span></span>

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="681f0-133">WPF, exemple ImageRender</span><span class="sxs-lookup"><span data-stu-id="681f0-133">WPF ImageRender Sample</span></span>

<span data-ttu-id="681f0-134">Le [ImageRender exemple de projet](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) transforme n’importe quelle carte en un fichier PNG à partir de la ligne de commande à l’aide de WPF.</span><span class="sxs-lookup"><span data-stu-id="681f0-134">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
