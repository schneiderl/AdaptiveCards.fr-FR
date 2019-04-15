---
title: Outils des cartes adaptatives
author: matthidinger
ms.author: mahiding
ms.date: 03/14/2019
ms.topic: article
ms.openlocfilehash: 35ce89653a6cf2a313518be0f221a166e1eb7711
ms.sourcegitcommit: 99c7b64d6fc66da336c454951406fb42cd2a7427
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59552501"
---
# <a name="card-designer"></a><span data-ttu-id="5e836-102">Concepteur de carte</span><span class="sxs-lookup"><span data-stu-id="5e836-102">Card Designer</span></span> 

<span data-ttu-id="5e836-103">Vous avez besoin d’un outil concevoir vos cartes ?</span><span class="sxs-lookup"><span data-stu-id="5e836-103">Need for a tool to design your cards?</span></span> <span data-ttu-id="5e836-104">Ne cherchez plus que le concepteur basée sur navigateur de carte adaptative à [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="5e836-104">Look no further than the browser-based adaptive card designer at [https://adaptivecards.io/designer](https://adaptivecards.io/designer)</span></span>

<span data-ttu-id="5e836-105">[![capture d’écran de concepteur](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span><span class="sxs-lookup"><span data-stu-id="5e836-105">[![designer screenshot](media/tools/designer.jpg)](https://adaptivecards.io/designer)</span></span>

## <a name="embed-the-designer-into-your-app"></a><span data-ttu-id="5e836-106">Incorporer le concepteur dans votre application</span><span class="sxs-lookup"><span data-stu-id="5e836-106">Embed the designer into your app</span></span>

<span data-ttu-id="5e836-107">Mais pourquoi diriger vos utilisateurs il dès que possible **incorporer le Concepteur de carte directement dans votre site web** application à l’aide de notre bibliothèque JavaScript.</span><span class="sxs-lookup"><span data-stu-id="5e836-107">But why send your users there when you can **embed the card designer directly into your web** app using our JavaScript library.</span></span> 

<span data-ttu-id="5e836-108">Découvrez le [adaptivecards-concepteur](https://npmjs.com/adaptivecards-designer) package pour commencer.</span><span class="sxs-lookup"><span data-stu-id="5e836-108">Check out the [adaptivecards-designer](https://npmjs.com/adaptivecards-designer) package to get started.</span></span>

# <a name="schema-validation"></a><span data-ttu-id="5e836-109">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="5e836-109">Schema validation</span></span>

<span data-ttu-id="5e836-110">Validation de schéma constitue un moyen efficace de faire plus simple de création et l’activation des outils.</span><span class="sxs-lookup"><span data-stu-id="5e836-110">Schema validation is a powerful way of making authoring easier and enabling tooling.</span></span>

## <a name="json-schema"></a><span data-ttu-id="5e836-111">JSON Schema</span><span class="sxs-lookup"><span data-stu-id="5e836-111">JSON Schema</span></span>
<span data-ttu-id="5e836-112">Nous avons fourni un complète [fichier de schéma JSON](http://adaptivecards.io/schemas/adaptive-card.json) pour l’édition et la validation des cartes adaptatives dans json.</span><span class="sxs-lookup"><span data-stu-id="5e836-112">We have provided a complete [JSON Schema file](http://adaptivecards.io/schemas/adaptive-card.json) for editing and validating adaptive cards in json.</span></span>

<span data-ttu-id="5e836-113">Dans Visual Studio et Visual Studio Code, vous pouvez obtenir Intellisense automatique en incluant un `$schema` référence.</span><span class="sxs-lookup"><span data-stu-id="5e836-113">In Visual Studio and Visual Studio Code you can get automatic Intellisense by including a `$schema` reference.</span></span>

![bad](media/tools/invalidjson1.png)

![Saisie semi-automatique](media/tools/autocomplete.png)

### <a name="example"></a><span data-ttu-id="5e836-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e836-116">Example</span></span>

```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "0.5",
    "body": []
}
```

# <a name="tools-and-samples"></a><span data-ttu-id="5e836-117">Outils et exemples</span><span class="sxs-lookup"><span data-stu-id="5e836-117">Tools and samples</span></span>
<span data-ttu-id="5e836-118">Il existe certains outils et des exemples dans l’arborescence source qui sont des références utiles, ainsi que des outils utiles.</span><span class="sxs-lookup"><span data-stu-id="5e836-118">There are some tools and samples in the source tree which are useful references as well as useful tools.</span></span>

## <a name="visual-studio-code-extension"></a><span data-ttu-id="5e836-119">Extension de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5e836-119">Visual Studio Code Extension</span></span>
<span data-ttu-id="5e836-120">Nous avons créé une extension de code de Visual Studio qui vous permet de visualiser la carte que vous modifiez en temps réel à l’intérieur de l’éditeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="5e836-120">We have created a Visual Studio code extension which allows you to visualize the card you are editing in real time inside the editor itself.</span></span> 

![extension](media/tools/vscode-extension.png)

<span data-ttu-id="5e836-122">Pour installer, ouvrez Extensions Marketplace et recherchez **ADAPTATIF visionneuse carte**.</span><span class="sxs-lookup"><span data-stu-id="5e836-122">To install, open Extensions Marketplace and search for **Adaptive Card Viewer**.</span></span>

![marketplace](media/tools/vscode-extension-marketplace.png)

### <a name="usage"></a><span data-ttu-id="5e836-124">Utilisation</span><span class="sxs-lookup"><span data-stu-id="5e836-124">Usage</span></span>

<span data-ttu-id="5e836-125">Lorsque vous modifiez un fichier .json avec une carte adaptative `$schema` propriété que vous pouvez afficher à l’aide de `Ctrl+Shift+V A`.</span><span class="sxs-lookup"><span data-stu-id="5e836-125">When you are editing a .json file with an Adaptive Card `$schema` property you can view by using `Ctrl+Shift+V A`.</span></span>
```json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": []
}
```

### <a name="options"></a><span data-ttu-id="5e836-126">Options</span><span class="sxs-lookup"><span data-stu-id="5e836-126">Options</span></span>

<span data-ttu-id="5e836-127">Le paramètre de Visual Studio Code suivant est disponible pour la visionneuse AdaptiveCards.</span><span class="sxs-lookup"><span data-stu-id="5e836-127">The following Visual Studio Code setting is available for the AdaptiveCards Viewer.</span></span> <span data-ttu-id="5e836-128">Cela peut être défini dans les paramètres de l’utilisateur ou de paramètres de l’espace de travail.</span><span class="sxs-lookup"><span data-stu-id="5e836-128">This can be set in User Settings or Workspace Settings.</span></span>

```js
{
    // Open or not open the preview screen automatically
    "adaptivecardsviewer.enableautopreview": true,
}
```

## <a name="wpf-visualizer-sample"></a><span data-ttu-id="5e836-129">Visualiseur WPF, exemple</span><span class="sxs-lookup"><span data-stu-id="5e836-129">WPF Visualizer Sample</span></span>
<span data-ttu-id="5e836-130">Le [exemple de projet WPF visualiseur](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) vous permet de visualiser les cartes à l’aide de WPF/Xaml sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="5e836-130">The [WPF visualizer sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/WPFVisualizer) lets you visualize cards using WPF/Xaml on a Windows machine.</span></span>  <span data-ttu-id="5e836-131">Un `hostconfig` éditeur est intégré pour la modification et l’affichage des paramètres de configuration d’hôte.</span><span class="sxs-lookup"><span data-stu-id="5e836-131">A `hostconfig` editor is built in for editing and viewing host config settings.</span></span> <span data-ttu-id="5e836-132">Enregistrer ces paramètres en tant que JSON pour les utiliser dans un rendu dans votre application.</span><span class="sxs-lookup"><span data-stu-id="5e836-132">Save these settings as a JSON to use them in rendering in your application.</span></span>

![visualiseur WPF](media/tools/wpfvisualizer.png)

## <a name="wpf-imagerender-sample"></a><span data-ttu-id="5e836-134">WPF, exemple ImageRender</span><span class="sxs-lookup"><span data-stu-id="5e836-134">WPF ImageRender Sample</span></span>
<span data-ttu-id="5e836-135">Le [ImageRender exemple de projet](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) transforme n’importe quelle carte en un fichier PNG à partir de la ligne de commande à l’aide de WPF.</span><span class="sxs-lookup"><span data-stu-id="5e836-135">The [ImageRender sample project](https://github.com/Microsoft/AdaptiveCards/tree/master/source/dotnet/Samples/AdaptiveCards.Sample.ImageRender) turns any card into a PNG from the command line using WPF.</span></span> 
